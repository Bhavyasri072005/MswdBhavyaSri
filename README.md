
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="Prajith" content="width=device-width, initial-scale=1">
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,700;0,900;1,100;1,200;1,300;1,400;1,700;1,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="./css/style.css">
  <title>Results</title>
  <style>
    body {
      background-image: url('https://img.freepik.com/free-photo/blank-papers-multicolor-pencils-grey_114579-28815.jpg');
      background-size: cover;
      background-repeat: no-repeat;
    }
    .success-message {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: #28a745;
      color: rgb(5, 5, 5);
      padding: 10px 20px;
      border-radius: 5px;
      display: none;
    }
    .captcha-container {
      display: flex;
      align-items: center;
      justify-content: center;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="row mt-5">
      <div class="col-md-4"></div>
      <div class="col-md-4">
        <div class="card">
          <div class="card-header text-center fw-bold">
            Login
          </div>
          <div class="card-body">
            <form>
              <div class="form-outline mb-4">
                <input type="Username" id="form2Example1" class="form-control" />
                <label class="form-label" for="form2Example1">Username</label>
              </div>
              <div class="form-outline mb-4">
                <input type="password" id="form2Example2" class="form-control" />
                <label class="form-label" for="form2Example2">Password</label>
              </div>
              <div class="form-outline mb-4">
                <div class="captcha-container">
                  <span id="captcha"></span>
                  <button type="button" class="btn btn-secondary btn-sm ms-2" onclick="generateCaptcha()">Refresh</button>
                </div>
                <input type="text" id="captchaInput" class="form-control" />
                <label class="form-label" for="captchaInput">Enter CAPTCHA</label>
              </div>
              <button type="button" class="btn btn-primary btn-block mb-2" onclick="signIn()">SignIn</button>
              <p class="text-center mb-0">Don't have an account? <a href="#registerModal" data-bs-toggle="modal" data-bs-dismiss="modal">Register</a></p>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="modal fade" id="registerModal" tabindex="-1" aria-labelledby="registerModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="registerModalLabel">Register</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form>
            <div class="mb-3">
              <label for="username" class="form-label">Username</label>
              <input type="text" class="form-control" id="username">
            </div>
            <div class="mb-3">
              <label for="password" class="form-label">Password</label>
              <input type="password" class="form-control" id="password">
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
        </div>
      </div>
    </div>
  </div>
  <div class="success-message" id="successMessage">Registration Successful!</div>
  <script>
    function generateCaptcha() {
      var chars = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXTZabcdefghiklmnopqrstuvwxyz";
      var length = 5;
      var captcha = "";
      for (var i = 0; i < length; i++) {
        var randomNumber = Math.floor(Math.random() * chars.length);
        captcha += chars[randomNumber];
      }
      document.getElementById("captcha").innerHTML = captcha;
    }
    
    function signIn() {
      var enteredUsername = document.getElementById("form2Example1").value;
      var enteredCaptcha = document.getElementById("captchaInput").value;
      var generatedCaptcha = document.getElementById("captcha").innerHTML;
      
      // Check if the username has exactly 10 digits
      if (!(/^\d{10}$/.test(enteredUsername))) {
        // Show invalid username message
        alert("Invalid Username.");
        return; // Exit function
      }
      
      // Check if the entered captcha is correct
      if (enteredCaptcha === generatedCaptcha) {
        window.location.href = "results.html";
      } else {
        // Show invalid credentials message
        alert("Invalid credentials. Please try again.");
      }
    }
</script>


  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js"
    integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM"
    crossorigin="anonymous"></script>
</body>
</html>
