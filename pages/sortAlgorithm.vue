<template>
  <div>

  </div>
</template>
<script>
export default {
  data() {
    return {
      arr: [10,2,6,9,4,1,3,8],
      select: [12,5,7,1,3,2,5]
    }
  },
  created() {
    this.bubbleSort(this.arr);
    this.selectSort(this.select);
  },
  mounted() {
  },
  methods: {
    // 冒泡排序
    bubbleSort(arr){
      let arrLen = arr.length;
      for(var i=0; i<arrLen-1; i++){
        for(var j=0; j<arrLen-1-i; j++){
          if(arr[j]>arr[j+1]){
            let temp = arr[j]
            arr[j] = arr[j+1]
            arr[j+1] = temp;
          }
        }
      }
      console.log('arr', arr);
      return arr
    },

    // 选择排序
    selectSort(arr){
      var len = arr.length;
      var minIndex, temp; //定义最小值索引及暂存值空间
      for (let i=0; i<len-1; i++) {
        minIndex = i;
        for(let j=i+1; j<len; j++){
          minIndex = i;
          if(arr[j]<arr[minIndex]){
            minIndex = j
          }
          temp = arr[i]
          arr[i] = arr[minIndex]
          arr[minIndex] = temp
        }
      }
      console.log('选择---->', arr);
      return arr

    }
  },
}
</script>
