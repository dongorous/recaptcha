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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>kyc</title>
</head>
<body>
    
    <form id="formKyc" novalidate>
        <div class="form-group">
            <div id="recaptcha"></div>
        </div>
        <button class="btn btn-primary btn-lg" id="sumbit_kyc" type="submit">Submit</button>
    </form>

    <script>
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
            console.log(response);
        };

        var onRecaptchaExpired = function() {
            grecaptcha.reset(widget1);
        };

        $('body').on('submit', '#formKyc', function (e) {
            e.preventDefault();
            var formData = new FormData( $(this)[0] );

            $.ajax({
                url : "xxx/idm/upload",
                type : 'POST',
                data : formData,
                contentType : false,
                processData : false,
                success : function (data){
                },
                error: function(XMLHttpRequest, textStatus, errorThrown) {

                }
            });
        });
    </script>

    <script src="https://www.google.com/recaptcha/api.js?onload=onloadCallback&render=explicit" async defer></script>
</body>
</html>
