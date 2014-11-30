datepicker
==========

datepicker not working


-----------------------
<?php
session_start();

$sapp = $_SESSION['app_session'];
$userId = $_SESSION['uid'];
if($_SESSION['app_session'])
{
}else {
    header("location: ../index.php");
    }

//require_once('../authen.php');
require("../include/dbcon.php"); 

?>


<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="">
    <meta name="author" content="">

     <title>Green Pasture</title>

    <!-- Bootstrap Core CSS -->
    <link href="css/bootstrap.min.css" rel="stylesheet">
    <link href="assets/css/bootstrap.css" rel="stylesheet">
    
    <!-- MetisMenu CSS -->
    <link href="css/plugins/metisMenu/metisMenu.min.css" rel="stylesheet">

    <!-- Timeline CSS -->
    <link href="css/plugins/timeline.css" rel="stylesheet">

    <!-- Custom CSS -->
    <link href="css/sb-admin-2.css" rel="stylesheet">
    <link href="assets/css/croppic.css" rel="stylesheet">

    <!-- Morris Charts CSS -->
    <link href="css/plugins/morris.css" rel="stylesheet">
    <link href="assets/css/main.css" rel="stylesheet">

    <link rel="stylesheet" href="css/jquery-ui.css">

    <!-- Custom Fonts -->
    <link href="font-awesome-4.1.0/css/font-awesome.min.css" rel="stylesheet" type="text/css">
    <link href='http://fonts.googleapis.com/css?family=Lato:300,400,900' rel='stylesheet' type='text/css'>
  <link href='http://fonts.googleapis.com/css?family=Mrs+Sheppards&subset=latin,latin-ext' rel='stylesheet' type='text/css'>

    <script src="js/jquery-1.3.2.min.js"></script>
    <script type="text/javascript" src="js/jquery.js"></script>
    
   
    
    <!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
        <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
        <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
    <![endif]-->
 
<script type="text/javascript">
  jQuery(document).ready(function(){        
    // when any option from country list is selected
    jQuery("select[name='country']").change(function(){ 
      
      // path of ajax-loader gif image
      
      
      // get the selected option value of country
      var optionValue = jQuery("select[name='country']").val();   
            
      /**
       * pass country value through POST method
       * the 'status' parameter is only a dummy parameter (just to show how multiple parameters can be passed)
       * if we get response from data.php, then only the cityAjax div is displayed 
       * otherwise the cityAjax div remains hidden
       */
      jQuery("#cityAjax")
        .load('data.php', {country: optionValue, status: 1}, function(response){          
          if(response) {
            jQuery("#cityAjax").css('display', '');
          } else {
            jQuery("#cityAjax").css('display', '');
          }
      });     
    });
  });
</script> 

<script>
 $(function() {

        $('#yrs').change(function(){

                $('.colors').hide();

            var select = $('#yrs option:selected').attr("id");

         if(select == "new"){
                 // $('#' + $(this).attr("id")).show(); 
                 $('.colors').hide();
                 $('#addButton').hide();
                 $('#removeButton').hide();
       }

        else if(select == "less" || select == "1" || select == "2" || select == "3" || select == "4" || select == "5" || select == "6" || select == "7" || select == "8" || select == "9" || select == "10" || select == "11" || select == "12" || select == "13" || select == "14" || select == "15" || select == "16" || select == "17" || select == "18" || select == "19" || select == "20" || select == ">20"){
            //$('#' + $(this).attr("id")).show(); 
            $('.colors').show();
              $('#addButton').show();
                 $('#removeButton').show();
          }
        });
    });


   $(document).ready(function(){
 
    var counter = 2;
 
    $("#addButton").click(function () {
    
  //  $("#myCheck").prop("disabled", "disabled");

    if(counter>10){
            alert("Only 10 textboxes allow");
            return false;
    }   


 
    var newTextBoxDiv = $(document.createElement('div'))
         .attr("id", 'TextBoxDiv1' + counter);
 
    newTextBoxDiv.after().html('<div class=""> &nbsp; </div> ' + ' <div class="form-group">' + '<label> Company name: </label>' + '<input type="text" name="cname' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:530px">' + '</div>' + '<div class="form-group">' + '<label> Position: </label>' + '<input type="text" name="skill1' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:530px">' + '</div>' + '<div class="form-group">' + '<label> Address: </label>' + '<input type="text" name="skill1' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:530px">' + '</div>' + '<div class="form-group">' + '<label> Job Description: </label>' + '<textarea name="skill1' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:530px"> </textarea> </div>' + '<div class="form-group">' + '<b> Date Employed </b>' + '<div class="form-inline">' + 'from:' + '<input type="text" name="cfrom' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:170px">' + 'to:' + '<input type="text" name="cto' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:170px">' + 'total years:' + '<input type="text" name="cto' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:40px" readonly>' + '</div></div>');
 
    newTextBoxDiv.appendTo("#TextBoxesGroup");
    counter++;
     });
 
     $("#removeButton").click(function () {

      // $("#myCheck").prop("disabled");
    
    if(counter==1){
          alert("No more textbox to remove");
          return false;
       }   
 
    counter--;
 
        $("#TextBoxDiv1" + counter).remove();
 
     });
 
     /*$("#getButtonValue").click(function () {
 
    var msg = '';
    for(i=1; i<counter; i++){
      msg += "\n Textbox #" + i + " : " + $('#textbox' + i).val();
    }
          alert(msg);
     });*/
  });


//second 
$(document).ready(function(){
 
    var counter = 2;
 
    $("#addButton2").click(function () {
 
  if(counter>10){
            alert("Only 10 textboxes allow");
            return false;
  }   
 
  var newTextBoxDiv = $(document.createElement('div'))
       .attr("id", 'TextBoxDiv2' + counter);
 
  newTextBoxDiv.after().html('<input type="checkbox" name="skill' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width:300px"> <br/>');
 
  newTextBoxDiv.appendTo("#TextBoxesGroup2");
 
 
  counter++;
     });
 
     $("#removeButton2").click(function () {
  if(counter==1){
          alert("No more textbox to remove");
          return false;
       }   
 
  counter--;
 
        $("#TextBoxDiv2" + counter).remove();
 
     });
 
     /*$("#getButtonValue2").click(function () {
 
  var msg = '';
  for(i=1; i<counter; i++){
      msg += "\n Textbox #" + i + " : " + $('#textbox' + i).val();
  }
        alert(msg);
     });*/
  });

//radio 
$(document).ready(function(){
$("input[name='optionsRadiosInline']").click(function () {
    if (this.id == "optionsRadiosInline2") {
        $("#show-me").show('slow');
    } else {
        $("#show-me").hide('slow');
    }
});

$("input[name='optionsRadiosInline11']").click(function () {
    if (this.id == "optionsRadiosInline22") {
          $("#colBoxfr").prop("disabled", true);
          $("#colBoxr").prop("disabled", true);
          $("#textBoxColc").prop("disabled", true);
          $("#textBoxCol").prop("disabled", true);
          $("#optionsRadiosInline1").prop("disabled", true);
          $("#optionsRadiosInline2").prop("disabled", true);
    } else {
         $("#colBoxfr").prop("disabled", false);
          $("#colBoxr").prop("disabled", false);
          $("#textBoxColc").prop("disabled", false);
          $("#textBoxCol").prop("disabled", false);
          $("#optionsRadiosInline1").prop("disabled", false);
          $("#optionsRadiosInline2").prop("disabled", false);
    }
});

$("input[name='optionsRadiosInline111']").click(function () {
    if (this.id == "optionsRadiosInline222") {
          $("#colBoxfr").prop("disabled", true);
          $("#colBoxr").prop("disabled", true);
          $("#textBoxColc").prop("disabled", true);
          $("#textBoxCol").prop("disabled", true);
          $("#optionsRadiosInline1").prop("disabled", true);
          $("#optionsRadiosInline2").prop("disabled", true);
          $("#optionsRadiosInline11").prop("disabled", true);
          $("#optionsRadiosInline22").prop("disabled", true);
          $("#textBoxSect").prop("disabled", true);
          $("#textBoxSecf").prop("disabled", true);
          $("#textBoxSec").prop("disabled", true);

    } else {
        
          $("#optionsRadiosInline11").prop("disabled", false);
          $("#optionsRadiosInline22").prop("disabled", false);
          $("#textBoxSect").prop("disabled", false);
          $("#textBoxSecf").prop("disabled", false);
          $("#textBoxSec").prop("disabled", false);
    }
});


});



//third 
$(document).ready(function(){

          $("#textBoxOne").prop("disabled", true);
          $("#textBoxOnet").prop("disabled", true);
          $("#textBoxOnef").prop("disabled", true);
          $("#textBoxSect").prop("disabled", true);
          $("#textBoxSecf").prop("disabled", true);
          $("#textBoxSec").prop("disabled", true);
          $("#colBoxfr").prop("disabled", true);
          $("#colBoxr").prop("disabled", true);
          $("#textBoxColc").prop("disabled", true);
          $("#textBoxCol").prop("disabled", true);
          $("#optionsRadiosInline1").prop("disabled", true);
          $("#optionsRadiosInline2").prop("disabled", true);
          $("#optionsRadiosInline11").prop("disabled", true);
          $("#optionsRadiosInline22").prop("disabled", true);
          $("#optionsRadiosInline111").prop("disabled", true);
          $("#optionsRadiosInline222").prop("disabled", true);
          
          

          $("#addButton3").hide();
           $("#removeButton3").hide();

          $('#educ').change(function(){
            var select = $('#educ option:selected').attr("id");
        
         if(select == "5"){
                 /* $('#' + $(this).attr("id")).show(); 
                 $('.colors').hide();
                 $('#addButton').hide();
                 $('#removeButton').hide();*/
                  $("#textBoxOne").prop("disabled", false);
                  $("#textBoxOnet").prop("disabled", false);
                  $("#textBoxOnef").prop("disabled", false);
                  $("#textBoxSect").prop("disabled", true);
                  $("#textBoxSecf").prop("disabled", true);
                  $("#textBoxSec").prop("disabled", true);
                  $("#colBoxfr").prop("disabled", true);
                  $("#colBoxr").prop("disabled", true);
                  $("#textBoxColc").prop("disabled", true);
                  $("#textBoxCol").prop("disabled", true);
                  $("#optionsRadiosInline111").prop("disabled", false);
                  $("#optionsRadiosInline222").prop("disabled", false);
                  $("#vocDiv").hide();
                
             
       }

        else if(select == "3"){
            //$('#' + $(this).attr("id")).show(); 
                 //$('.colors').show();
                // $('#addButton').show();
                // $('#removeButton').show();
                  $("#textBoxOne").prop("disabled", false);
                  $("#textBoxOnet").prop("disabled", false);
                  $("#textBoxOnef").prop("disabled", false);
                  $("#textBoxSect").prop("disabled", false);
                  $("#textBoxSecf").prop("disabled", false);
                  $("#textBoxSec").prop("disabled", false);
                  $("#colBoxfr").prop("disabled", true);
                  $("#colBoxr").prop("disabled", true);
                  $("#textBoxColc").prop("disabled", true);
                  $("#textBoxCol").prop("disabled", true);
                  $("#vocDiv").hide();
                  $("#optionsRadiosInline111").prop("disabled", false);
                  $("#optionsRadiosInline222").prop("disabled", false);
                  $("#optionsRadiosInline11").prop("disabled", false);
                  $("#optionsRadiosInline22").prop("disabled", false);
          }
           else if(select == "2"){
              $('#vocDiv').show();


          }

          else if(select == "1"){
                  $("#textBoxOne").prop("disabled", false);
                  $("#textBoxOnet").prop("disabled", false);
                  $("#textBoxOnef").prop("disabled", false);
                  $("#textBoxSect").prop("disabled", false);
                  $("#textBoxSecf").prop("disabled", false);
                  $("#textBoxSec").prop("disabled", false); 
                  $("#colBoxfr").prop("disabled", false);
                  $("#colBoxr").prop("disabled", false);
                  $("#textBoxColc").prop("disabled", false);
                  $("#textBoxCol").prop("disabled", false);
                  $("#vocDiv").hide();
                  $("#optionsRadiosInline111").prop("disabled", false);
                  $("#optionsRadiosInline222").prop("disabled", false);
                  $("#optionsRadiosInline11").prop("disabled", false);
                  $("#optionsRadiosInline22").prop("disabled", false);
                  $("#optionsRadiosInline1").prop("disabled", false);
                  $("#optionsRadiosInline2").prop("disabled", false);
               
          }else{
          $("#textBoxOne").prop("disabled", true);
          $("#textBoxOnet").prop("disabled", true);
          $("#textBoxOnef").prop("disabled", true);
          $("#textBoxSect").prop("disabled", true);
          $("#textBoxSecf").prop("disabled", true);
          $("#textBoxSec").prop("disabled", true);
          $("#colBoxfr").prop("disabled", true);
          $("#colBoxr").prop("disabled", true);
          $("#textBoxColc").prop("disabled", true);
          $("#textBoxCol").prop("disabled", true);
          $("#vocDiv").hide();
          $("#optionsRadiosInline111").prop("disabled", true);
          $("#optionsRadiosInline222").prop("disabled", true);
          $("#optionsRadiosInline11").prop("disabled", true);
          $("#optionsRadiosInline22").prop("disabled", true);
          }

        });
    });

$(document).ready(function(){
      

    var counter = 2;
    
    $("#addButton3").click(function () {
 
  if(counter>10){
            alert("Only 10 textboxes allow");
            return false;
  }   
 
  var newTextBoxDiv = $(document.createElement('div'))
       .attr("id", 'TextBoxDiv3' + counter);
 
  newTextBoxDiv.after().html('<div class="form-group">' + '<div class="col-sm-12">' + '<div class="col-sm-offset-1">' + '<b> Name of School: </b> '+ '<input type="text" name="cschooltwo' + counter + '" id="textbox' + counter + '" value="" class="form-control" style="width: 550px;"> ' + '</div>' + '</div>' + '</div>' + '<div class=""> &nbsp; </div>' + '<div class="form-group">' + '<div class="col-sm-12">' + '<div class="col-sm-offset-1">' + '<b> Course: </b>' + '<input type="text" name="ccoursetwo' + counter + '" id="textbox' + counter + '" value="" class="form-control" style="width: 550px;">' + '</div>' + ' </div>' + '</div>' + '<div class=""> &nbsp; </div>' + '<div class="col-sm-offset-1"> <b> Number of units earned: </b> '+ '<input type="number" name="unitsearned' + counter + '" id="textbox' + counter + '" value="" class="form-control" style="width: 550px;"> </div>' + '<div class=""> &nbsp; </div>' + '<div class="col-sm-offset-1"><b> Year Graduated </b> <br/>' + '<div class="form-inline">' +
        ' <b> From: </b> <input type="date" name="cyrfromtwo' + counter + 
        '" id="textbox' + counter + '" value="" class="form-control" style="width: 250px;"> <b>To: </b> <input type="date" name="cyrtotwo' + counter + '" id="textbox' + counter + '" value="" class="form-control" style="width: 250px;"> <br/>' + '</div></div><br/>' );
 
  newTextBoxDiv.appendTo("#TextBoxesGroup3");
 
 
  counter++;
     });
 
     $("#removeButton3").click(function () {
  if(counter==1){
          alert("No more textbox to remove");
          return false;
       }   
 
  counter--;
 
        $("#TextBoxDiv3" + counter).remove();
 
     });
 
     /*$("#getButtonValue2").click(function () {
 
  var msg = '';
  for(i=1; i<counter; i++){
      msg += "\n Textbox #" + i + " : " + $('#textbox' + i).val();
  }
        alert(msg);
     });*/
  });

//checkbox
$(document).ready(function(){
 $('#myCheck').change(function(){
       $("#textboxto").prop("disabled", $(this).is(':checked'));
    
    });
});


//total yrs
  
  $(function() {
    $( "#datepickerln1" ).datepicker({
      //defaultDate: "+1w",
      changeYear: true,
      changeMonth: true,
      onClose: function( selectedDate ) {
        $( "#datepickerln2" ).datepicker( "option", "minDate", selectedDate );
      }
    });
    $( "#datepickerln2" ).datepicker({
     // defaultDate: "+1w",
      changeMonth: true,
      changeYear: true,
      onClose: function( selectedDate ) {
        $( "#datepickerln1" ).datepicker( "option", "maxDate", selectedDate );
      }
    });
  });

$(document).ready(function () {
    var selector = function (dateStr) {
        var d1 = $('#datepickerln1').datepicker('getDate'),
            d2 = $('#datepickerln2').datepicker('getDate'),
            diff = 0,
            d = 0,
            m = 0,
            y = 0;
        if (d1 && d2) {
            diff = new Date(d2.getTime() - d1.getTime());
            d = diff.getUTCDate() - 1;
            m = diff.getUTCMonth();
            y = Math.abs(1970 - diff.getUTCFullYear());
        }
        $('#total').val(d);
        $('#mtotal').val(m);
        $('#ytotal').val(y);
    }
    $("#datepickerln1").datepicker();
    $('#datepickerln2').datepicker();
    $('#datepickerln1,#datepickerln2').change(selector)
});
//date of birth
$(function() {
$('#dob').datepicker({
    onSelect: function(value, ui) {
        var today = new Date(), 
            age = today.getFullYear() - ui.selectedYear;
        $('#age').val(age);
    },
    changeMonth: true,
    changeYear: true,
    defaultDate: '-18yr',

    //minDate: '-18yr',
    maxDate: '-18yr', 
  });
});
</script>
</head>


<body>

    <div id="wrapper">

        <!-- Navigation -->
        <nav class="navbar navbar-default navbar-static-top" role="navigation" style="margin-bottom: 0">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                    <span class="sr-only">Toggle navigation</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                <a class="navbar-brand" href="index.php">Hello <?php echo strtoupper($sapp).'!' ?></a>
            </div>
            <!-- /.navbar-header -->

            <ul class="nav navbar-top-links navbar-right">
                <li class="dropdown">
                    <a class="dropdown-toggle" data-toggle="dropdown" href="#">
                        <i class="fa fa-envelope fa-fw"></i>  <i class="fa fa-caret-down"></i>
                    </a>
                 
                    <!-- /.dropdown-messages -->
                </li>
                <!-- /.dropdown -->
                <li class="dropdown">
                    <a class="dropdown-toggle" data-toggle="dropdown" href="#">
                        <i class="fa fa-tasks fa-fw"></i>  <i class="fa fa-caret-down"></i>
                    </a>
                  
                    <!-- /.dropdown-tasks -->
                </li>
                <!-- /.dropdown -->
                <li class="dropdown">
                    
                    <!-- /.dropdown-alerts -->
                </li>
                <!-- /.dropdown -->
                
                    
                     <li> <a href="logout.php" onclick="return confirm('Are you sure you want to log out?');"><i class="fa fa-sign-out fa-fw"></i> Logout</a> </li>
                    <!-- /.dropdown-user -->
          
                <!-- /.dropdown -->
            </ul>
            <!-- /.navbar-top-links -->

            <div class="navbar-default sidebar" role="navigation">
                <div class="sidebar-nav navbar-collapse">
                    <ul class="nav" id="side-menu">
                        
                        <li>
                            <a href="index.php"><i class="fa fa-dashboard fa-fw"></i> Profile <span class="fa arrow"></a>
                             <ul class="nav nav-second-level">
                                <li>
                                    <a href="appedit.php">Edit Profile</a>
                                </li>
                                <li>
                                    <a href="index.php">View </a>
                                </li>
                            </ul>
                        </li>
                        <li>
                            <a href="#"><i class="fa fa-bar-chart-o fa-fw"></i> Charts<span class="fa arrow"></span></a>
                           
                            <!-- /.nav-second-level -->
                        </li>
                       
                     
                    
                    </ul>
                </div>
                <!-- /.sidebar-collapse -->
            </div>
            <!-- /.navbar-static-side -->
        </nav>

        <div id="page-wrapper">
            <div class="row">
                <div class="col-lg-12">
                    <h1 class="page-header">Edit Profile</h1>
                	<b> Note: </b> Please put correct and true information in this form. This form will serve's as your <i> Curriculum Vitae.</i>

                </div> 
                <!-- /.col-lg-12 -->
            </div>
            <br/>
            <!-- /.row -->
            <div class="row">
                <div class="col-lg-12">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                           <label> Personal Details </label>
                        </div>
            <form method="POST" action="appview.php">
                        <div class="panel-body">
         
                            <div class="row">
                                  <div class="col-md-9">
                                    <div class="form-group">

                              <b> Position your applying for: </b>
                                  <select class="form-control" name="position">
                                    <option value=""> Hotel Driver </option>
                                    <option value=""> Bellman/Concierge </option>
                                    <option value=""> Office Assistant </option>
                                    <option value=""> Cashier/Collection Assistant </option>
                                    <option value=""> Waiter/Waitress </option>
                                    <option value=""> Sports and Recreation Receptionist/Lifeguard </option>
                                    <option value=""> Bartender </option>
                                    <option value=""> Tournament Coordinator </option>
                                    <option value=""> IT Programmer </option>
                                    <option value=""> Account/Bookeeper </option>
                                    <optgroup label="Housekeeping"/>
                                    <option value=""> - Room Attedant </option>
                                    <option value=""> - Public Area </option>
                                    <option value=""> - Wardrobe/Laundry Attendant </option>
                                    <optgroup label="Culinary"/>
                                    <option value=""> - Steward </option>
                                    <option value=""> - Assistant/Helper </option>
                                    <option value=""> Lobby Attendant/Receptionist </option>
                                    <optgroup label="Associates"/>
                                    <option value=""> - Promodizers/Retail Sales Asssociates </option>
                                    <option value=""> - Club Membership Reservations Asssociates </option>
                               
                                    
                                   </select> 
                                 </div>
                                 </div>
                            </div>

                            <div class="row">
                              
                             <div class="col-md-3">
                                   <div class="form-group">
                                        <b> First Name: </b> <input type="text" class="form-control" name="fname" style="width:250px;"> 
                                   </div>
                              </div>
                            
                              <div class="col-md-3">
                                   <div class="form-group">
                                       <b> Last Name: </b> <input type="text" class="form-control" name="lname" style="width:250px;"> 
                                   </div>
                              </div>
                               
                               <div class="col-md-3">
                                   <div class="form-group">
                                       <b> Middle Name: </b> <input type="text" class="form-control" name="mname" style="width:250px;"> 
                                   </div>
                                </div>
                            
                            </div>

                                <div class=""> &nbsp; </div>

                            <div class="row">

                                <div class="col-md-3">
                                      <div class="form-group">
                                       <b> Birth Date: </b> <input type="text" class="form-control" id="dob" name="dob" style="width:250px;">
                                      </div>
                                  
                                </div>
                                 <div class="col-md-3">
                                      <div class="form-group">
                                       <b> Age: </b> <input type="text" class="form-control" id="age" style="width:250px;" readonly />
                                      </div>
                                </div>
                                <div class="col-md-3">
                                      <div class="form-group">
                                       <b> Birth of Place: </b> <input type="text" class="form-control" name="bplace" placeholder="Ex. Antipolo City" style="width:250px;">
                                      </div>
                                </div>

                              </div>

                                  <div class=""> &nbsp; </div>  

                              <div class="row">

                                   <div class="col-md-3">
                                    <div class="form-group">
                                     <b>   Gender: </b>
                                        <div class="form-inline">
                                            <input type="radio" value="Male" name="gender" checked>  Male
                                
                                   
                                            <input type="radio" value="Female" name="gender">  Female
                                         </div>
                                      </div>
                                    </div>
                                    
                                    <div class="col-md-3">
                                      <div class="form-group">
                                      <b> Height: </b>  <input type="number" name="height"   class="form-control" placeholder="Ex. 5'4" style="width:250px;"> 
                                        </div>
                                    </div>
                                    <div class="col-md-3">
                                       <div class="form-group">
                                       <b> Weight: </b> <input type="number" name="weight"   class="form-control" placeholder="Ex. 100kg" style="width:250px;">
                                      </div>
                                     </div>
                                </div>

             <div class=""> &nbsp; </div>

                        <div class="row">
                                  <div class="col-md-3">   
                                    <div class="form-group">

                                   <b>     Civil Status: </b>  <select  class="form-control" name="cstatus" style="width:250px;">
                                        <option value="">Please choose</option>
                                        <option value="single">Single</option>
                                        <option value="married">Married</option>
                                        <option value="widowed">Widowed</option>
                                        <option value="separated">Separated</option>
                                        <option value="divorced">Divorced</option>
                                                          </select> 
                                    </div>
                                  </div>
                                  
                                  <div class="col-md-3">
                                    <div class="form-group">
                                       
                                      <b>  Nationality: </b>
                                               <select class="form-control" name="nation" style="width:250px;">
                                                        <option value=”—”>Please choose</option>
                                                        <option value=”AF”>Afghan</option>
                                                        <option value=”AX”>Åland Islander</option>
                                                        <option value=”AL”>Albanianr</option>
                                                        <option value=”DZ”>Algerian</option>
                                                        <option value=”AS”>American Samoan</option>
                                                        <option value=”AD”>Andorran</option>
                                                        <option value=”AO”>Angolan</option>
                                                        <option value=”AI”>Anguillan</option>
                                                        <option value=”AG”>of Antigua and Barbuda</option>
                                                        <option value=”AR”>Argentinian</option>
                                                        <option value=”AM”>Armenian</option>
                                                        <option value=”AW”>Aruban</option>
                                                        <option value=”AU”>Australian</option>
                                                        <option value=”AT”>Austrian</option>
                                                        <option value=”AZ”>Azerbaijani</option>
                                                        <option value=”BS”>Bahamian</option>
                                                        <option value=”BH”>Bahraini</option>
                                                        <option value=”BD”>Bangladeshi</option>
                                                        <option value=”BB”>Barbadian</option>
                                                        <option value=”BY”>Belarusian</option>
                                                        <option value=”BE”>Belgian</option>
                                                        <option value=”BZ”>Belizean</option>
                                                        <option value=”BJ”>Beninese</option>
                                                        <option value=”BM”>Bermudian</option>
                                                        <option value=”BT”>Bhutanese</option>
                                                        <option value=”BO”>Bolivian</option>
                                                        <option value=”BA”>of Bosnia and Herzegovina</option>
                                                        <option value=”BW”>Botswanan</option>
                                                        <option value=”BR”>Brazilian</option>
                                                        <option value=”VG”>British Virgin Islander</option>
                                                        <option value=”BN”>Bruneian</option>
                                                        <option value=”BG”>Bulgarian</option>
                                                        <option value=”BF”>Burkinabe</option>
                                                        <option value=”MM”>of Burma/Myanmar</option>
                                                        <option value=”BI”>Burundian</option>
                                                        <option value=”KH”>Cambodian</option>
                                                        <option value=”CM”>Cameroonian</option>
                                                        <option value=”CA”>Canadian</option>
                                                        <option value=”CV”>Cape Verdean</option>
                                                        <option value=”KY”>Caymanian</option>
                                                        <option value=”CF”>Central African</option>
                                                        <option value=”TD”>Chadian</option>
                                                        <option value=”CL”>Chilean</option>
                                                        <option value=”CN”>Chinese</option>
                                                        <option value=”CX”>Christmas Islander</option>
                                                        <option value=”CC”>Cocos Islander</option>
                                                        <option value=”CO”>Colombian</option>
                                                        <option value=”KM”>Comorian</option>
                                                        <option value=”CG”>Congolese</option>
                                                        <option value=”CK”>Cook Islander</option>
                                                        <option value=”CR”>Costa Rican</option>
                                                        <option value=”CI”>Ivorian</option>
                                                        <option value=”HR”>Croat</option>
                                                        <option value=”CU”>Cuban</option>
                                                        <option value=”CW”>Curaçaoan</option>
                                                        <option value=”CY”>Cypriot</option>
                                                        <option value=”CZ”>Czech</option>
                                                        <option value=”CD”>of the Democratic Republic of the Congo</option>
                                                        <option value=”DK”>Dane</option>
                                                        <option value=”DJ”>Djiboutian</option>
                                                        <option value=”DM”>Dominican</option>
                                                        <option value=”DO”>Dominican</option>
                                                        <option value=”TL”>East Timorese</option>
                                                        <option value=”EC”>Ecuadorian</option>
                                                        <option value=”EG”>Egyptian</option>
                                                        <option value=”SV”>Salvadorian</option>
                                                        <option value=”GQ”>Equatorial Guinean</option>
                                                        <option value=”ER”>Eritrean</option>
                                                        <option value=”EE”>Estonian</option>
                                                        <option value=”ET”>Ethiopian</option>
                                                        <option value=”FO”>Faeroese</option>
                                                        <option value=”FK”>Falkland Islander</option>
                                                        <option value=”FJ”>Fijian</option>
                                                        <option value=”FI”>Finn</option>
                                                        <option value=”FR”>Frenchman; Frenchwoman</option>
                                                        <option value=”GF”>Guianese</option>
                                                        <option value=”PF”>Polynesian</option>
                                                        <option value=”GA”>Gabonese</option>
                                                        <option value=”GM”>Gambian</option>
                                                        <option value=”GE”>Georgian</option>
                                                        <option value=”DE”>German</option>
                                                        <option value=”GH”>Ghanaian</option>
                                                        <option value=”GI”>Gibraltarian</option>
                                                        <option value=”EL”>Greek</option>
                                                        <option value=”GL”>Greenlander</option>
                                                        <option value=”GD”>Grenadian</option>
                                                        <option value=”GP”>Guadeloupean</option>
                                                        <option value=”GU”>Guamanian</option>
                                                        <option value=”GT”>Guatemalan</option>
                                                        <option value=”GG”>of Guernsey</option>
                                                        <option value=”GN”>Guinean</option>
                                                        <option value=”GW”>Guinea-Bissau national</option>
                                                        <option value=”GY”>Guyanese</option>
                                                        <option value=”HT”>Haitian</option>
                                                        <option value=”VA”>of the Holy See/of the Vatican</option>
                                                        <option value=”HN”>Honduran</option>
                                                        <option value=”HK”>Hong Kong Chinese</option>
                                                        <option value=”HU”>Hungarian</option>
                                                        <option value=”IS”>Icelander</option>
                                                        <option value=”IN”>Indian</option>
                                                        <option value=”ID”>Indonesian</option>
                                                        <option value=”IR”>Iranian</option>
                                                        <option value=”IQ”>Iraqi</option>
                                                        <option value=”IE”>Irishman; Irishwoman</option>
                                                        <option value=”IM”>Manxman; Manxwoman</option>
                                                        <option value=”IL”>Israeli</option>
                                                        <option value=”IT”>Italian</option>
                                                        <option value=”JM”>Jamaican</option>
                                                        <option value=”JP”>Japanese</option>
                                                        <option value=”JE”>of Jersey</option>
                                                        <option value=”JO”>Jordanian</option>
                                                        <option value=”KZ”>Kazakh</option>
                                                        <option value=”KE”>Kenyan</option>
                                                        <option value=”KI”>Kiribatian</option>
                                                        <option value=”KW”>Kuwaiti</option>
                                                        <option value=”KG”>Kyrgyz</option>
                                                        <option value=”LA”>Lao</option>
                                                        <option value=”LV”>Latvian</option>
                                                        <option value=”LB”>Lebanese</option>
                                                        <option value=”LS”>Basotho</option>
                                                        <option value=”LR”>Liberian</option>
                                                        <option value=”LY”>Libyan</option>
                                                        <option value=”LI”>Liechtensteiner</option>
                                                        <option value=”LT”>Lithuanian</option>
                                                        <option value=”LU”>Luxembourger</option>
                                                        <option value=”MO”>Macanese</option>
                                                        <option value=”MG”>Malagasy</option>
                                                        <option value=”MW”>Malawian</option>
                                                        <option value=”MY”>Malaysian</option>
                                                        <option value=”MV”>Maldivian</option>
                                                        <option value=”ML”>Malian</option>
                                                        <option value=”MT”>Maltese</option>
                                                        <option value=”MH”>Marshallese</option>
                                                        <option value=”MQ”>Martinican</option>
                                                        <option value=”MR”>Mauritanian</option>
                                                        <option value=”MU”>Mauritian</option>
                                                        <option value=”YT”>Mahorais</option>
                                                        <option value=”MX”>Mexican</option>
                                                        <option value=”FM”>Micronesian</option>
                                                        <option value=”MD”>Moldovan</option>
                                                        <option value=”MC”>Monegasque</option>
                                                        <option value=”MN”>Mongolian</option>
                                                        <option value=”ME”>Montenegrin</option>
                                                        <option value=”MS”>Montserratian</option>
                                                        <option value=”MA”>Moroccan</option>
                                                        <option value=”MZ”>Mozambican</option>
                                                        <option value=”NA”>Namibian</option>
                                                        <option value=”NR”>Nauruan</option>
                                                        <option value=”NP”>Nepalese</option>
                                                        <option value=”NL”>Dutchman; Dutchwoman; Netherlander</option>
                                                        <option value=”NC”>New Caledonian</option>
                                                        <option value=”NZ”>New Zealander</option>
                                                        <option value=”NI”>Nicaraguan</option>
                                                        <option value=”NE”>Nigerien</option>
                                                        <option value=”NG”>Nigerian</option>
                                                        <option value=”NU”>Niuean</option>
                                                        <option value=”NF”>Norfolk Islander</option>
                                                        <option value=”KP”>North Korean</option>
                                                        <option value=”MP”>Northern Mariana Islander</option>
                                                        <option value=”NO”>Norwegian</option>
                                                        <option value=”OM”>Omani</option>
                                                        <option value=”PK”>Pakistani</option>
                                                        <option value=”PW”>Palauan</option>
                                                        <option value=”PA”>Panamanian</option>
                                                        <option value=”PG”>Papua New Guinean</option>
                                                        <option value=”PY”>Paraguayan</option>
                                                        <option value=”PE”>Peruvian</option>
                                                        <option value=”PH” selected>Filipino</option>
                                                        <option value=”PN”>Pitcairner</option>
                                                        <option value=”PL”>Pole</option>
                                                        <option value=”PT”>Portuguese</option>
                                                        <option value=”PR”>Puerto Rican</option>
                                                        <option value=”QA”>Qatari</option>
                                                        <option value=”RE”>Reunionese</option>
                                                        <option value=”RO”>Romanian</option>
                                                        <option value=”RU”>Russian</option>
                                                        <option value=”RW”>Rwandan; Rwandese</option>
                                                        <option value=”BL”>of Saint Barthélemy</option>
                                                        <option value=”SH”>Saint Helenian</option>
                                                        <option value=”KN”>Kittsian; Nevisian</option>
                                                        <option value=”LC”>Saint Lucian</option>
                                                        <option value=”MF”>of Saint Martin</option>
                                                        <option value=”PM”>St-Pierrais; Miquelonnais</option>
                                                        <option value=”VC”>Vincentian</option>
                                                        <option value=”WS”>Samoan</option>
                                                        <option value=”SM”>San Marinese</option>
                                                        <option value=”ST”>São Toméan</option>
                                                        <option value=”SA”>Saudi Arabian</option>
                                                        <option value=”SN”>Senegalese</option>
                                                        <option value=”RS”>Serb</option>
                                                        <option value=”SC”>Seychellois</option>
                                                        <option value=”SL”>Sierra Leonean</option>
                                                        <option value=”SG”>Singaporean</option>
                                                        <option value=”SX”>Sint Maartener</option>
                                                        <option value=”SK”>Slovak</option>
                                                        <option value=”SI”>Slovene</option>
                                                        <option value=”SB”>Solomon Islander</option>
                                                        <option value=”SO”>Somali</option>
                                                        <option value=”ZA”>South African</option>
                                                        <option value=”KR”>South Korean</option>
                                                        <option value=”SS”>South Sudanese</option>
                                                        <option value=”ES”>Spaniard</option>
                                                        <option value=”LK”>Sri Lankan</option>
                                                        <option value=”SD”>Sudanese</option>
                                                        <option value=”SR”>Surinamer</option>
                                                        <option value=”SJ”>of Svalbard, of Jan Mayen</option>
                                                        <option value=”SZ”>Swazi</option>
                                                        <option value=”SE”>Swede</option>
                                                        <option value=”CH”>Swiss</option>
                                                        <option value=”SY”>Syrian</option>
                                                        <option value=”TW”>Taiwanese</option>
                                                        <option value=”TJ”>Tajik</option>
                                                        <option value=”TZ”>Tanzanian</option>
                                                        <option value=”TH”>Thai</option>
                                                        <option value=”TG”>Togolese</option>
                                                        <option value=”TK”>Tokelauan</option>
                                                        <option value=”TO”>Tongan</option>
                                                        <option value=”TT”>Trinidadian; Tobagonian</option>
                                                        <option value=”TN”>Tunisian</option>
                                                        <option value=”TR”>Turk</option>
                                                        <option value=”TM”>Turkmen</option>
                                                        <option value=”TC”>Turks and Caicos Islander</option>
                                                        <option value=”TV”>Tuvaluan</option>
                                                        <option value=”UG”>Ugandan</option>
                                                        <option value=”UA”>Ukrainian</option>
                                                        <option value=”AE”>Emirian</option>
                                                        <option value=”UK”>Briton</option>
                                                        <option value=”US”>American;US citizen</option>
                                                        <option value=”UY”>Uruguayan</option>
                                                        <option value=”VI”>US Virgin Islander</option>
                                                        <option value=”UZ”>Uzbek</option>
                                                        <option value=”VU”>Vanuatuan</option>
                                                        <option value=”VE”>Venezuelan</option>
                                                        <option value=”VN”>Vietnamese</option>
                                                        <option value=”WF”>Wallisian</option>
                                                        <option value=”EH”>Sahrawi</option>
                                                        <option value=”YE”>Yemenite</option>
                                                        <option value=”ZM”>Zambian</option>
                                                        <option value=”ZW”>Zimbabwean</option>
                                                </select>
                                          </div>      
                                    </div>

                                  <div class="col-sm-4">
                                      <div class="form-group">
                                       <b> Religion: </b>  <select name="religion" class="form-control" style="width:250px">
                                            
                                              <option value="">-- select one --</option>
                                              <option value="Roman Catholic">Roman Catholic</option>
                                              <option value="Muslim">Muslim</option>
                                              <option value="Evangelical">Evangelical</option>
                                              <option value="Iglesia ni Kristo">Iglesia ni Kristo</option>
                                              <option value="Aglipayan">Aglipayan</option>
                                              <option value="other Christian"> other Christian</option>
                                              <option value="other">other</option>
                                             <option value="unspecified">unspecified</option>
                                            </select>
                                      </div>
                            
                                  </div>

                          </div>

                           <div class=""> &nbsp; </div>

                            <div class="row">
                                <div class="col-sm-6">   
                                    <div class="form-group">
                                    <b> Primary </b> 
                                         <b> Contact Number: </b> 
                                            <div class="form-inline">
                                            <select name="areacode" id="" class="form-control"> <option value="">Area Code</option>
                                              <option value="62 ">62</option>
                                              <option value="65">65</option>
                                              <option value="47">47</option>
                                              <option value="4761">4761</option>
                                              <option value="4765">4765</option>
                                              <option value="55">55</option>
                                              <option value="68">68</option>
                                              <option value="45">45</option>
                                              <option value="8622">8622</option>
                                              <option value="86">86</option>
                                              <option value="64">64</option>
                                              <option value="83">83</option>
                                              <option value="56">56</option>
                                              <option value="2">2</option>
                                              <option value="42">42</option>
                                              <option value="4244">4244</option>
                                              <option value="4235">4235</option>
                                              <option value="4251">4251</option>
                                              <option value="4264">4264</option>
                                              <option value="42793">42793</option>
                                              <option value="75">75</option>
                                              <option value="45">45</option>
                                              <option value="4593">4593</option>
                                              <option value="4594">4594</option>
                                              <option value="4597">4597</option>
                                              <option value="48">48</option>
                                              <option value="78">78</option>
                                              <option value="6422">6422</option>
                                              <option value="6423">6423</option>              
                                              <option value="35">35</option>           
                                              <option value="34">34</option>
                                              <option value="3461">3461</option>
                                              <option value="34691">34691</option>
                                              <option value="74">74</option>
                                              <option value="88">88</option>
                                             


                                            </select>
                                            <input type="tel" class="form-control" name="pcontl" placeholder="Landline" style="width:230px;">
                                            </div>
                                            <div class=""> &nbsp; </div>
                                            <div class="form-inline">
                                            +69 
                                            <input type="tel" class="form-control" name="pcontc" placeholder="Cellphone" style="width:230px;">
                                            </div>
                                     </div>
                                  </div>

                                   <div class="col-md-6"> 
                                      <div class="form-group">
                                        <b> Secondary </b> 
                                           <b> Contact Number: </b> <span class="" style="color:red;"> (Optional) </span>
                                              
                                              <input type="tel" class="form-control" name="stel" placeholder="Landline" style="width:230px;">
                                              <div class=""> &nbsp; </div>
                                              <div class="form-inline">
                                              +69
                                              <input type="tel" class="form-control" name="scel" placeholder="Cellphone" style="width:230px;"> 
                                              </div>
                                       </div>
                                    </div>      
                              </div>
                          

                            <div class=""> &nbsp; </div>

                            <div class="row">

                                 <div class="col-sm-3">   
                                       <b> Present Address </b>
                                 </div>
                            </div>

                            <div class="row col-sm-offset-0">   
                                  <div class="col-sm-4">
                                       <div class="form-group"> 
                                          <b> Street: </b>  
                                            <input type="text" name="addstrt" placeholder="Ex. 561 J.Rizal St." class="form-control"  style="width: 300px;"> 
                                        </div>
                                  </div>

                                  <div class="col-sm-4">
                                       <div class="form-group"> 
                                          <b> Village: </b>  
                                            <input type="text" name="addstrt" placeholder="Ex. Subdivision village" class="form-control"  style="width: 300px;"> 
                                        </div>
                                  </div>

                                  <div class="col-sm-4">
                                       <div class="form-group"> 
                                          <b> Barangay: </b>  
                                            <input type="text" name="addstrt" placeholder="Ex. Barangay Vergara" class="form-control"  style="width: 300px;"> 
                                        </div>
                                  </div>

                            </div>

                            <div class="row col-sm-offset-0">   
                                  <div class="col-sm-4">
                                    <div class="form-group">
                                            <b>   City: </b> 
                                                     <input type="text" name="addcity" placeholder="Ex. Mandaluyong" class="form-control"  style="width: 300px;"> 
                                    </div>
                                  </div>

                                  <div class="col-sm-4">
                                    <div class="form-group">
                                            <b>   Province: </b> 
                                            
                                                    <select name="country" class="form-control" style="width: 300px;">
                                                      <option value="">Please Select</option>
                                                      <option value="1">Metro Manila</option>
                                                      <option value="2">Abra</option>
                                                      <option value="3">Agusan del Norte</option>
                                                      <option value="4">Agusan del Sur</option>
                                                      <option value="5">Aklan</option>
                                                      <option value="6">Albay</option>
                                                      <option value="7">Antique</option>
                                                      <option value="8">Apayao</option>
                                                      <option value="9">Aurora</option>
                                                      <option value="10">Basilan</option>
                                                      <option value="11">Bataan</option>
                                                      <option value="12">Batanes</option>
                                                      <option value="13">Batangas </option>
                                                      <option value="14">Benguet </option>
                                                      <option value="15">Biliran </option>
                                                      <option value="16">Bohol </option>
                                                      <option value="17">Bukidnon </option>
                                                      <option value="18">Bulacan </option>
                                                      <option value="19">Cagayan </option>
                                                      <option value="20">Camarines Norte </option>
                                                      <option value="21">Camarines Sur </option>
                                                      <option value="22">Camiguin </option>
                                                      <option value="23">Capiz </option>
                                                      <option value="24">Catanduanes </option>
                                                      <option value="25">Cavite </option>
                                                      <option value="26">Cebu </option>
                                                      <option value="27">Compostela Valley </option>
                                                      <option value="28">Cotabato </option>
                                                      <option value="29">Davao del Norte </option>
                                                      <option value="30">Davao del Sur </option>
                                                      <option value="31">Davao Oriental </option>
                                                      <option value="32">Dinagat Islands </option>
                                                      <option value="33">Eastern Samar </option>
                                                      <option value="34">Guimaras </option>
                                                      <option value="35">Ifugao </option>
                                                      <option value="36">Ilocos Norte </option>
                                                      <option value="37">Ilocos Sur </option>
                                                      <option value="38">Iloilo </option>
                                                      <option value="39">Isabela </option>
                                                      <option value="40">Kalinga </option>
                                                      <option value="41">La Union </option>
                                                      <option value="42">  Laguna </option>
                                                      <option value="43">  Lanao del Norte </option>
                                                      <option value="44">  Lanao del Sur </option>
                                                      <option value="45">  Leyte </option>
                                                      <option value="46">  Maguindanao </option>
                                                      <option value="47"> Marinduque </option>
                                                      <option value="48">  Masbate </option>
                                                      <option value="49">  Misamis Occidental </option>
                                                      <option value="50">  Misamis Oriental </option>
                                                      <option value="51">  Mountain Province </option>
                                                      <option value="52">  Negros Occidental </option>
                                                      <option value="53">  Negros Oriental </option>
                                                      <option value="54">  Northern Samar </option>
                                                      <option value="55">  Nueva Ecija </option>
                                                      <option value="56">  Nueva Vizcaya </option>
                                                      <option value="57">  Occidental Mindoro </option>
                                                      <option value="58">  Oriental Mindoro </option>
                                                      <option value="59">  Palawan </option>
                                                      <option value="60">  Pampanga </option>
                                                      <option value="61">  Pangasinan </option>
                                                      <option value="62">  Quezon </option>
                                                      <option value="63">  Quirino </option>
                                                      <option value="64">  Rizal </option>
                                                      <option value="65">  Romblon </option>
                                                      <option value="66">  Samar </option>
                                                      <option value="67">  Sarangani </option>
                                                      <option value="68">  Siquijor </option>
                                                      <option value="69">  Sorsogon </option>
                                                      <option value="70">  South Cotabato </option>
                                                      <option value="71">  Southern Leyte </option>
                                                      <option value="72">  Sultan Kudarat </option>
                                                      <option value="73">  Sulu </option>
                                                      <option value="74">  Surigao del Norte </option>
                                                      <option value="75">  Surigao del Sur </option>
                                                      <option value="76">  Tarlac </option>
                                                      <option value="77">  Tawi-Tawi </option>
                                                      <option value="78">  Zambales </option>
                                                      <option value="79">  Zamboanga del Norte </option>
                                                      <option value="80">  Zamboanga del Sur </option>
                                                      <option value="81"> Zamboanga Sibugay </option>
                                                    </select>
 
                                                          

                                    </div>
                                  </div>
                                


                                   <div class="col-sm-4">
                                    <div class="form-group">
                                            <b>   Municipal: </b> 
                                                
                                                              <select id="cityAjax" name="city" class="form-control" style="width: 300px;">
                                                                 <option value="">Please Select</option>
                                                             </select>
                                                   
                                    </div>
                                  </div>

                             </div>

                             <div class="row col-sm-offset-0"> 
                                  <div class="col-sm-4">
                                    <div class="form-group">
                                            <b>   Country: </b> 
                                            <select name="addcountry"  class="form-control" style="width: 300px;">
                                            <option value="0">----</option>
                                            <option value="260">Afghanistan</option>
                                            <option value="100">Aland Islands</option>
                                            <option value="103">Albania</option>
                                            <option value="104">Algeria</option>
                                            <option value="119">American Samoa</option>
                                            <option value="135">Andorra</option>
                                            <option value="175">Angola</option>
                                            <option value="200">Anguilla</option>
                                            <option value="221">Antigua and Barbuda</option>
                                            <option value="236">Argentina</option>
                                            <option value="14">Armenia</option>
                                            <option value="13">Aruba</option>
                                            <option value="1">Australia</option>
                                            <option value="15">Austria</option>
                                            <option value="16">Azerbaijan</option>
                                            <option value="17">Bahamas, The</option>
                                            <option value="18">Bahrain</option>
                                            <option value="19">Bangladesh</option>
                                            <option value="20">Barbados</option>
                                            <option value="21">Belarus</option>
                                            <option value="22">Belgium</option>
                                            <option value="23">Belize</option>
                                            <option value="24">Benin</option>
                                            <option value="25">Bermuda</option>
                                            <option value="26">Bhutan</option>
                                            <option value="27">Bolivia</option>
                                            <option value="28">Bonaire, Sint Eustatius and Saba</option>
                                            <option value="29">Bosnia and Herzegovina</option>
                                            <option value="30">Botswana</option>
                                            <option value="31">Bouvet Island</option>
                                            <option value="32">Brazil</option>
                                            <option value="33">British Indian Ocean Territory</option>
                                            <option value="250">British Virgin Islands</option>
                                            <option value="34">Brunei Darussalam</option>
                                            <option value="35">Bulgaria</option>
                                            <option value="36">Burkina Faso</option>
                                            <option value="37">Burundi</option>
                                            <option value="38">Cambodia</option>
                                            <option value="39">Cameroon</option>
                                            <option value="40">Canada</option>
                                            <option value="41">Cape Verde</option>
                                            <option value="42">Cayman Islands</option>
                                            <option value="43">Central African Republic</option>
                                            <option value="44">Chad</option>
                                            <option value="251">Channel Islands</option>
                                            <option value="45">Chile</option>
                                            <option value="46">China</option>
                                            <option value="47">Christmas Island</option>
                                            <option value="48">Cocos (Keeling) Islands</option>
                                            <option value="49">Colombia</option>
                                            <option value="50">Comoros</option>
                                            <option value="51">Congo, Democratic Republic of the</option>
                                            <option value="52">Congo, Republic of the</option>
                                            <option value="53">Cook Islands</option><option value="54">Costa Rica</option><option value="55">Cote d'Ivoire</option><option value="56">Croatia</option><option value="57">Cuba</option><option value="58">Curacao</option><option value="59">Cyprus</option><option value="60">Czech Republic</option><option value="61">Denmark</option><option value="62">Djibouti</option><option value="63">Dominica</option><option value="64">Dominican Republic</option><option value="65">Ecuador</option><option value="66">Egypt</option><option value="67">El Salvador</option><option value="68">Equatorial Guinea</option><option value="69">Eritrea</option><option value="70">Estonia</option><option value="71">Ethiopia</option><option value="72">Falkland Islands (Islas Malvinas)</option><option value="73">Faroe Islands</option><option value="74">Fiji</option><option value="75">Finland</option><option value="76">France</option><option value="77">French Guiana</option><option value="78">French Polynesia</option><option value="79">French Southern and Antarctic Lands</option><option value="80">Gabon</option><option value="81">Gambia</option><option value="82">Georgia</option><option value="83">Germany</option><option value="84">Ghana</option><option value="85">Gibraltar</option><option value="86">Greece</option><option value="87">Greenland</option><option value="88">Grenada</option><option value="89">Guadeloupe</option><option value="90">Guam</option><option value="91">Guatemala</option><option value="93">Guinea</option><option value="94">Guinea-Bissau, Republic of</option><option value="95">Guyana</option><option value="96">Haiti</option><option value="97">Heard Island and McDonald Islands</option><option value="98">Holy See (Vatican City)</option><option value="99">Honduras</option><option value="2">Hong Kong</option><option value="101">Hungary</option><option value="102">Iceland</option><option value="3">India</option><option value="4">Indonesia</option><option value="105">Iran, Islamic Republic of</option><option value="106">Iraq</option><option value="107">Ireland</option><option value="108">Isle of Man</option><option value="109">Israel</option><option value="110">Italy</option><option value="111">Jamaica</option><option value="112">Japan</option><option value="114">Jordan</option><option value="115">Kazakhstan</option><option value="116">Kenya</option><option value="117">Kiribati</option><option value="118">Korea, North</option><option value="5">Korea, South</option><option value="252">Kosovo</option><option value="120">Kuwait</option><option value="121">Kyrgyzstan</option><option value="122">Lao People'S Democratic Republic</option><option value="123">Latvia</option><option value="124">Lebanon</option><option value="125">Lesotho</option><option value="126">Liberia</option><option value="127">Libya</option><option value="128">Liechtenstein</option><option value="129">Lithuania</option><option value="130">Luxembourg</option><option value="131">Macau</option><option value="132">Macedonia</option><option value="133">Madagascar</option><option value="134">Malawi</option><option value="6">Malaysia</option><option value="136">Maldives</option><option value="137">Mali</option><option value="138">Malta</option><option value="139">Marshall Islands</option><option value="140">Martinique</option><option value="141">Mauritania</option><option value="142">Mauritius</option><option value="143">Mayotte</option><option value="144">Mexico</option><option value="145">Micronesia, Federated States of</option><option value="146">Moldova</option><option value="147">Monaco</option><option value="148">Mongolia</option><option value="149">Montenegro</option><option value="150">Montserrat</option><option value="151">Morocco</option><option value="152">Mozambique</option><option value="153">Myanmar</option><option value="154">Namibia</option><option value="155">Nauru</option><option value="156">Nepal</option><option value="157">Netherlands</option><option value="158">New Caledonia</option><option value="159">New Zealand</option><option value="160">Nicaragua</option><option value="161">Niger</option><option value="162">Nigeria</option><option value="163">Niue</option><option value="164">Norfolk Island</option><option value="165">Northern Mariana Islands</option><option value="166">Norway</option><option value="167">Oman</option><option value="168">Pakistan</option><option value="169">Palau</option><option value="170">Palestinian Territory</option><option value="171">Panama</option><option value="172">Papua New Guinea</option><option value="173">Paraguay</option><option value="174">Peru</option><option value="PH" selected>Philippines</option><option value="176">Pitcairn</option><option value="177">Poland</option><option value="178">Portugal</option><option value="179">Puerto Rico</option><option value="180">Qatar</option><option value="181">Reunion</option><option value="182">Romania</option><option value="183">Russian Federation</option><option value="184">Rwanda</option><option value="185">Saint Barthelemy</option><option value="186">Saint Helena, Ascension, and Tristan da Cunha</option><option value="187">Saint Kitts and Nevis</option><option value="188">Saint Lucia</option><option value="189">Saint Martin (French Part)</option><option value="190">Saint Pierre and Miquelon</option><option value="191">Saint Vincent and the Grenadines</option><option value="192">Samoa</option><option value="193">San Marino</option><option value="194">Sao Tome and Principe</option><option value="195">Saudi Arabia</option><option value="196">Senegal</option><option value="197">Serbia</option><option value="198">Seychelles</option><option value="199">Sierra Leone</option><option value="8">Singapore</option><option value="201">Sint Maarten (Dutch Part)</option><option value="202">Slovakia</option><option value="203">Slovenia</option><option value="204">Solomon Islands</option><option value="205">Somalia</option><option value="206">South Africa</option><option value="207">South Georgia and South Sandwich Islands</option><option value="208">South Sudan</option><option value="209">Spain</option><option value="210">Sri Lanka</option><option value="211">Sudan</option><option value="212">Suriname</option><option value="213">Svalbard and Jan Mayen</option><option value="214">Swaziland</option><option value="215">Sweden</option><option value="216">Switzerland</option><option value="217">Syria</option><option value="9">Taiwan</option><option value="219">Tajikistan</option><option value="220">Tanzania</option><option value="10">Thailand</option><option value="222">Timor-Leste</option><option value="223">Togo</option><option value="224">Tokelau</option><option value="225">Tonga</option><option value="226">Trinidad and Tobago</option><option value="227">Tunisia</option><option value="228">Turkey</option><option value="229">Turkmenistan</option><option value="230">Turks and Caicos Islands</option><option value="231">Tuvalu</option><option value="232">Uganda</option><option value="233">Ukraine</option><option value="234">United Arab Emirates</option><option value="235">United Kingdom</option><option value="237">United States Minor Outlying Islands</option><option value="11">USA</option><option value="238">Uruguay</option><option value="239">Uzbekistan</option><option value="240">Vanuatu</option><option value="241">Venezuela</option><option value="242">Vietnam</option><option value="244">Virgin Islands (U.S.)</option><option value="245">Wallis and Futuna</option><option value="246">Western Sahara</option><option value="247">Yemen</option><option value="248">Zambia</option><option value="249">Zimbabwe</option></select>

                                        </div>      
                                  </div>
                            </div>

                                      
                                  </div>
                            </div>


                            <!-- /.row (nested) -->
                   
                     
                        <!-- /.panel-body -->
              
                    <!-- /.panel -->
             <div class="row">    
                <div class="col-sm-12">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                             <label>   Educational Background </label>
                         </div>

                        <!-- /.panel-heading -->
                        <div class="panel-body">

                          <div class="row">
                          <div class="col-sm-9">
                              <div class="form-group">

                          <b> Highest Education Level: </b> 
                                 <div class="col-sm-offset-1">
                                              <select name="highed" class="form-control" id="educ">
                                                   <option id="0" value=""> -- Please choose --</option>
                                                   <option id="1" value="1">Degree</option>
                                                   <option id="2" value="2">Vocational/Short Courses/Diploma</option>
                                                   <option id="3" value="3">High School</option>
                                                   <option id="5" value="5">Elementary</option>
                                              </select>   
                                  </div>
                              </div>

                          </div> 
                        </div>

                            

                                     <div id='TextBoxesGroup3'>
                                                     <div id="TextBoxDiv3">
                                                              
                                                     </div>
                                       </div>

                               <div class=""> &nbsp; </div>                  
                               <div class="form-inline pull-right">
                                  <input type='button' class="btn-default" value='Add' id='addButton3'> 
                                  <input type='button' class="btn-danger" value='Remove' id='removeButton3'>
                               </div>


                        <div class="row">
                          <div class="col-sm-12">
                                   <label>  College </label>
                            </div>
                          </div>

                          <div class="row">
                                 <div class="col-sm-12 col-sm-offset-1">
                                <div class="form-group">
                                          <label class="radio-inline">
                                                <input type="radio" name="optionsRadiosInline" id="optionsRadiosInline1" value="colgrad" checked>Graduate
                                            </label>
                                            <label class="radio-inline">
                                                <input type="radio" name="optionsRadiosInline" id="optionsRadiosInline2" value="colungrad">Undergraduate
                                            </label>
                              </div>
                            </div>
                          </div> 

                          <div class="row">
                          <div class="col-sm-12">
                            <div class="form-group">
                              
                              <div class="col-sm-offset-1">
                                 <label>   Name of School:  </label>
                                 <input type="text" class="form-control" placeholder="Ex. FEU Institute of Technology" name="cschool" style="width:550px;" id="textBoxCol" disabled>
                                  <label> Course: </label>
                                  <input type="text" class="form-control" name="course" placeholder="Ex. Bachelor of Science in Information Technology"  style="width:550px;"  id="textBoxColc" disabled>
                                   <div class="">  &nbsp; </div>
                                 <label>  Year Graduated </label>
                                  
                                  <div class="form-inline">
                                    <label>    From:</label>  <input type="text" class="form-control" name="yrfrom"  id="colBoxfr"> 
                         <label>   To: </label>  <input type="text" class="form-control" name="yrto"  id="colBoxr"> 
                                  <label> <div id='show-me' style='display:none'> Highest Educational Attainment: <select id="" name=""> 
                                        <option value="1st"> 1st year college </option>
                                         <option value="2nd"> 2nd year college </option>
                                          <option value="3rd"> 3rd year college </option>
                                           <option value="4th"> 4th year college </option>
                                  </select></div> </label>

                                  </div>
                            

                                </div> 
                            </div>
                          </div>    
                       </div>



                          <div class="row">
                              <div class="col-sm-12" id="vocDiv" style="display:none;">
                                  <label> Vocational </label>
                                <div class="form-group">
                                  <div class="col-sm-offset-1">
                                        <label> Name of school: </label> <input type="text" id="" name="vocname"  class="form-control" style="width:550px;" />
                                         <label> Certificate title: </label>  <input type="text" id="" name="voccours"  class="form-control" style="width:550px;" />
                                       <label> Year finished:</label>
                                        <div class="form-inline">
                                          From: <input type="text" name="vocfrom" id=""  class="form-control" />
                                          To: <input type="text" name="vocto" id=""  class="form-control"/>
                                        </div>
                                  </div>
                                </div>
                              </div>
                            </div>




                     <div class=""> &nbsp; </div>

                         <div class="row">
                          <div class="col-sm-12">
                                   <label>  Secondary </label>
                            </div>
                          </div>

                          <div class="row">
                              <div class="col-sm-12 col-sm-offset-1">
                                <div class="form-group">
                                          <label class="radio-inline">
                                                <input type="radio" name="optionsRadiosInline11" id="optionsRadiosInline11" value="secgrad" checked>Graduate
                                            </label>
                                            <label class="radio-inline">
                                                <input type="radio" name="optionsRadiosInline11" id="optionsRadiosInline22" value="secungrad">Undergraduate
                                            </label>
                              </div>
                            </div>
                          </div>

                          <div class="row">
                            <div class="col-sm-12">
                              <div class="form-group">
                                 <div class="col-sm-offset-1">
                                   <label>  Name of School: </label>
                                    <input type="text" class="form-control" name="secschool" style="width:550px;" id="textBoxSec" disabled> 
                                    <div class="">  &nbsp; </div>
                                      <div class="form-inline">
                                     <label>    From: </label>  <input type="text" class="form-control" name="secyrfrom"  id="textBoxSecf" disabled> 
                                   <label>   To: </label>   <input type="text" class="form-control" name="secyrto"  id="textBoxSect" disabled> 
                                    </div>
                                  </div>  
                                </div>
                            </div>
                          </div>
                           
                         <div class="row">
                          <div class="col-sm-12">
                                   <label>  Primary </label>
                            </div>
                          </div>

                          <div class="row">
                              <div class="col-sm-12 col-sm-offset-1">
                                <div class="form-group">
                                          <label class="radio-inline">
                                                <input type="radio" name="optionsRadiosInline111" id="optionsRadiosInline111" value="prigrad" checked>Graduate
                                            </label>
                                            <label class="radio-inline">
                                                <input type="radio" name="optionsRadiosInline111" id="optionsRadiosInline222" value="priungrad">Undergraduate
                                            </label>
                              </div>
                            </div>
                          </div>

                          <div class="row">
                            <div class="col-sm-12">
                              <div class="form-group">
                                 <div class="col-sm-offset-1">
                                   <label>  Name of School: </label>
                                    <input type="text" class="form-control" name="pricschool" style="width:550px;" id="textBoxOne"> 
                                    <div class=""> &nbsp; </div>
                                    <div class="form-inline">
                                        <label>    From: </label>  <input type="date" class="form-control" name="priyrfrom" id="textBoxOnef"> 
                                   <label>   To: </label>   <input type="date" class="form-control" name="priyrto" id="textBoxOnet"> 
                                    </div>
                                  </div>
                                </div>
                            </div>
                          </div>
                           
                                    
                        </div>
                    </div>
                 </div>
                </div>
             

            <div class="row">    
                <div class="col-sm-12">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                             <label>   Skills /  Qualification</label>
                         </div>

                        <!-- /.panel-heading -->
                        <div class="panel-body">
                            <div class="row">
                              <div class="col-sm-3">
                              <div class="form-group">
                                    
                                            <label> IT/PROGRAMMER </label>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">PHP
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">JSON
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">JQuery
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">AJAX
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">mySQL
                                                </label>
                                            </div>
                                      
   <!--
                                            <div class=""></div>

                                                <div id='TextBoxesGroup2'>
                                                     <div id="TextBoxDiv2">
                                                                
                                                       
                                                     </div>
                                                </div>
                                                <br/>
                                                         <input type='button' class="btn-default" value='Add' id='addButton2'> 
                                                         <input type='button' class="btn-danger" value='Remove' id='removeButton2'>
                                             
                                     <input type='button' value='Get TextBox Value' id='getButtonValue2'> -->

                                   </div> 
                                </div>
                                 <div class="col-sm-3">
                              <div class="form-group">
                                    
                                            <label> HOTEL DRIVER </label>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Knows how to drive
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Knows how to drive
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Knows how to drive
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Knows how to drivew
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Knows how to drive
                                                </label>
                                            </div>
                                      
   <!--
                                            <div class=""></div>

                                                <div id='TextBoxesGroup2'>
                                                     <div id="TextBoxDiv2">
                                                                
                                                       
                                                     </div>
                                                </div>
                                                <br/>
                                                         <input type='button' class="btn-default" value='Add' id='addButton2'> 
                                                         <input type='button' class="btn-danger" value='Remove' id='removeButton2'>
                                             
                                     <input type='button' value='Get TextBox Value' id='getButtonValue2'> -->

                                   </div> 
                                </div>
                                 <div class="col-sm-3">
                              <div class="form-group">
                                    
                                            <label> BELLMAN/CONCIERGE </label>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Clean room
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Clean room
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Clean room
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Clean room
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Clean room
                                                </label>
                                            </div>
                                      
   <!--
                                            <div class=""></div>

                                                <div id='TextBoxesGroup2'>
                                                     <div id="TextBoxDiv2">
                                                                
                                                       
                                                     </div>
                                                </div>
                                                <br/>
                                                         <input type='button' class="btn-default" value='Add' id='addButton2'> 
                                                         <input type='button' class="btn-danger" value='Remove' id='removeButton2'>
                                             
                                     <input type='button' value='Get TextBox Value' id='getButtonValue2'> -->

                                   </div> 
                                </div>
                                 <div class="col-sm-3">
                              <div class="form-group">
                                    
                                            <label> Office Assistant  </label>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Paper works
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Paper works
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Paper works
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Paper works
                                                </label>
                                            </div>
                                            <div class="checkbox">
                                                <label>
                                                    <input type="checkbox" value="">Paper works 
                                                </label>
                                            </div>
                                      
   <!--
                                            <div class=""></div>

                                                <div id='TextBoxesGroup2'>
                                                     <div id="TextBoxDiv2">
                                                                
                                                       
                                                     </div>
                                                </div>
                                                <br/>
                                                         <input type='button' class="btn-default" value='Add' id='addButton2'> 
                                                         <input type='button' class="btn-danger" value='Remove' id='removeButton2'>
                                             
                                     <input type='button' value='Get TextBox Value' id='getButtonValue2'> -->

                                   </div> 
                                </div>
                           </div>
                        </div>
                    </div>
                 </div>
          </div>

          <div class="">

            

          </div>

          <div class="row">
            <div class="col-sm-12">
              <div class="panel panel-default">
                <div class="panel-heading">
                  <label> Career Details</label>
                </div> 
                <div class="panel-body">
                  <div class="form-group">
                     <label> Company name: </label><input type="text" name="cnane" id="" class="form-control" style="width:530px;"/>
                     <label> Position:</label> <input type="text" name="cposition" id=""  class="form-control" style="width:530px;"/>
                     <label> Address:</label></label> <input type="text" name="caddress" id=""  class="form-control" style="width:530px;"/>
                     <label> Date Employed</label>
                        <div class="form-inline">
                            from: <input type="text" name="cfrom" id="datepickerln1"  class="form-control" style="width:170px"/>
                            to: <input type="Text" name="cto" id="datepickerln2"  class="form-control" style="width:170px"/>
                            total years: <input type="text" class="form-control" name="ytotal" readonly id="ytotal" style="width:40px"/>
                        </div>
                       
                                 
                               <!--  Year: <input type="text" name=""  readonly/>
                                  Month: <input type="text" name="mtotal" id="mtotal" readonly/>
                                  Day: <input type="text" name="total" id="total" readonly/>

                              -->
                          
                            
                            <div id='TextBoxesGroup'>
                                                     <div id="TextBoxDiv">
                                                              
                                                     </div>
                                                </div>

                               <div class=""> &nbsp; </div>                  
                               <div class="form-inline pull-right">
                                  <input type='button' class="btn-default" value='Add' id='addButton'> 
                                  <input type='button' class="btn-danger" value='Remove' id='removeButton'>
                               </div>
                  </div>                    
                </div>
              </div>
            </div>
          </div>



             <div class="row">    
                <div class="col-sm-12">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                             <label>   Photo </label>
                         </div>

                        <!-- /.panel-heading -->
                        <div class="panel-body">
                              <div class="row">
                                <div class="col-md-3">
                                 <div class="form-group"> 

                                   <b> Upload your 2x2: </b> <div class=""> &nbsp; </div>
                                        <block> Supported Format: <span style="color: red;"> .jpg/.jpeg/.jpe/ </span></block> 
                                  
                                </div>
                              </div>
                         
                                                       
                               <div class="col-md-3">
                                <div class="form-group">
                                    <div id="croppic"></div>

                                    <div class="col-sm-offset-5">
                                   <span class="btn" id="cropContainerHeaderButton">Choose File</span>
                                 </div>
                               </div>
                                  </div><!-- /col-lg-6 -->
                            </div>
                        </div>
                    </div>
                 </div>
             </div>

              <div class="row">    
                <div class="col-sm-12">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                             <label>   Account Settings</label>
                         </div>

                        <!-- /.panel-heading -->
                        <div class="panel-body">
                        

                               <?php             
                                  include('../include/dbcon.php');
                                  
                                  $result = mysql_query("SELECT email,password FROM tb_info WHERE uid='$userId'");
                                  while($row = mysql_fetch_array($result))
                                  { 
                                ?>  


                            
                                 <div class="form-group"> 

                                   <b> Username: </b>
                                          <div class="col-sm-offset-1"> <input type="email" class="form-control" name="email" Placeholder="Email" value='<?php echo $row['email'] ?>' style="width: 300px;"> </div>
                                  </div>
                              
                                    
                                 <div class="form-group"> 

                                   <b> Password: </b>
                                           <div class="col-sm-offset-1"> <input type="password" class="form-control" name="pword" Placeholder="Password" value='<?php echo $row['password'] ?>' style="width: 300px;">
                                            </div>
                                <?php 
                                    }
                                  ?>
                                  </div>
                                  

                           </div>
                        </div>
                    </div>
                 </div>
                
          

                 <div class="well">
                    <div class="form-inline">
                            <input type="submit" value="Save" class="btn btn-success">  </input>  
                             <a href="appedit.php" class="btn btn-danger"> Cancel </a>
                    </div>
                </div>
        </form>

       
                <!-- /.col-lg-12 -->
            </div>
            <!-- /.row -->
        </div>
        <!-- /#page-wrapper -->

    </div>
    <!-- /#wrapper -->

    <!-- jQuery Version 1.11.0 -->

    <script src="js/jquery-1.11.0.js"></script>
    <script src="js/jquery-1.10.2.js"></script>

    <!-- Bootstrap Core JavaScript -->
     <script src="assets/js/bootstrap.min.js"></script>
    <script src="js/bootstrap.min.js"></script>
   
    <!--  Menu Plugin JavaScript -->
    <script src="js/plugins/metisMenu/metisMenu.min.js"></script>
     <script src="js/jquery-ui.js"></script>

    <!-- Custom Theme JavaScript -->
    <script src="js/sb-admin-2.js"></script>


       <!-- Morris Charts JavaScript -->
    <script src="js/plugins/morris/raphael.min.js"></script>
    <script src="js/plugins/morris/morris.min.js"></script>
    <script src="js/plugins/morris/morris-data.js"></script>

     <!-- DataTables JavaScript -->
    <script src="js/plugins/dataTables/jquery.dataTables.js"></script>
    <script src="js/plugins/dataTables/dataTables.bootstrap.js"></script>
    
    <script src="croppic.min.js"></script>
    <script src="assets/js/main.js"></script>

    <script>
    $(document).ready(function() {
        $('#dataTables-example').dataTable();
    });
    </script>
    <script>
    var croppicHeaderOptions = {
        uploadUrl:'img_save_to_file.php',
        cropData:{
          "dummyData":1,
          "dummyData2":"asdas"
        },
        cropUrl:'img_crop_to_file.php',
        customUploadButtonId:'cropContainerHeaderButton',
        modal:false,
        loaderHtml:'<div class="loader bubblingG"><span id="bubblingG_1"></span><span id="bubblingG_2"></span><span id="bubblingG_3"></span></div> ',
        onBeforeImgUpload: function(){ console.log('onBeforeImgUpload') },
        onAfterImgUpload: function(){ console.log('onAfterImgUpload') },
        onImgDrag: function(){ console.log('onImgDrag') },
        onImgZoom: function(){ console.log('onImgZoom') },
        onBeforeImgCrop: function(){ console.log('onBeforeImgCrop') },
        onAfterImgCrop:function(){ console.log('onAfterImgCrop') }
    } 
    var croppic = new Croppic('croppic', croppicHeaderOptions);
    
    
    var croppicContainerModalOptions = {
        uploadUrl:'img_save_to_file.php',
        cropUrl:'img_crop_to_file.php',
        modal:true,
        imgEyecandyOpacity:0.4,
        loaderHtml:'<div class="loader bubblingG"><span id="bubblingG_1"></span><span id="bubblingG_2"></span><span id="bubblingG_3"></span></div> '
    }
    var cropContainerModal = new Croppic('cropContainerModal', croppicContainerModalOptions);
    
    
    var croppicContaineroutputOptions = {
        uploadUrl:'img_save_to_file.php',
        cropUrl:'img_crop_to_file.php', 
        outputUrlId:'cropOutput',
        modal:false,
        loaderHtml:'<div class="loader bubblingG"><span id="bubblingG_1"></span><span id="bubblingG_2"></span><span id="bubblingG_3"></span></div> '
    }
    var cropContaineroutput = new Croppic('cropContaineroutput', croppicContaineroutputOptions);
    
    var croppicContainerEyecandyOptions = {
        uploadUrl:'img_save_to_file.php',
        cropUrl:'img_crop_to_file.php',
        imgEyecandy:false,
        loaderHtml:'<div class="loader bubblingG"><span id="bubblingG_1"></span><span id="bubblingG_2"></span><span id="bubblingG_3"></span></div> '
    }
    var cropContainerEyecandy = new Croppic('cropContainerEyecandy', croppicContainerEyecandyOptions);
    
  </script>


</body>
</html>
