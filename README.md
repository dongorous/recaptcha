Google Captcha

//Render captcha:
//Add this to form
<div id="recaptcha"></div>

```
	var widget1;
	var onloadCallback = function() {
		var sitekey = 'xxxxxxxxx';

			if ( $('#recaptcha1').length ) {
			    widget1 = grecaptcha.render('recaptcha', {
				'sitekey': sitekey,
				'callback': verifyCallbackCaptcha,
				'expired-callback': onRecaptchaExpired
			    });
			}
		};
	}

	var verifyCallbackCaptcha = function(response) {
	    console.log(response);7
	};

	var onRecaptchaExpired = function() {
	    grecaptcha.reset(widget1);
	};
```

// Place script before the end of BODY tag
<script src="https://www.google.com/recaptcha/api.js?onload=onloadCallback&render=explicit" async defer></script>


==================================================================================

// SAMPLE
<form id="formKyc" novalidate>
	<div class="form-group">
	     <div id="recaptcha"></div>
	</div>
	<button class="btn btn-primary btn-lg" id="sumbit_kyc" type="submit">Submit</button>
</form>

