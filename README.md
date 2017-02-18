##Vedic Rishi Astro APIs

Vedic Rishi does all the complex astronomical and algorithmic calculations for your astrology websites or astro-matching apps and provides you with simple APIs to create awesome user interfaces for your users

#### Vedic Rishi REST Web Service Interface

Since the Vedic Rishi Astro API is based on REST principles, it's very easy to write and test applications. You can use your browser to access URLs, and you can use pretty much any HTTP client in any programming language to interact with the API.

#### API Endpoint

All API URLs listed in this documentation are relative to **https://api.vedicrishiastro.com/v1**  
For example - the /horo_chart/D1/ API call is reachable at-  
<span class="text-info">https://api.vedicrishiastro.com/v1/horo_chart/D1/</span>

#### RESTful

All Vedic Rishi Astro APIs are RESTful APIs. Following are the known caveats -

1.  All API calls should be made with HTTP POST unless mentioned otherwise
2.  Response status other than HTTP 200 can be considered as an error
3.  Basic HTTP header authorization data is must for every API call

#### Passing Requested Data RESTfully

Request data is passed to the API by POSTing JSON objects to the API endpoints with the appropriate parameters. The documentation for each API call will contain more detail on the parameters accepted by the call. As an alternative, you can also use HTTP POST parameters, just like submitting an HTML FORM, but JSON objects are recommended.

#### Output Format

Response data for each and every Vedic Rishi Astro API will be encoded in JSON format.

#### Authentication

Vedic Rishi authenticates the API access using header authentication, therefore every API call to Vedic Rishi must have authorisation header set as- _Authorization: Basic ("userId:APIKey")_  
API key and userId will be mailed to you once you subscribe and activate your plan.

#### How to get latitude ,longitude and timezone ?

For all the astrological calculcations and other reports generation (Except Numerology), Vedic Rishi APIs expect birth details which contain date of birth, time of birth, longitude of birth place, latitude of birth place and timezone of birth country. We know that getting latitude, longitude and timezone of all the places are difficult to get and therefore Vedic Rishi solves this problem by providing FREE APIs for getting the geo-details given city. These APIs are included in each and every plan you subscribe from VedicRishi. [Know More..](/docs/api-ref/geodetails)

#### Official API Clients

We have an official github account which maintains the official API clients written in various languages.

[Vedic Rishi Astro API PHP Client](https://github.com/chandantiwari/Vedic-Rishi-Astro-API-PHP-Client)

##Advanced Panchang

This is the extension of basic panchang which provides various yog such as dwi-pushakar timing, tri-pushkar timing, sarvarth siddhi yog, amrit siddhi yog, ravi yog along with malefic yog such as rahu kal, yam-ghant kal and gulik kal.

#### We have two types of Panchang APIs

**1\. Panchang at specified date and time**
Here, following APIs are used and date and time along with latitude, longitude and timezone are expected -

*   [1\. basic_panchang](#-basic-panchang/basic_panchang)
*   [2\. planet_panchang](#-basic-panchang/planet_panchang)
*   [3\. advanced_panchang](#-advanced-panchang/advanced_panchang)

**2\. Panchang at Sunsrise for given day**
Following APIs should be used for getting the panchang data points at the time of sunrise which are used by traditional calendars-

*   [1\. basic_panchang/sunrise](#-basic-panchang/basic_panchang/sunrise)
*   [2\. planet_panchang/sunrise](#-basic-panchang/planet_panchang/sunrise)
*   [2\. advanced_panchang/sunrise](#-advanced-panchang/advanced_panchang/sunrise)
*   [4\. chaughadiya_muhurta](#-advanced-panchang/chaughadiya_muhurta)
*   [5\. hora_muhurta](#-advanced-panchang/hora_muhurta)

**" Here only date along with latitude, longitude and timezone are expected to be passed. No time is required. "**

### advanced_panchang

Provides panchang in details for given day at perticular given time.

#### API Endpoint

advanced_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/advanced_panchang |



#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| hour | int | Panchang hour, eg:12 |
| min | int | Panchang minute, eg:34 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "day": "Wednesday",
  "sunrise": "7:3:17",
  "sunset": "18:43:38",
  "moonrise": "10:59:45",
  "moonset": "0:9:13",
  "tithi": {
    "details": {
      "tithi_number": 7,
      "tithi_name": "Shukla-Saptami",
      "special": "Bhadra Tithi",
      "summary": "Favourable for starting any new work, debate, beginning of a journey and physical exercise.",
      "deity": "Indra"
    },
    "end_time": {
      "hour": 10,
      "minute": 55,
      "second": 8
    }
  },
  "nakshatra": {
    "details": {
      "nak_number": 3,
      "nak_name": "Krittika",
      "ruler": "Sun",
      "deity": "Agni",
      "special": "Adhomukh Nakshatra",
      "summary": "This nakshatra is of a mixed quality. Good for immediate actions, competition, work with metals. It is suitable to perform the routine activities, day-to-day duties, but it is not recommended to start new important deeds."
    },
    "end_time": {
      "hour": 17,
      "minute": 48,
      "second": 8
    }
  },
  "yog": {
    "details": {
      "yog_number": 26,
      "yog_name": "Endra",
      "special": "Auspicious yoga,Good for all Auspicious Deeds.",
      "meaning": "(Chief) � interest in education and knowledge; helpful, well-off."
    },
    "end_time": {
      "hour": 7,
      "minute": 57,
      "second": 19
    }
  },
  "karan": {
    "details": {
      "karan_number": 7,
      "karan_name": "Vanija",
      "special": "It is suited for sale transactions and sellers may reap good profits whereas buyers may incur losses in this Karana.",
      "deity": "Manibhadra"
    },
    "end_time": {
      "hour": 10,
      "minute": 57,
      "second": 8
    }
  },
  "hindu_maah": {
    "adhik_status": false,
    "purnimanta": "Phalguna",
    "amanta": "Phalguna"
  },
  "paksha": "Shukla-Paksha",
  "ritu": "Shishir",
  "sun_sign": "Aquarius",
  "moon_sign": "Taurus",
  "ayana": "Uttarayana",
  "panchang_yog": " Sarvarth Siddhi Yog",
  "vikram_samvat": 2071,
  "shaka_samvat": 1936,
  "shaka_samvat_name": "Jay",
  "vkram_samvat_name": "Plavang",
  "disha_shool": "NORTH",
  "disha_shool_remedies": [],
  "nak_shool": "none",
  "moon_nivas": "SOUTH",
  "abhijit_muhurta": {
    "start": "12:29",
    "end": "01:15"
  },
  "rahukaal": {
    "start": "12 : 52 : 59",
    "end": "2 : 20 : 29"
  },
  "guliKaal": {
    "start": "11 : 25 : 29",
    "end": "12 : 52 : 59"
  },
  "yamghant_kaal": {
    "start": "08 : 30 : 29",
    "end": "09 : 57 : 59"
  }
}

```

### advanced_panchang/sunrise

Provides panchang in details at the time of sunrise for given day.

#### API Endpoint

advanced_panchang/sunrise

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/advanced_panchang/sunrise |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "day": "Wednesday",
  "sunrise": "7:3:17",
  "sunset": "18:43:38",
  "moonrise": "10:59:45",
  "moonset": "0:9:13",
  "tithi": {
    "details": {
      "tithi_number": 7,
      "tithi_name": "Shukla-Saptami",
      "special": "Bhadra Tithi",
      "summary": "Favourable for starting any new work, debate, beginning of a journey and physical exercise.",
      "deity": "Indra"
    },
    "end_time": {
      "hour": 10,
      "minute": 55,
      "second": 8
    }
  },
  "nakshatra": {
    "details": {
      "nak_number": 3,
      "nak_name": "Krittika",
      "ruler": "Sun",
      "deity": "Agni",
      "special": "Adhomukh Nakshatra",
      "summary": "This nakshatra is of a mixed quality. Good for immediate actions, competition, work with metals. It is suitable to perform the routine activities, day-to-day duties, but it is not recommended to start new important deeds."
    },
    "end_time": {
      "hour": 17,
      "minute": 48,
      "second": 8
    }
  },
  "yog": {
    "details": {
      "yog_number": 26,
      "yog_name": "Endra",
      "special": "Auspicious yoga,Good for all Auspicious Deeds.",
      "meaning": "(Chief) � interest in education and knowledge; helpful, well-off."
    },
    "end_time": {
      "hour": 7,
      "minute": 57,
      "second": 19
    }
  },
  "karan": {
    "details": {
      "karan_number": 7,
      "karan_name": "Vanija",
      "special": "It is suited for sale transactions and sellers may reap good profits whereas buyers may incur losses in this Karana.",
      "deity": "Manibhadra"
    },
    "end_time": {
      "hour": 10,
      "minute": 57,
      "second": 8
    }
  },
  "hindu_maah": {
    "adhik_status": false,
    "purnimanta": "Phalguna",
    "amanta": "Phalguna"
  },
  "paksha": "Shukla-Paksha",
  "ritu": "Shishir",
  "sun_sign": "Aquarius",
  "moon_sign": "Taurus",
  "ayana": "Uttarayana",
  "panchang_yog": " Sarvarth Siddhi Yog",
  "vikram_samvat": 2071,
  "shaka_samvat": 1936,
  "shaka_samvat_name": "Jay",
  "vkram_samvat_name": "Plavang",
  "disha_shool": "NORTH",
  "disha_shool_remedies": [],
  "nak_shool": "none",
  "moon_nivas": "SOUTH",
  "abhijit_muhurta": {
    "start": "12:29",
    "end": "01:15"
  },
  "rahukaal": {
    "start": "12 : 52 : 59",
    "end": "2 : 20 : 29"
  },
  "guliKaal": {
    "start": "11 : 25 : 29",
    "end": "12 : 52 : 59"
  },
  "yamghant_kaal": {
    "start": "08 : 30 : 29",
    "end": "09 : 57 : 59"
  }
}

```

### chaughadiya_muhurta

Provides both day and night chaughadiya data.

#### API Endpoint

chaughadiya_muhurta

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/chaughadiya_muhurta |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Chaughadiya day, eg: 10 |
| month     | int      |   Chaughadiya month, eg:5 |
| year | int      |    Chaughadiya year, eg:2015 |
| lat | float | Chaughadiya place latitude, eg: 19.234|
| lon | float | Chaughadiya place longitude, eg: 72.843|
| tzone | float | Chaughadiya place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "chaughadiya": {
    "day": [
      {
        "time": "5 : 41 : 01 - 4 : 06 : 50",
        "muhurta": "Labh"
      },
      {
        "time": "4 : 06 : 50 - 2 : 32 : 39",
        "muhurta": "Amrit"
      },
      {
        "time": "2 : 32 : 39 - 12 : 58 : 27",
        "muhurta": "Kaal"
      },
      {
        "time": "12 : 58 : 27 - 11 : 24 : 16",
        "muhurta": "Shubh"
      },
      {
        "time": "11 : 24 : 16 - 09 : 50 : 05",
        "muhurta": "Rog"
      },
      {
        "time": "09 : 50 : 05 - 08 : 15 : 53",
        "muhurta": "Udveg"
      },
      {
        "time": "08 : 15 : 53 - 06 : 41 : 42",
        "muhurta": "Char"
      },
      {
        "time": "06 : 41 : 42 - 05 : 07 : 30",
        "muhurta": "Labh"
      }
    ],
    "night": [
      {
        "time": "05 : 07 : 30 - 06 : 41 : 38",
        "muhurta": "Udveg"
      },
      {
        "time": "06 : 41 : 38 - 08 : 15 : 46",
        "muhurta": "Shubh"
      },
      {
        "time": "08 : 15 : 46 - 09 : 49 : 55",
        "muhurta": "Amrit"
      },
      {
        "time": "09 : 49 : 55 - 11 : 24 : 03",
        "muhurta": "Char"
      },
      {
        "time": "11 : 24 : 03 - 12 : 58 : 11",
        "muhurta": "Rog"
      },
      {
        "time": "12 : 58 : 11 - 2 : 32 : 19",
        "muhurta": "Kaal"
      },
      {
        "time": "2 : 32 : 19 - 4 : 06 : 27",
        "muhurta": "Labh"
      },
      {
        "time": "4 : 06 : 27 - 5 : 40 : 35",
        "muhurta": "Udveg"
      }
    ]
  }
}

```
### hora_muhurta

Provides day and night hora data.

#### API Endpoint

hora_muhurta

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/chaughadiya_muhurta |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Hora day, eg: 10 |
| month     | int      |   Hora month, eg:5 |
| year | int      |    Hora year, eg:2015 |
| lat | float | Hora place latitude, eg: 19.234|
| lon | float | Hora place longitude, eg: 72.843|
| tzone | float | Hora place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "hora": {
    "day": [
      {
        "time": "17:41 - 18:41",
        "hora": "Mercury"
      },
      {
        "time": "18:41 - 19:41",
        "hora": "Moon"
      },
      {
        "time": "19:41 - 20:41",
        "hora": "Saturn"
      },
      {
        "time": "20:41 - 21:41",
        "hora": "Jupiter"
      },
      {
        "time": "21:41 - 22:41",
        "hora": "Mars"
      },
      {
        "time": "22:41 - 23:41",
        "hora": "Sun"
      },
      {
        "time": "23:41 - 0:41",
        "hora": "Venus"
      },
      {
        "time": "0:41 - 1:41",
        "hora": "Mercury"
      },
      {
        "time": "1:41 - 2:41",
        "hora": "Moon"
      },
      {
        "time": "2:41 - 3:41",
        "hora": "Saturn"
      },
      {
        "time": "3:41 - 4:41",
        "hora": "Jupiter"
      },
      {
        "time": "4:41 - 5:41",
        "hora": "Mars"
      }
    ],
    "night": [
      {
        "time": "5:41 - 6:41",
        "hora": "Sun"
      },
      {
        "time": "6:41 - 7:41",
        "hora": "Venus"
      },
      {
        "time": "7:41 - 8:41",
        "hora": "Mercury"
      },
      {
        "time": "8:41 - 9:41",
        "hora": "Moon"
      },
      {
        "time": "9:41 - 10:41",
        "hora": "Saturn"
      },
      {
        "time": "10:41 - 11:41",
        "hora": "Jupiter"
      },
      {
        "time": "11:41 - 12:41",
        "hora": "Mars"
      },
      {
        "time": "12:41 - 13:41",
        "hora": "Sun"
      },
      {
        "time": "13:41 - 14:41",
        "hora": "Venus"
      },
      {
        "time": "14:41 - 15:41",
        "hora": "Mercury"
      },
      {
        "time": "15:41 - 16:41",
        "hora": "Moon"
      },
      {
        "time": "16:41 - 17:41",
        "hora": "Saturn"
      }
    ]
  }
}

```

## Basic Ashtakvarga

Provide details of Bhinnashtak varga And Servashtak Varga.

### planet_ashtak/:planet_name

Provides astakvarga chart points and table points.

#### API Endpoint
planet_ashtak/:planet_name

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planet_ashtak/:planet_name |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Planet Name
Here planet name means for which planet you want data.
>Planet name's are as follow:- 
>sun, moon, mars, mercury, jupiter, venus, saturn , ascendant

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")

``` javascript
{
  "ashtak_varga": {
    "type": "Bhinnashtak",
    "planet": "Sun",
    "sign": "virgo",
    "sign_id": 6
  },
  "ashtak_points": {
    "aries": {
      "sun": 0,
      "moon": 0,
      "mars": 1,
      "mercury": 0,
      "jupiter": 0,
      "venus": 0,
      "saturn": 0,
      "ascendant": 0,
      "total": 1
    },
    "taurus": {
      "sun": 1,
      "moon": 1,
      "mars": 0,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 6
    },
    "gemini": {
      "sun": 0,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 0,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 4
    },
    "cancer": {
      "sun": 0,
      "moon": 0,
      "mars": 0,
      "mercury": 0,
      "jupiter": 0,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 2
    },
    "leo": {
      "sun": 1,
      "moon": 1,
      "mars": 0,
      "mercury": 0,
      "jupiter": 0,
      "venus": 1,
      "saturn": 1,
      "ascendant": 0,
      "total": 4
    },
    "virgo": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 0,
      "venus": 1,
      "saturn": 1,
      "ascendant": 0,
      "total": 5
    },
    "libra": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 0,
      "venus": 0,
      "saturn": 0,
      "ascendant": 1,
      "total": 4
    },
    "scorpio": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 6
    },
    "sagittarius": {
      "sun": 1,
      "moon": 1,
      "mars": 1,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 1,
      "ascendant": 0,
      "total": 6
    },
    "capricorn": {
      "sun": 0,
      "moon": 1,
      "mars": 1,
      "mercury": 0,
      "jupiter": 0,
      "venus": 0,
      "saturn": 0,
      "ascendant": 1,
      "total": 3
    },
    "aquarius": {
      "sun": 1,
      "moon": 0,
      "mars": 0,
      "mercury": 0,
      "jupiter": 0,
      "venus": 1,
      "saturn": 1,
      "ascendant": 0,
      "total": 3
    },
    "pisces": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 0,
      "ascendant": 0,
      "total": 4
    }
  }
}

```

### sarvashtak

Provides sarvashtak varga chart points and table points.

#### API Endpoint
sarvashtak

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sarvashtak |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")

``` javascript
{
  "ashtak_varga": {
    "type": "Sarvashtak"
  },
  "ashtak_points": {
    "aries": {
      "sun": 1,
      "moon": 5,
      "mars": 3,
      "mercury": 3,
      "jupiter": 8,
      "venus": 4,
      "saturn": 1,
      "ascendant": 0,
      "total": 25
    },
    "taurus": {
      "sun": 6,
      "moon": 6,
      "mars": 5,
      "mercury": 5,
      "jupiter": 4,
      "venus": 5,
      "saturn": 5,
      "ascendant": 0,
      "total": 36
    },
    "gemini": {
      "sun": 4,
      "moon": 3,
      "mars": 6,
      "mercury": 8,
      "jupiter": 3,
      "venus": 5,
      "saturn": 3,
      "ascendant": 0,
      "total": 32
    },
    "cancer": {
      "sun": 2,
      "moon": 5,
      "mars": 2,
      "mercury": 3,
      "jupiter": 3,
      "venus": 4,
      "saturn": 1,
      "ascendant": 0,
      "total": 20
    },
    "leo": {
      "sun": 4,
      "moon": 4,
      "mars": 4,
      "mercury": 3,
      "jupiter": 4,
      "venus": 3,
      "saturn": 6,
      "ascendant": 0,
      "total": 28
    },
    "virgo": {
      "sun": 5,
      "moon": 4,
      "mars": 2,
      "mercury": 4,
      "jupiter": 6,
      "venus": 4,
      "saturn": 3,
      "ascendant": 0,
      "total": 28
    },
    "libra": {
      "sun": 4,
      "moon": 3,
      "mars": 3,
      "mercury": 5,
      "jupiter": 5,
      "venus": 3,
      "saturn": 2,
      "ascendant": 0,
      "total": 25
    },
    "scorpio": {
      "sun": 6,
      "moon": 4,
      "mars": 3,
      "mercury": 5,
      "jupiter": 5,
      "venus": 6,
      "saturn": 4,
      "ascendant": 0,
      "total": 33
    },
    "sagittarius": {
      "sun": 6,
      "moon": 4,
      "mars": 3,
      "mercury": 6,
      "jupiter": 4,
      "venus": 3,
      "saturn": 4,
      "ascendant": 0,
      "total": 30
    },
    "capricorn": {
      "sun": 3,
      "moon": 7,
      "mars": 4,
      "mercury": 6,
      "jupiter": 7,
      "venus": 5,
      "saturn": 5,
      "ascendant": 0,
      "total": 37
    },
    "aquarius": {
      "sun": 3,
      "moon": 1,
      "mars": 2,
      "mercury": 2,
      "jupiter": 4,
      "venus": 4,
      "saturn": 3,
      "ascendant": 0,
      "total": 19
    },
    "pisces": {
      "sun": 4,
      "moon": 3,
      "mars": 2,
      "mercury": 4,
      "jupiter": 3,
      "venus": 6,
      "saturn": 2,
      "ascendant": 0,
      "total": 24
    }
  }
}
```

## Basic Astro
This package contains basic astrological details. Planetary configurations such as full degrees, normalised degrees, house position , nakshatra name, house lord and other details.

### birth_details
Along with birth details it provides sunrise, sunset, ayanamsha.

#### API Endpoint
birth_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/birth_details |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "year": 1992,
  "month": 7,
  "day": 22,
  "hour": 9,
  "minute": 21,
  "latitude": 25.31668,
  "longitude": 83.01042,
  "timezone": 5.5,
  "sunrise": "5:21:28",
  "sunset": "18:49:35",
  "ayanamsha": 23.753052294684778
}
```

### astro_details
Provides the complete avakahada details e.g. nakshtatra, charan, tithe, karan, yog ,varna, vashaya

#### API Endpoint
astro_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/astro_details |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "Varna": "Kshatriya",
  "Vashya": "Chatuspad",
  "Yoni": "Gaj",
  "Gan": "Manushya",
  "Nadi": "Madhya",
  "SignLord": "Mars",
  "sign": "Aries",
  "Naksahtra": "Bharni",
  "NaksahtraLord": "Venus",
  "Charan": 3,
  "Yog": "Dhriti",
  "Karan": "Baalav",
  "Tithi": "Krishna Ekadashi",
  "yunja": "Poorva",
  "tatva": "Fire",
  "name_alphabet": "Le",
  "paya": "Gold"
}
```

### planets
Full planetary positions including ascendant along with retrograde status and nakshatra, house, sign

#### API Endpoint
planets

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planets |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 75.01867995815415,
    "normDegree": 15.018679958154152,
    "speed": 0.9536705592639696,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 21.349425872500603,
    "normDegree": 21.349425872500603,
    "speed": 14.508795375227711,
    "isRetro": "false",
    "sign": "Aries",
    "signLord": "Mars",
    "nakshatra": "Bharni",
    "nakshatraLord": "Venus",
    "house": 6
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 208.9733013285976,
    "normDegree": 28.973301328597614,
    "speed": 0.006922409248668087,
    "isRetro": "false",
    "sign": "Libra",
    "signLord": "Venus",
    "nakshatra": "Vishakha",
    "nakshatraLord": "Jupiter",
    "house": 12
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 66.99705831618833,
    "normDegree": 6.99705831618833,
    "speed": 2.1177691946516783,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 142.918341542849,
    "normDegree": 22.918341542848992,
    "speed": 0.1342132692506382,
    "isRetro": "false",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 81.47939061863748,
    "normDegree": 21.47939061863748,
    "speed": 1.2289210832023776,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Punarvasu",
    "nakshatraLord": "Jupiter",
    "house": 8
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 227.1367070622203,
    "normDegree": 17.136707062220296,
    "speed": -0.06081092063358652,
    "isRetro": "true",
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 141.91126603349858,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 321.9112660334986,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Aquarius",
    "signLord": "Saturn",
    "nakshatra": "Purva Bhadrapad",
    "nakshatraLord": "Jupiter",
    "house": 4
  },
  {
    "id": 9,
    "name": "Ascendant",
    "fullDegree": 226.9999482337994,
    "normDegree": 16.999948233799387,
    "speed": 0,
    "isRetro": false,
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  }
]
```

### planets/extended
Full planetary positions including ascendant along with,neptune,pluto,uranus, retrograde status and nakshatra, house, sign

#### API Endpoint
planets/extended

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planets/extended |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 75.01867995815415,
    "normDegree": 15.018679958154152,
    "speed": 0.9536705592639696,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 21.349425872500603,
    "normDegree": 21.349425872500603,
    "speed": 14.508795375227711,
    "isRetro": "false",
    "sign": "Aries",
    "signLord": "Mars",
    "nakshatra": "Bharni",
    "nakshatraLord": "Venus",
    "house": 6
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 208.9733013285976,
    "normDegree": 28.973301328597614,
    "speed": 0.006922409248668087,
    "isRetro": "false",
    "sign": "Libra",
    "signLord": "Venus",
    "nakshatra": "Vishakha",
    "nakshatraLord": "Jupiter",
    "house": 12
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 66.99705831618833,
    "normDegree": 6.99705831618833,
    "speed": 2.1177691946516783,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 142.918341542849,
    "normDegree": 22.918341542848992,
    "speed": 0.1342132692506382,
    "isRetro": "false",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 81.47939061863748,
    "normDegree": 21.47939061863748,
    "speed": 1.2289210832023776,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Punarvasu",
    "nakshatraLord": "Jupiter",
    "house": 8
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 227.1367070622203,
    "normDegree": 17.136707062220296,
    "speed": -0.06081092063358652,
    "isRetro": "true",
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 141.91126603349858,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 321.9112660334986,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Aquarius",
    "signLord": "Saturn",
    "nakshatra": "Purva Bhadrapad",
    "nakshatraLord": "Jupiter",
    "house": 4
  },
  {
    "id": 9,
    "name": "Uranus",
    "fullDegree": 0.07398734010829626,
    "normDegree": 0.07398734010829626,
    "speed": 0.023347690928066378,
    "isRetro": "false",
    "sign": "Aries",
    "signLord": "Mars",
    "nakshatra": "Ashwini",
    "nakshatraLord": "Ketu",
    "house": 6
  },
  {
    "id": 10,
    "name": "Neptune",
    "fullDegree": 317.8804645006421,
    "normDegree": 17.88046450064212,
    "speed": -0.008730756309788675,
    "isRetro": "true",
    "sign": "Aquarius",
    "signLord": "Saturn",
    "nakshatra": "Shatbhisha",
    "nakshatraLord": "Rahu",
    "house": 4
  },
  {
    "id": 11,
    "name": "Pluto",
    "fullDegree": 262.3049584494822,
    "normDegree": 22.30495844948223,
    "speed": -0.024507476510135368,
    "isRetro": "true",
    "sign": "Sagittarius",
    "signLord": "Jupiter",
    "nakshatra": "Purva Shadha",
    "nakshatraLord": "Venus",
    "house": 2
  },
  {
    "id": 12,
    "name": "Ascendant",
    "fullDegree": 226.9999482337994,
    "normDegree": 16.999948233799387,
    "speed": 0,
    "isRetro": false,
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  }
]
```


### planets/tropical
Full planetary positions including ascendant along with,neptune,pluto,uranus, retrograde status and nakshatra, house, sign

#### API Endpoint
planets/tropical

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planets/tropical |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "name": "Sun",
    "fullDegree": 99.1050399130805,
    "normDegree": 9.105039913080503,
    "speed": 0.9536792374523747,
    "isRetro": "false",
    "sign": "Cancer",
    "house": 8
  },
  {
    "name": "Moon",
    "fullDegree": 45.43578582742696,
    "normDegree": 15.435785827426962,
    "speed": 14.508803543221283,
    "isRetro": "false",
    "sign": "Taurus",
    "house": 6
  },
  {
    "name": "Mars",
    "fullDegree": 233.05966128352392,
    "normDegree": 23.059661283523923,
    "speed": 0.006931346565207917,
    "isRetro": "false",
    "sign": "Scorpio",
    "house": 12
  },
  {
    "name": "Mercury",
    "fullDegree": 91.08341827111468,
    "normDegree": 1.083418271114681,
    "speed": 2.1177778714756146,
    "isRetro": "false",
    "sign": "Cancer",
    "house": 8
  },
  {
    "name": "Jupiter",
    "fullDegree": 167.00470149777536,
    "normDegree": 17.004701497775358,
    "speed": 0.13422175459680458,
    "isRetro": "false",
    "sign": "Virgo",
    "house": 10
  },
  {
    "name": "Venus",
    "fullDegree": 105.56575057356383,
    "normDegree": 15.565750573563832,
    "speed": 1.228929722803493,
    "isRetro": "false",
    "sign": "Cancer",
    "house": 8
  },
  {
    "name": "Saturn",
    "fullDegree": 251.22306701714663,
    "normDegree": 11.223067017146633,
    "speed": -0.06080233543846638,
    "isRetro": "true",
    "sign": "Sagittarius",
    "house": 1
  },
  {
    "name": "Rahu",
    "fullDegree": 24.16034729503465,
    "normDegree": 24.16034729503465,
    "speed": 0.023356277817296992,
    "isRetro": "false",
    "sign": "Aries",
    "house": 5
  },
  {
    "name": "Ketu",
    "fullDegree": 341.9668244555685,
    "normDegree": 11.966824455568485,
    "speed": -0.008722211638006301,
    "isRetro": "true",
    "sign": "Pisces",
    "house": 4
  },
  {
    "name": "Uranus",
    "fullDegree": 286.3913184044086,
    "normDegree": 16.391318404408594,
    "speed": -0.02449873391267724,
    "isRetro": "true",
    "sign": "Capricorn",
    "house": 2
  },
  {
    "name": "Ascendant",
    "fullDegree": 251.08743445798456,
    "normDegree": 11.087434457984557,
    "speed": "-",
    "isRetro": false,
    "sign": "Sagittarius",
    "house": 1
  }
]
```
### bhav_madhya
Provide chalit table.

#### API Endpoint
bhav_madhya

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/bhav_madhya |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "ascendant": 236.60716263691694,
  "midheaven": 154.07226770931206,
  "ayanamsha": -24.087525507536782,
  "bhav_madhya": [
    {
      "house": 1,
      "degree": 236.60716263691694
    },
    {
      "house": 2,
      "degree": 269.095530994382
    },
    {
      "house": 3,
      "degree": 301.58389935184704
    },
    {
      "house": 4,
      "degree": 334.0722677093121
    },
    {
      "house": 5,
      "degree": 1.5838993518469806
    },
    {
      "house": 6,
      "degree": 29.09553099438199
    },
    {
      "house": 7,
      "degree": 56.60716263691694
    },
    {
      "house": 8,
      "degree": 89.09553099438199
    },
    {
      "house": 9,
      "degree": 121.58389935184704
    },
    {
      "house": 10,
      "degree": 154.0722677093121
    },
    {
      "house": 11,
      "degree": 181.583899351847
    },
    {
      "house": 12,
      "degree": 209.095530994382
    }
  ],
  "bhav_sandhi": [
    {
      "house": 1,
      "degree": 252.85134681564944
    },
    {
      "house": 2,
      "degree": 285.3397151731145
    },
    {
      "house": 3,
      "degree": 317.82808353057953
    },
    {
      "house": 4,
      "degree": 347.82808353057953
    },
    {
      "house": 5,
      "degree": 15.339715173114485
    },
    {
      "house": 6,
      "degree": 42.851346815649435
    },
    {
      "house": 7,
      "degree": 72.85134681564944
    },
    {
      "house": 8,
      "degree": 105.33971517311448
    },
    {
      "house": 9,
      "degree": 137.82808353057953
    },
    {
      "house": 10,
      "degree": 167.82808353057953
    },
    {
      "house": 11,
      "degree": 195.33971517311448
    },
    {
      "house": 12,
      "degree": 222.85134681564946
    }
  ]
}
```

## Basic Char Dasha
Get the sequence of all Char Dasha

### major_chardasha
Get the complete Major Char Dasha periods along with start and end dates for the given birth detail.

#### API Endpoint
major_chardasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/major_chardasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "sign_id": 7,
    "sign_name": "Scorpio",
    "duration": "11 Years",
    "start_date": "30-6-2016",
    "end_date": "30-6-2027"
  },
  {
    "sign_id": 6,
    "sign_name": "Libra",
    "duration": "8 Years",
    "start_date": "30-6-2027",
    "end_date": "30-6-2035"
  },
  {
    "sign_id": 5,
    "sign_name": "Virgo",
    "duration": "3 Years",
    "start_date": "30-6-2035",
    "end_date": "30-6-2038"
  },
  {
    "sign_id": 4,
    "sign_name": "Leo",
    "duration": "2 Years",
    "start_date": "30-6-2038",
    "end_date": "30-6-2040"
  },
  {
    "sign_id": 3,
    "sign_name": "Cancer",
    "duration": "3 Years",
    "start_date": "30-6-2040",
    "end_date": "30-6-2043"
  },
  {
    "sign_id": 2,
    "sign_name": "Gemini",
    "duration": "12 Years",
    "start_date": "30-6-2043",
    "end_date": "30-6-2055"
  },
  {
    "sign_id": 1,
    "sign_name": "Taurus",
    "duration": "1 Years",
    "start_date": "30-6-2055",
    "end_date": "30-6-2056"
  },
  {
    "sign_id": 0,
    "sign_name": "Aries",
    "duration": "6 Years",
    "start_date": "30-6-2056",
    "end_date": "30-6-2062"
  },
  {
    "sign_id": 11,
    "sign_name": "Pisces",
    "duration": "7 Years",
    "start_date": "30-6-2062",
    "end_date": "30-6-2069"
  },
  {
    "sign_id": 10,
    "sign_name": "Aquarius",
    "duration": "6 Years",
    "start_date": "30-6-2069",
    "end_date": "30-6-2075"
  },
  {
    "sign_id": 9,
    "sign_name": "Capricorn",
    "duration": "2 Years",
    "start_date": "30-6-2075",
    "end_date": "30-6-2077"
  },
  {
    "sign_id": 8,
    "sign_name": "Sagittarius",
    "duration": "8 Years",
    "start_date": "30-6-2077",
    "end_date": "30-6-2085"
  }
]
```

### current_chardasha
Returns the currently undergoing Char Dasha. It provides Major Period, Sub Period and Complete sub-sub period for the current date.

#### API Endpoint
current_chardasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/current_chardasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "dasha_date": "30-6-2016",
  "major_dasha": {
    "sign_id": 7,
    "sign_name": "Scorpio",
    "duration": "11 Years",
    "start_date": "30-6-2016",
    "end_date": "30-6-2027"
  },
  "sub_dasha": {
    "sign_id": 6,
    "sign_name": "Libra",
    "duration": "11 Months",
    "start_date": "30-6-2016",
    "end_date": "30-5-2017"
  },
  "sub_sub_dasha": {
    "sign_id": 7,
    "sign_name": "Scorpio",
    "start_date": "30-6-2016",
    "end_date": "27-7-2016"
  }
}
```

### sub_chardasha/:sign_name
Get all the sub periods of char dasha for the given major period rashi name in the API variable

#### API Endpoint
sub_chardasha/:sign_name

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_chardasha/:sign_name |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json{
  "major_dasha": {
    "sign_id": 0,
    "sign_name": "Aries",
    "duration": "3 Years",
    "start_date": "16-8-2027",
    "end_date": "16-8-2030"
  },
  "sub_dasha": [
    {
      "sign_id": 1,
      "sign_name": "Taurus",
      "start_date": "16-8-2027",
      "end_date": "16-11-2027",
      "start_ms": 1818388800000,
      "end_ms": 1826341200000
    },
    {
      "sign_id": 2,
      "sign_name": "Gemini",
      "start_date": "16-11-2027",
      "end_date": "16-2-2028",
      "start_ms": 1826341200000,
      "end_ms": 1834290000000
    },
    {
      "sign_id": 3,
      "sign_name": "Cancer",
      "start_date": "16-2-2028",
      "end_date": "16-5-2028",
      "start_ms": 1834290000000,
      "end_ms": 1842062400000
    },
    {
      "sign_id": 4,
      "sign_name": "Leo",
      "start_date": "16-5-2028",
      "end_date": "16-8-2028",
      "start_ms": 1842062400000,
      "end_ms": 1850011200000
    },
    {
      "sign_id": 5,
      "sign_name": "Virgo",
      "start_date": "16-8-2028",
      "end_date": "16-11-2028",
      "start_ms": 1850011200000,
      "end_ms": 1857963600000
    },
    {
      "sign_id": 6,
      "sign_name": "Libra",
      "start_date": "16-11-2028",
      "end_date": "16-2-2029",
      "start_ms": 1857963600000,
      "end_ms": 1865912400000
    },
    {
      "sign_id": 7,
      "sign_name": "Scorpio",
      "start_date": "16-2-2029",
      "end_date": "16-5-2029",
      "start_ms": 1865912400000,
      "end_ms": 1873598400000
    },
    {
      "sign_id": 8,
      "sign_name": "Sagittarius",
      "start_date": "16-5-2029",
      "end_date": "16-8-2029",
      "start_ms": 1873598400000,
      "end_ms": 1881547200000
    },
    {
      "sign_id": 9,
      "sign_name": "Capricorn",
      "start_date": "16-8-2029",
      "end_date": "16-11-2029",
      "start_ms": 1881547200000,
      "end_ms": 1889499600000
    },
    {
      "sign_id": 10,
      "sign_name": "Aquarius",
      "start_date": "16-11-2029",
      "end_date": "16-2-2030",
      "start_ms": 1889499600000,
      "end_ms": 1897448400000
    },
    {
      "sign_id": 11,
      "sign_name": "Pisces",
      "start_date": "16-2-2030",
      "end_date": "16-5-2030",
      "start_ms": 1897448400000,
      "end_ms": 1905134400000
    },
    {
      "sign_id": 0,
      "sign_name": "Aries",
      "start_date": "16-5-2030",
      "end_date": "16-8-2030",
      "start_ms": 1905134400000,
      "end_ms": 1913083200000
    }
  ]
}
```

### sub_chardasha/:majorSign/:subSign
Get all the sub periods of char dasha for the given major period rashi name in the API variable

#### API Endpoint
sub_chardasha/:majorSign/:subSign

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_chardasha/:majorSign/:subSign |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "major_dasha": {
    "sign_id": 0,
    "sign_name": "Aries",
    "duration": "6 Years",
    "start_date": "30-6-2056",
    "end_date": "30-6-2062"
  },
  "sub_dasha": {
    "sign_id": 3,
    "sign_name": "Cancer",
    "duration": "6 Months",
    "start_date": "30-6-2057",
    "end_date": "30-12-2057"
  },
  "sub_sub_dasha": [
    {
      "sign_id": 2,
      "sign_name": "Gemini",
      "start_date": "30-6-2057",
      "end_date": "15-7-2057",
      "start_ms": 2761099200000,
      "end_ms": 2762416800000
    },
    {
      "sign_id": 1,
      "sign_name": "Taurus",
      "start_date": "15-7-2057",
      "end_date": "30-7-2057",
      "start_ms": 2762416800000,
      "end_ms": 2763734400000
    },
    {
      "sign_id": 0,
      "sign_name": "Aries",
      "start_date": "30-7-2057",
      "end_date": "14-8-2057",
      "start_ms": 2763734400000,
      "end_ms": 2765052000000
    },
    {
      "sign_id": 11,
      "sign_name": "Pisces",
      "start_date": "14-8-2057",
      "end_date": "30-8-2057",
      "start_ms": 2765052000000,
      "end_ms": 2766369600000
    },
    {
      "sign_id": 10,
      "sign_name": "Aquarius",
      "start_date": "30-8-2057",
      "end_date": "14-9-2057",
      "start_ms": 2766369600000,
      "end_ms": 2767687200000
    },
    {
      "sign_id": 9,
      "sign_name": "Capricorn",
      "start_date": "14-9-2057",
      "end_date": "29-9-2057",
      "start_ms": 2767687200000,
      "end_ms": 2769004800000
    },
    {
      "sign_id": 8,
      "sign_name": "Sagittarius",
      "start_date": "29-9-2057",
      "end_date": "14-10-2057",
      "start_ms": 2769004800000,
      "end_ms": 2770322400000
    },
    {
      "sign_id": 7,
      "sign_name": "Scorpio",
      "start_date": "14-10-2057",
      "end_date": "30-10-2057",
      "start_ms": 2770322400000,
      "end_ms": 2771640000000
    },
    {
      "sign_id": 6,
      "sign_name": "Libra",
      "start_date": "30-10-2057",
      "end_date": "14-11-2057",
      "start_ms": 2771640000000,
      "end_ms": 2772961200000
    },
    {
      "sign_id": 5,
      "sign_name": "Virgo",
      "start_date": "14-11-2057",
      "end_date": "29-11-2057",
      "start_ms": 2772961200000,
      "end_ms": 2774278800000
    },
    {
      "sign_id": 4,
      "sign_name": "Leo",
      "start_date": "29-11-2057",
      "end_date": "14-12-2057",
      "start_ms": 2774278800000,
      "end_ms": 2775596400000
    },
    {
      "sign_id": 3,
      "sign_name": "Cancer",
      "start_date": "14-12-2057",
      "end_date": "30-12-2057",
      "start_ms": 2775596400000,
      "end_ms": 2776914000000
    }
  ]
}

```


## Basic Gemstone Suggestions
Provides report of Gems and Remedies with Life Stone, Lucky Stone, Benefic Stone, Stone details as per Vimsottari Mahadasha period.

### basic_gem_suggestion
This api recommends life stone,lucky stone,benefic stone.


#### API Endpoint
basic_gem_suggestion

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_gem_suggestion|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "LIFE": {
    "name": "Red Coral",
    "semi_gem": "Red Agate",
    "wear_finger": "Index",
    "weight_caret": "6 - 10.25",
    "wear_metal": "Gold",
    "wear_day": "Tuesday",
    "gem_deity": "Mars"
  },
  "BENEFIC": {
    "name": "Opal",
    "semi_gem": "Opal/Zircon",
    "wear_finger": "Little",
    "weight_caret": "1 - 4.25",
    "wear_metal": "Silver",
    "wear_day": "Friday",
    "gem_deity": "Venus"
  },
  "LUCKY": {
    "name": "Emerald",
    "semi_gem": "Onyx",
    "wear_finger": "Little",
    "weight_caret": " 4 - 6.25",
    "wear_metal": "Gold",
    "wear_day": "Wednesday",
    "gem_deity": "Mercury"
  }
}

```

## Basic Numerology
Provides detailed Numerology report.

### numero_table
Provides detailed Numerology report.

#### API Endpoint
numero_table

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_table|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "name": "Ajeet Kanojia",
  "date": "6-121-2014",
  "destiny_number": 8,
  "radical_number": 6,
  "name_number": 1,
  "evil_num": "1,8",
  "fav_color": "White",
  "fav_day": "Thursday, Tuesday, Friday",
  "fav_god": "Devi",
  "fav_mantra": "|| Om Shum Shukray Namah ||",
  "fav_metal": "Sillver",
  "fav_stone": "Diamond, Opal",
  "fav_substone": "Zircon, White Sapphire",
  "friendly_num": "4,3,9",
  "neutral_num": "2,5,7",
  "radical_num": "6",
  "radical_ruler": "Venus"
}

```

## Basic Panchang
The package consists of the five panchang elements which are day, nakshatra, yog, karan and tithi along with sunrise and sunset timings. This also includes chaugadiya and planetary degrees at that point of time.

#### We have two types of Panchang APIs

**1\. Panchang at specified date and time**
Here, following APIs are used and date and time along with latitude, longitude and timezone are expected -

*   [1\. basic_panchang](#-basic-panchang/basic_panchang)
*   [2\. planet_panchang](#-basic-panchang/planet_panchang)
*   [3\. advanced_panchang](#-advanced-panchang/advanced_panchang)

**2\. Panchang at Sunsrise for given day**
Following APIs should be used for getting the panchang data points at the time of sunrise which are used by traditional calendars-

*   [1\. basic_panchang/sunrise](#-basic-panchang/basic_panchang/sunrise)
*   [2\. planet_panchang/sunrise](#-basic-panchang/planet_panchang/sunrise)
*   [2\. advanced_panchang/sunrise](#-advanced-panchang/advanced_panchang/sunrise)
*   [4\. chaughadiya_muhurta](#-advanced-panchang/chaughadiya_muhurta)
*   [5\. hora_muhurta](#-advanced-panchang/hora_muhurta)

**" Here only date along with latitude, longitude and timezone are expected to be passed. No time is required. "**

### basic_panchang

Provides data points for panchang elements.

#### API Endpoint

basic_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_panchang |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| hour | int | Panchang hour, eg:12 |
| min | int | Panchang minute, eg:34 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "day": "Wednesday",
  "tithi": "Shukla-Ashtami",
  "yog": "Vaidhriti",
  "nakshatra": "Krittika",
  "karan": "Vishti",
  "sunrise": "7:3:17",
  "sunset": "18:43:38"
}

```

### basic_panchang/sunrise

Provides data points for panchang elements.

#### API Endpoint

basic_panchang/sunrise

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_panchang/sunrise |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| hour | int | Panchang hour, eg:12 |
| min | int | Panchang minute, eg:34 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "day": "Wednesday",
  "tithi": "Shukla-Ashtami",
  "yog": "Vaidhriti",
  "nakshatra": "Krittika",
  "karan": "Vishti",
  "sunrise": "7:3:17",
  "sunset": "18:43:38"
}

```

### planet_panchang

Provides panchang planetary degrees ,retrograde and positions.

#### API Endpoint

planet_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planet_panchang |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| hour | int | Panchang hour, eg:12 |
| min | int | Panchang minute, eg:34 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 312.30400347269256,
    "normDegree": 12.304003472692557,
    "isRetro": "false",
    "sign": "Aquarius",
    "sign_lord": "Saturn",
    "nakshatra": "Shatbhisha",
    "nakshatra_lord": "Rahu"
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 37.45112477913563,
    "normDegree": 7.4511247791356325,
    "isRetro": "false",
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Krittika",
    "nakshatra_lord": "Sun"
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 340.0086052768496,
    "normDegree": 10.008605276849607,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 285.56691716258143,
    "normDegree": 15.566917162581433,
    "isRetro": "false",
    "sign": "Capricorn",
    "sign_lord": "Saturn",
    "nakshatra": "Shravan",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 111.19916911928078,
    "normDegree": 21.199169119280782,
    "isRetro": "true",
    "sign": "Cancer",
    "sign_lord": "Moon",
    "nakshatra": "Ashlesha",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 341.4409638339589,
    "normDegree": 11.440963833958904,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 220.60759834888617,
    "normDegree": 10.607598348886171,
    "isRetro": "false",
    "sign": "Scorpio",
    "sign_lord": "Mars",
    "nakshatra": "Anuradha",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 167.93931821066,
    "normDegree": 17.93931821065999,
    "isRetro": "true",
    "sign": "Virgo",
    "sign_lord": "Mercury",
    "nakshatra": "Hast",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 347.93931821065996,
    "normDegree": 17.939318210659962,
    "isRetro": "true",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Revati",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 9,
    "name": "Asc",
    "fullDegree": 57.565378655311946,
    "normDegree": 27.565378655311946,
    "isRetro": false,
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Mrigshira",
    "nakshatra_lord": "Mars"
  }
]

```

### planet_panchang/sunrise

Provides panchang planetary degrees and positions for sunrise.

#### API Endpoint

planet_panchang/sunrise

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planet_panchang/sunrise |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| hour | int | Panchang hour, eg:12 |
| min | int | Panchang minute, eg:34 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 312.30400347269256,
    "normDegree": 12.304003472692557,
    "isRetro": "false",
    "sign": "Aquarius",
    "sign_lord": "Saturn",
    "nakshatra": "Shatbhisha",
    "nakshatra_lord": "Rahu"
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 37.45112477913563,
    "normDegree": 7.4511247791356325,
    "isRetro": "false",
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Krittika",
    "nakshatra_lord": "Sun"
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 340.0086052768496,
    "normDegree": 10.008605276849607,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 285.56691716258143,
    "normDegree": 15.566917162581433,
    "isRetro": "false",
    "sign": "Capricorn",
    "sign_lord": "Saturn",
    "nakshatra": "Shravan",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 111.19916911928078,
    "normDegree": 21.199169119280782,
    "isRetro": "true",
    "sign": "Cancer",
    "sign_lord": "Moon",
    "nakshatra": "Ashlesha",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 341.4409638339589,
    "normDegree": 11.440963833958904,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 220.60759834888617,
    "normDegree": 10.607598348886171,
    "isRetro": "false",
    "sign": "Scorpio",
    "sign_lord": "Mars",
    "nakshatra": "Anuradha",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 167.93931821066,
    "normDegree": 17.93931821065999,
    "isRetro": "true",
    "sign": "Virgo",
    "sign_lord": "Mercury",
    "nakshatra": "Hast",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 347.93931821065996,
    "normDegree": 17.939318210659962,
    "isRetro": "true",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Revati",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 9,
    "name": "Asc",
    "fullDegree": 57.565378655311946,
    "normDegree": 27.565378655311946,
    "isRetro": false,
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Mrigshira",
    "nakshatra_lord": "Mars"
  }
]

```

## Basic Vimshottari Dasha
Get analysis of precise period of events to come.

### current_vdasha
Provides details of current vimshottari dasha

#### API Endpoint
current_vdasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/current_vdasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "major": {
    "end": "17-9-2028 14:32",
    "planet": "MERCURY",
    "start": "18-9-2011 11:43"
  },
  "minor": {
    "end": "11-2-2015 7:29",
    "planet": "KETU",
    "start": "14-2-2014 2:43"
  },
  "sub_minor": {
    "end": "22-12-2014 0:0",
    "planet": "SATURN",
    "start": "25-10-2014 15:39"
  },
  "sub_sub_minor": {
    "end": "14-12-2014 8:30",
    "planet": "RAHU",
    "start": "5-12-2014 18:2"
  },
  "sub_sub_sub_minor": {
    "end": "10-12-2014 18:28",
    "planet": "MERCURY",
    "start": "9-12-2014 13:13"
  }
}
```

### current_vdasha_all
Provides details of All Level of current vimshottari dasha

#### API Endpoint
current_vdasha_all

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/current_vdasha_all |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "major": {
    "dasha_period": [
      {
        "planet": "Rahu",
        "start": "14-1-2013 23:56",
        "end": "15-1-2031 8:34"
      },
      {
        "planet": "Jupiter",
        "start": "15-1-2031 8:34",
        "end": "15-1-2047 5:34"
      },
      {
        "planet": "Saturn",
        "start": "15-1-2047 5:34",
        "end": "14-1-2066 20:1"
      },
      {
        "planet": "Mercury",
        "start": "14-1-2066 20:1",
        "end": "14-1-2083 22:50"
      },
      {
        "planet": "Ketu",
        "start": "14-1-2083 22:50",
        "end": "14-1-2090 15:31"
      },
      {
        "planet": "Venus",
        "start": "14-1-2090 15:31",
        "end": "15-1-2110 11:46"
      },
      {
        "planet": "Sun",
        "start": "15-1-2110 11:46",
        "end": "15-1-2116 22:39"
      },
      {
        "planet": "Moon",
        "start": "15-1-2116 22:39",
        "end": "15-1-2126 8:47"
      },
      {
        "planet": "Mars",
        "start": "15-1-2126 8:47",
        "end": "15-1-2133 1:28"
      }
    ]
  },
  "minor": {
    "planet": {
      "major": "Rahu"
    },
    "dasha_period": [
      {
        "planet": "Rahu",
        "start": "14-1-2013 23:56",
        "end": "28-9-2015 3:38"
      },
      {
        "planet": "Jupiter",
        "start": "28-9-2015 3:38",
        "end": "20-2-2018 17:35"
      },
      {
        "planet": "Saturn",
        "start": "20-2-2018 17:35",
        "end": "27-12-2020 16:9"
      },
      {
        "planet": "Mercury",
        "start": "27-12-2020 16:9",
        "end": "17-7-2023 0:58"
      },
      {
        "planet": "Ketu",
        "start": "17-7-2023 0:58",
        "end": "3-8-2024 13:4"
      },
      {
        "planet": "Venus",
        "start": "3-8-2024 13:4",
        "end": "4-8-2027 6:31"
      },
      {
        "planet": "Sun",
        "start": "4-8-2027 6:31",
        "end": "27-6-2028 23:44"
      },
      {
        "planet": "Moon",
        "start": "27-6-2028 23:44",
        "end": "27-12-2029 20:28"
      },
      {
        "planet": "Mars",
        "start": "27-12-2029 20:28",
        "end": "15-1-2031 8:34"
      }
    ]
  },
  "sub_minor": {
    "planet": {
      "major": "Rahu",
      "minor": "Rahu"
    },
    "dasha_period": [
      {
        "planet": "Rahu",
        "start": "14-1-2013 23:56",
        "end": "11-6-2013 22:5"
      },
      {
        "planet": "Jupiter",
        "start": "11-6-2013 22:5",
        "end": "21-10-2013 9:47"
      },
      {
        "planet": "Saturn",
        "start": "21-10-2013 9:47",
        "end": "26-3-2014 13:10"
      },
      {
        "planet": "Mercury",
        "start": "26-3-2014 13:10",
        "end": "13-8-2014 6:5"
      },
      {
        "planet": "Ketu",
        "start": "13-8-2014 6:5",
        "end": "9-10-2014 18:42"
      },
      {
        "planet": "Venus",
        "start": "9-10-2014 18:42",
        "end": "23-3-2015 3:19"
      },
      {
        "planet": "Sun",
        "start": "23-3-2015 3:19",
        "end": "11-5-2015 10:42"
      },
      {
        "planet": "Moon",
        "start": "11-5-2015 10:42",
        "end": "1-8-2015 15:1"
      },
      {
        "planet": "Mars",
        "start": "1-8-2015 15:1",
        "end": "28-9-2015 3:38"
      }
    ]
  },
  "sub_sub_minor": {
    "planet": {
      "major": "Rahu",
      "minor": "Rahu",
      "sub_minor": "Venus"
    },
    "dasha_period": [
      {
        "planet": "Venus",
        "start": "9-10-2014 18:42",
        "end": "6-11-2014 4:8"
      },
      {
        "planet": "Sun",
        "start": "6-11-2014 4:8",
        "end": "14-11-2014 9:22"
      },
      {
        "planet": "Moon",
        "start": "14-11-2014 9:22",
        "end": "28-11-2014 2:5"
      },
      {
        "planet": "Mars",
        "start": "28-11-2014 2:5",
        "end": "7-12-2014 16:11"
      },
      {
        "planet": "Rahu",
        "start": "7-12-2014 16:11",
        "end": "1-1-2015 7:53"
      },
      {
        "planet": "Jupiter",
        "start": "1-1-2015 7:53",
        "end": "23-1-2015 5:50"
      },
      {
        "planet": "Saturn",
        "start": "23-1-2015 5:50",
        "end": "18-2-2015 6:24"
      },
      {
        "planet": "Mercury",
        "start": "18-2-2015 6:24",
        "end": "13-3-2015 13:13"
      },
      {
        "planet": "Ketu",
        "start": "13-3-2015 13:13",
        "end": "23-3-2015 3:19"
      }
    ]
  },
  "sub_sub_sub_minor": {
    "planet": {
      "major": "Rahu",
      "minor": "Rahu",
      "sub_minor": "Venus",
      "sub_sub_minor": "Ketu"
    },
    "dasha_period": [
      {
        "planet": "Ketu",
        "start": "13-3-2015 13:13",
        "end": "14-3-2015 2:38"
      },
      {
        "planet": "Venus",
        "start": "14-3-2015 2:38",
        "end": "15-3-2015 16:59"
      },
      {
        "planet": "Sun",
        "start": "15-3-2015 16:59",
        "end": "16-3-2015 4:30"
      },
      {
        "planet": "Moon",
        "start": "16-3-2015 4:30",
        "end": "16-3-2015 23:40"
      },
      {
        "planet": "Mars",
        "start": "16-3-2015 23:40",
        "end": "17-3-2015 13:6"
      },
      {
        "planet": "Rahu",
        "start": "17-3-2015 13:6",
        "end": "18-3-2015 23:37"
      },
      {
        "planet": "Jupiter",
        "start": "18-3-2015 23:37",
        "end": "20-3-2015 6:17"
      },
      {
        "planet": "Saturn",
        "start": "20-3-2015 6:17",
        "end": "21-3-2015 18:43"
      },
      {
        "planet": "Mercury",
        "start": "21-3-2015 18:43",
        "end": "23-3-2015 3:19"
      }
    ]
  }
}
```


### major_vdasha
Provides details of Major vimshottari dasha

#### API Endpoint
major_vdasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/major_vdasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "JUPITER",
    "start": "18-1-2010 8:54",
    "end": "18-1-2026 5:55"
  },
  {
    "planet": "SATURN",
    "start": "18-1-2026 5:55",
    "end": "17-1-2045 20:21"
  },
  {
    "planet": "MERCURY",
    "start": "17-1-2045 20:21",
    "end": "17-1-2062 23:10"
  },
  {
    "planet": "KETU",
    "start": "17-1-2062 23:10",
    "end": "17-1-2069 15:52"
  },
  {
    "planet": "VENUS",
    "start": "17-1-2069 15:52",
    "end": "17-1-2089 12:7"
  },
  {
    "planet": "SUN",
    "start": "17-1-2089 12:7",
    "end": "17-1-2095 22:59"
  },
  {
    "planet": "MOON",
    "start": "17-1-2095 22:59",
    "end": "18-1-2105 9:7"
  },
  {
    "planet": "MARS",
    "start": "18-1-2105 9:7",
    "end": "19-1-2112 1:49"
  },
  {
    "planet": "RAHU",
    "start": "19-1-2112 1:49",
    "end": "18-1-2130 10:26"
  }
]
```

### major_vdasha
Provides details of Major vimshottari dasha

#### API Endpoint
major_vdasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/major_vdasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "JUPITER",
    "start": "18-1-2010 8:54",
    "end": "18-1-2026 5:55"
  },
  {
    "planet": "SATURN",
    "start": "18-1-2026 5:55",
    "end": "17-1-2045 20:21"
  },
  {
    "planet": "MERCURY",
    "start": "17-1-2045 20:21",
    "end": "17-1-2062 23:10"
  },
  {
    "planet": "KETU",
    "start": "17-1-2062 23:10",
    "end": "17-1-2069 15:52"
  },
  {
    "planet": "VENUS",
    "start": "17-1-2069 15:52",
    "end": "17-1-2089 12:7"
  },
  {
    "planet": "SUN",
    "start": "17-1-2089 12:7",
    "end": "17-1-2095 22:59"
  },
  {
    "planet": "MOON",
    "start": "17-1-2095 22:59",
    "end": "18-1-2105 9:7"
  },
  {
    "planet": "MARS",
    "start": "18-1-2105 9:7",
    "end": "19-1-2112 1:49"
  },
  {
    "planet": "RAHU",
    "start": "19-1-2112 1:49",
    "end": "18-1-2130 10:26"
  }
]
```

### sub_vdasha/:mahaDashaLord
Provide antardasha details

#### API Endpoint
sub_vdasha/:mahaDashaLord

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_vdasha/:mahaDashaLord |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "Mars",
    "start": "16-12-2028 14:52",
    "end": "14-5-2029 18:19"
  },
  {
    "planet": "Rahu",
    "start": "14-5-2029 18:19",
    "end": "2-6-2030 6:37"
  },
  {
    "planet": "Jupiter",
    "start": "2-6-2030 6:37",
    "end": "9-5-2031 4:13"
  },
  {
    "planet": "Saturn",
    "start": "9-5-2031 4:13",
    "end": "16-6-2032 23:52"
  },
  {
    "planet": "Mercury",
    "start": "16-6-2032 23:52",
    "end": "14-6-2033 4:49"
  },
  {
    "planet": "Ketu",
    "start": "14-6-2033 4:49",
    "end": "10-11-2033 8:16"
  },
  {
    "planet": "Venus",
    "start": "10-11-2033 8:16",
    "end": "10-1-2035 11:16"
  },
  {
    "planet": "Sun",
    "start": "10-1-2035 11:16",
    "end": "18-5-2035 7:22"
  },
  {
    "planet": "Moon",
    "start": "18-5-2035 7:22",
    "end": "17-12-2035 8:52"
  }
]
```

### sub_sub_vdasha/:mahaDashaLord/:antarDashaLord
Provide pratyantar dasha details

#### API Endpoint
sub_sub_vdasha/:mahaDashaLord/:antarDashaLord

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_sub_vdasha/:mahaDashaLord/:antarDashaLord |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "Sun",
    "start": "10-1-2035 11:16",
    "end": "16-1-2035 20:41"
  },
  {
    "planet": "Moon",
    "start": "16-1-2035 20:41",
    "end": "27-1-2035 12:21"
  },
  {
    "planet": "Mars",
    "start": "27-1-2035 12:21",
    "end": "3-2-2035 23:20"
  },
  {
    "planet": "Rahu",
    "start": "3-2-2035 23:20",
    "end": "23-2-2035 3:33"
  },
  {
    "planet": "Jupiter",
    "start": "23-2-2035 3:33",
    "end": "12-3-2035 4:37"
  },
  {
    "planet": "Saturn",
    "start": "12-3-2035 4:37",
    "end": "1-4-2035 10:24"
  },
  {
    "planet": "Mercury",
    "start": "1-4-2035 10:24",
    "end": "19-4-2035 13:3"
  },
  {
    "planet": "Ketu",
    "start": "19-4-2035 13:3",
    "end": "27-4-2035 0:1"
  },
  {
    "planet": "Venus",
    "start": "27-4-2035 0:1",
    "end": "18-5-2035 7:22"
  }
]
```

### sub_sub_sub_vdasha/:mahaDashaLord/:antarDashaLord/:pratyantarDashaLord
Provide sookshma dasha details

#### API Endpoint
sub_sub_sub_vdasha/:mahaDashaLord/:antarDashaLord/:pratyantarDashaLord

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_sub_sub_vdasha/:mahaDashaLord/:antarDashaLord/:pratyantarDashaLord|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "Moon",
    "start": "16-1-2035 20:41",
    "end": "17-1-2035 17:59"
  },
  {
    "planet": "Mars",
    "start": "17-1-2035 17:59",
    "end": "18-1-2035 8:54"
  },
  {
    "planet": "Rahu",
    "start": "18-1-2035 8:54",
    "end": "19-1-2035 23:15"
  },
  {
    "planet": "Jupiter",
    "start": "19-1-2035 23:15",
    "end": "21-1-2035 9:20"
  },
  {
    "planet": "Saturn",
    "start": "21-1-2035 9:20",
    "end": "23-1-2035 1:49"
  },
  {
    "planet": "Mercury",
    "start": "23-1-2035 1:49",
    "end": "24-1-2035 14:3"
  },
  {
    "planet": "Ketu",
    "start": "24-1-2035 14:3",
    "end": "25-1-2035 4:57"
  },
  {
    "planet": "Venus",
    "start": "25-1-2035 4:57",
    "end": "26-1-2035 23:34"
  },
  {
    "planet": "Sun",
    "start": "26-1-2035 23:34",
    "end": "27-1-2035 12:21"
  }
]
```

### sub_sub_sub_sub_vdasha/:mahaDashaLord/:antarDashaLord/:pratyantarDashaLord/:sookshmDashaLord
Provide pran dasha details

#### API Endpoint
sub_sub_sub_sub_vdasha/:mahaDashaLord/:antarDashaLord/:pratyantarDashaLord/:sookshmDashaLord

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_sub_sub_sub_vdasha/:mahaDashaLord/:antarDashaLord/:pratyantarDashaLord/:sookshmDashaLord|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "Sun",
    "start": "3-1-2035 16:51",
    "end": "3-1-2035 17:29"
  },
  {
    "planet": "Moon",
    "start": "3-1-2035 17:29",
    "end": "3-1-2035 18:33"
  },
  {
    "planet": "Mars",
    "start": "3-1-2035 18:33",
    "end": "3-1-2035 19:18"
  },
  {
    "planet": "Rahu",
    "start": "3-1-2035 19:18",
    "end": "3-1-2035 21:13"
  },
  {
    "planet": "Jupiter",
    "start": "3-1-2035 21:13",
    "end": "3-1-2035 22:55"
  },
  {
    "planet": "Saturn",
    "start": "3-1-2035 22:55",
    "end": "4-1-2035 0:57"
  },
  {
    "planet": "Mercury",
    "start": "4-1-2035 0:57",
    "end": "4-1-2035 2:45"
  },
  {
    "planet": "Ketu",
    "start": "4-1-2035 2:45",
    "end": "4-1-2035 3:30"
  },
  {
    "planet": "Venus",
    "start": "4-1-2035 3:30",
    "end": "4-1-2035 5:38"
  }
]
```

## Basic Yogini Dasha
Get sequence of all eight yogini dasha, their lords and dasha periods.

### major_yogini_dasha
Gives a list of Major yogini dasha for two cycles

#### API Endpoint
major_yogini_dasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/major_yogini_dasha|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "dasha_id": 1,
    "dasha_name": "Pingla",
    "start_date": "9-11-2000 5:9",
    "end_date": "9-11-2002 5:9",
    "start_ms": 973726740000,
    "end_ms": 1036798740000,
    "duration": 2
  },
  {
    "dasha_id": 2,
    "dasha_name": "Dhanya",
    "start_date": "9-11-2002 5:9",
    "end_date": "9-11-2005 5:9",
    "start_ms": 1036798740000,
    "end_ms": 1131493140000,
    "duration": 3
  },
  {
    "dasha_id": 3,
    "dasha_name": "Bhramari",
    "start_date": "9-11-2005 5:9",
    "end_date": "9-11-2009 5:9",
    "start_ms": 1131493140000,
    "end_ms": 1257723540000,
    "duration": 4
  },
  {
    "dasha_id": 4,
    "dasha_name": "Bhadrika",
    "start_date": "9-11-2009 5:9",
    "end_date": "9-11-2014 5:9",
    "start_ms": 1257723540000,
    "end_ms": 1415489940000,
    "duration": 5
  },
  {
    "dasha_id": 5,
    "dasha_name": "Ulka",
    "start_date": "9-11-2014 5:9",
    "end_date": "9-11-2020 5:9",
    "start_ms": 1415489940000,
    "end_ms": 1604878740000,
    "duration": 6
  },
  {
    "dasha_id": 6,
    "dasha_name": "Siddha",
    "start_date": "9-11-2020 5:9",
    "end_date": "9-11-2027 5:9",
    "start_ms": 1604878740000,
    "end_ms": 1825717140000,
    "duration": 7
  },
  {
    "dasha_id": 7,
    "dasha_name": "Sankata",
    "start_date": "9-11-2027 5:9",
    "end_date": "9-11-2035 5:9",
    "start_ms": 1825717140000,
    "end_ms": 2078177940000,
    "duration": 8
  },
  {
    "dasha_id": 0,
    "dasha_name": "Mangla",
    "start_date": "9-11-2035 5:9",
    "end_date": "9-11-2036 5:9",
    "start_ms": 2078177940000,
    "end_ms": 2109800340000,
    "duration": 1
  },
  {
    "dasha_id": 1,
    "dasha_name": "Pingla",
    "start_date": "9-11-2036 5:9",
    "end_date": "9-11-2038 5:9",
    "start_ms": 2109800340000,
    "end_ms": 2172872340000,
    "duration": 2
  },
  {
    "dasha_id": 2,
    "dasha_name": "Dhanya",
    "start_date": "9-11-2038 5:9",
    "end_date": "9-11-2041 5:9",
    "start_ms": 2172872340000,
    "end_ms": 2267566740000,
    "duration": 3
  },
  {
    "dasha_id": 3,
    "dasha_name": "Bhramari",
    "start_date": "9-11-2041 5:9",
    "end_date": "9-11-2045 5:9",
    "start_ms": 2267566740000,
    "end_ms": 2393797140000,
    "duration": 4
  },
  {
    "dasha_id": 4,
    "dasha_name": "Bhadrika",
    "start_date": "9-11-2045 5:9",
    "end_date": "9-11-2050 5:9",
    "start_ms": 2393797140000,
    "end_ms": 2551563540000,
    "duration": 5
  },
  {
    "dasha_id": 5,
    "dasha_name": "Ulka",
    "start_date": "9-11-2050 5:9",
    "end_date": "9-11-2056 5:9",
    "start_ms": 2551563540000,
    "end_ms": 2740952340000,
    "duration": 6
  },
  {
    "dasha_id": 6,
    "dasha_name": "Siddha",
    "start_date": "9-11-2056 5:9",
    "end_date": "9-11-2063 5:9",
    "start_ms": 2740952340000,
    "end_ms": 2961790740000,
    "duration": 7
  },
  {
    "dasha_id": 7,
    "dasha_name": "Sankata",
    "start_date": "9-11-2063 5:9",
    "end_date": "9-11-2071 5:9",
    "start_ms": 2961790740000,
    "end_ms": 3214251540000,
    "duration": 8
  },
  {
    "dasha_id": 0,
    "dasha_name": "Mangla",
    "start_date": "9-11-2071 5:9",
    "end_date": "9-11-2072 5:9",
    "start_ms": 3214251540000,
    "end_ms": 3245873940000,
    "duration": 1
  }
]
```

### sub_yogini_dasha
Get all the yogini dasha for both the major yogini dasha cycle. Sub Yogini dasha for 72 Years.

#### API Endpoint
sub_yogini_dasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_yogini_dasha|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "major_dasha": {
      "dasha_id": 1,
      "dasha_name": "Pingla",
      "start_date": "9-11-2000 5:9",
      "end_date": "9-11-2002 5:9",
      "start_ms": 973726740000,
      "end_ms": 1036798740000,
      "duration": 2
    },
    "sub_dasha": [
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "9-11-2000 5:9",
        "end_date": "19-12-2000 19:9",
        "start_ms": 973726740000,
        "end_ms": 977233140000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "19-12-2000 19:9",
        "end_date": "18-2-2001 16:9",
        "start_ms": 977233140000,
        "end_ms": 982492740000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "18-2-2001 16:9",
        "end_date": "10-5-2001 20:9",
        "start_ms": 982492740000,
        "end_ms": 989505540000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "10-5-2001 20:9",
        "end_date": "20-8-2001 7:9",
        "start_ms": 989505540000,
        "end_ms": 998271540000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "20-8-2001 7:9",
        "end_date": "20-12-2001 1:9",
        "start_ms": 998271540000,
        "end_ms": 1008790740000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "20-12-2001 1:9",
        "end_date": "11-5-2002 2:9",
        "start_ms": 1008790740000,
        "end_ms": 1021063140000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "11-5-2002 2:9",
        "end_date": "20-10-2002 10:9",
        "start_ms": 1021063140000,
        "end_ms": 1035088740000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "20-10-2002 10:9",
        "end_date": "9-11-2002 5:9",
        "start_ms": 1035088740000,
        "end_ms": 1036798740000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 2,
      "dasha_name": "Dhanya",
      "start_date": "9-11-2002 5:9",
      "end_date": "9-11-2005 5:9",
      "start_ms": 1036798740000,
      "end_ms": 1131493140000,
      "duration": 3
    },
    "sub_dasha": [
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "9-11-2002 5:9",
        "end_date": "8-2-2003 12:39",
        "start_ms": 1036798740000,
        "end_ms": 1044688140000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "8-2-2003 12:39",
        "end_date": "10-6-2003 6:39",
        "start_ms": 1044688140000,
        "end_ms": 1055207340000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "10-6-2003 6:39",
        "end_date": "9-11-2003 11:9",
        "start_ms": 1055207340000,
        "end_ms": 1068356340000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-11-2003 11:9",
        "end_date": "10-5-2004 2:9",
        "start_ms": 1068356340000,
        "end_ms": 1084135140000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "10-5-2004 2:9",
        "end_date": "9-12-2004 3:39",
        "start_ms": 1084135140000,
        "end_ms": 1102543740000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "9-12-2004 3:39",
        "end_date": "9-8-2005 15:39",
        "start_ms": 1102543740000,
        "end_ms": 1123582140000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "9-8-2005 15:39",
        "end_date": "9-9-2005 2:9",
        "start_ms": 1123582140000,
        "end_ms": 1126211940000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "9-9-2005 2:9",
        "end_date": "9-11-2005 5:9",
        "start_ms": 1126211940000,
        "end_ms": 1131493140000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 3,
      "dasha_name": "Bhramari",
      "start_date": "9-11-2005 5:9",
      "end_date": "9-11-2009 5:9",
      "start_ms": 1131493140000,
      "end_ms": 1257723540000,
      "duration": 4
    },
    "sub_dasha": [
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "9-11-2005 5:9",
        "end_date": "20-4-2006 13:9",
        "start_ms": 1131493140000,
        "end_ms": 1145518740000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "20-4-2006 13:9",
        "end_date": "9-11-2006 11:9",
        "start_ms": 1145518740000,
        "end_ms": 1163050740000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-11-2006 11:9",
        "end_date": "10-7-2007 23:9",
        "start_ms": 1163050740000,
        "end_ms": 1184089140000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "10-7-2007 23:9",
        "end_date": "20-4-2008 1:9",
        "start_ms": 1184089140000,
        "end_ms": 1208633940000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "20-4-2008 1:9",
        "end_date": "10-3-2009 17:9",
        "start_ms": 1208633940000,
        "end_ms": 1236685140000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "10-3-2009 17:9",
        "end_date": "20-4-2009 7:9",
        "start_ms": 1236685140000,
        "end_ms": 1240191540000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "20-4-2009 7:9",
        "end_date": "10-7-2009 11:9",
        "start_ms": 1240191540000,
        "end_ms": 1247204340000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "10-7-2009 11:9",
        "end_date": "9-11-2009 5:9",
        "start_ms": 1247204340000,
        "end_ms": 1257723540000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 4,
      "dasha_name": "Bhadrika",
      "start_date": "9-11-2009 5:9",
      "end_date": "9-11-2014 5:9",
      "start_ms": 1257723540000,
      "end_ms": 1415489940000,
      "duration": 5
    },
    "sub_dasha": [
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "9-11-2009 5:9",
        "end_date": "20-7-2010 20:39",
        "start_ms": 1257723540000,
        "end_ms": 1279638540000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "20-7-2010 20:39",
        "end_date": "21-5-2011 5:39",
        "start_ms": 1279638540000,
        "end_ms": 1305936540000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "21-5-2011 5:39",
        "end_date": "10-5-2012 8:9",
        "start_ms": 1305936540000,
        "end_ms": 1336617540000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "10-5-2012 8:9",
        "end_date": "20-6-2013 4:9",
        "start_ms": 1336617540000,
        "end_ms": 1371681540000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "20-6-2013 4:9",
        "end_date": "9-8-2013 21:39",
        "start_ms": 1371681540000,
        "end_ms": 1376064540000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "9-8-2013 21:39",
        "end_date": "19-11-2013 8:39",
        "start_ms": 1376064540000,
        "end_ms": 1384830540000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "19-11-2013 8:39",
        "end_date": "20-4-2014 13:9",
        "start_ms": 1384830540000,
        "end_ms": 1397979540000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "20-4-2014 13:9",
        "end_date": "9-11-2014 5:9",
        "start_ms": 1397979540000,
        "end_ms": 1415489940000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 5,
      "dasha_name": "Ulka",
      "start_date": "9-11-2014 5:9",
      "end_date": "9-11-2020 5:9",
      "start_ms": 1415489940000,
      "end_ms": 1604878740000,
      "duration": 6
    },
    "sub_dasha": [
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-11-2014 5:9",
        "end_date": "9-11-2015 11:9",
        "start_ms": 1415489940000,
        "end_ms": 1447047540000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "9-11-2015 11:9",
        "end_date": "8-1-2017 14:9",
        "start_ms": 1447047540000,
        "end_ms": 1483864740000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "8-1-2017 14:9",
        "end_date": "10-5-2018 14:9",
        "start_ms": 1483864740000,
        "end_ms": 1525941540000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "10-5-2018 14:9",
        "end_date": "10-7-2018 11:9",
        "start_ms": 1525941540000,
        "end_ms": 1531201140000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "10-7-2018 11:9",
        "end_date": "9-11-2018 5:9",
        "start_ms": 1531201140000,
        "end_ms": 1541720340000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "9-11-2018 5:9",
        "end_date": "10-5-2019 20:9",
        "start_ms": 1541720340000,
        "end_ms": 1557499140000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "10-5-2019 20:9",
        "end_date": "9-1-2020 8:9",
        "start_ms": 1557499140000,
        "end_ms": 1578537540000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "9-1-2020 8:9",
        "end_date": "9-11-2020 5:9",
        "start_ms": 1578537540000,
        "end_ms": 1604878740000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 6,
      "dasha_name": "Siddha",
      "start_date": "9-11-2020 5:9",
      "end_date": "9-11-2027 5:9",
      "start_ms": 1604878740000,
      "end_ms": 1825717140000,
      "duration": 7
    },
    "sub_dasha": [
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "9-11-2020 5:9",
        "end_date": "21-3-2022 8:39",
        "start_ms": 1604878740000,
        "end_ms": 1647832140000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "21-3-2022 8:39",
        "end_date": "10-10-2023 12:39",
        "start_ms": 1647832140000,
        "end_ms": 1696921740000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "10-10-2023 12:39",
        "end_date": "20-12-2023 13:9",
        "start_ms": 1696921740000,
        "end_ms": 1703057940000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "20-12-2023 13:9",
        "end_date": "10-5-2024 14:9",
        "start_ms": 1703057940000,
        "end_ms": 1715330340000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "10-5-2024 14:9",
        "end_date": "9-12-2024 15:39",
        "start_ms": 1715330340000,
        "end_ms": 1733738940000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "9-12-2024 15:39",
        "end_date": "19-9-2025 17:39",
        "start_ms": 1733738940000,
        "end_ms": 1758283740000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "19-9-2025 17:39",
        "end_date": "9-9-2026 20:9",
        "start_ms": 1758283740000,
        "end_ms": 1788964740000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-9-2026 20:9",
        "end_date": "9-11-2027 5:9",
        "start_ms": 1788964740000,
        "end_ms": 1825717140000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 7,
      "dasha_name": "Sankata",
      "start_date": "9-11-2027 5:9",
      "end_date": "9-11-2035 5:9",
      "start_ms": 1825717140000,
      "end_ms": 2078177940000,
      "duration": 8
    },
    "sub_dasha": [
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "9-11-2027 5:9",
        "end_date": "19-8-2029 13:9",
        "start_ms": 1825717140000,
        "end_ms": 1881819540000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "19-8-2029 13:9",
        "end_date": "8-11-2029 17:9",
        "start_ms": 1881819540000,
        "end_ms": 1888832340000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "8-11-2029 17:9",
        "end_date": "20-4-2030 1:9",
        "start_ms": 1888832340000,
        "end_ms": 1902857940000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "20-4-2030 1:9",
        "end_date": "19-12-2030 13:9",
        "start_ms": 1902857940000,
        "end_ms": 1923896340000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "19-12-2030 13:9",
        "end_date": "9-11-2031 5:9",
        "start_ms": 1923896340000,
        "end_ms": 1951947540000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "9-11-2031 5:9",
        "end_date": "19-12-2032 1:9",
        "start_ms": 1951947540000,
        "end_ms": 1987011540000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "19-12-2032 1:9",
        "end_date": "20-4-2034 1:9",
        "start_ms": 1987011540000,
        "end_ms": 2029088340000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "20-4-2034 1:9",
        "end_date": "9-11-2035 5:9",
        "start_ms": 2029088340000,
        "end_ms": 2078177940000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 0,
      "dasha_name": "Mangla",
      "start_date": "9-11-2035 5:9",
      "end_date": "9-11-2036 5:9",
      "start_ms": 2078177940000,
      "end_ms": 2109800340000,
      "duration": 1
    },
    "sub_dasha": [
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "9-11-2035 5:9",
        "end_date": "19-11-2035 8:39",
        "start_ms": 2078177940000,
        "end_ms": 2079054540000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "19-11-2035 8:39",
        "end_date": "9-12-2035 15:39",
        "start_ms": 2079054540000,
        "end_ms": 2080807740000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "9-12-2035 15:39",
        "end_date": "9-1-2036 2:9",
        "start_ms": 2080807740000,
        "end_ms": 2083437540000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "9-1-2036 2:9",
        "end_date": "18-2-2036 16:9",
        "start_ms": 2083437540000,
        "end_ms": 2086943940000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "18-2-2036 16:9",
        "end_date": "9-4-2036 9:39",
        "start_ms": 2086943940000,
        "end_ms": 2091326940000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-4-2036 9:39",
        "end_date": "9-6-2036 6:39",
        "start_ms": 2091326940000,
        "end_ms": 2096586540000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "9-6-2036 6:39",
        "end_date": "19-8-2036 7:9",
        "start_ms": 2096586540000,
        "end_ms": 2102722740000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "19-8-2036 7:9",
        "end_date": "9-11-2036 5:9",
        "start_ms": 2102722740000,
        "end_ms": 2109800340000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 1,
      "dasha_name": "Pingla",
      "start_date": "9-11-2036 5:9",
      "end_date": "9-11-2038 5:9",
      "start_ms": 2109800340000,
      "end_ms": 2172872340000,
      "duration": 2
    },
    "sub_dasha": [
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "9-11-2036 5:9",
        "end_date": "19-12-2036 19:9",
        "start_ms": 2109800340000,
        "end_ms": 2113306740000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "19-12-2036 19:9",
        "end_date": "18-2-2037 16:9",
        "start_ms": 2113306740000,
        "end_ms": 2118566340000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "18-2-2037 16:9",
        "end_date": "10-5-2037 20:9",
        "start_ms": 2118566340000,
        "end_ms": 2125579140000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "10-5-2037 20:9",
        "end_date": "20-8-2037 7:9",
        "start_ms": 2125579140000,
        "end_ms": 2134345140000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "20-8-2037 7:9",
        "end_date": "20-12-2037 1:9",
        "start_ms": 2134345140000,
        "end_ms": 2144864340000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "20-12-2037 1:9",
        "end_date": "11-5-2038 2:9",
        "start_ms": 2144864340000,
        "end_ms": 2157136740000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "11-5-2038 2:9",
        "end_date": "20-10-2038 10:9",
        "start_ms": 2157136740000,
        "end_ms": 2171162340000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "20-10-2038 10:9",
        "end_date": "9-11-2038 5:9",
        "start_ms": 2171162340000,
        "end_ms": 2172872340000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 2,
      "dasha_name": "Dhanya",
      "start_date": "9-11-2038 5:9",
      "end_date": "9-11-2041 5:9",
      "start_ms": 2172872340000,
      "end_ms": 2267566740000,
      "duration": 3
    },
    "sub_dasha": [
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "9-11-2038 5:9",
        "end_date": "8-2-2039 12:39",
        "start_ms": 2172872340000,
        "end_ms": 2180761740000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "8-2-2039 12:39",
        "end_date": "10-6-2039 6:39",
        "start_ms": 2180761740000,
        "end_ms": 2191280940000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "10-6-2039 6:39",
        "end_date": "9-11-2039 11:9",
        "start_ms": 2191280940000,
        "end_ms": 2204429940000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-11-2039 11:9",
        "end_date": "10-5-2040 2:9",
        "start_ms": 2204429940000,
        "end_ms": 2220208740000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "10-5-2040 2:9",
        "end_date": "9-12-2040 3:39",
        "start_ms": 2220208740000,
        "end_ms": 2238617340000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "9-12-2040 3:39",
        "end_date": "9-8-2041 15:39",
        "start_ms": 2238617340000,
        "end_ms": 2259655740000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "9-8-2041 15:39",
        "end_date": "9-9-2041 2:9",
        "start_ms": 2259655740000,
        "end_ms": 2262285540000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "9-9-2041 2:9",
        "end_date": "9-11-2041 5:9",
        "start_ms": 2262285540000,
        "end_ms": 2267566740000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 3,
      "dasha_name": "Bhramari",
      "start_date": "9-11-2041 5:9",
      "end_date": "9-11-2045 5:9",
      "start_ms": 2267566740000,
      "end_ms": 2393797140000,
      "duration": 4
    },
    "sub_dasha": [
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "9-11-2041 5:9",
        "end_date": "20-4-2042 13:9",
        "start_ms": 2267566740000,
        "end_ms": 2281592340000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "20-4-2042 13:9",
        "end_date": "9-11-2042 11:9",
        "start_ms": 2281592340000,
        "end_ms": 2299124340000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-11-2042 11:9",
        "end_date": "10-7-2043 23:9",
        "start_ms": 2299124340000,
        "end_ms": 2320162740000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "10-7-2043 23:9",
        "end_date": "20-4-2044 1:9",
        "start_ms": 2320162740000,
        "end_ms": 2344707540000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "20-4-2044 1:9",
        "end_date": "10-3-2045 17:9",
        "start_ms": 2344707540000,
        "end_ms": 2372758740000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "10-3-2045 17:9",
        "end_date": "20-4-2045 7:9",
        "start_ms": 2372758740000,
        "end_ms": 2376265140000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "20-4-2045 7:9",
        "end_date": "10-7-2045 11:9",
        "start_ms": 2376265140000,
        "end_ms": 2383277940000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "10-7-2045 11:9",
        "end_date": "9-11-2045 5:9",
        "start_ms": 2383277940000,
        "end_ms": 2393797140000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 4,
      "dasha_name": "Bhadrika",
      "start_date": "9-11-2045 5:9",
      "end_date": "9-11-2050 5:9",
      "start_ms": 2393797140000,
      "end_ms": 2551563540000,
      "duration": 5
    },
    "sub_dasha": [
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "9-11-2045 5:9",
        "end_date": "20-7-2046 20:39",
        "start_ms": 2393797140000,
        "end_ms": 2415712140000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "20-7-2046 20:39",
        "end_date": "21-5-2047 5:39",
        "start_ms": 2415712140000,
        "end_ms": 2442010140000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "21-5-2047 5:39",
        "end_date": "10-5-2048 8:9",
        "start_ms": 2442010140000,
        "end_ms": 2472691140000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "10-5-2048 8:9",
        "end_date": "20-6-2049 4:9",
        "start_ms": 2472691140000,
        "end_ms": 2507755140000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "20-6-2049 4:9",
        "end_date": "9-8-2049 21:39",
        "start_ms": 2507755140000,
        "end_ms": 2512138140000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "9-8-2049 21:39",
        "end_date": "19-11-2049 8:39",
        "start_ms": 2512138140000,
        "end_ms": 2520904140000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "19-11-2049 8:39",
        "end_date": "20-4-2050 13:9",
        "start_ms": 2520904140000,
        "end_ms": 2534053140000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "20-4-2050 13:9",
        "end_date": "9-11-2050 5:9",
        "start_ms": 2534053140000,
        "end_ms": 2551563540000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 5,
      "dasha_name": "Ulka",
      "start_date": "9-11-2050 5:9",
      "end_date": "9-11-2056 5:9",
      "start_ms": 2551563540000,
      "end_ms": 2740952340000,
      "duration": 6
    },
    "sub_dasha": [
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-11-2050 5:9",
        "end_date": "9-11-2051 11:9",
        "start_ms": 2551563540000,
        "end_ms": 2583121140000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "9-11-2051 11:9",
        "end_date": "8-1-2053 14:9",
        "start_ms": 2583121140000,
        "end_ms": 2619938340000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "8-1-2053 14:9",
        "end_date": "10-5-2054 14:9",
        "start_ms": 2619938340000,
        "end_ms": 2662015140000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "10-5-2054 14:9",
        "end_date": "10-7-2054 11:9",
        "start_ms": 2662015140000,
        "end_ms": 2667274740000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "10-7-2054 11:9",
        "end_date": "9-11-2054 5:9",
        "start_ms": 2667274740000,
        "end_ms": 2677793940000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "9-11-2054 5:9",
        "end_date": "10-5-2055 20:9",
        "start_ms": 2677793940000,
        "end_ms": 2693572740000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "10-5-2055 20:9",
        "end_date": "9-1-2056 8:9",
        "start_ms": 2693572740000,
        "end_ms": 2714611140000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "9-1-2056 8:9",
        "end_date": "9-11-2056 5:9",
        "start_ms": 2714611140000,
        "end_ms": 2740952340000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 6,
      "dasha_name": "Siddha",
      "start_date": "9-11-2056 5:9",
      "end_date": "9-11-2063 5:9",
      "start_ms": 2740952340000,
      "end_ms": 2961790740000,
      "duration": 7
    },
    "sub_dasha": [
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "9-11-2056 5:9",
        "end_date": "21-3-2058 8:39",
        "start_ms": 2740952340000,
        "end_ms": 2783905740000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "21-3-2058 8:39",
        "end_date": "10-10-2059 12:39",
        "start_ms": 2783905740000,
        "end_ms": 2832995340000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "10-10-2059 12:39",
        "end_date": "20-12-2059 13:9",
        "start_ms": 2832995340000,
        "end_ms": 2839131540000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "20-12-2059 13:9",
        "end_date": "10-5-2060 14:9",
        "start_ms": 2839131540000,
        "end_ms": 2851403940000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "10-5-2060 14:9",
        "end_date": "9-12-2060 15:39",
        "start_ms": 2851403940000,
        "end_ms": 2869812540000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "9-12-2060 15:39",
        "end_date": "19-9-2061 17:39",
        "start_ms": 2869812540000,
        "end_ms": 2894357340000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "19-9-2061 17:39",
        "end_date": "9-9-2062 20:9",
        "start_ms": 2894357340000,
        "end_ms": 2925038340000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-9-2062 20:9",
        "end_date": "9-11-2063 5:9",
        "start_ms": 2925038340000,
        "end_ms": 2961790740000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 7,
      "dasha_name": "Sankata",
      "start_date": "9-11-2063 5:9",
      "end_date": "9-11-2071 5:9",
      "start_ms": 2961790740000,
      "end_ms": 3214251540000,
      "duration": 8
    },
    "sub_dasha": [
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "9-11-2063 5:9",
        "end_date": "19-8-2065 13:9",
        "start_ms": 2961790740000,
        "end_ms": 3017893140000
      },
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "19-8-2065 13:9",
        "end_date": "8-11-2065 17:9",
        "start_ms": 3017893140000,
        "end_ms": 3024905940000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "8-11-2065 17:9",
        "end_date": "20-4-2066 1:9",
        "start_ms": 3024905940000,
        "end_ms": 3038931540000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "20-4-2066 1:9",
        "end_date": "19-12-2066 13:9",
        "start_ms": 3038931540000,
        "end_ms": 3059969940000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "19-12-2066 13:9",
        "end_date": "9-11-2067 5:9",
        "start_ms": 3059969940000,
        "end_ms": 3088021140000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "9-11-2067 5:9",
        "end_date": "19-12-2068 1:9",
        "start_ms": 3088021140000,
        "end_ms": 3123085140000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "19-12-2068 1:9",
        "end_date": "20-4-2070 1:9",
        "start_ms": 3123085140000,
        "end_ms": 3165161940000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "20-4-2070 1:9",
        "end_date": "9-11-2071 5:9",
        "start_ms": 3165161940000,
        "end_ms": 3214251540000
      }
    ]
  },
  {
    "major_dasha": {
      "dasha_id": 0,
      "dasha_name": "Mangla",
      "start_date": "9-11-2071 5:9",
      "end_date": "9-11-2072 5:9",
      "start_ms": 3214251540000,
      "end_ms": 3245873940000,
      "duration": 1
    },
    "sub_dasha": [
      {
        "dasha_id": 0,
        "dasha_name": "Mangla",
        "start_date": "9-11-2071 5:9",
        "end_date": "19-11-2071 8:39",
        "start_ms": 3214251540000,
        "end_ms": 3215128140000
      },
      {
        "dasha_id": 1,
        "dasha_name": "Pingla",
        "start_date": "19-11-2071 8:39",
        "end_date": "9-12-2071 15:39",
        "start_ms": 3215128140000,
        "end_ms": 3216881340000
      },
      {
        "dasha_id": 2,
        "dasha_name": "Dhanya",
        "start_date": "9-12-2071 15:39",
        "end_date": "9-1-2072 2:9",
        "start_ms": 3216881340000,
        "end_ms": 3219511140000
      },
      {
        "dasha_id": 3,
        "dasha_name": "Bhramari",
        "start_date": "9-1-2072 2:9",
        "end_date": "18-2-2072 16:9",
        "start_ms": 3219511140000,
        "end_ms": 3223017540000
      },
      {
        "dasha_id": 4,
        "dasha_name": "Bhadrika",
        "start_date": "18-2-2072 16:9",
        "end_date": "9-4-2072 9:39",
        "start_ms": 3223017540000,
        "end_ms": 3227400540000
      },
      {
        "dasha_id": 5,
        "dasha_name": "Ulka",
        "start_date": "9-4-2072 9:39",
        "end_date": "9-6-2072 6:39",
        "start_ms": 3227400540000,
        "end_ms": 3232660140000
      },
      {
        "dasha_id": 6,
        "dasha_name": "Siddha",
        "start_date": "9-6-2072 6:39",
        "end_date": "19-8-2072 7:9",
        "start_ms": 3232660140000,
        "end_ms": 3238796340000
      },
      {
        "dasha_id": 7,
        "dasha_name": "Sankata",
        "start_date": "19-8-2072 7:9",
        "end_date": "9-11-2072 5:9",
        "start_ms": 3238796340000,
        "end_ms": 3245873940000
      }
    ]
  }
]
```

### current_yogini_dasha
Get the currently undergoing Yogini Dasha upto three levels viz. Major, Sub and Sub-Sub.

#### API Endpoint
current_yogini_dasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/current_yogini_dasha|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "major_dasha": {
    "dasha_id": 4,
    "dasha_name": "Bhadrika",
    "duration": "5 Years",
    "start_date": "1-3-2014 2:30",
    "end_date": "1-3-2019 2:30"
  },
  "sub_dasha": {
    "dasha_id": 5,
    "dasha_name": "Ulka",
    "start_date": "9-11-2014 18:0",
    "end_date": "10-9-2015 4:0"
  },
  "sub_sub_dasha": {
    "dasha_id": 4,
    "dasha_name": "Bhadrika",
    "start_date": "29-7-2015 21:25",
    "end_date": "10-9-2015 4:0"
  }
}
```

## Beginner
Create free kundali on your own way absolutly free.

### basic_astro
Provides the complete avakahada details e.g. nakshtatra, charan, tithe, karan, yog ,varna, vashaya etc.

#### API Endpoint
basic_astro

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_astro|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "Varna": "Vaishya",
  "Vashya": "Chatuspad",
  "Yoni": "Sarp",
  "sign_lord": 5,
  "sign": "Taurus",
  "Naksahtra": "Rohini",
  "naksahtra_lord": "Moon",
  "nakshatra_charan": 3,
  "name_alphabet": "Vi"
}
```

### birth_details
Provide basic birth details of the given birth data.

#### API Endpoint
birth_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/birth_details|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "year": 2016,
  "month": 2,
  "day": 16,
  "hour": 14,
  "minute": 53,
  "latitude": 18.975,
  "longitude": 72.8258,
  "timezone": 5.5,
  "sunrise": "7:8:47",
  "sunset": "18:39:48",
  "ayanamsha": 24.082319099809013
}
```

### numero_table
Provides detailed Numerology report.

#### API Endpoint
numero_table

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_table|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | string | Your full name, eg: Ajeet kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "name": "Ajeet kanojia",
  "date": "16-2-2016",
  "destiny_number": 9,
  "radical_number": 7,
  "name_number": 7,
  "evil_num": "1,9",
  "fav_color": "Black",
  "fav_day": "Sunday, Monday",
  "fav_god": "Narsingh Bhagawan",
  "fav_mantra": "|| Om Keng Ketave Namah ||",
  "fav_metal": "Iron",
  "fav_stone": "Cat's Eye",
  "fav_substone": "Golden Hakik",
  "friendly_num": "3,2,6",
  "neutral_num": "4,5,8",
  "radical_num": "7",
  "radical_ruler": "Ketu"
}
```

### basic_panchang
Provides data points for panchang elements, chaugadiya and sunrise and set timings

#### API Endpoint
basic_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_panchang|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "day": "Tuesday",
  "tithi": "Shukla-Navami",
  "nakshatra": "Rohini",
  "yog": "Vaidhriti",
  "karan": "Kaulav",
  "sunrise": "7:8:47",
  "sunset": "18:39:48"
}
```

## Biorhythm
This package provides you biorhythms charts points,trends and biorhythms details.

### biorhythm
Get biorhythmic details.

#### API Endpoint
biorhythm

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/biorhythm|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "physical": {
    "percent": -39,
    "trend": 1
  },
  "emotional": {
    "percent": 23,
    "trend": 0
  },
  "intellectual": {
    "percent": 62,
    "trend": 0
  },
  "average": {
    "percent": 16,
    "trend": 0
  }
}
```

## Daily Nakshatra Prediction
Provides you daily nakshatra prediction.

### daily_nakshatra_prediction
Gives you your daily nakshatra prediction.

#### API Endpoint
daily_nakshatra_prediction

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/daily_nakshatra_prediction|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "birth_moon_sign": "Virgo",
  "birth_moon_nakshatra": "Chitra",
  "prediction": {
    "health": "You will feel full of energy and a new cheerfulness today. You will come across a fitness freak who will inspire you to achieve your fitness goals. Spending some time in the countryside will be extremely beneficial.",
    "emotions": "Feelings of relaxation and freedom are likely to dominate. You will tend to avoid stressful confrontations or demanding situations.",
    "profession": "Finances will definitely get a boost- but at the same time expenditures too will increase. You will have to use your intuition to take any decision at work. You have the ability to turn a negative to a positive easily today.",
    "luck": "You shall feel positive and creative today. Your desire to make something beautiful is stimulated now."
  },
  "prediction_date": "20 February 2015"
}
```

## General Reports
Calculates general reports and predictions like, house report ,rashi report ,nakshatra report, ascendent report etc.

### general_house_report/:planet_name
Calculates complete general house reports.

#### API Endpoint
general_house_report/:planet_name

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/general_house_report/:planet_name|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|
#### Planet Name ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
>Here planet name means for which planet you want data.
>Planet name's are as follow-
>sun, moon, mars, mercury, jupiter, venus, saturn

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "planet": "sun",
  "house_report": "You have an abundance of physical vitality. Sometimes there is so much energy that you
   become reckless, impulsive, and throw caution to the wind. You may experience cuts and burns on your
   head and face which may leave some sort of scar. You are assertive, independent, impatient and want to
    do your own thing. You have strong organizing ability. You are usually self-confident. Guard against
     accidents due to rushing around in your impulsiveness. You may be subject to higher than normal fevers."
}
```

### general_rashi_report/:planet_name
Calculates complete general sign reports.

#### API Endpoint
general_rashi_report/:planet_name

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/general_house_report/:planet_name|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Planet Name ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
>Here planet name means for which planet you want data.
>Planet name's are as follow-
>moon, mars, mercury, jupiter, venus, saturn

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "planet": "sun",
  "rashi_report": "You tend to be efficient and hard-working, with a flair for business and finance.
  You are resourceful and willing to do all the work necessary in the fulfillment of a task.
  You are secretive, but there is, also, great inner strength and courage. You have a magnetism
   that draws people to you. You have an ardent, aggressive, self-reliant nature and an enthusiastic,
   constructive mind. On the negative side, there may be trouble and loss through the indulgence of the
    lower nature and love of rich and expensive food and sickness on that account. Any tendencies for
    wild speculation and risk-taking should be controlled. There is interest in the occult. Strong healing
    abilities may be present. These energies are meant to be used to gain a higher consciousness and greater
     universal wisdom."
}
```

### general_nakshatra_report
Calculates complete general nakshatra reports

#### API Endpoint
general_nakshatra_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/general_nakshatra_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "nak_report": {
    "physical": [
      "Normally he is of middle stature. However, native with Saturn's aspect to this segment has a tall body. His nose is prominent and his eyes sympathetic, neck thick and stout, solidly built body with big shoulders and well developed muscles, countenance peaceful and his behaviour respectful. He has a commanding appearance. "
    ],
    "character": [
      "While he is on the one hand very intelligent, on the other hand he cannot pursue any goal for long. In other words he easily gets bored with any particular thing and jump upon another without knowing the pros and cons. He is capable of rendering good advise and tell others the way out for any problem. But in his own life, he does what he thinks at a particular time. ",
      "He will discard any friendship if that friendship questions his ego and freedom. But at the same time he does not like to achieve name, fame and wealth through unfair means or at the mercy of others. His needs or wants are not beyond reason nor his accumulations always spectacular, although his money making abilities are often phenomenal, his motivation however derives from an emphatic wish to remain free from obligations. He cannot find fault in his own action. Optimism followed with self pride is one of the characteristics of these persons. He is determined to go ahead with great energy and shows his stubborn and tenacious nature.",
      "Orthodoxy and monotheism are combined in him i.e. while he is orthodox he does not believe in age old blind belief and customs. Persistent effort and hard work are his moto. He is eager to render some positive service to the world but he cannot shine for longer period. He involves himself in public life sincerely but loss and failures are ultimate gain. This drawback is attributable to lack of ability to move according to the situation. ",
      "He tries to impose certain restriction and control through self assessment and modify them according to his sweet will. Once a promise is made, it will be carried out at any cost. ",
      "In the public life he can attain name, fame and respect. Excess of sincerity will be the means of his downfall. Frustration start hunting him even on small matters and lead him to outburst. Once he got heated up, subsequent steps will be dangerous. Hence he has to observe maximum mental balance and keep away the out bursting temperament. Remarkable ability will be shown in arguments and counter arguments with reasoning. It is quite often seen that these types of persons will be bereft of truth and money, undertakes unnecessary travel. They are thankless and will utter cruel words. "
    ],
    "education": [
      "Mostly Kritika born will not stay in the home town. That means his livelihood will be in the foreign land. When I say foreign, it is not necessary that it should be a foreign country. Foreign land means a little away from the place where he is born. Partnership business is not suitable to him. ",
      "He derives benefits from the government. Engineer, doctor specialised in veneral diseases, treasury department, draftsman. In case the native is interested in business he can derive maximum benefits from yarn export, medicines and decorative industries. A large legacy at any part of his life is a waiting for him. He is very slow in any work. Hence for success in life, he is advised to increase the speed while doing any work as otherwise he may be dragged behind others. "
    ],
    "family": [
      "He is generally lucky in his married life. His spouse will be expert in household administration, dedicated and devoted, faithful and virtuous. With all these plus points, health of the spouse will be a concern for him and/or circumstances may so be created that he has to quite often live separately. When I say separation, it may be due to work or due to ill health to either of the family members i.e., parents of the spouse etc. and not due to disharmony between the couple. ",
      "While he has to confront with many obstacles in various walks of life, he will be contended and lucky in the family field, where he enjoys the utmost satisfaction and peace. ",
      "He is more attached to mother. Among his co-borns, the native will enjoy more favour and love from the mother. While his father will be a pious and well known person, the native cannot enjoy comforts and benefits from father. His life up to 50 years of age will be full of trial and have to face frequent changes in surroundings. However, period between 25 years and 35 years and 50 years and 56 years will be very good. ",
      "Love marriage is indicated to the native. Sometimes, it has been found that Kritika born marries a girl known to his family. "
    ],
    "health": [
      "He has good apitite but he cannot have a systematic food habit. Diseases to which he is prone to are dental problem, weak eye sight, tuberculosis, wind and piles, brain fever, accident, wounds, malaria or cerebral meningits. ",
      "Whatever may be the condition of his health, whether good or bad, neither he is afraid of any disease nor he is ready to observe daily care of his health."
    ]
  }
}
```

### general_ascendant_report
Calculates complete general ascendant reports.

#### API Endpoint
general_ascendant_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/general_ascendant_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
   "asc_report": {
     "ascendant": "Aquarius",
     "report": "People with Aquarius rising tend to be altruistic, friendly, yet detached, impersonal,
     humanitarian, sociable, intellectual, freedom-loving, rebellious, independent, and unusual. You are
     here to learn altruism, brotherhood, and working for the common good, to forget yourself and your needs
     for the sake of your friends, who can also be strangers. You have new and different ways of looking at
     things. You can be very original and inventive, perhaps eccentric or bohemian. You are prone to uncertain
      and sudden impulses. You tend to be very intuitive, possessing a good mind. You have organizing
      ability and are capable and practical. You are intelligent, but sometimes cold and calculating where
       feelings are concerned. There is a certain detachment about you. You cannot stand possessiveness and
       jealousy and you require plenty of freedom. Depending on the relative strengths of Saturn and Uranus
        in your chart, caution, coldness and selfishness may be exhibited (Saturn stronger) or there will be
         more altruism, freedom and free-flowingness (Uranus stronger). If Uranus is stronger, then the things
          of the spirit will be stronger than materialistic worldliness. Spiritual lesson to learn: Warmth
          (less head and more heart). Saturn and Uranus both rule Aquarius so Saturn and Uranus will be
          important in your chart."
   }
 }
```
## Geo Details
Provide latitude and logitude of the given place.

### geo_details
Calculates complete general ascendant reports.

#### API Endpoint
geo_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/geo_details|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| place      | string | place , eg: 'mumbai'|
| maxRows     | int      |  number of result at time, eg: 6 |

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "geonames": [
    {
      "place_name": "Mumbai",
      "latitude": 19.07283,
      "longitude": "72.88261",
      "timezone_id": "Asia/Kolkata",
      "country_code": "IN"
    },
    {
      "place_name": "Navi Mumbai",
      "latitude": 19.03681,
      "longitude": "73.01582",
      "timezone_id": "Asia/Kolkata",
      "country_code": "IN"
    }
  ]
}
```

### timezone
Return a time zone of the given place.

#### API Endpoint
timezone

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/timezone|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| country_code      | string | time zone id , get from geo_details api|
| isDst     | boolean      |  is for dst , eg: true or false|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "timezone": "5.5"
}
```

## Horoscope Chart
This package provides data points to create horoscope charts or kundali in whichever type you want (North, south, bengali or oriya).

### horo_chart/:chart_id
based on chart type(all D-charts) - The data points include various planetary positions along with ascendant and their respective house positions to draw charts.

#### API Endpoint
horo_chart/:chart_id

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/horo_chart/:chart_id|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

chart_id ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
> chart_id means the type of chart for which you want data.For example:-
> chalit : For Chalit Chart,
> SUN : For Sun Chart,
> MOON : For Moon Chart,
> D1 : For Brith Chart,
> D2 : For Hora Chart,
> D3 : For Dreshkan Chart,
> D4 : For Chathurthamasha Chart,
> D5 : For Panchmansha Chart,
> D7 : For Saptamansha Chart,
> D8 : For Ashtamansha Chart,
> D9 : For Navamansha Chart,
> D10 : For Dashamansha Chart,
> D12 : For Dwadashamsha chart,
> D16 : For Shodashamsha Chart,
> D20 : For Vishamansha Chart,
> D24 : For Chaturvimshamsha Chart,
> D27 : For Bhamsha Chart,
> D30 : For Trishamansha Chart,
> D40 : For Khavedamsha Chart,
> D45 : For Akshvedansha Chart,
> D60 : For Shashtymsha Chart,
> chalit : For Chalit Chart


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "sign": 6,
    "sign_name": "Virgo",
    "planet": [
      "RAHU"
    ]
  },
  {
    "sign": 7,
    "sign_name": "Libra",
    "planet": []
  },
  {
    "sign": 8,
    "sign_name": "Scorpio",
    "planet": [
      "MOON",
      "SATURN"
    ]
  },
  {
    "sign": 9,
    "sign_name": "Sagittarius",
    "planet": []
  },
  {
    "sign": 10,
    "sign_name": "Capricorn",
    "planet": []
  },
  {
    "sign": 11,
    "sign_name": "Aquarius",
    "planet": []
  },
  {
    "sign": 12,
    "sign_name": "Pisces",
    "planet": [
      "SUN",
      "MERCURY",
      "KETU"
    ]
  },
  {
    "sign": 1,
    "sign_name": "Aries",
    "planet": [
      "MARS"
    ]
  },
  {
    "sign": 2,
    "sign_name": "Taurus",
    "planet": [
      "VENUS"
    ]
  },
  {
    "sign": 3,
    "sign_name": "Gemini",
    "planet": []
  },
  {
    "sign": 4,
    "sign_name": "Cancer",
    "planet": [
      "JUPITER"
    ]
  },
  {
    "sign": 5,
    "sign_name": "Leo",
    "planet": []
  }
]
```

### horo_chart_extended/:chart_id
based on chart type(all D-charts) - The data points include various planetary positions including Neptune,Pluto,Uranus along with ascendant and their respective house positions to draw charts.

#### API Endpoint
horo_chart_extended/:chart_id

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/horo_chart_extended/:chart_id|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

chart_id ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
> chart_id means the type of chart for which you want data.For example:-
> chalit : For Chalit Chart,
> SUN : For Sun Chart,
> MOON : For Moon Chart,
> D1 : For Brith Chart,
> D2 : For Hora Chart,
> D3 : For Dreshkan Chart,
> D4 : For Chathurthamasha Chart,
> D5 : For Panchmansha Chart,
> D7 : For Saptamansha Chart,
> D8 : For Ashtamansha Chart,
> D9 : For Navamansha Chart,
> D10 : For Dashamansha Chart,
> D12 : For Dwadashamsha chart,
> D16 : For Shodashamsha Chart,
> D20 : For Vishamansha Chart,
> D24 : For Chaturvimshamsha Chart,
> D27 : For Bhamsha Chart,
> D30 : For Trishamansha Chart,
> D40 : For Khavedamsha Chart,
> D45 : For Akshvedansha Chart,
> D60 : For Shashtymsha Chart,
> chalit : For Chalit Chart


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "sign": 3,
    "sign_name": "Gemini",
    "planet": [
      "MOON"
    ]
  },
  {
    "sign": 4,
    "sign_name": "Cancer",
    "planet": []
  },
  {
    "sign": 5,
    "sign_name": "Leo",
    "planet": [
      "JUPITER",
      "RAHU"
    ]
  },
  {
    "sign": 6,
    "sign_name": "Virgo",
    "planet": []
  },
  {
    "sign": 7,
    "sign_name": "Libra",
    "planet": [
      "MARS"
    ]
  },
  {
    "sign": 8,
    "sign_name": "Scorpio",
    "planet": [
      "SATURN"
    ]
  },
  {
    "sign": 9,
    "sign_name": "Sagittarius",
    "planet": [
      "PLUTO"
    ]
  },
  {
    "sign": 10,
    "sign_name": "Capricorn",
    "planet": [
      "MERCURY",
      "VENUS"
    ]
  },
  {
    "sign": 11,
    "sign_name": "Aquarius",
    "planet": [
      "SUN",
      "KETU",
      "NEPTUNE"
    ]
  },
  {
    "sign": 12,
    "sign_name": "Pisces",
    "planet": [
      "URANUS"
    ]
  },
  {
    "sign": 1,
    "sign_name": "Aries",
    "planet": []
  },
  {
    "sign": 2,
    "sign_name": "Taurus",
    "planet": []
  }
]
```
## Kal Sarpa Dosha
Offers Complete kalsarpa dosha analysis report and kalsarpa dosha nivaran remedies.

### kalsarpa_details
Calculate Kal Sarpa Dosha report.

#### API Endpoint
kalsarpa_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/kalsarpa_details|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
   "present":true,
   "type":"Partial Ascending",
   "one_line":"You have ascending kalsarpa dosha direction, which is treated as powerful. The KalSarpa Dosha is having partial effect in your horoscope.",
   "report":{
      "house_id":3,
      "report":"In your horoscope the Vasuki Kaal Sarp Yog is present. Due to this reason the native does not believe in gods and generally is non-religious.There are hurdles in life and native has to struggle for moving ahead but the native usually gets a chance to serve in government. The native may suffer hardships during his stay at a foreign country. His esteem could be low and he may be lazy for some period. Due to Kaal Sarp Yog the native suffers from diseases many times that cause loss of money and the native may suffer due to debts. However things are all right later on.The married life is normal but painful and disturbed. The family life remains disturbed; peace and happiness remain absent on many occasions. The own relatives try to cause harm from time to time. The native may sign in a hurry on important legal documents thus incurring huge loss. He may suffer due to adverse attitude of government officials. However the native also gets a miraculous time in life."
   }
}
```

## Lal Kitab
Lal Kitab Provides LalKitab horoscope,debts and remedies.

### lalkitab_horoscope
Provides lal kitab horoscope chart points.

#### API Endpoint
lalkitab_horoscope

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/lalkitab_horoscope|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
   {
      "sign":1,
      "sign_name":"Aries",
      "planet":[
         "JUPITER"
      ]
   },
   {
      "sign":2,
      "sign_name":"Taurus",
      "planet":[

      ]
   },
   {
      "sign":3,
      "sign_name":"Gemini",
      "planet":[
         "RAHU"
      ]
   },
   {
      "sign":4,
      "sign_name":"Cancer",
      "planet":[

      ]
   },
   {
      "sign":5,
      "sign_name":"Leo",
      "planet":[
         "SATURN"
      ]
   },
   {
      "sign":6,
      "sign_name":"Virgo",
      "planet":[

      ]
   },
   {
      "sign":7,
      "sign_name":"Libra",
      "planet":[

      ]
   },
   {
      "sign":8,
      "sign_name":"Scorpio",
      "planet":[
         "MOON",
         "MERCURY"
      ]
   },
   {
      "sign":9,
      "sign_name":"Sagittarius",
      "planet":[
         "SUN",
         "MARS",
         "KETU"
      ]
   },
   {
      "sign":10,
      "sign_name":"Capricorn",
      "planet":[
         "VENUS"
      ]
   },
   {
      "sign":11,
      "sign_name":"Aquarius",
      "planet":[

      ]
   },
   {
      "sign":12,
      "sign_name":"Pisces",
      "planet":[

      ]
   }
]
```

### lalkitab_debts
Provides details of lal kitab debts.

#### API Endpoint
lalkitab_debts

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/lalkitab_debts|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "debt_name": "Self Debts",
    "indications": "Fear from King, punishment or payment of penalty in legal suitseven though you are faultless; heart diseases, pain inshoulders, physical weakness, difficulty in eyes, spoiling life.",
    "events": "The native will become an atheist, do not care dharma/religion,Health will not be favourable; the native will not follow the customs of ancestors."
  },
  {
    "debt_name": "Debts to Relatives",
    "indications": "killing or getting killed a she buffalo which is going to deliver a calf, performing black magic at the time of construction of a house or laying foundation stone by others, hating those people who mingle with the relatives of the native, keeping away in the functions like birth days of children or family festivals.",
    "events": "The native cheats his friends, spoils the work done by others or burns the ripe crops in the agricultural fields of others."
  },
  {
    "debt_name": "Father Debts",
    "indications": "Changing or defaming of family priest, districting the shrine constructed along with residence, cutting or having holy long pepper tree.",
    "events": "The hair of the any one of the elder's persons in the family will become white. After turning to white,the hair colour starts becoming pale. Complaining of cough, or events like keeping the stigma of the bad actions of all other people on his head, etc., will happen."
  }
]
```

### lalkitab_remedies/:planet_name
Provides lal kitab remedies based on planet selection.

#### API Endpoint
lalkitab_remedies/:planet_name

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/lalkitab_remedies/:planet_name|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Planet Name ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
> Here planet name means for which planet you want data.
> Planet name's are as follow:-
> sun, moon, mars, mercury, jupiter, venus, saturn

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "planet": "Sun",
  "house": "Ninth",
  "lal_kitab_desc": [
    "Benefits and favours from government, good health and financially stronger. ",
    "The native will get a government job and comforts of vehicles and servants. ",
    "The native will always be suspicious about others.",
    "If the Sun is in the 4th house, the native.s father will die in his childhood. ",
    "If the Sun is in the 10th house and moon is in the 5th house the native will have a very short life. ",
    "If the 4th house is without any planet, the native will be deprived of government favours and benefits. "
  ],
  "lal_kitab_remedies": [
    "Never wear blue or black clothes.",
    "Throwing a copper coin in a river or canal for 43 years will be highly beneficial.",
    "Abstain from liquor and meat."
  ]
}
```
## Manglik Dosha
Calculate the detailed report on manglik dosha and its nivaran remedies.

### manglik
Calculate if Manglik Dosha present or not .

#### API Endpoint
manglik

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/manglik|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "manglik_present_rule": {
    "based_on_aspect": [
      "Your first house in birth chart is aspected by planet KETU.",
      "Seventh house of your birth chart is aspected by SATURN",
      "Seventh house of your birth chart is aspected by RAHU",
      "Fourth house of your birth chart is aspected by MARS",
      "Twelfth house of your birth chart is aspected by MARS.",
      "SUN is aspecting second house of your birth chart.",
      "SATURN is aspecting second house of your birth chart."
    ],
    "based_on_house": [
      "Planet Sun is situated in EIGHTH house in your birth chart."
    ]
  },
  "is_mars_manglik_cancelled": false,
  "manglik_status": "EFFECTIVE",
  "percentage_manglik_present": 27.5,
  "percentage_manglik_after_cancellation": 27.5,
  "manglik_report": "Manglik dosha has been detected in your horosocpe and the extent of mangal dosha present is effective and therefore needs due carefulness. You are manglik.",
  "is_present": true
}
```

## Match Making
Provides complete match making report like ashtakoot milaan points,manglik report,vedh karak details,rajju chakra ,match conclusion and etc.

### match_birth_details
Provide basic birth details of both male and female.

#### API Endpoint
match_birth_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_birth_details|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "male_birth_details": {
    "year": 1982,
    "month": 9,
    "day": 27,
    "hour": 6,
    "minute": 24,
    "latitude": 19,
    "longitude": 72,
    "timezone": 5,
    "sunrise": "6:32:51",
    "sunset": "18:36:24",
    "ayanamsha": 23.615910306003798
  },
  "female_birth_details": {
    "year": 1983,
    "month": 8,
    "day": 25,
    "hour": 11,
    "minute": 31,
    "latitude": 19,
    "longitude": 72,
    "timezone": 5,
    "sunrise": "6:26:45",
    "sunset": "19:5:9",
    "ayanamsha": 23.628614764758197
  }
}
```

### match_astro_details
Provide basic Avakhada (Astro) details of both male and female.

#### API Endpoint
match_astro_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_astro_details|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "male_astro_details": {
    "Varna": "Vipra",
    "Vashya": "Jalchar",
    "Yoni": "Gau",
    "Gan": "Manushya",
    "Nadi": "Madhya",
    "SignLord": "Jupiter",
    "Naksahtra": "Uttra Bhadrapad",
    "NaksahtraLord": "Saturn",
    "Charan": 4,
    "Yog": "Shubh",
    "Karan": "Vanija",
    "Tithi": "Shukla Chaturthi",
    "yunja": "Parbhaag",
    "tatva": "Water",
    "name_alphabet": "Doo,Tha,Jha,N",
    "paya": "Copper"
  },
  "female_astro_details": {
    "Varna": "Shoodra",
    "Vashya": "Maanav",
    "Yoni": "Vyaaghra",
    "Gan": "Rakshasa",
    "Nadi": "Madhya",
    "SignLord": "Venus",
    "Naksahtra": "Chitra",
    "NaksahtraLord": "Mars",
    "Charan": 3,
    "Yog": "Shool",
    "Karan": "Gara",
    "Tithi": "Krishna Shashthi",
    "yunja": "Madhya",
    "tatva": "Air",
    "name_alphabet": "Pe,Po,Ra,Ree",
    "paya": "Silver"
  }
}
```

### match_planet_details
Get planatory details of mail and femail.

#### API Endpoint
match_planet_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_planet_details|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "male_planet_details": [
    {
      "id": 0,
      "name": "Sun",
      "fullDegree": 75.95974673970524,
      "normDegree": 15.959746739705238,
      "speed": 0.9537019752026631,
      "isRetro": "false",
      "sign": "Gemini",
      "signLord": "Mercury",
      "nakshatra": "Ardra",
      "nakshatraLord": "Rahu",
      "house": 8
    },
    {
      "id": 1,
      "name": "Moon",
      "fullDegree": 35.70759132946863,
      "normDegree": 5.707591329468627,
      "speed": 14.576577570735925,
      "isRetro": "false",
      "sign": "Taurus",
      "signLord": "Venus",
      "nakshatra": "Krittika",
      "nakshatraLord": "Sun",
      "house": 7
    },
    {
      "id": 2,
      "name": "Mars",
      "fullDegree": 208.98678403828225,
      "normDegree": 28.986784038282252,
      "speed": 0.020471329733881917,
      "isRetro": "false",
      "sign": "Libra",
      "signLord": "Venus",
      "nakshatra": "Vishakha",
      "nakshatraLord": "Jupiter",
      "house": 12
    },
    {
      "id": 3,
      "name": "Mercury",
      "fullDegree": 69.09730737295142,
      "normDegree": 9.09730737295142,
      "speed": 2.138226568494943,
      "isRetro": "false",
      "sign": "Gemini",
      "signLord": "Mercury",
      "nakshatra": "Ardra",
      "nakshatraLord": "Rahu",
      "house": 8
    },
    {
      "id": 4,
      "name": "Jupiter",
      "fullDegree": 143.0516993314069,
      "normDegree": 23.051699331406894,
      "speed": 0.13614032745717822,
      "isRetro": "false",
      "sign": "Leo",
      "signLord": "Sun",
      "nakshatra": "Purva Phalguni",
      "nakshatraLord": "Venus",
      "house": 10
    },
    {
      "id": 5,
      "name": "Venus",
      "fullDegree": 82.69209010485653,
      "normDegree": 22.692090104856533,
      "speed": 1.2289819763466134,
      "isRetro": "false",
      "sign": "Gemini",
      "signLord": "Mercury",
      "nakshatra": "Punarvasu",
      "nakshatraLord": "Jupiter",
      "house": 8
    },
    {
      "id": 6,
      "name": "Saturn",
      "fullDegree": 227.07712216560267,
      "normDegree": 17.077122165602674,
      "speed": -0.059870453983687545,
      "isRetro": "true",
      "sign": "Scorpio",
      "signLord": "Mars",
      "nakshatra": "Jyeshtha",
      "nakshatraLord": "Mercury",
      "house": 1
    },
    {
      "id": 7,
      "name": "Rahu",
      "fullDegree": 141.8589732373409,
      "normDegree": 21.858973237340905,
      "speed": -0.05295375766704849,
      "isRetro": "true",
      "sign": "Leo",
      "signLord": "Sun",
      "nakshatra": "Purva Phalguni",
      "nakshatraLord": "Venus",
      "house": 10
    },
    {
      "id": 8,
      "name": "Ketu",
      "fullDegree": 321.85897323734093,
      "normDegree": 21.858973237340933,
      "speed": -0.05295375766704849,
      "isRetro": "true",
      "sign": "Aquarius",
      "signLord": "Saturn",
      "nakshatra": "Purva Bhadrapad",
      "nakshatraLord": "Jupiter",
      "house": 4
    },
    {
      "id": 9,
      "name": "Ascendant",
      "fullDegree": 223.64473065441229,
      "normDegree": 13.644730654412285,
      "speed": 0,
      "isRetro": false,
      "sign": "Scorpio",
      "signLord": "Mars",
      "nakshatra": "Anuradha",
      "nakshatraLord": "Saturn",
      "house": 1
    }
  ],
  "female_planet_details": [
    {
      "id": 0,
      "name": "Sun",
      "fullDegree": 75.95974673970524,
      "normDegree": 15.959746739705238,
      "speed": 0.9537019752026631,
      "isRetro": "false",
      "sign": "Gemini",
      "signLord": "Mercury",
      "nakshatra": "Ardra",
      "nakshatraLord": "Rahu",
      "house": 8
    },
    {
      "id": 1,
      "name": "Moon",
      "fullDegree": 35.70759132946863,
      "normDegree": 5.707591329468627,
      "speed": 14.576577570735925,
      "isRetro": "false",
      "sign": "Taurus",
      "signLord": "Venus",
      "nakshatra": "Krittika",
      "nakshatraLord": "Sun",
      "house": 7
    },
    {
      "id": 2,
      "name": "Mars",
      "fullDegree": 208.98678403828225,
      "normDegree": 28.986784038282252,
      "speed": 0.020471329733881917,
      "isRetro": "false",
      "sign": "Libra",
      "signLord": "Venus",
      "nakshatra": "Vishakha",
      "nakshatraLord": "Jupiter",
      "house": 12
    },
    {
      "id": 3,
      "name": "Mercury",
      "fullDegree": 69.09730737295142,
      "normDegree": 9.09730737295142,
      "speed": 2.138226568494943,
      "isRetro": "false",
      "sign": "Gemini",
      "signLord": "Mercury",
      "nakshatra": "Ardra",
      "nakshatraLord": "Rahu",
      "house": 8
    },
    {
      "id": 4,
      "name": "Jupiter",
      "fullDegree": 143.0516993314069,
      "normDegree": 23.051699331406894,
      "speed": 0.13614032745717822,
      "isRetro": "false",
      "sign": "Leo",
      "signLord": "Sun",
      "nakshatra": "Purva Phalguni",
      "nakshatraLord": "Venus",
      "house": 10
    },
    {
      "id": 5,
      "name": "Venus",
      "fullDegree": 82.69209010485653,
      "normDegree": 22.692090104856533,
      "speed": 1.2289819763466134,
      "isRetro": "false",
      "sign": "Gemini",
      "signLord": "Mercury",
      "nakshatra": "Punarvasu",
      "nakshatraLord": "Jupiter",
      "house": 8
    },
    {
      "id": 6,
      "name": "Saturn",
      "fullDegree": 227.07712216560267,
      "normDegree": 17.077122165602674,
      "speed": -0.059870453983687545,
      "isRetro": "true",
      "sign": "Scorpio",
      "signLord": "Mars",
      "nakshatra": "Jyeshtha",
      "nakshatraLord": "Mercury",
      "house": 1
    },
    {
      "id": 7,
      "name": "Rahu",
      "fullDegree": 141.8589732373409,
      "normDegree": 21.858973237340905,
      "speed": -0.05295375766704849,
      "isRetro": "true",
      "sign": "Leo",
      "signLord": "Sun",
      "nakshatra": "Purva Phalguni",
      "nakshatraLord": "Venus",
      "house": 10
    },
    {
      "id": 8,
      "name": "Ketu",
      "fullDegree": 321.85897323734093,
      "normDegree": 21.858973237340933,
      "speed": -0.05295375766704849,
      "isRetro": "true",
      "sign": "Aquarius",
      "signLord": "Saturn",
      "nakshatra": "Purva Bhadrapad",
      "nakshatraLord": "Jupiter",
      "house": 4
    },
    {
      "id": 9,
      "name": "Ascendant",
      "fullDegree": 223.64473065441229,
      "normDegree": 13.644730654412285,
      "speed": 0,
      "isRetro": false,
      "sign": "Scorpio",
      "signLord": "Mars",
      "nakshatra": "Anuradha",
      "nakshatraLord": "Saturn",
      "house": 1
    }
  ]
}
```

### match_ashtakoot_points
Get Ashtakoot Points.

#### API Endpoint
match_ashtakoot_points

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_ashtakoot_points|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "varna": {
    "description": "Natural Refinement / Work",
    "male_koot_attribute": "Kshatriya",
    "female_koot_attribute": "Kshatriya",
    "total_points": 1,
    "received_points": 1
  },
  "vashya": {
    "description": "Innate Giving / Attraction towards each other",
    "male_koot_attribute": "Chatuspad",
    "female_koot_attribute": "Chatuspad",
    "total_points": 2,
    "received_points": 2
  },
  "tara": {
    "description": "Comfort - Prosperity - Health",
    "total_points": 3,
    "received_points": 0
  },
  "yoni": {
    "description": "Intimate Physical",
    "total_points": 4,
    "received_points": 0
  },
  "maitri": {
    "description": "Friendship",
    "male_koot_attribute": "Mars",
    "female_koot_attribute": "Mars",
    "total_points": 5,
    "received_points": 5
  },
  "gan": {
    "description": "Temperament",
    "male_koot_attribute": "",
    "female_koot_attribute": "",
    "total_points": 6,
    "received_points": 6
  },
  "bhakut": {
    "description": "Constructive Ability / Constructivism / Society and Couple",
    "male_koot_attribute": "Aries",
    "female_koot_attribute": "Aries",
    "total_points": 7,
    "received_points": 7
  },
  "nadi": {
    "description": "Progeny / Excess",
    "male_koot_attribute": "",
    "female_koot_attribute": "",
    "total_points": 8,
    "received_points": 0
  },
  "total": {
    "total_points": 36,
    "received_points": 21,
    "minimum_required": 18
  },
  "conclusion": {
    "status": true,
    "report": "Ashtakoota Matching between male and female is 21 points out of 36 points. This is a reasonably good score. Moreover, your rashi lords are friendly with each other thereby signifying mental compatibility and mutual affection between the two. Hence, this is a favourable Ashtakoota match."
  }
}
```

### match_ashtakoot_points
Get Ashtakoot Points.

#### API Endpoint
match_ashtakoot_points

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_ashtakoot_points|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "varna": {
    "description": "Natural Refinement / Work",
    "male_koot_attribute": "Kshatriya",
    "female_koot_attribute": "Kshatriya",
    "total_points": 1,
    "received_points": 1
  },
  "vashya": {
    "description": "Innate Giving / Attraction towards each other",
    "male_koot_attribute": "Chatuspad",
    "female_koot_attribute": "Chatuspad",
    "total_points": 2,
    "received_points": 2
  },
  "tara": {
    "description": "Comfort - Prosperity - Health",
    "total_points": 3,
    "received_points": 0
  },
  "yoni": {
    "description": "Intimate Physical",
    "total_points": 4,
    "received_points": 0
  },
  "maitri": {
    "description": "Friendship",
    "male_koot_attribute": "Mars",
    "female_koot_attribute": "Mars",
    "total_points": 5,
    "received_points": 5
  },
  "gan": {
    "description": "Temperament",
    "male_koot_attribute": "",
    "female_koot_attribute": "",
    "total_points": 6,
    "received_points": 6
  },
  "bhakut": {
    "description": "Constructive Ability / Constructivism / Society and Couple",
    "male_koot_attribute": "Aries",
    "female_koot_attribute": "Aries",
    "total_points": 7,
    "received_points": 7
  },
  "nadi": {
    "description": "Progeny / Excess",
    "male_koot_attribute": "",
    "female_koot_attribute": "",
    "total_points": 8,
    "received_points": 0
  },
  "total": {
    "total_points": 36,
    "received_points": 21,
    "minimum_required": 18
  },
  "conclusion": {
    "status": true,
    "report": "Ashtakoota Matching between male and female is 21 points out of 36 points. This is a reasonably good score. Moreover, your rashi lords are friendly with each other thereby signifying mental compatibility and mutual affection between the two. Hence, this is a favourable Ashtakoota match."
  }
}
```

### match_making_report
Get complete match making report.

#### API Endpoint
match_making_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_making_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "ashtakoota": {
    "status": true,
    "received_points": 21
  },
  "manglik": {
    "status": true,
    "male_percentage": 27.5,
    "female_percentage": 28.25
  },
  "rajju_dosha": {
    "status": false
  },
  "vedha_dosha": {
    "status": false
  },
  "conclusion": {
    "match_report": "Marriage between the prospective bride and groom is highly recommended.
     The couple would have a long-lasting relationship, which would be filled with happiness and affluence."
  }
}
```

### match_manglik_report
Get manglik report of both male and female.

#### API Endpoint
match_manglik_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_manglik_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "male": {
    "manglik_present_rule": {
      "based_on_aspect": [
        "Fourth house of your birth chart is aspected by KETU",
        "Twelfth house of your birth chart is aspected by KETU.",
        "RAHU is aspecting eighth house of your birth chart.",
        "MARS is aspecting second house of your birth chart.",
        "KETU is aspecting second house of your birth chart.",
        "Your first house in birth chart is aspected by planet SUN.",
        "Your first house in birth chart is aspected by planet SATURN."
      ],
      "based_on_house": [
        "Planet Rahu is situated in SECOND house in your birth chart.",
        "Planet Saturn is in FOURTH house in your horoscope.",
        "Planet Sun is situated in SEVENTH house in your birth chart.",
        "EIGHTH house is occupied by planet Mars in your birth chart.",
        "Planet Ketu is situated in EIGHTH house in your birth chart."
      ]
    },
    "manglik_cancel_rule": [
      "Mars mangalik dosha is get cancelled because Mars is situated in Eighth house with Pisces"
    ],
    "is_mars_manglik_cancelled": true,
    "manglik_status": "LESS_EFFECTIVE",
    "percentage_manglik_present": 23.5,
    "percentage_manglik_after_cancellation": 18.5,
    "manglik_report": "The manglik dosha is present in your horoscope, however it is less effective. With some remedies related to mangalik dosha this can be reduced further.",
    "is_present": false
  },
  "female": {
    "manglik_present_rule": {
      "based_on_aspect": [
        "Fourth house of your birth chart is aspected by KETU",
        "Twelfth house of your birth chart is aspected by KETU.",
        "RAHU is aspecting eighth house of your birth chart.",
        "MARS is aspecting second house of your birth chart.",
        "KETU is aspecting second house of your birth chart.",
        "Your first house in birth chart is aspected by planet SUN.",
        "Your first house in birth chart is aspected by planet SATURN."
      ],
      "based_on_house": [
        "Planet Rahu is situated in SECOND house in your birth chart.",
        "Planet Saturn is in FOURTH house in your horoscope.",
        "Planet Sun is situated in SEVENTH house in your birth chart.",
        "EIGHTH house is occupied by planet Mars in your birth chart.",
        "Planet Ketu is situated in EIGHTH house in your birth chart."
      ]
    },
    "manglik_cancel_rule": [
      "Mars mangalik dosha is get cancelled because Mars is situated in Eighth house with Pisces"
    ],
    "is_mars_manglik_cancelled": true,
    "manglik_status": "LESS_EFFECTIVE",
    "percentage_manglik_present": 23.5,
    "percentage_manglik_after_cancellation": 18.5,
    "manglik_report": "The manglik dosha is present in your horoscope, however it is less effective. With some remedies related to mangalik dosha this can be reduced further.",
    "is_present": false
  },
  "conclusion": {
    "match": true,
    "report": "The boy is not a Manglik; nor is the girl a Manglik. Mangal Dosha being absent in either horoscopes, there shall be no ill effect on their marriage. This match is recommended."
  }
}
```

### match_obstructions
Get Obstruction(Vedh Karak) report.

#### API Endpoint
match_obstructions

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_obstructions|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "is_present": false,
  "vedha_report": "The Nakshatras of male and female does not belong to Vedha Kutir pair and therefore no Vedha dosha.",
  "vedha_name": false
}
```

### match_simple_report
Get simple matching report

#### API Endpoint
match_simple_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/match_simple_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| m_day      | int | Male Birth day, eg: 10 |
| m_month     | int      | Male  Birth month, eg:5 |
| m_year | int      |   Male Birth year, eg:2015 |
| m_hour | int      |   Male Birth hour, eg:5 |
| m_min | int      |   Male Birth minute, eg:44 |
| m_lat | float |Male Birth place latitude, eg: 19.234|
| m_lon | float |Male Birth place longitude, eg: 72.843|
| m_tzone | float | Male Birth place timezone, eg: 5.5|
| f_day      | int |Female Birth day, eg: 10 |
| f_month     | int      | Female  Birth month, eg:5 |
| f_year | int      |   Female Birth year, eg:2015 |
| f_hour | int      |   Female Birth hour, eg:5 |
| f_min | int      |   Female Birth minute, eg:44 |
| f_lat | float | Female Birth place latitude, eg: 19.234|
| f_lon | float |Female  Birth place longitude, eg: 72.843|
| f_tzone | float |Female Birth place timezone, eg: 5.5|


#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "ashtakoota": {
    "status": true,
    "received_points": 22
  },
  "manglik": {
    "status": true,
    "male_percentage": 18.75,
    "female_percentage": 18.75
  },
  "rajju_dosha": {
    "status": false
  },
  "vedha_dosha": {
    "status": false
  },
  "conclusion": {
    "match_report": "Marriage between the prospective bride and groom is highly recommended. The couple would have a long-lasting relationship, which would be filled with happiness and affluence."
  }
}
```

## Numerology Predictions
Provides numerological predictions report. Provides report about name.

### numero_report
Provides Numerology report.

#### API Endpoint
numero_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "title": "What the Number Says About You",
  "description": "Your Radical number is 8. The ruler of Radical number 8 is Saturn. Due to Saturns influence you will rise slowly in life. To attain success after crossing obstacles and hardships is in your nature. You will not be deterred by failures though on occasions you may sink in despair. Your staunchest enemy is lethargy and this will be the reason for your decline. Therefore, dont procrastinate. Due to Saturns influence you will do many important jobs, which will render you name, acclaim and eminence. Not many people will understand your style of work. This will create many critics. You will have less tendency for show-off. This may lead people to regard you as a rough and tough person, while deep inside your heart you are quite sentimental and kind hearted. Mostly you will concern yourself with your work. Your tendency will be to confine yourself to your business. This attitude will generate many adverse people.You will have spirit of sacrifice. You will never waver from desired exertion, dedication and sacrifice desired for an endeavour. Therefore, you will certainly attain your goal after crossing hurdles. The people under the influence of Saturn are hardworking and struggling. As they have to cross many obstacles, they attain success somewhat late but their achievements are stable and permanent."
}

```

### numero_fav_time
Suggest favourable time.

#### API Endpoint
numero_fav_time

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_fav_time|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "title": "Favourable Time For You",
  "description": " According to western view the Sun remains in Capricorn and Aquarius from 23rd December to 19th February and by Indian thought it is in these signs from 14th January to 13th March. These are the own signs of Saturn. From 17th October to 13th November the Sun is in Libra which is the exalted sign of Saturn. These dates are lucky for people of Radical number 8."
}
```

### numero_place_vastu
Gives report of place and vastu

#### API Endpoint
numero_place_vastu

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_place_vastu|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "title": "Favourable Place Vastu For You",
  "description": "Choose the west direction for your house, flat or shopping complex as for Radical number 8 West is a lucky direction. If the total of your house number is 8 it will be good. To reside in western area of a city or in Western part of your house will be beneficial. Similarly to perform your important jobs by sitting in this direction will be good for you."
}
```

### numero_fasts_report
Suggest fasts days for native

#### API Endpoint
numero_fasts_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_fasts_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "title": "Fast Vrata Timing For You",
  "description": "Observe fast on Saturday for elimination of malefic effects of Saturn. Wear black or blue clothes on these days. Observe this fast for 19 or 51 Saturdays. Massage oil on your body, donate oil and worship Peepal tree. Recite Shani mantra on beads of rudraksha as much as possible."
}
```
### numero_fav_lord
Provides favourable lords for native

#### API Endpoint
numero_fav_lord

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_fav_lord|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "title": "Favourable Lord For You",
  "description": "You should worship Saturn or Batuk Bhairav. Recite Batuk Bhairav Mantra daily 108 times on rudraksha beads. All your problems and diseases will be over. The Batuk Bhairav mantra is \"Hreem Batukay Aapdudharnay Kuru Kuru Batukay Hreem\". This mantra of 21 letters can fulfill all desires. Its recitation on ashtami (8th day of Indian calender) of Krishna paksh (dark half of lunar month) is very advantageous."
}
```

### numero_fav_mantra
Provides favourable mantra for native

#### API Endpoint
numero_fav_mantra

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_fav_mantra|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "title": "Favourable Gayatri Mantra For You",
  "description": "You should recite Sani Gayatri mantra for increasing the benefic effects of Saturn daily after bath 11, 21 or 108 times. The Sani Gayatri Mantra : ||\"Om Bhagbhavay Vidmahe Mrityuroopay Dheemahi Tanno Shanih Prachodyat\" ||"
}
```

## Pitri Dosha Report
Pitri Dosha Report Calculates Pitra Dosha report

### pitra_dosha_report
Returns the whether given horoscope has pitra dosha or not and if present it provides with the matching rules for pitra dosha analysis.

#### API Endpoint
pitra_dosha_report

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/pitra_dosha_report|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "what_is_pitri_dosha": "Pitri Dosha is a Karmic Debt of the ancestors and reflected in the horoscope in the form of planetary combinations. It can also happen due to the neglect of ancestors and not providing them their proper due in the form of shraddh or charity or spiritual upliftments.",
  "is_pitri_dosha_present": true,
  "rules_matched": [
    "Conjuction of Moon and Rahu and/or Rahu and Saturn causes Pitri Dosha."
  ],
  "conclusion": "Your horoscope is having Pitri Dosha as it is satisfying 1 rules laid down for Pitri Dosha. You should not worry as there are remedies for Pitri Dosha which you can perform and be relieved from this dosha.",
  "remedies": [
    "Following are the remedies to be performed for Pitri Dosha",
    "Pitri dosha nivaran puja should be performed to pacify that malefic planet in Pitri paksha.",
    "Auspicious Puja, Vrat for destroying the effects of past sinful deeds or Pitra Dosha.",
    "Charity on Akshaya Tritiya.",
    "Perform Trapandi Shraad to get rid of Pitri dosha.",
    "Giving water to the Banyan tree is also a remedial measure for pitri dosha.",
    "Offer food to Brahmins on every \"Amavasya\".",
    "Donate food items on every \"Amavasya\" and \"Poornima\" in some temple or other religious places.",
    "Conduct Mantra Jap, Puja, Charity in Adhik or Purushottam Maas.",
    "Perform Puja, Vrat on Falharini Kalika Jyeshtha Amvasya.",
    "Worship Lord Shiva regularly to have peace to you and your ancestors."
  ],
  "effects": [
    "Following are the effects of Pitri Dosha - ",
    "Pitri Dosha leads to unfavorable environment in the family.",
    "It also leads to delay in marriage and having unsuccessful marriages.",
    "Pitri Dosh can also cause accidents or unwanted incidents in the family.",
    "It can cause delay or obstructions in education with or may land one into never ending debts.",
    "Inherited diseases and prolong illness is one of the ill effects of pitri dosha"
  ]
}
```

## Puja Suggesstion
Returns the personalised puja recommendations based on horoscope.

### puja_suggestion
Returns the personalised puja recommendations based on horoscope. This API takes in to account the Pitra Dosha in the horoscope, whether there is dasha change, presence of Kal Sarp dosha and Nakshatra

#### API Endpoint
puja_suggestion

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/puja_suggestion|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "summary": "Following are the puja suggestions based on your horoscope and planetary combinations.",
  "suggestions": [
    {
      "status": true,
      "priority": 5,
      "title": "Kal Sarpa Dosha Shanti Pujan",
      "puja_id": "KAL_SARPA",
      "summary": "If all the 7 planets are situated between Rahu and Ketu then Kaal Sarp Yog is formed.According to the situation of Rahu in 12 houses of horoscope there are Kaal Sarp Yogas of 12 types. These are : 1. Anant, 2. Kulik, 3. Vasuki, 4. Shankhpal, 5. Padma, 6. Mahapadma, 7. Takshak, 8. Karkotak, 9. Shankhchud, 10. Ghaatak, 11. Vishdhar and 12. Sheshnag. The Kaal Sarp Yog is of two types- Ascending and Descending. If all the 7 planets are eaten away by Rahus mouth then it is Ascending Kaal Sarp Yog. If all planets are situated in back of Rahu then Descending Kaal Sarp Yog is formed.",
      "one_line": "You have ascending kalsarpa dosha direction, which is treated as powerful. The KalSarpa Dosha is having partial effect in your horoscope."
    },
    {
      "status": true,
      "priority": 3,
      "title": "Nakshatra Pujan",
      "puja_id": "NAKSHATRA_PUJA",
      "summary": "Moon nakshatra is one of the most important nakshatra is horoscope. In horoscope, fifth, seventh and ninth houses are for children, life partner and luck respectively. And if their lords are in vedha (obstructive position) with Moon naksahtra then various hardships might be faced in your life. To reduce the effect of obsctructions and make your constellations in sync with other house lords, Nakshatra Puja is recommended.",
      "one_line": "Ninth house lord is in VIPAT vedha with your Moon nakshatra and therefore it is recommended that you perform nakshatra puja to mitigate evil effects of vedha."
    }
  ]
}
```

## Rudraksha Suggestion
Recommends suitable rudraksha with details

### rudraksha_suggestion
Returns the personalised puja recommendations based on horoscope. This API takes in to account the Pitra Dosha in the horoscope, whether there is dasha change, presence of Kal Sarp dosha and Nakshatra

#### API Endpoint
rudraksha_suggestion

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/rudraksha_suggestion|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "img_url": "/img/two+thirteen.jpg",
  "name": "Two + Thirteen Faced Rudraksha (Do + Terah Mukhi)",
  "recommend": "You are recommended to wear a combination of TWO and THIRTEEN FACED Rudraksha.",
  "detail": "The ruling planet of two Mukhi Rudraksha is Moon. It controls the malefic effects of Moon and diseases of the left eye, kidney, intestines etc.It helps in stabilizing the mind, making a person purposeful, making a person to complete a task before moving onto the next one."
}
```

## Sadhe Sati Report
Provides the Sade Sati report and recommend the remedies.

### sadhesati_life_details
Get the complete sadhesati details with all their phases and description. This API returns 3 sadhesati life cycles for the given birth detail.

#### API Endpoint
sadhesati_life_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sadhesati_life_details|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "what_is_sadhesati": "Sadhe Sati refers to the seven-and-a-half year period in which Saturn moves through three signs, the moon sign, one before the moon and the one after it. Sadhe Sati starts when Saturn (Shani) enters the 12th sign from the birth Moon sign and ends when Saturn leaves 2nd sign from the birth Moon sign. Since Saturn approximately takes around two and half years to transit a sign which is called Shanis dhaiya it takes around seven and half year to transit three signs and that is why it is known as Sadhe Sati. Generally Sade-Sati comes thrice in a horoscope in the life time - first in childhood, second in youth & third in old-age. First Sade-Sati has effect on education & parents. Second Sade-Sati has effect on profession, finance & family. The last one affects health more than anything else.",
  "report": [
    {
      "moon_sign": "Leo",
      "saturn_sign": "Cancer",
      "is_saturn_retrograde": false,
      "type": "RISING_START",
      "millisecond": "2036365200000",
      "date": "12-7-2034",
      "summary": "Sadhesati Rise Phase starting."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Leo",
      "is_saturn_retrograde": false,
      "type": "PEAK_START",
      "millisecond": "2103411600000",
      "date": "26-8-2036",
      "summary": "Sadhesati Peak Phase starting with Rise Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Virgo",
      "is_saturn_retrograde": false,
      "type": "SETTING_START",
      "millisecond": "2171322000000",
      "date": "21-10-2038",
      "summary": "Sadhesati Setting Phase starting with Peak Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Virgo",
      "is_saturn_retrograde": true,
      "type": "PEAK_START",
      "millisecond": "2185578000000",
      "date": "4-4-2039",
      "summary": "Sadhesati Peak Phase starting with Rise Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Virgo",
      "is_saturn_retrograde": false,
      "type": "SETTING_START",
      "millisecond": "2194131600000",
      "date": "12-7-2039",
      "summary": "Sadhesati Setting Phase starting with Peak Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Libra",
      "is_saturn_retrograde": false,
      "type": "SETTING_END",
      "millisecond": "2242947600000",
      "date": "27-1-2041",
      "summary": "Sadhesati Setting Phase ending and with this Sadhesati is also ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Libra",
      "is_saturn_retrograde": true,
      "type": "SETTING_START",
      "millisecond": "2243725200000",
      "date": "5-2-2041",
      "summary": "Sadhesati Setting Phase starting with Peak Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Libra",
      "is_saturn_retrograde": false,
      "type": "SETTING_END",
      "millisecond": "2263770000000",
      "date": "25-9-2041",
      "summary": "Sadhesati Setting Phase ending and with this Sadhesati is also ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Cancer",
      "is_saturn_retrograde": false,
      "type": "RISING_START",
      "millisecond": "2955142800000",
      "date": "23-8-2063",
      "summary": "Sadhesati Rise Phase starting."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Cancer",
      "is_saturn_retrograde": true,
      "type": "RISING_END",
      "millisecond": "2969398800000",
      "date": "4-2-2064",
      "summary": "Sadhesati Rise Phase ending and with this Sadhesati is also ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Cancer",
      "is_saturn_retrograde": false,
      "type": "RISING_START",
      "millisecond": "2977520400000",
      "date": "8-5-2064",
      "summary": "Sadhesati Rise Phase starting."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Leo",
      "is_saturn_retrograde": false,
      "type": "PEAK_START",
      "millisecond": "3022621200000",
      "date": "12-10-2065",
      "summary": "Sadhesati Peak Phase starting with Rise Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Leo",
      "is_saturn_retrograde": true,
      "type": "RISING_START",
      "millisecond": "3032384400000",
      "date": "2-2-2066",
      "summary": "Sadhesati Rise Phase starting."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Leo",
      "is_saturn_retrograde": false,
      "type": "PEAK_START",
      "millisecond": "3045344400000",
      "date": "2-7-2066",
      "summary": "Sadhesati Peak Phase starting with Rise Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Virgo",
      "is_saturn_retrograde": false,
      "type": "SETTING_START",
      "millisecond": "3113514000000",
      "date": "29-8-2068",
      "summary": "Sadhesati Setting Phase starting with Peak Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Libra",
      "is_saturn_retrograde": false,
      "type": "SETTING_END",
      "millisecond": "3182288400000",
      "date": "3-11-2070",
      "summary": "Sadhesati Setting Phase ending and with this Sadhesati is also ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Cancer",
      "is_saturn_retrograde": false,
      "type": "RISING_START",
      "millisecond": "3897334800000",
      "date": "1-7-2093",
      "summary": "Sadhesati Rise Phase starting."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Leo",
      "is_saturn_retrograde": false,
      "type": "PEAK_START",
      "millisecond": "3964467600000",
      "date": "17-8-2095",
      "summary": "Sadhesati Peak Phase starting with Rise Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Virgo",
      "is_saturn_retrograde": false,
      "type": "SETTING_START",
      "millisecond": "4032291600000",
      "date": "10-10-2097",
      "summary": "Sadhesati Setting Phase starting with Peak Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Virgo",
      "is_saturn_retrograde": true,
      "type": "PEAK_START",
      "millisecond": "4049830800000",
      "date": "1-5-2098",
      "summary": "Sadhesati Peak Phase starting with Rise Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Virgo",
      "is_saturn_retrograde": false,
      "type": "SETTING_START",
      "millisecond": "4054064400000",
      "date": "19-6-2098",
      "summary": "Sadhesati Setting Phase starting with Peak Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Libra",
      "is_saturn_retrograde": false,
      "type": "SETTING_END",
      "millisecond": "4101930000000",
      "date": "25-12-2099",
      "summary": "Sadhesati Setting Phase ending and with this Sadhesati is also ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Libra",
      "is_saturn_retrograde": true,
      "type": "SETTING_START",
      "millisecond": "4108928400000",
      "date": "16-3-2100",
      "summary": "Sadhesati Setting Phase starting with Peak Phase ending."
    },
    {
      "moon_sign": "Leo",
      "saturn_sign": "Libra",
      "is_saturn_retrograde": false,
      "type": "SETTING_END",
      "millisecond": "4124739600000",
      "date": "15-9-2100",
      "summary": "Sadhesati Setting Phase ending and with this Sadhesati is also ending."
    }
  ]
}
```

### sadhesati_current_status
Returns whether the given data is undergoing sadhesati or not. It also returns the current saturn transit, birth moon sign and retrograde status of saturn.

#### API Endpoint
sadhesati_current_status

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sadhesati_current_status|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "consideration_date": "16-8-2015",
  "is_saturn_retrograde": true,
  "moon_sign": "Leo",
  "saturn_sign": "Scorpio",
  "is_undergoing_sadhesati": "No, currently you are not undergoing Sadhesati.",
  "sadhesati_status": false,
  "what_is_sadhesati": "Sadhe Sati refers to the seven-and-a-half year period in which Saturn moves through three signs, the moon sign, one before the moon and the one after it. Sadhe Sati starts when Saturn (Shani) enters the 12th sign from the birth Moon sign and ends when Saturn leaves 2nd sign from the birth Moon sign. Since Saturn approximately takes around two and half years to transit a sign which is called Shanis dhaiya it takes around seven and half year to transit three signs and that is why it is known as Sadhe Sati. Generally Sade-Sati comes thrice in a horoscope in the life time - first in childhood, second in youth & third in old-age. First Sade-Sati has effect on education & parents. Second Sade-Sati has effect on profession, finance & family. The last one affects health more than anything else."
}
```

### sadhesati_remedies
Returns the list of sadhesati remedies which can be performed when one is under sadhesati transit.

#### API Endpoint
sadhesati_remedies

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sadhesati_remedies|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| hour | int      |    Birth hour, eg:5 |
| min | int      |    Birth minute, eg:55 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|
| gender | string | OPTIONAL - User gender, eg: male OR female|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "what_is_sadhesati": "Sadhe Sati refers to the seven-and-a-half year period in which Saturn moves through three signs, the moon sign, one before the moon and the one after it. Sadhe Sati starts when Saturn (Shani) enters the 12th sign from the birth Moon sign and ends when Saturn leaves 2nd sign from the birth Moon sign. Since Saturn approximately takes around two and half years to transit a sign which is called Shanis dhaiya it takes around seven and half year to transit three signs and that is why it is known as Sadhe Sati. Generally Sade-Sati comes thrice in a horoscope in the life time - first in childhood, second in youth & third in old-age. First Sade-Sati has effect on education & parents. Second Sade-Sati has effect on profession, finance & family. The last one affects health more than anything else.",
  "remedies": [
    "Following are the remedies for Sadhe Sati - ",
    "Give respect to your subordinate, servant, poor and lower class people.",
    "Serve and respect your parents and elderly people.",
    "Recite Shri Hanuman Chalisa.",
    "Shani Yantra is used to pacify an afflicted Shani and get blessings of Lord Shani. When Saturn is malefic in a horoscope due to wrong placement, Sadhe Sati or Small Affliction, use of Shani Yantra is very Beneficial. ",
    "It is good and beneficial to fast on Saturdays starting from sunrise to ending at sunset when Sadhe Sati is in effect.",
    "Donate urad (a type of pulse), oil, sapphire, black sesame seeds, black buffalo, iron, money and black clothes as per your financial situation to poor and needy people.",
    "Wearing of seven faced Rudraksha tends to mitigate the ill effects of Sadhe Sati."
  ]
}
```
## Sun Sign Daily
Get today's daily prediction based on Sun Sign.

### sun_sign_prediction/daily/:zodiacName
Returns the list of sadhesati remedies which can be performed when one is under sadhesati transit.

#### API Endpoint
sun_sign_prediction/daily/:zodiacName

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sun_sign_prediction/daily/:zodiacName|

#### zodiacName ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
> Where Zodiac name is -
> aries,
> taurus,
> gemini,
> cancer,
> leo,
> virgo,
> libra,
> scorpio,
> sagittarius,
> capricorn,
> aquarius,
> pisces

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "status": true,
  "sun_sign": "aries",
  "prediction_date": "26-2-2016",
  "prediction": {
    "health": "You shall enjoy good health. There shall be no physical ailments. . Despite a hectic day you will still be able to retain your high energy levels.",
    "emotional": "You will experience happiness and contentment. Romantic feelings and satisfaction will play a key role in your bliss today.",
    "personal": "You shall enjoy conjugal comfort and happiness. You shall be intimately drawn towards someone. You may celebrate the day with your beloved. Relations with friends and relatives will be rewarding and enjoyable. Overall, it is a satisfying period for pleasure and happiness.",
    "professional": "You will get rewards, results and appreciation for your work. There shall be a boost in your earnings and profits.",
    "travel": "Today is a perfect day to go for a romantic outing with your partner.",
    "luck": "Today is a very auspicious day for you. Your wishes shall be fulfilled."
  }
}
```

