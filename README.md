# Tend API

Organized around [REST](http://en.wikipedia.org/wiki/Representational_state_transfer), using [JSON](http://www.json.org/) for serialization and [HTTP Basic Auth](http://en.wikipedia.org/wiki/Basic_access_authentication) for authentication.

## Authentication
Authenticate into the Tend API by providing our username and password.

**Via Browser:**
<pre><code>https://tend.io/api/v1/contacts
</code></pre>
And enter your Tend username & password when prompted.

**With CURL:**
<pre><code>curl -u user:pass https://tend.io/api/v1/contacts
</code></pre>

All API requests must be made over HTTPS. Calls made over plain HTTP will fail.

## Pagination

Most collection APIs paginate their results. The first request returns up to 50 records. Check the next page for more results by adding &page=2, then &page=3, and so on until you get an empty response.

## Errors

Tend uses conventional HTTP response codes to indicate success or failure of an API request. 

<pre><code>200 OK - Everything worked as expected.

400 Bad Request - Often missing a required parameter.

401 Unauthorized - Authentication failed.

402 Request Failed - Parameters were valid but request failed.

404 Not Found - The requested item doesn't exist.

500, 502, 503, 504 Server errors - something went wrong on Tend's end.
</code></pre>

## Rate limiting

You can perform up to 10,000 requests per 5 minute period from the same IP address for the same account. If you exceed this limit, you'll get a 429 Too Many Requests response for subsequent requests. 

## Methods

* [Contacts](#contacts)
* [Visits](#visits)
* [Campaigns](#campaigns)
* [Referrers](#referrers)
* [Segments](#segments)

## <a name="contacts"></a>Contacts 

### Get all contacts

* <code>GET /contacts</code> will return all of the contacts in the account.

<pre><code>curl -u user:pass https://tend.io/api/v1/contacts
</code></pre>

<pre><code>{
    "data": [
        {
            "id": 123,
            "name": "Marty Thomas",
            "firstName": "Marty",
            "lastName": "Thomas",
            "email": "marty@tend.io",
            "company": "Tend",
            "title": "Co-Founder",
            "bio": "Co-Founder at Tend. Founder & Developer at Purlem. Husband to my biggest cheerleader. And father to the new loves of my life.",
            "website": "https://www.tend.io",
            "address": "2 N. LaSalle St.",
            "city": "Chicago",
            "state": "IL",
            "zip": "",
            "country": "",
            "photo": "https://d2ojpxxtu63wzl.cloudfront.net/static/0cf998559aa4eae658ff31c0b338f155_344b70e63894af453574c5e548d38496ca282ca605c6225d10e2856518bf570c",
            "facebook": "",
            "twitter": "http://twitter.com/martyjthomas",
            "linkedin": "https://www.linkedin.com/in/martinjthomas",
            "activity": {
                "sessions": 1,
                "visits": 6
            },
            "segments": [
                {
                    "id": 1,
                    "name": "Customer"
                },
                {
                    "id": 2,
                    "name": "BasicUser"
                }
            ],
            "referrers": [
                {
                    "id": 2,
                    "name": "direct"
                }
            ],
            "campaigns": [
            {
                "id": 4,
                "domain": "",
                "name": "facebook-ad-1",
                "source": "facebook",
                "medium": "ppc",
                "term": "learnmore",
                "content": "stuff",
                "start": "",
                "end": "",
                "image": "",
                "notes": "some notes about this campaign"
            }
        },
        {
            "id": 456,
            "name": "Ryan Evans",
            "firstName": "Ryan",
            "lastName": "Evans",
            "email": "ryan@tend.io",
            "company": "Tend",
            "title": "Co-Founder",
            "bio": "Co-Founder: Tend [New] (http://tend.io ) Bitesize PR (http://BitesizePR.com ) // Source Sleuth (http://SourceSleuth.com ) // Lift (http://ThisIsLift.com )",
            "website": "https://www.tend.io",
            "address": "2 N. LaSalle St.",
            "city": "Chicago",
            "state": "IL",
            "zip": "",
            "country": "",
            "photo": "https://d2ojpxxtu63wzl.cloudfront.net/static/ae852ad1a29f3a06cc2af1fa4a3f9638_cef81b960bfeff853bddc25324d95107c7b6a5c7f9f77abbfbca394d0190102d",
            "facebook": "",
            "twitter": "https://twitter.com/ryanevans",
            "linkedin": "https://www.linkedin.com/profile/view?id=11981929",
            "activity": {
                "sessions": 32,
                "visits": 102
            },
            "segments": [
                {
                    "id": 1,
                    "name": "Customer"
                }
            ],
            "referrers": [
                {
                    "id": 2,
                    "name": "direct"
                }
            ],
            "campaigns": [
                {
                    "id": 1,
                    "domain": "",
                    "name": "remarketing",
                    "source": "ppc",
                    "medium": "remarketing",
                    "term": "",
                    "content": "",
                    "start": "",
                    "end": "",
                    "image": "",
                    "notes": ""
                }
            ]
        }
}
</code></pre>

### Get contact

* <code>GET /contacts/123</code> will return the specified contact.

<pre><code>curl -u user:pass https://tend.io/api/v1/contacts/123
</code></pre>

<pre><code>{
    "data": [
        {
            "id": 123,
            "name": "Marty Thomas",
            "firstName": "Marty",
            "lastName": "Thomas",
            "email": "marty@tend.io",
            "company": "Tend",
            "title": "Co-Founder"
            "bio": "Co-Founder at Tend. Founder & Developer at Purlem. Husband to my biggest cheerleader. And father to the new loves of my life.",
            "website": "https://www.tend.io",
            "address": "2 N. LaSalle St.",
            "city": "Chicago",
            "state": "IL",
            "zip": "",
            "country": "",
            "photo": "https://d2ojpxxtu63wzl.cloudfront.net/static/0cf998559aa4eae658ff31c0b338f155_344b70e63894af453574c5e548d38496ca282ca605c6225d10e2856518bf570c",
            "facebook": "",
            "twitter": "http://twitter.com/martyjthomas",
            "linkedin": "https://www.linkedin.com/in/martinjthomas",
            "activity": {
                "sessions": 1,
                "visits": 6
            },
            "segments": [
                {
                    "id": 1,
                    "name": "Customer"
                },
                {
                    "id": 2,
                    "name": "BasicUser"
                }
            ],
            "referrers": [
                {
                    "id": 2,
                    "name": "direct"
                }
            ],
            "campaigns": [
            {
                "id": 4,
                "domain": "",
                "name": "facebook-ad-1",
                "source": "facebook",
                "medium": "ppc",
                "term": "learnmore",
                "content": "stuff",
                "start": "",
                "end": "",
                "image": "",
                "notes": "some notes about this campaign"
            }
        }
}
</code></pre>

### Update contact

* <code>PUT /contacts/123</code> will update the project from the parameters passed.

<pre><code>curl -u user:pass -i -X PUT -d 'city=Boulder&state=CO' https://tend.io/api/v1/contacts/801
</code></pre>

This will return <code>200 OK</code> if the update was a success along with the current JSON representation of the contact.

### Delete contact

* <code>DELETE /contacts/123</code> will delete the contact.

<pre><code>curl -u user:pass -i -X DELETE https://tend.io/api/v1/contacts/123
</code></pre>

This will return <code>200 Ok</code> if successful.

### Get contact visit history

* <code>GET /contacts/123/visits</code> will return the visits for the specified contact.

<pre><code>curl -u user:pass https://tend.io/api/v1/contacts/123/visits</code></pre>

<pre><code>{
    "data": [
        {
            "id": 1,
            "domain": "tend.io",
            "page": "/",
            "query": "?utm_campaign=X",
            "referrer": "google",
            "campaign": "ppc",
            "date": "2014-08-05 04:41:06"
        },
        {
            "id": 2,
            "domain": "tend.io",
            "page": "/pricing",
            "query": "",
            "referrer": "",
            "campaign": "",
            "date": "2014-08-05 04:42:06"
        }
    ]
}
</code></pre>

### Get contact segments

* <code>GET /contacts/123/segments</code> will return the segments associated with the specified contact.

<pre><code>curl -u user:pass https://tend.io/api/v1/contacts/123/segments</code></pre>

<pre><code>{
    "data": [
        {
            "id": 235,
            "name": "signup"
        }
    ]
}
</code></pre>


## <a name="visits"></a>Visits 

### Get all vists

* <code>GET /visits</code> will return the full visit history.

<pre><code>curl -u user:pass https://tend.io/api/v1/visits
</code></pre>

<pre><code>{
    "data": [
        {
            "id": 1234,
            "domain": "tend.io",
            "page": "/",
            "query": "?utm_campaign=X",
            "referrer": "google",
            "campaign": "ppc",
            "date": "2014-08-05 04:41:06"
        },
        {
            "id": "TFf7rFIVGTaSTr8Gd4GRtH6zVFCBEfVoWuFxGBhk",
            "domain": "tend.io",
            "page": "/pricing",
            "query": "",
            "referrer": "",
            "campaign": "",
            "date": "2014-08-05 04:42:06"
        }
    ]
}
</code></pre>

If the visit is associated it a contact, the contact's ID will be passed as the <code>id</code> integer.  Otherwise, the visitor's anonymous ID will be provided.

### Get all pages

* <code>GET /pages</code> will return all pages visited and their count.

<pre><code>curl -u user:pass https://tend.io/api/v1/pages
</code></pre>

<pre><code>{
    "data": [
        {
            "page": "/",
            "visits": 9491
        },
        {
            "page": "/pricing",
            "visits": 2880
        },
        {
            "page": "/features",
            "visits": 2190
        },
    ]
}
</code></pre>

## <a name="campaigns"></a>Campaigns 

### Get all campaigns

* <code>GET /campaigns</code> will return all of the campaigns in the account.

<pre><code>curl -u user:pass https://tend.io/api/v1/campaigns
</code></pre>

<pre><code>{
    "data": [
        {
            "id": 1,
            "domain": "tend.io",
            "name": "remarketing",
            "source": "ppc",
            "medium": "blogs",
            "term": "",
            "content": "",
            "start": "2015-02-05",
            "end": "2015-03-05",
            "image": "",
            "notes": ""
        },
        {
            "id": 2,
            "domain": "tend.io",
            "name": "facebook-ad1",
            "source": "facebook",
            "medium": "",
            "term": "",
            "content": "",
            "start": "",
            "end": "",
            "image": "",
            "notes": ""
        }
    ]
}
</code></pre>

### Get campaign

* <code>GET /campaigns/1</code> will return the selected referrer.

<pre><code>curl -u user:pass https://tend.io/api/v1/campaigns/1
</code></pre>

<pre><code>{
    "data": {
        "id": 1,
        "domain": "tend.io",
        "name": "remarketing",
        "source": "ppc",
        "medium": "blogs",
        "term": "",
        "content": "",
        "start": "2015-02-05",
        "end": "2015-03-05",
        "image": "",
        "notes": ""
    }
}
</code></pre>

### Update campaign

* <code>PUT /campaigns/123</code> will update the campaign from the parameters passed.

<pre><code>curl -u user:pass -i -X PUT -d 'name=New Campaign' https://tend.io/api/v1/campaign/1
</code></pre>

This will return <code>200 Ok</code> if the update was a success along with the current JSON representation of the campaign.

### Delete campaign

* <code>DELETE /campaigns/1</code> will delete the campaign.

<pre><code>curl -u user:pass -i -X DELETE https://tend.io/api/v1/campaigns/1
</code></pre>

This will return <code>200 Ok</code> if successful.

### Get all campaign contacts

* <code>GET /campaigns/1/contacts</code> will return all of the contacts associated with a campaign.

<pre><code>curl -u user:pass https://tend.io/api/v1/campaigns/1/contacts
</code></pre>

This will return <code>200 OK</code> if the contacts are found, along with the JSON representation of the associated contacts. 

### Get all campaign visits

* <code>GET /campaigns/1/visits</code> will return all of the visits associated with a campaign.

<pre><code>curl -u user:pass https://tend.io/api/v1/campaigns/1/visits
</code></pre>

This will return <code>200 OK</code> if the contacts are found, along with the JSON representation of the associated visits.

## <a name="referrers"></a>Referrers 

### Get all referrers

* <code>GET /referrers</code> will return all of the referrers in the account.

<pre><code>curl -u user:pass https://tend.io/api/v1/referrers
</code></pre>

<pre><code>{
    "data": [
        {
            "id": 1,
            "name": "direct"
        },
        {
            "id": 2,
            "name": "google"
        },
        {
            "id": 3,
            "name": "feedburner"
        }
    ]
}
</code></pre>

### Get referrer

* <code>GET /referrers/1</code> will return the selected referrer.

<pre><code>curl -u user:pass https://tend.io/api/v1/referrers/4
</code></pre>

<pre><code>{
    "data": {
        "id": 4,
        "name": "feedburner"
    }
}
</code></pre>

### Get all referrer contacts

* <code>GET /referrers/1/contacts</code> will return all of the contacts associated with a referrer.

<pre><code>curl -u user:pass https://tend.io/api/v1/referrers/1/contacts
</code></pre>

This will return <code>200 OK</code> if the contacts are found, along with the JSON representation of the associated contacts. 

### Get all referrer visits

* <code>GET /referrers/1/visits</code> will return all of the visits associated with a referrer.

<pre><code>curl -u user:pass https://tend.io/api/v1/referrers/1/visits
</code></pre>

This will return <code>200 OK</code> if the contacts are found, along with the JSON representation of the associated visits.

## <a name="segments"></a>Segments 

### Get all segments

* <code>GET /segments</code> will return all of the segments in the account.

<pre><code>curl -u user:pass https://tend.io/api/v1/segments
</code></pre>

<pre><code>{
    "data": [
        {
            "id": 1,
            "name": "Customer"
        },
        {
            "id": 2,
            "name": "ViewedPricingPage"
        }
    ]
}
</code></pre>

### Get segment

* <code>GET /segments/1</code> will return the selected referrer.

<pre><code>curl -u user:pass https://tend.io/api/v1/segments/1
</code></pre>

<pre><code>{
    "data": [
        {
            "id": 1,
            "name": "Customer"
        }
    ]
}
</code></pre>

### Add segment

* <code>POST /segments</code> will add the segment from the parameters passed.

<pre><code>curl -u user:pass -i -X POST -d 'name=API' https://tend.io/api/v1/segments
</code></pre>

This will return <code>201 Success</code> if the insert was a success along with the current JSON representation of the segment.

### Update segment

* <code>PUT /segments/123</code> will update the segment from the parameters passed.

<pre><code>curl -u user:pass -i -X PUT -d 'name=API2' https://tend.io/api/v1/segments/123
</code></pre>

This will return <code>200 Ok</code> if the update was a success along with the current JSON representation of the segment.

### Delete segment

* <code>DELETE /segments/123</code> will delete the segment.

<pre><code>curl -u user:pass -i -X DELETE https://tend.io/api/v1/segments/123
</code></pre>

This will return <code>200 Ok</code> if successful.

### Assign a Contact to a Segment

* <code>POST /segments/assign</code> will assign the segment from the parameters passed.

Will need to POST the contact's email, along with a comma-separated list of segments to apply to the contact.

<pre><code>curl -u user:pass -i -X POST -d 'email=user@domain&segments=Customer,BasicUser' https://tend.io/api/v1/segments/assign
</code></pre>

<pre><code>{
    "message": "segments assigned to user@domain.com"
    ]
}
</code></pre>

### Detach a Contact from a Segment

* <code>POST /segments/detach</code> will detach the segment from the parameters passed.

Will need to POST the contact's email, along with a comma-separated list of segments to detach to the contact.

<pre><code>curl -u user:pass -i -X POST -d 'email=user@domain&segments=Customer,BasicUser' https://tend.io/api/v1/segments/detach
</code></pre>

<pre><code>{
    "message": "segments detached from user@domain.com"
    ]
}
</code></pre>
