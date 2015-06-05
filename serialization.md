# Data Transmission Between Platforms  

The tables below show the possible combinations for sending various data types between platforms.

There is currently a bug that prevents data transmission in the following cases:
* **When Serialization is set to `binary` or `binary-utf8`, and you are sending binary data from Android to JavaScript.**
* **When Serialization is set to `none` and you are sending binary data.**

Please refer to the tables for more details.

---


## Serialization：`binary` and `binary-utf8`
|Sender/Recipient|String|Number|Array|Hash|Binary|
|:---:|:---:|:---:|:---:|:---:|:---:|
|iOS ⇄ iOS|○|○|○|○|○|
|iOS ⇄ Android|○|○|○|○|○|
|iOS ⇄ JS|○|○|○|○|○|
|Android ⇄ Android|○|○|○|○|○|
|Android ⇄ JS|○|○|○|○|× <sup>1</sup>|
|JS ⇄ JS|○|○|○|○|○|

```
1. It is currently not possible to send binary data from Android to JavaScript.  
```

## Serialization : `json`
|Sender/Recipient|Array<sup>1</sup>|Hash<sup>2</sup>|
|:---:|:---:|:---:|
|iOS ⇄ iOS|○<sup>3</sup>|○<sup>3</sup>|
|iOS ⇄ Android|○<sup>3,4</sup>|○<sup>3,5</sup>|
|iOS ⇄ JS|○|○|
|Android ⇄ Android|○<sup>4</sup>|○<sup>5</sup>|
|Android ⇄ JS|○<sup>4</sup>|○<sup>5</sup>|
|JS ⇄ JS|○|○|

```
1. When sending from Android, it is possible to send both Array and JSONArray objects.
2. When sending from Android, it is possible to send both Map and JSONArray objects.
3. iOS receives data as an NSString object.
4. Android receives data as a JSONArray object.
5. Android receives data as a JSONObject object.
```

## Serialization : `none`

|Sender/Recipient|String|Number|Binary|
|:---:|:---:|:---:|:---:|
|iOS ⇄ iOS|○|○|×<sup>1</sup>|
|iOS ⇄ Android|○|○|×<sup>1</sup>|
|iOS ⇄ JS|○|○|×<sup>1</sup>|
|Android ⇄ JS|○|○|×<sup>1</sup>|
|JS ⇄ JS|○|○|○|

```
1. It is currently not possible for Android and iOS to send and receive binary data when serialization is set to none.
```

---


#### Definitions of data types

|Platform|String|Number|Array|Hash|Binary|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Android|String|Short Integer Long Float Double|Array|Map|byte[] ByteBuffer|
|iOS|NSString|NSNumber|NSArray|NSDictionary|NSData|
|JS|string|number|array|object|ArrayBuffer|
