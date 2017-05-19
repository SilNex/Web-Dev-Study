<!DOCTYPE html>
<html lang="ko">
    <head>
        <title>JZ quiz</title>
        <meta charset="UTF-8">
        <script>
            function is_leap(_year){ //윤년은 leaf year가 아니라 leap year입니다.
                if(_year)
                    if(((_year % 4) == 0) && ((_year %100) != 0) || ((_year % 400) == 0))        
                        return true
                return false
            }
            function calc_year(day_){
                leap_stamp_cnt = 477    // Number of leap years by 1970
                year_= Math.floor(day_ / 365) + 1970; day_ = day_ % 365
                leap_now_cnt = Math.floor((year_ - 1) / 4) - Math.floor((year_ - 1) / 100) + Math.floor((year_ - 1) / 400)

                return {
                    day_: day_ - (leap_now_cnt - leap_stamp_cnt),   // remove day of leap year
                    year_: year_
            }

                /* Legacy Code */
                // year_ = 1970
                // while(day_ > 365 || ((day_ > 366) && (is_leap(year_))) ){
                //     if(is_leap(year_)){
                //         day_ -= 366
                //     } else {
                //         day_ -= 365
                //     }
                //     year_++
                // }
                // return {
                //     day_: day_,
                //     year_: year_
                // }
                
            }
            function calc_month(day_,year_){
                month_ = 1
                while(month_ <= 7 && ((day_ >= 31 && month_ & 1) || (day_ >= 30 && !(month_ & 1))) ) {
                    if(month_ == 2){
                        day_ -= 28
                        if(is_leap(year_)){
                            day_--
                        }
                        month_++
                    } else if(month_ & 1){
                        day_ -= 31
                        month_++
                    } else {
                        day_ -= 30
                        month_++
                    }
                }
                while(month_ <= 12 && ((day_ >= 30 && month_ & 1) || (day_ >= 31 && !(month_ & 1))) ){
                    if(month_ & 0){
                        day_ -= 31
                        month_++
                    } else {
                        day_ -= 30
                        month_++
                    }
                }
                
                return {
                    day_: day_ + 1,
                    month_: month_
                }
            }
            function calc_weekday (day_,month_,year_){
                /* Using zeller's congruence */
                k = year_ % 100
                j = year_ / 100
                return Math.floor((day_ + Math.floor(13 * (month_ + 1) / 5) + k + Math.floor(k / 4) + 5 * j + Math.floor(j / 4) ) % 7)
            }
            
            days = ['토', '일', '월', '화', '수', '목', '금']
            
            date_ = new Date()
            getTime_ = date_.getTime()
            sec = Math.floor(getTime_ / 1000) + 32400   //UTC+9
            min = Math.floor(sec / 60); sec = sec % 60 
            hour = Math.floor(min / 60); min = min % 60
            day = Math.floor(hour / 24); hour = hour %24
            calc = new calc_year(day)
            year = calc.year_;day = calc.day_
            calc = new calc_month(day, year)
            month = calc.month_; day = calc.day_
            weekday = days[calc_weekday(day,month,year)]

            /* DEBUG CODE */
            // console.log(sec+'초')
            // console.log(min+'분')
            // console.log(hour+'시')
            // console.log(day+'일')
            // console.log(month+'월')
            // console.log(year+'년')
            // console.log(weekday[calc_weekday(day,month,year)]+'요일')

            </script>
    </head>
    <body>
    <p id='date'></p>
    <p id='time'></p>
    <script>
        document.getElementById('date').innerHTML = "오늘은 "+year+"년 "+month+"월 "+day+"일 "+weekday+"요일 입니다."
        document.getElementById('time').innerHTML = "현재 시각은 "+hour+"시 "+min+"분 "+sec+"초 입니다."
    </script>
    </body>
</html>
