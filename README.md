#### 時間轉換器
1分鐘前,2分鐘前,...59分鐘前<br>
1小時前,2小時前,...23小時前<br>
1天前,2天前,...6天前<br>
1週前,2週前,...3週前<br>
1個月前,2個月前,...11個月前<br>
1年前,2年前,3年前...
```
<?php

class Service_Format_Datetime
{
    public static function toText($datetime){
        $second = strtotime("now")-strtotime($datetime);
    
        if($second >= pow(60,2) * 24 * 30 * 12) {         //1年前,2年前,3年前...
            $year = $second / (pow(60,2) * 24 * 30 * 12);
            return intval($year).' 年前';
        }else if($second >= pow(60,2) * 24 * 30) {        //1個月前,2個月前,...11個月前
            $month = $second / (pow(60,2) * 24 * 30);
            return intval($month).' 個月前';
        }else if($second >= pow(60,2) * 24 * 7) {         //1週前,2週前,...4週前
            $week = $second / (pow(60,2) * 24 * 7);
            return intval($week).' 週前';
        }else if($second >= pow(60,2) * 24) {             //1天前,2天前,...6天前
            $day = $second / (pow(60,2) * 24);
            return intval($day).' 天前';
        }else if($second >= pow(60,2)) {                  //1小時前,2小時前,...23小時前
            $hour = $second / pow(60,2);
            return intval($hour).' 小時前';
        }else if($second >= pow(60,1)) {                  //1分鐘前,2分鐘前,...59分鐘前
            $minute = $second / pow(60,1);
            return intval($minute).' 分鐘前';
        }else {
            return $second.' 秒鐘前';
        }
    }
}
?>
```