# Facial Mask Identificator

This is an API to analyze and identify if a person is using mask.

## Usage

API Endpoint
``` html
https://us-central1-meu-projeto-e33b9.cloudfunctions.net/ia-mask-ml
```
#### Javascript
```
var formdata = new FormData();
formdata.append("image", fileInput.files[0], "image.jpeg");

var requestOptions = {
  method: 'POST',
  body: formdata,
  redirect: 'follow'
};

fetch("https://us-central1-meu-projeto-e33b9.cloudfunctions.net/ia-mask-ml", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
#### Java
```
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = new MultipartBody.Builder().setType(MultipartBody.FORM)
  .addFormDataPart("image","image.jpeg",
    RequestBody.create(MediaType.parse("application/octet-stream"),
    new File("image.jpeg")))
  .build();
Request request = new Request.Builder()
  .url("https://us-central1-meu-projeto-e33b9.cloudfunctions.net/ia-mask-ml")
  .method("POST", body)
  .build();
Response response = client.newCall(request).execute();
```

#### Node
```
var request = require('request');
var fs = require('fs');
var options = {
  'method': 'POST',
  'url': 'https://us-central1-meu-projeto-e33b9.cloudfunctions.net/ia-mask-ml',
  'headers': {
  },
  formData: {
    'image': {
      'value': fs.createReadStream('image.jpeg'),
      'options': {
        'filename': 'image.jpeg',
        'contentType': null
      }
    }
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```

#### Python
```
import requests

url = "https://us-central1-meu-projeto-e33b9.cloudfunctions.net/ia-mask-ml"

payload={}
files=[
  ('image',('image.jpeg',open('image.jpeg','rb'),'image/jpeg'))
]
headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)
```
#### PHP
```
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://us-central1-meu-projeto-e33b9.cloudfunctions.net/ia-mask-ml');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->addForm(array(

), array(
    array('name' => 'image', 'type' => '<Content-type header>', 'file' => 
'image.jpeg', 'data' => null)
));
$request->setBody($body);
$request->setOptions(array());

$client->enqueue($request)->send();
$response = $client->getResponse();
echo $response->getBody();
```
Response
```
{
    "msg": "success",
    "result": "Com mascara"
}

or

{
    "msg": "success",
    "result": "Sem mascara"
}
```


## License
[APACHE 2.0](https://www.apache.org/licenses/LICENSE-2.0)
