
# cURL Sample Code

### Authentication

An Api-Key header is needed authenticate to the Api and will allow you access to read-only operations. The curl option for setting the Api-Key header is:

    -H "Api-Key:{your-api-key}"

### Authorization

An Authorization header is required to perform download operations. The format of the header is the word **Bearer** followed by the token received from a call to oauth2/token as follows:

	curl -d 'grant_type=client_credentials&client_id={your-api-key}&client_secret={your-api-secret}' https://api.gettyimages.com/oauth2/token

The curl option for setting the Authorization header is:

	-H "Authorization: Bearer {your-token}"

### Search

Use the authentication/authorization header option in the operations below depending on the operation used:

##### Images
    curl {headers} https://api.gettyimages.com/v3/search/images?phrase=kitties

##### Images Creative
    curl {headers} https://api.gettyimages.com/v3/search/images/creative?phrase=kitties

##### Images Editorial
    curl {headers} https://api.gettyimages.com/v3/search/images/editorial?phrase=kitties

##### Paging Results
    curl {headers} https://api.gettyimages.com/v3/search/images?phrase=kitties&page=1&page_size=10

### Image Metadata
NOTE: Some command line tools may require you to quote the url

    curl {headers} https://api.gettyimages.com/v3/images/83454811,186239980
### Downloads
NOTE: This operation requires an Authorization Header

    curl -H "Api-Key:{your-api-key}" -H "Authorization: Bearer {your-token}" https://api.gettyimages.com/v3/downloads/83454811 -d "'" -L -o 83454811.jpg

### Countries
This endpoint returns allowed country codes for use with other endpoints. It supports localization.

    curl -i -H "Api-Key:{your-api-key}" -H "Accept-Language:en-US" https://api.gettyimages.com/v3/countries
