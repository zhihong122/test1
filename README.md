
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>日曆</title>
    <style type="text/css">
        *{
            padding: 0;
            margin: 0;
        }
        #calendar{
            width: 100%;
            height: 600px;
            background:linear-gradient(#c4f185,#86d2f3);
        }
        #box{
            position: relative;
            left: 50%;
            transform: translate(-50%,10%);
            width: 80%;
        }
        #calendarbox{
            position: relative;
            /* height: 100px; */
            width: 100%;
        }
        #calendartittle{
            height: 150px;
            font-size: 24px;
        }
        /* #suntosat{
            background-color: rgb(255, 215, 235);
        } */
        td{
            height: 45px;
            width: 80px;
            text-align: center;
            border: 3px solid rgb(0, 0, 0);
            font-size: 28px;
            color: rgb(0, 0, 0);
            font-family: cursive;
        }
        td:hover {
            background-color: rgb(168, 198, 255);
            border: 3px solid #2600ff;
        }
    </style>
</head>
<body>
    <div id="calendar">
        <div id="box">
            <table id="calendarbox">
            <tr id="calendartittle">
                <td colspan="2">
                    <p id="nowtime">
                        <script type="text/javascript">
                                var time = setInterval(function() {
                                document.getElementById("nowtime").innerHTML = new Date();
                                }, 1000);
                        </script>
                    </p>
                </td>
                <td colspan="3">
                    <p id="today">
                        <script type="text/javascript">
                        var date = new Date();
                        var year = date.getFullYear();
                        var month = date.getMonth()+1;
                        var dates = date.getDate();
                        document.getElementById("today").innerHTML = (year + ' 年 ' + month + ' 月 ' + dates + ' 日 ');
                    </script>
                    </p>
                    
                </td>
                <td colspan="2">
                    <p id="todays">
                        <script type="text/javascript">
                            var date = new Date();
                            var year = date.getFullYear();
                            var month = date.getMonth()+1;
                            var dates = date.getDate();
                            var arr = ['星期日' , '星期一' , '星期二' , '星期三' , '星期四' , '星期五' , '星期六'];
                            var day = date.getDay();
                            document.getElementById("todays").innerHTML = arr[day];
                        </script>
                    </p>
                </td>
            </tr>
            
            <tr id="suntosat">
                <td>日</td>
                <td>一</td>
                <td>二</td>
                <td>三</td>
                <td>四</td>
                <td>五</td>
                <td>六</td>
            </tr>
            <tr id="W1">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr id="W2">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr id="W3">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr id="W4">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr id="W5">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr id="W6">
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            </table>
                
        </div>
        
        
        <script type="text/javascript"> 
        var Now = new Date();
        var Calendar = [Now.getFullYear(), Now.getMonth(), Now.getDate()];
        var UseCalendar = Calendar;

        window.onload = Today();

        function Today(){
            var Now = new Date;
            UseCalendar = Calendar;
            SetMonth(UseCalendar);
        }

        function SetMonth(UseCalendar){//設置日曆
            var Now = new Date();
            var CalendarNum = new Date(UseCalendar[0], UseCalendar[1]+1, 0).getDate();
            var CalendarFirstDay = new Date(UseCalendar[0], UseCalendar[1], 1).getDay();
            var Col = 1;
            var Day = CalendarFirstDay;
            

            for (var i=1; i<=42; i++) {
                var SetWeek = "W" + Col;
                if (i > CalendarNum) {
                    document.getElementById(SetWeek).children[Day%7].innerHTML = "";
                }
                else {
                    document.getElementById(SetWeek).children[Day%7].innerHTML = i;
                }
                
                if (Calendar[0] == UseCalendar[0] && Calendar[1] == UseCalendar[1] && i == Calendar[2]) {
                    document.getElementById(SetWeek).children[Day%7].style = "background-color: yellow";
                }

                if (Day%7 == 6) {
                    if (Col != 6) {
                        Col += 1;
                    }
                    else {
                        Col = 1;
                    }
                }
                Day += 1;
            }
            
        }
        
        </script>
    </div>
</body>
</html>