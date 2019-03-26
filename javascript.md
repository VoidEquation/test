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

### 숫자 회계 형태로
- Number.prototype.toLocaleString()
```javascript
var number = 3500;
console.log(number.toLocaleString()); // Displays "3,500" if in U.S. English locale
```
