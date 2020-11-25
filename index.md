Enter your weight in kilograms and your height in centimeters in the form below and press the "Let's see" button (Please read disclaimer below before using this form)

<FORM NAME="BMI" method=POST>

<TR>
<TD>
    <DIV ALIGN=CENTER>Your Weight (kg)</DIV>
    <INPUT TYPE=TEXT NAME=weight  SIZE=10 onFocus="this.form.weight.value=''"></TD>
<TD><DIV ALIGN=CENTER>Your Height (cm)</DIV>
    <INPUT TYPE=TEXT NAME=height  SIZE=10 onFocus="this.form.height.value=''"></TD>
<TD>
    <DIV ALIGN=CENTER>Your BMI</DIV>
    <INPUT TYPE=TEXT NAME=bmi     SIZE=8 disable></TD>
<TD>
    <DIV ALIGN=CENTER>My Comment</DIV>
    <INPUT TYPE=TEXT NAME=my_comment size=35 disable></TD>

    
<INPUT TYPE="button" VALUE="Let's see" onClick="computeform(this.form)">
<INPUT TYPE="reset"  VALUE="Reset" onClick="ClearForm(this.form)">
    
<HR>




<SCRIPT LANGUAGE="JAVASCRIPT">

function ClearForm(form){

    form.weight.value = "";
    form.height.value = "";
    form.bmi.value = "";
    form.my_comment.value = "";

}

function bmi(weight, height) {

          bmindx=weight/eval(height*height);
          return bmindx;
}

function checkform(form) {

       if (form.weight.value==null||form.weight.value.length==0 || form.height.value==null||form.height.value.length==0){
            alert("\nPlease complete the form first");
            return false;
       }

       else if (parseFloat(form.height.value) <= 0||
                parseFloat(form.height.value) >=500||
                parseFloat(form.weight.value) <= 0||
                parseFloat(form.weight.value) >=500){
                alert("\nReally know what you're doing? \nPlease enter values again. \nWeight in kilos and \nheight in cm");
                ClearForm(form);
                return false;
       }
       return true;

}

function computeform(form) {

       if (checkform(form)) {

       yourbmi=Math.round(bmi(form.weight.value, form.height.value/100));
       form.bmi.value=yourbmi;

       if (yourbmi >40) {
          form.my_comment.value="Class 3 Obese, consult your physician!";
       }

       else if (yourbmi >30 && yourbmi <=40) {
          form.my_comment.value="Obese.";
       }

       else if (yourbmi >25 && yourbmi <=30) {
          form.my_comment.value="Overweight";
       }
       
       else if (yourbmi >=18.5 && yourbmi <=24.9) {
          form.my_comment.value="Healthy weight";
       }

       else if (yourbmi <18.5) {
          form.my_comment.value="Underweight";
       }

       }
       return;
}
</SCRIPT>
