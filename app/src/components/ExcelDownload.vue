<template>
    <div class="result-table">
      <b-table striped hover bordered :items="items"></b-table>

        <download-excel
            class="btn btn-default"
            :data="locates"
            :fields="json_fields"
            type="csv"
            name="filename.xls"
            >
            <button type="button" class="download-btn" v-on:click="download">Download</button>
        </download-excel>


    </div>
</template>

<style scoped>
.result-table {
  width: 50%;
  text-align: center;
}
.download-btn {
  background-color: DodgerBlue;
  border: none;
  color: white;
  padding: 12px 30px;
  margin: 12px 0;
  cursor: pointer;
  font-size: 20px;  
}
/* Darker background on mouse-over */
.download-btn:hover {
  background-color: RoyalBlue;
}
</style>

<script>
import axios from 'axios'
import { BTable } from 'bootstrap-vue';
// import JsonExcel from "vue-json-excel";
 

export default {
    name: 'ExcelDownloadDemo',
    components: {
      BTable
    },
    data() {
      return {

        locates: [],




        items: [
          { age: 40, first_name: 'Dickerson', last_name: 'Macdonald' },
          { age: 21, first_name: 'Larsen', last_name: 'Shaw' },
          { age: 89, first_name: 'Geneva', last_name: 'Wilson' },
          { age: 38, first_name: 'Jami', last_name: 'Carney' }
        ],

            table: [{
                id: 1,
                        название: 'Тест 1',
                age: 21
            }, {
                id: 2,
                        название: 'Тест 2',
                age: 22
            }, {
                id: 3,
                        название: 'Тест 3',
                age: 23
            }],


            json_fields: {
                "ID": "id",
                "Полное имя": "fullname",
                "Логин": "login",
                "Пароль": "password",
                "Роль": "role",
            },
                json_data: [
                {
                    id: "Tony Peña",
                    fullname: "New York",
                    login: "United States",
                    password: "1978-03-15",
                    role: "1978-03-15",
                },
                {
                    id: "Tony Peña",
                    fullname: "New York",
                    login: "United States",
                    password: "1978-03-15",
                    role: "1978-03-15",
                },

                ],

                //
            json_meta: [
                [
                    {
                        key: "charset",
                        value: "utf-8",
                    },
                ],
            ],
      }
    },
    methods: {
        // download: function () {
        //     var tHeader = ['id', 'Name', 'Age'] // заголовок excel
        //     var filterVal = ['id', 'name', 'age'] // необходимо экспортировать все данные, соответствующие его собственному списку
        //     var list = this.table // список данных
        //     var data = this.formatJson(filterVal, list)
        //     // export_json_to_excel(tHeader, data, 'excelname')

        // },







      downloadCsv : function() {
        // const data = XLSX.utils.json_to_sheet(this.items)
        // const wb = XLSX.utils.book_new()
        // XLSX.utils.book_append_sheet(wb, data, 'data')
        // XLSX.writeFile(wb,'demo.xlsx')
      }
    },


    mounted() {
        axios
           .get('http://localhost:3001/api/userlogins')
            .then(response => {
                this.locates = response.data
                console.log(response.data)
            })
            .catch(error => console.log(error))
    }
}
</script>