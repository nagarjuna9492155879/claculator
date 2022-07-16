<!DOCTYPE html>
<html>
<head>
	<title>calculator</title>
	<style type="text/css">
		.title{
			color: blue;
			font-size: 60px;

		}
		.cal{
			border: blue;

		}
		.calci{
			background-color :blue;


			height: 800px;
			width: 60%;
			border-radius: 30px;
}
		td{
			width: 10px;

			height: 15px;
			border-radius: 10px;
		}
		.hi{
			align-items: center;
		}
		.button{
			width: 200px;
			height: 95px;
			background-color: lightblue;
			font-size: 30px;
		}
		.hea{
			height: 10px;
		}
		.h{
			height: 80px;
			width: 80px;
			font-size: 30px;
		}
		.res{
			width: 800px;
			height: 200px;
			font-size: 30px;
		}
		
	</style>
	<script type="text/javascript">
		var th = ['','thousand','million', 'billion','trillion'];
var dg = ['zero','one','two','three','four', 'five','six','seven','eight','nine'];
 var tn = ['ten','eleven','twelve','thirteen', 'fourteen','fifteen','sixteen', 'seventeen','eighteen','nineteen'];
 var tw = ['twenty','thirty','forty','fifty', 'sixty','seventy','eighty','ninety'];
 
function toWords(s) {
    s = s.toString();
    s = s.replace(/[\, ]/g,'');
    if (s != parseFloat(s)) return 'not a number';
    var x = s.indexOf('.');
    if (x == -1)
        x = s.length;
    if (x > 15)
        return 'too big';
    var n = s.split(''); 
    var str = '';
    var sk = 0;
    for (var i=0;   i < x;  i++) {
        if ((x-i)%3==2) { 
            if (n[i] == '1') {
                str += tn[Number(n[i+1])] + ' ';
                i++;
                sk=1;
            } else if (n[i]!=0) {
                str += tw[n[i]-2] + ' ';
                sk=1;
            }
        } else if (n[i]!=0) {
            str += dg[n[i]] +' ';
            if ((x-i)%3==0) str += 'hundred ';
            sk=1;
        }
        if ((x-i)%3==1) {
            if (sk)
                str += th[(x-i-1)/3] + ' ';
            sk=0;
        }
    }
    
    if (x != s.length) {
        var y = s.length;
        str += 'point ';
        for (var i=x+1; i<y; i++)
            str += dg[n[i]] +' ';
    }
    return str.replace(/\s+/g,' ');
}
       
function dis(v){
var f=document.querySelector("#result")
var rgex=/^[0-9]+$|[0-9]+[+*/-][0-9]+/g
var reg=/^[\d]+[/][0]/
f.value+=v;
if(rgex.test(f.value) & !(reg.test(f.value))){
document.querySelector("#result").style.backgroundColor="lightgreen";
}
else{
document.querySelector("#result").style.backgroundColor="red"
}
}

      function solve() {
        let x = document.getElementById("result").value;
        let y = eval(x);
        var words=toWords(y);
        document.getElementById("result").value = y;
        document.getElementById("result").value=words;

        
      }

      function clr() {
        document.getElementById("result").value = "";
        document.querySelector("#result").style.backgroundColor="#232323";


      }
	</script>
</head>
<body bgcolor="lightpink" class="hi">
	<div class="calci" align="center">
        <h1>Calculator</h1>
        
      <table align="center">
        <tr >
          <td colspan="4" ><input type="text"  class="res" id="result" /></td>
        </tr>
        <tr>
          <td>
            <input class="button"type="button" value="1" onclick="dis('1')" />
          </td>
          <td>
            <input class="button" type="button" value="2" onclick="dis('2')" />
          </td>
          <td>
            <input class="button" type="button" value="3" onclick="dis('3')" />
          </td>
          <td>
            <input class="button" type="button" value="/" onclick="dis('/')" />
          </td></a>
        </tr>
        <tr>
          <td>
            <input class="button" type="button" value="4" onclick="dis('4')" />
          </td>
          <td>
            <input class="button" type="button" value="5" onclick="dis('5')" />
          </td>
          <td>
            <input class="button" type="button" value="6" onclick="dis('6')" />
          </td>
          <td>
            <input class="button" type="button" value="-" onclick="dis('-')" />
          </td>
        </tr>
        <tr>
          <td>
            <input class="button" type="button" value="7" onclick="dis('7')" />
          </td>
          <td>
            <input class="button" type="button" value="8" onclick="dis('8')" />
          </td>
          <td>
            <input class="button" type="button" value="9" onclick="dis('9')" />
          </td>
          <td>
            <input class="button" type="button" value="+" onclick="dis('+')" />
          </td>
        </tr>
        <tr>
          <td>
            <input class="button" type="button" value="." onclick="dis('.')" />
          </td>
          <td>
            <input class="button" type="button" value="0" onclick="dis('0')" />
          </td>

          <td>
            <input class="button" type="button" value="=" onclick="solve()" />
          </td>
          <td>
            <input class="button" type="button" value="" onclick="dis('')" />
          </td>
        </tr>
        <tr>
          <td><input class="button"type="button" value="Clear" onclick="clr()" /></td>
        </tr>
      </table>
    </div>

</body>
</html>
	
