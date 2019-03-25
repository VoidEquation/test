# Javascript
### 날짜 포맷
```javascript
var d = new Date();
var curr_date = d.getDate();
var curr_month = d.getMonth() + 1;
var curr_year = d.getFullYear();
if(curr_month < 10) this.startDt = curr_year + '-0' + curr_month + '-' + curr_date;
else this.startDt = curr_year + '-' + curr_month + '-' + curr_date;
this.startTm = d.getHours() + ':' + d.getMinutes() + ':' + '00';
```
