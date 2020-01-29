<template>
  <b-container>
    <b-row>
      <b-col lg="6" class="my-1">
        <b-form-group label="Filter" label-cols-sm="3" label-align-sm="left" label-size="sm" label-for="filterInput" class="mb-0">
          <b-input-group size="sm">
            <b-form-input v-model="filter" type="search" id="filterInput" placeholder="Type to Search"></b-form-input>
            <b-input-group-append>
              <b-button :disabled="!filter" @click="filter = ''">Clear</b-button>
            </b-input-group-append>
          </b-input-group>
        </b-form-group>
      </b-col>

      <b-col lg="6" class="my-1">
        <b-form-group label="Filter On" label-cols-sm="3" label-align-sm="right" label-size="sm" description="Leave all unchecked to filter on all data" class="mb-0">
          <b-form-checkbox-group v-model="filterOn" class="mt-1">
            <b-form-checkbox value="host">Host</b-form-checkbox>
            <b-form-checkbox value="message">Messgae</b-form-checkbox>
            <b-form-checkbox value="time">Time</b-form-checkbox>
          </b-form-checkbox-group>
        </b-form-group>
      </b-col>
    </b-row>
    <b-row>
      <b-col lg="12" class="my-1">
        <b-table striped hover :items="items" :fields="fields" :filter="filter" :filterIncludedFields="filterOn"></b-table>

        <download-excel class="btn btn-secondary" :data="items" type="csv" worksheet="My Worksheet" name="filename.xls">
          Export Data
        </download-excel>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
  export default {
    data() {
      return {
        dataToExport: [],
        fields: [{
            key: 'host',
            label: 'Host',
            sortable: true
          },
          {
            key: 'message',
            label: 'Message',
            sortable: true
          },
          {
            key: 'time',
            label: 'Time',
            sortable: true
          }
        ],
        filter: null,
        filterOn: [],
        items: [{
            host: "bSYSABRU2K03",
            message: "HEARTBEAT 30",
            time: "15:09"
          },
          {
            host: "bSYSABRU2K03",
            message: "INV/WF/J01 (531/531) Waiting on A",
            time: "14:35"
          },
          {
            host: "bSYSABRU2K03",
            message: "HEARTBEAT 30",
            time: "15:11"
          },
          {
            host: "bSYSABRU2K14",
            message: "(DBA)BDOM/messageEXCHANGE/DMSIIAGENT",
            time: "14:53"
          },
          {
            host: "bSYSABRU2K14",
            message: "(CIRM2)IRM/PO/209 (6207/2504) Dse",
            time: "14:30"
          },
          {
            host: "bSYSABRU2K14",
            message: "(DBA)BDOM/messageEXCHANGE/DMSIIAGENT",
            time: "14:22"
          },
          {
            host: "bSYSABRU2K14",
            message: "(CIRM2)IRM/PO/710 (6207/6339) Wai",
            time: "14:20"
          },
          {
            host: "bSYSABRU2K14",
            message: "(CIRM2)IRM/PO/209 (6207/1366) Dse",
            time: "14:13"
          },
          {
            host: "bSYSABRU2K14",
            message: "(DBA)BDOM/messageEXCHANGE/DMSIIAGENT",
            time: "13:52"
          },
          {
            host: "bSYSABRU2K14",
            message: "(DBA)BDOM/messageEXCHANGE/DMSIIAGENT",
            time: "13:22"
          },
          {
            host: "bSYSABRU2K14",
            message: "(BBLP)ICH/PO/908 (974/974) Dsed o",
            time: "13:21"
          }
        ]
      }
    },
    computed: {
      sortOptions() {
        return this.fields
          .filter(f => f.sortable)
          .map(f => {
            return {
              text: f.label,
              value: f.key
            }
          })
      }
    },
  }
</script>
