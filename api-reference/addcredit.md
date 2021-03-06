+++
title = "AddCredit"
toc = true
+++

Adds credit to a given client.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "AddCredit" | Required |
| clientid | int |  | Required |
| description | string | Admin only notes for credit justification | Required |
| amount | float |  | Required |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |
| newbalance | float | The new total credit balance |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'AddCredit',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'clientid' => '1',
            'description' => 'Adding funds via api',
            'amount' => '12.34',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'AddCredit';
$postData = array(
    'clientid' => '1',
    'description' => 'Adding funds via api',
    'amount' => '12.34',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success",
    "newbalance": "123.45"
}
```


### Error Responses

Possible error condition responses include:

* Client ID Not Found


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |
