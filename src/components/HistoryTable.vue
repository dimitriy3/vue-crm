<template>
  <table>
    <thead>
    <tr>
      <th class="th">#</th>
      <th>Сумма</th>
      <th class="th">Дата</th>
      <th>Категория</th>
      <th>Тип</th>
      <th>Расход</th>
    </tr>
    </thead>

    <tbody>
    <tr v-for="(record, idx) of records" :key="record.id">
      <td class="td">{{ idx + 1 }}</td>
      <td>{{ record.amount | currency('RUB') }}</td>
      <td class="td">{{ record.date | date('datetime') }}</td>
      <td>{{ record.categoryName }}</td>
      <td>
        <span :class="[record.typeClass]" class="white-text badge">{{ record.typeText }}</span>
      </td>
      <td>
        <button class="btn-small btn" @click="$router.push('/detail/' + record.id)">
          <i class="material-icons">open_in_new</i>
        </button>
      </td>
    </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    records: {
      required: true,
      type: Array
    }
  }
}
</script>
