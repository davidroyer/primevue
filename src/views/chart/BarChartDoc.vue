<template>
	<div class="content-section documentation">
		<TabView>
			<TabPanel header="Source">
<CodeHighlight>
<template v-pre>
&lt;template&gt;
	&lt;div&gt;
		&lt;div class="content-section introduction"&gt;
			&lt;div class="feature-intro"&gt;
				&lt;h1&gt;BarChart&lt;/h1&gt;
				&lt;p&gt;A bar chart or bar graph is a chart that presents grouped data with rectangular bars with lengths proportional to the values that they represent.&lt;/p&gt;
			&lt;/div&gt;
		&lt;/div&gt;

		&lt;div class="content-section implementation"&gt;
			&lt;h3 class="vertical"&gt;Vertical&lt;/h3&gt;
			&lt;Chart type="bar" :data="basicData" /&gt;

			&lt;h3&gt;Horizontal&lt;/h3&gt;
			&lt;Chart type="horizontalBar" :data="basicData" /&gt;

			&lt;h3&gt;Multi Axis&lt;/h3&gt;
			&lt;Chart type="bar" :data="multiAxisData" :options="multiAxisOptions"/&gt;

			&lt;h3&gt;Stacked&lt;/h3&gt;
			&lt;Chart type="bar" :data="stackedData" :options="stackedOptions"/&gt;
		&lt;/div&gt;
	&lt;/div&gt;
&lt;/template&gt;
</template>
</CodeHighlight>

<CodeHighlight lang="javascript">
export default {
	data() {
		return {
			basicData: {
				labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
				datasets: [
					{
						label: 'My First dataset',
						backgroundColor: '#42A5F5',
						data: [65, 59, 80, 81, 56, 55, 40]
					},
					{
						label: 'My Second dataset',
						backgroundColor: '#9CCC65',
						data: [28, 48, 40, 19, 86, 27, 90]
					}
				]
			},
			multiAxisData: {
				labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
				datasets: [
					{
						label: 'Dataset 1',
						backgroundColor: [
							'#EC407A',
							'#AB47BC',
							'#42A5F5',
							'#7E57C2',
							'#66BB6A',
							'#FFCA28',
							'#26A69A'
						],
						yAxisID: 'y-axis-1',
						data: [65, 59, 80, 81, 56, 55, 10]
					},
					{
						label: 'Dataset 2',
						backgroundColor: '#78909C',
						yAxisID: 'y-axis-2',
						data: [28, 48, 40, 19, 86, 27, 90]
					}
				]
			},
			multiAxisOptions: {
				responsive: true,
				tooltips: {
					mode: 'index',
					intersect: true
				},
				scales: {
					yAxes: [
						{
							type: 'linear',
							display: true,
							position: 'left',
							id: 'y-axis-1',
							ticks: {
								min: 0,
								max: 100
							}
						},
						{
							type: 'linear',
							display: true,
							position: 'right',
							id: 'y-axis-2',
							gridLines: {
								drawOnChartArea: false
							},
							ticks: {
								min: 0,
								max: 100
							}
						}
					]
				}
			},
			stackedData: {
				labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
				datasets: [
					{
						type: 'bar',
						label: 'Dataset 1',
						backgroundColor: '#66BB6A',
						data: [
							50,
							25,
							12,
							48,
							90,
							76,
							42
						]
					},
					{
						type: 'bar',
						label: 'Dataset 2',
						backgroundColor: '#FFCA28',
						data: [
							21,
							84,
							24,
							75,
							37,
							65,
							34
						]
					},
					{
						type: 'bar',
						label: 'Dataset 3',
						backgroundColor: '#42A5F5',
						data: [
							41,
							52,
							24,
							74,
							23,
							21,
							32
						]
					}
				]
			},
			stackedOptions: {
				tooltips: {
					mode: 'index',
					intersect: false
				},
				responsive: true,
				scales: {
					xAxes: [{
						stacked: true,
					}],
					yAxes: [{
						stacked: true
					}]
				}
			}
		}
	}
}
</CodeHighlight>
			</TabPanel>
		</TabView>
	</div>
</template>