<!DOCTYPE html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <!-- Bootstrap CSS -->
    <link
      rel="stylesheet"
      href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css"
      integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm"
      crossorigin="anonymous"
/>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script src="https://kit.fontawesome.com/2ab6d65101.js" crossorigin="anonymous"></script>

    <title>ToDo's List</title>
    <style>
        table{
            overflow: scroll;
        }
        .searchBox{
            display: none;
        }
        .search{
            display: block;
            width: 100%;
        }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="row 1">
        <div class="col-12">
          <h1 class="text-center py-2">ToDo's List</h1>
        </div>
      </div>
      <div class="row">
            <div class="col">
            <!-- <form> -->
            <div class="form-row">
                <div class="col-8">
                    <input
                        type="text"
                        class="form-control getTask"
                        placeholder="Enter Your Task"
                    />
                    </div>
                    <div class="col">
                    <input
                        type="button"
                        class="form-control btn btn-success submit"
                        value="Submit"
                    />
                    </div>
                    <div class="col">
                        <input
                        type="button"
                        class="form-control btn btn-primary update"
                        value="Update"
                        />
                    </div>
                </div>
                <!-- </form> -->
            </div>
        </div>
        <div class="row py-3 form-row">
            <div class="col-8">
                <input type="text" class="form-control searchBox" placeholder="Search">
            </div>
            <div class="col">
                <button type="button" class="form-control btn btn-primary search"><i class="fas fa-search"></i></button>
            </div>
        </div>
      <div class="row table pt-4">
        <div class="col">
          <table class="table">
            <thead class="taskAdded tableText">
              <tr>
                <th scope="col">S.no</th>
                <th scope="col">Task</th>
                <th scope="col">Edit</th>
                <th scope="col">Delete</th>
              </tr>
            </thead>
          </table>
        </div>
      </div>
    </div>
    <!-- script -->
    <script>
        let abc;
      document.querySelector(".getTask").addEventListener("keyup",function(event){
          if(event.keyCode === 13){
              document.querySelector(".submit").click();
          }
      });
      let sno = 0;
      document.querySelector(".submit").addEventListener("click",() => {
          let getTask = document.querySelector(".getTask").value;
          sno++;
          let text = "<tr class='tableRow'>";
            text += `<td class="sno${sno}">` + sno + "</td>";
            text += "<td class='filedData'>" + getTask + "</td>";
            text += "<td>" + `<button class='btn btn-warning edit${sno}'>Edit</button>` + "</td>";
            text += `<td> <button class="btn btn-danger delete${sno}">Delete</button> </td>`;
          text += "</tr>";
          document.querySelector(".taskAdded").innerHTML += text;
          document.querySelector(".getTask").value = "";
      });
        $(document).on('click' , '.btn-danger', function(){
            $(this).parents('tr').remove();
        });
        $(document).on("click",".btn-warning",function(){
            abc = $(this).parents('tr').find(".filedData");
            let def = abc.text();
            document.querySelector(".getTask").value = def;
            $(document).on('click','.update',function(){
                abc.text(document.querySelector(".getTask").value);
            });
        });
        $(".search").on('click',function(){
            let checkSearch = $(".searchBox").css("display");
            if(checkSearch == "none")
                {
                    $(this).css("display","none");  
                    $(".searchBox").css("display","block");
                }
        });
        // $(document).ready(function(){
            $(".searchBox").on("keyup", function() {
                var value = $(this).val().toLowerCase();
                $(".tableText tr").filter(function() {
                $(this).toggle($(this).text().toLowerCase().indexOf(value) > -1)
                });
            });
        // });
    </script>
  </body>   
</html>
