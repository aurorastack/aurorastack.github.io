+++
date = "2024-03-16"
aliases = ["sign-up", "register"]
author = "Hugo Authors"
+++

{{< rawhtml >}}
<style>
/* Full-width input fields */
input[type=text], input[type=password] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type=text]:focus, input[type=password]:focus {
  background-color: #ddd;
  outline: none;
}

hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

/* Set a style for all buttons */
button {
  background-color: #04AA6D;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

button:hover {
  opacity:1;
}

utton:disabled,
button[disabled]{
  border: 1px solid #999999;
  background-color: #cccccc;
  color: #666666;
}

/* Extra styles for the cancel button */
.cancelbtn {
  padding: 14px 20px;
  background-color: #f44336;
}

/* Float cancel and signup buttons and add an equal width */
.cancelbtn, .signupbtn {
  float: left;
  width: 50%;
}

/* Clear floats */
.clearfix::after {
  content: "";
  clear: both;
  display: table;
}

/* Change styles for cancel button and signup button on extra small screens */
@media screen and (max-width: 300px) {
  .cancelbtn, .signupbtn {
     width: 100%;
  }
}
</style>

<form id="register" >
  <div class="container">
    <h1>Start your free trial</h1>
    <p>No credit card needed.</p>
    <hr>

    <label for="email"><b>Email</b></label>
    <input type="text" id="email" placeholder="tom@example.com" name="email" required>

    <label for="name"><b>Name</b></label>
    <input type="text" id="org_name" placeholder="Tom Smith" name="org_name" required>

    <p>By signing up, I agree to the AuroraStack <a href="#">Privacy Policy</a> and <a href="#">Terms of Service</a>.</p>

    <div class="clearfix">
      <button type="submit" id="clk" value="Submit" class="signupbtn">Continue</button>
    </div>
  </div>
</form>

<script>
async function handleFormSubmit(event) {
    document.getElementById("clk").disabled = true;
	event.preventDefault();
	const form = event.currentTarget;

	const url = "http://register.aurorastack.io/registration/v1/user/create";

	try {
		const formData = new FormData(form);
		const responseData = await postFormDataAsJson({ url, formData });
        document.getElementById("clk").disabled = false;
		console.log({ responseData });

	} catch (error) {
        document.getElementById("clk").disabled = false;
		console.error(error);
	}
}
async function postFormDataAsJson({ url, formData }) {
	const plainFormData = Object.fromEntries(formData.entries());
	const formDataJsonString = JSON.stringify(plainFormData);

    console.log(formDataJsonString)
	const fetchOptions = {
		method: "POST",

		headers: {
			"Content-Type": "application/json",
			"Accept": "application/json"
		},
		body: formDataJsonString,
	};

	const response = await fetch(url, fetchOptions);

	if (!response.ok) {
		const errorMessage = await response.text();
		throw new Error(errorMessage);
	}
    alert("Check your email");
	return response.json();
}
const sendForm = document.querySelector("#register");
sendForm.addEventListener("submit", handleFormSubmit);
</script>


{{< /rawhtml >}}

