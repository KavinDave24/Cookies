# Cookies
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <h1> Your Name, Granded Exercise 1</h1>
    <script type = "text/javascript">
        var days = 730; // days until cookie expires = 2 years.
        var lastVisit=new Object();
        var fistVisitMessage=" Your Name, this is your first visit."; // Message to dispay on first visit 
        lastVisit.LastVisitMessage="Your Name, your last visit was [showdate]";// Message to Dispaly on visit again


        lastVisit.getCookie=function(Name){ 
        var re=new RegExp(Name+"=[^;]+", "i"); 
        if (document.cookie.match(re)) 
        return document.cookie.match(re)[0].split("=")[1];
        return''; 
        } 

        lastVisit.setCookie=function(name, value, days){ 

        var expireDate = new Date();
        var expiresString=expireDate.setDate(expireDate.getDate()+parseInt(days));
        document.cookie = name+"="+value+"; expires="+expireDate.toGMTString()+"; path=/";
        }
        lastVisit.showmessage = function() {
        var date = new Date(); //get date 
        if (lastVisit.getCookie("visitc") == "") { 
        lastVisit.setCookie("visitc", date, days); 
        document.write(fistVisitMessage);
        } 
        else {
        var lv = lastVisit.getCookie("visitc");
        var lvp = Date.parse(lv);
        var nowDate = new Date();
        nowDate.setTime(lvp);
        var weekDays = new Array("Sunday", "Monday", "Tuesday", "Wedensday", "Thursday", "Friday", "Saturday");
        var dd = nowDate.getDate();
        var dy = nowDate.getDay();
        dy = weekDays[dy];
        var mn = nowDate.getMonth();
        yy = nowDate.getFullYear();
        var hh = nowDate.getHours();
        var ampm = "AM";
        if (hh >= 12) {ampm = "PM"}
        if (hh >12){hh = hh - 12};
        if (hh == 0) {hh = 12}
        if (hh < 10) {hh = "0" + hh};
        var mins = nowDate.getMinutes();
        if (mins < 10) {mins = "0"+ mins}
        var secs = nowDate.getSeconds();
        if (secs < 10) {secs = "0" + secs}
        var dispDate = dy + " " + mn + "/ " + dd + "/ " + yy +" " +"at " + hh + ":" + mins + ":" + secs + " " + ampm
        document.write(lastVisit.LastVisitMessage.replace("\[showdate\]", dispDate))
        }
        
        lastVisit.setCookie("visitc", date, days);
        
        }
        
        lastVisit.showmessage();
        
        </script>
</body>
</html>
