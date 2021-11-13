<template>
  <div>
    <el-table
        :data="filteredUsers"
        style="width: 100%">
      <el-table-column
          label="ФИО"
          prop="lastName"
          :formatter="formatter">
      </el-table-column>
      <el-table-column
          width="110"
          label="СНИЛС"
          prop="snils">
      </el-table-column>
      <el-table-column
          align="right">
        <template slot="header">
          <el-input
              v-model="search"
              size="mini"
              placeholder="Поиск по имени или СНИЛС"/>
        </template>
      </el-table-column>
    </el-table>
    <!--<el-table
        :data="filteredUsers"
        style="width: 100%">
      <el-table-column
          label="ФИО"
          prop="lastName"
          :formatter="formatter">
      </el-table-column>
      <el-table-column
          width="110"
          label="СНИЛС"
          prop="snils">
      </el-table-column>
      <el-table-column
          align="right">
        <template slot="header" slot-scope="scope">
          <el-input
              v-model="search"
              size="mini"
              placeholder="Поиск по имени или СНИЛС"/>
        </template>
        <template slot-scope="scope">
          <el-button
              size="mini"
              type="primary"
              @click="$router.push({ name: 'User', params: { id: scope.row.id } })">Просмотр</el-button>
          <el-button
              size="mini"
              @click="$router.push({ name: 'Edit', params: { id: scope.row.id } })">Редактировать</el-button>
          <el-button
              size="mini"
              type="danger"
              @click="deleteUser(scope.row.id)">Удалить</el-button>
        </template>
      </el-table-column>
    </el-table>-->
  </div>
</template>

<script lang="ts">
import { Component, Vue, ModelSync } from 'vue-property-decorator';
//import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

/*@Component({
  components: {
    HelloWorld,
  },
})*/


declare interface User {
  id: number,
  firstName: string,
  lastName: string,
  middleName: string,
  dateBirth: string,
  gender: string,
  snils: string
}

export default class List extends Vue {

  users: Array<User> = [{
    "id": 0,
    "firstName": "Пётр",
    "lastName": "Петров",
    "middleName": "Петрович",
    "dateBirth": "01-01-1990",
    "gender": "мужской",
    "snils": "12345678901"
  }, {
    "id": 3,
    "firstName": "Пётр",
    "lastName": "Иванов",
    "middleName": "Петрович",
    "dateBirth": "02-04-1934",
    "gender": "мужской",
    "snils": "12345678902"
  }, {
    "id": 17,
    "firstName": "Светлана",
    "lastName": "Иванова",
    "middleName": "Петровна",
    "dateBirth": "03-06-1993",
    "gender": "женский",
    "snils": "12345678903"
  }, {
    "id": 105,
    "firstName": "Иван",
    "lastName": "Иванов",
    "middleName": "Иванович",
    "dateBirth": "04-08-1980",
    "gender": "мужской",
    "snils": "12345678904"
  }]
  search: '' = ''

  get filteredUsers(): Array<User> { // Получаем массив пациентов отфильтрованный в соответствии с поисковым запросом
    return this.users.filter(data => !this.search || (`${data.snils} ${data.firstName} ${data.lastName} ${data.middleName}`).toLowerCase().includes(this.search.toLowerCase()))
  }

  formatter(row: User ): string {
    return `${row.lastName} ${row.firstName} ${row.middleName}`
  }
}
</script>
