<!-- 
	This is the tables page, it uses the dashboard layout in: 
	"./layouts/Dashboard.vue" .
 -->

<template>
	<div>
		<!-- Authors Table -->
		<a-row :gutter="24" type="flex">

			<!-- Authors Table Column -->
			<a-col :span="24" class="mb-24">

				<!-- Authors Table Card -->
				<CardAuthorTable :data="table1Data" :columns="table1Columns"></CardAuthorTable>
				<!-- / Authors Table Card -->

			</a-col>
			<!-- / Authors Table Column -->

		</a-row>
		<!-- / Authors Table -->



	</div>
</template>

<script>
import CardAuthorTable from '../components/Cards/CardAuthorTable';
import CardProjectTable2 from '../components/Cards/CardProjectTable2';
export default {
	components: {
		CardAuthorTable,
		CardProjectTable2,
	},
	data() {
		return {
			table1Data: [],
			table1Columns: [
				{
					title: 'ชื่อหน่วยงาน',
					dataIndex: 'name',
				},
				{
					title: 'รหัสหน่วยบริการ',
					dataIndex: 'code',
				},
				{
					title: 'วันที่ขึ้นทะเบียน',
					dataIndex: 'createDate',
				},
				{
					title: 'ชื่อผู้ตรวจสอบ',
					dataIndex: 'verifyBy',
					class: 'text-muted',
				},
				{
					title: 'วันที่ตรวจสอบ',
					dataIndex: 'verifyDate'
				},
				{
					title: 'สถานะ',
					dataIndex: 'status',
					scopedSlots: { customRender: 'status' },
				},
			],
			colors: ['red', 'blue', 'green', 'yellow', 'purple', 'pink', 'cyan'],
		}
	},
	async created() {
		await this.axios.get('https://test-api-py77dwlbxa-df.a.run.app/data').then((response) => {
			response.data.forEach((el, i) => {
				this.table1Data[i] = {}
				this.$set(this.table1Data, i, { 'key': (i + 1) + '', ...this.table1Data[i], ...el, color: this.colors[i] })
			});
		}).catch(err => console.error('err ', err))
	}
}
</script>

<style lang="scss"></style>