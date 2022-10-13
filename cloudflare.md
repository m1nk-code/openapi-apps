# Create an API token
### Prerequisite
Before you begin, find your zone and account IDs.

1. From the Cloudflare dashboard, go to **My Profile > API Tokens**.

2. Select **Create Token**.

3. Select a template from the available API token templates or create a custom token. We use the **Edit zone DNS** template in the following examples.

4. Add or edit the token name to describe why or how the token is used. Templates are prefilled with a token name and permissions.

![image](https://user-images.githubusercontent.com/58112539/195727004-8f627645-ad60-4a7e-a403-7d2dc10767a7.png)

5. Modify the token’s permissions. After selecting a permissions group (Account, User, or Zone), choose what level of access to grant the token. Most groups offer Edit or Read options. Edit is full CRUDL (create, read, update, delete, list) access, while Read is the read permission and list where appropriate. Refer to the [https://developers.cloudflare.com/api/reference/permissions/](available token permissions) for more information.

6. Select which resources the token is authorized to access. For example, granting Zone DNS Read access to a zone example.com will allow the token to read DNS records only for that specific zone. Any other zone will return an error for DNS record reads operations. Any other operation on that zone will also return an error.

7. (Optional) Restrict how a token is used in the Client IP Address Filtering and TTL (time to live) fields.

8. Select Continue to summary.

9. Review the token summary. Select Edit token to make adjustments. You can also edit a token after creation.

![image](https://user-images.githubusercontent.com/58112539/195727043-3401f18c-bfa5-4a43-b817-97a8d302f1b9.png)

10. Select Create Token to generate the token’s secret.

11. Copy the secret to a secure place.

**Warning**
The token secret is only **shown once**. Do not store the secret in plaintext where others can access it. Anyone with this token can perform the authorized actions against the resources that the token has access to

![image](https://user-images.githubusercontent.com/58112539/195727069-8e3b6eea-f6ea-4c1e-89ad-bd7150063b6c.png)

The token secret page also includes an example command to test the token. Use the /user/tokens/verify endpoint to fetch the current status of the given token.

``` 
$ curl "https://api.cloudflare.com/client/v4/user/tokens/verify" \
     -H "Authorization: Bearer <API_TOKEN>" 
```
The result:

``` 
{
  "result": {
    "id": "100bf38cc8393103870917dd535e0628",
    "status": "active"
  },
  "success": true,
  "errors": [],
  "messages": [
    {
      "code": 10000,
      "message": "This API Token is valid and active",
      "type": null
    }
  ]

}
```

With this you have successfully created an API token and can start working with the Cloudflare API. After creating your first API token, you can create additional API tokens [https://developers.cloudflare.com/api/how-to/create-via-api/](via the API).
