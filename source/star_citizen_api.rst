Star Citizen Api
================

Schnittstelle zu verschiedenen Diensten von Star Citizen ( https://robertsspaceindustries.com/ )


Crowdfund Statistiken
---------------------
API zur Abfrage des aktuellen Spendenstatuses, der Fleet sowie der Fans.

Ein Import der Daten erfolgt stündlich.


Alle Statistiken
^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/stats``


|query_param|

=========  =======      =======================================================================================================================  ==============  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte  Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  ==============  ========  ========  ========
page       integer      Seite der Ausgabe. Anzahl der Seiten sowie derzeitige Seite stehen in den Metadaten der Ausgabe                                          Ja        1         1
limit      integer      Limitiert die Anzahl der Daten auf die angegebene Zahl. Ein Limit von '0' deaktiviert das Limit und gibt alle Daten aus                  Ja        1         10
=========  =======      =======================================================================================================================  ==============  ========  ========  ========


.. code-block:: json
    :caption: |caption_response_no_query_params|

    {
      "data": [
        {
          "funds": "192674121.56",
          "fans": 2088028,
          "fleet": 1639454,
          "timestamp": "2018-08-26 20:00:03"
        },
        {
          "funds": "192564446.10",
          "fans": 2080913,
          "fleet": 1639019,
          "timestamp": "2018-08-25 20:00:05"
        },
        {
          "funds": "...",
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 1957,
          "count": 10,
          "per_page": 10,
          "current_page": 1,
          "total_pages": 196,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/stats?page=2"
          }
        }
      }
    }


|api_endpoint| ``/api/stats?limit=1``

.. code-block:: json
    :caption: Ausgabe der Anfrage mit Limit Parameter = 1:

    {
      "data": [
        {
          "funds": "192674121.56",
          "fans": 2088028,
          "fleet": 1639454,
          "timestamp": "2018-08-26 20:00:03"
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 1957,
          "count": 1,
          "per_page": 1,
          "current_page": 1,
          "total_pages": 1957,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/stats?page=2"
          }
        }
      }
    }



Aktuelle Statistik
^^^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/stats/latest``

.. code-block:: json
    :caption: |caption_response|

    {
      "data": {
        "funds": "192674121.56",
        "fans": 2088028,
        "fleet": 1639454,
        "timestamp": "2018-08-26 20:00:03"
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
      }
    }



Raumschiffe
-----------
API zur Abfrage der Raumschiffe aus der Ship Matrix ( https://robertsspaceindustries.com/ship-matrix )

Ein Import der Daten erfolgt wöchentlich, oder bei der Herausgabe eines neuen Raumschiffes.


Alle Raumschiffe
^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/ships``


|query_param|

=========  =======      =======================================================================================================================  ==============  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte  Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  ==============  ========  ========  ========
page       integer      Seite der Ausgabe. Anzahl der Seiten sowie derzeitige Seite stehen in den Metadaten der Ausgabe                                          Ja        1         1
limit      integer      Limitiert die Anzahl der Daten auf die angegebene Zahl. Ein Limit von '0' deaktiviert das Limit und gibt alle Daten aus                  Ja        1         5
locale     string       Sprache der zurückgegebenen Daten. Ersatzsprache ist en_EN (Englisch) bei fehlender deutscher Übersetzung                de_DE en_EN     Ja        de_DE
=========  =======      =======================================================================================================================  ==============  ========  ========  ========


.. code-block:: json
    :caption: |caption_response_no_query_params|

    {
      "data": [
        {
          "id": 1,
          "chassis_id": 1,
          "name": "Aurora ES",
          "slug": "aurora-es",
          "sizes": {
            "length": "118.00",
            "beam": "8.00",
            "height": "4.00"
          },
          "mass": 25172,
          "cargo_capacity": 0,
          "crew": {
            "min": 1,
            "max": 1
          },
          "speed": {
            "scm": 190,
            "afterburner": 1140
          },
          "agility": {
            "pitch": "70.00",
            "yaw": "70.00",
            "roll": "95.00",
            "acceleration": {
              "x_axis": "43.00",
              "y_axis": "45.70",
              "z_axis": "44.20"
            }
          },
          "foci": [
            {
              "en_EN": "Starter",
              "de_DE": "Einsteiger"
            },
            {
              "en_EN": "Pathfinder",
              "de_DE": "Pfadfinder"
            }
          ],
          "production_status": {
            "en_EN": "flight-ready",
            "de_DE": "Flugbereit"
          },
          "production_note": {
            "en_EN": "None",
            "de_DE": "Keine"
          },
          "type": {
            "en_EN": "multi",
            "de_DE": "Mehrzweck"
          },
          "description": {
            "en_EN": "The Aurora is the modern-day descendant of the Roberts Space Industries X-7 spacecraft which tested the very first jump engines. Utilitarian to a T, the Aurora Essential is the perfect choice for new ship owners: versatile enough to tackle a myriad of challenges, yet with a straightforward and intuitive design."
          },
          "size": {
            "en_EN": "small",
            "de_DE": "Klein"
          },
          "manufacturer": {
            "code": "RSI",
            "name": "Roberts Space Industries"
          },
          "updated_at": "2017-10-24 19:40:49"
        },
        {
          "id": 2,
          "chassis_id": 1,
          "..."
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 118,
          "count": 5,
          "per_page": 5,
          "current_page": 1,
          "total_pages": 24,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/ships?page=2"
          }
        }
      }
    }


|api_endpoint| ``/api/ships?locale=de_DE``

.. code-block:: json
    :caption: |caption_response_german_localisation|

    {
      "data": [
        {
          "id": 1,
          "chassis_id": 1,
          "name": "Aurora ES",
          "slug": "aurora-es",
          "sizes": {
            "length": "118.00",
            "beam": "8.00",
            "height": "4.00"
          },
          "mass": 25172,
          "cargo_capacity": 0,
          "crew": {
            "min": 1,
            "max": 1
          },
          "speed": {
            "scm": 190,
            "afterburner": 1140
          },
          "agility": {
            "pitch": "70.00",
            "yaw": "70.00",
            "roll": "95.00",
            "acceleration": {
              "x_axis": "43.00",
              "y_axis": "45.70",
              "z_axis": "44.20"
            }
          },
          "foci": [
            "Einsteiger",
            "Pfadfinder"
          ],
          "production_status": "Flugbereit",
          "production_note": "Keine",
          "type": "Mehrzweck",
          "description": "The Aurora is the modern-day descendant of the Roberts Space Industries X-7 spacecraft which tested the very first jump engines. Utilitarian to a T, the Aurora Essential is the perfect choice for new ship owners: versatile enough to tackle a myriad of challenges, yet with a straightforward and intuitive design.",
          "size": "Klein",
          "manufacturer": {
            "code": "RSI",
            "name": "Roberts Space Industries"
          },
          "updated_at": "2017-10-24 19:40:49"
        },
        {
          "id": 2,
          "chassis_id": 1,
          "..."
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 118,
          "count": 5,
          "per_page": 5,
          "current_page": 1,
          "total_pages": 24,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/ships?page=2"
          }
        }
      }
    }


Einzelnes Raumschiff
^^^^^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/ships/{Raumschiff_Name}``

|url_param| Der Name des Raumschiffes in URL oder Slug enkodierter Form. Zum Beispiel ``Aurora+CL`` oder ``aurora-cl``


|query_param|

=========  =======      =======================================================================================================================  ==============  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte  Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  ==============  ========  ========  ========
locale     string       Sprache der zurückgegebenen Daten. Ersatzsprache ist en_EN (Englisch) bei fehlender deutscher Übersetzung                de_DE en_EN     Ja        de_DE
=========  =======      =======================================================================================================================  ==============  ========  ========  ========


|api_endpoint| ``/api/ships/300i``

.. code-block:: json
    :caption: |caption_response_no_query_params|

    {
      "data": {
        "id": 7,
        "chassis_id": 2,
        "name": "300i",
        "slug": "300i",
        "sizes": {
          "length": "23.00",
          "beam": "15.50",
          "height": "7.00"
        },
        "mass": 65925,
        "cargo_capacity": 2,
        "crew": {
          "min": 1,
          "max": 1
        },
        "speed": {
          "scm": 275,
          "afterburner": 1190
        },
        "agility": {
          "pitch": "85.00",
          "yaw": "85.00",
          "roll": "120.00",
          "acceleration": {
            "x_axis": "68.00",
            "y_axis": "80.30",
            "z_axis": "71.70"
          }
        },
        "foci": [
          {
            "en_EN": "Touring",
            "de_DE": "Reisen"
          }
        ],
        "production_status": {
          "en_EN": "flight-ready",
          "de_DE": "Flugbereit"
        },
        "production_note": {
          "en_EN": "Update Pass Scheduled",
          "de_DE": "Aktualisierungsprozess geplant"
        },
        "type": {
          "en_EN": "exploration",
          "de_DE": "Erkundung"
        },
        "description": {
          "en_EN": "If you're going to travel the stars... why not do it in style? The 300i is Origin Jumpworks' premiere luxury spacecraft. It is a sleek, silver killer that sends as much of a message with its silhouette as it does with its weaponry."
        },
        "size": {
          "en_EN": "small",
          "de_DE": "Klein"
        },
        "manufacturer": {
          "code": "ORIG",
          "name": "Origin Jumpworks GmbH"
        },
        "updated_at": "2017-10-24 19:41:06"
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
      }
    }


|api_endpoint| ``/api/ships/300i?locale=de_DE``

.. code-block:: json
    :caption: |caption_response_german_localisation|

    {
      "data": {
        "id": 7,
        "chassis_id": 2,
        "name": "300i",
        "slug": "300i",
        "sizes": {
          "length": "23.00",
          "beam": "15.50",
          "height": "7.00"
        },
        "mass": 65925,
        "cargo_capacity": 2,
        "crew": {
          "min": 1,
          "max": 1
        },
        "speed": {
          "scm": 275,
          "afterburner": 1190
        },
        "agility": {
          "pitch": "85.00",
          "yaw": "85.00",
          "roll": "120.00",
          "acceleration": {
            "x_axis": "68.00",
            "y_axis": "80.30",
            "z_axis": "71.70"
          }
        },
        "foci": [
          "Reisen"
        ],
        "production_status": "Flugbereit",
        "production_note": "Aktualisierungsprozess geplant",
        "type": "Erkundung",
        "description": "If you're going to travel the stars... why not do it in style? The 300i is Origin Jumpworks' premiere luxury spacecraft. It is a sleek, silver killer that sends as much of a message with its silhouette as it does with its weaponry.",
        "size": "Klein",
        "manufacturer": {
          "code": "ORIG",
          "name": "Origin Jumpworks GmbH"
        },
        "updated_at": "2017-10-24 19:41:06"
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
      }
    }


|api_endpoint| ``/api/ships/300``

.. code-block:: json
    :caption: |caption_response_404|

    {
      "message": "No Results for Query '300'",
      "status_code": 404
    }


Suche
^^^^^
|post|

|api_endpoint| ``/api/ships/search``

**Request Body**: ``query``

.. code-block:: php
    :caption: Beispielanfrage:

    $client = new GuzzleHttp\Client([
        'timeout' => 3.0,
        'base_uri' => 'https://api.star-citizen.wiki/api',
        'headers' => [
            'Auth' => 'Bearer <API Key>',
            'Accept' => 'application/x.StarCitizenWikiApi.v1+json',
        ]
    ]);

    $res = $client->request(
        'POST',
        '/ships/search',
        [
            'query' => 'Aurora'
        ]
    );

.. code-block:: json
    :caption: |caption_response|

    {
      "data": [
        {
          "id": 1,
          "chassis_id": 1,
          "name": "Aurora ES",
          "..."
        },
        {
          "id": 5,
          "chassis_id": 1,
          "name": "Aurora CL",
          "..."
        },
        {
          "id": 6,
          "chassis_id": 1,
          "name": "Aurora LN",
          "..."
        },
        {
          "id": 3,
          "chassis_id": 1,
          "name": "Aurora LX",
          "..."
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 5,
          "count": 5,
          "per_page": 5,
          "current_page": 1,
          "total_pages": 1,
          "links": []
        }
      }
    }


.. code-block:: json
    :caption: |caption_response_404|

    {
      "message": "No Results for Query 'not existent'",
      "status_code": 404
    }



Bodenfahrzeuge
--------------
API zur Abfrage der Bodenfahrzeuge aus der Ship Matrix ( https://robertsspaceindustries.com/ship-matrix )

Ein Import der Daten erfolgt wöchentlich, oder bei der Herausgabe eines neuen Fahrzeuges.


Alle Bodenfahrzeuge
^^^^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/vehicles``


|query_param|

=========  =======      =======================================================================================================================  ==============  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte  Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  ==============  ========  ========  ========
page       integer      Seite der Ausgabe. Anzahl der Seiten sowie derzeitige Seite stehen in den Metadaten der Ausgabe                                          Ja        1         1
limit      integer      Limitiert die Anzahl der Daten auf die angegebene Zahl. Ein Limit von '0' deaktiviert das Limit und gibt alle Daten aus                  Ja        1         5
locale     string       Sprache der zurückgegebenen Daten. Ersatzsprache ist en_EN (Englisch) bei fehlender deutscher Übersetzung                de_DE en_EN     Ja        de_DE
=========  =======      =======================================================================================================================  ==============  ========  ========  ========


.. code-block:: json
    :caption: |caption_response_no_query_params|

    {
      "data": [
        {
          "id": 134,
          "chassis_id": 53,
          "name": "Cyclone",
          "slug": "cyclone",
          "sizes": {
            "length": "6.00",
            "beam": "4.00",
            "height": "2.50"
          },
          "mass": 3022,
          "cargo_capacity": 1,
          "crew": {
            "min": 1,
            "max": 2
          },
          "speed": {
            "scm": 0
          },
          "foci": [
            {
              "en_EN": "Exploration",
              "de_DE": "Erkundung"
            },
            {
              "en_EN": "Recon",
              "de_DE": "Aufkl\u00e4rung"
            }
          ],
          "production_status": {
            "en_EN": "flight-ready",
            "de_DE": "Flugbereit"
          },
          "production_note": {
            "en_EN": "None",
            "de_DE": "Keine"
          },
          "type": {
            "en_EN": "ground",
            "de_DE": "Gel\u00e4nde"
          },
          "description": {
            "en_EN": "With a potent combination of speed, maneuverability, and rugged durability, the Cyclone is a perfect choice for local deliveries and transport between planetside homesteads and outposts."
          },
          "size": {
            "en_EN": "vehicle",
            "de_DE": "Fahrzeug"
          },
          "manufacturer": {
            "code": "TMBL",
            "name": "Tumbril"
          },
          "updated_at": "2017-10-24 19:42:39"
        },
        {
          "id": 135,
          "chassis_id": 53,
          "name": "Cyclone-TR",
          "..."
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 9,
          "count": 5,
          "per_page": 5,
          "current_page": 1,
          "total_pages": 2,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/vehicles?page=2"
          }
        }
      }
    }


|api_endpoint| ``/api/vehicles?locale=de_DE``

.. code-block:: json
    :caption: |caption_response_german_localisation|

    {
      "data": [
        {
          "id": 134,
          "chassis_id": 53,
          "name": "Cyclone",
          "slug": "cyclone",
          "sizes": {
            "length": "6.00",
            "beam": "4.00",
            "height": "2.50"
          },
          "mass": 3022,
          "cargo_capacity": 1,
          "crew": {
            "min": 1,
            "max": 2
          },
          "speed": {
            "scm": 0
          },
          "foci": {
            "Erkundung",
            "Aufklärung"
          },
          "production_status": "Flugbereit",
          "production_note": "Keine",
          "type": "Gelände",
          "description": "With a potent combination of speed, maneuverability, and rugged durability, the Cyclone is a perfect choice for local deliveries and transport between planetside homesteads and outposts.",
          "size": "Fahrzeug",
          "manufacturer": {
            "code": "TMBL",
            "name": "Tumbril"
          },
          "updated_at": "2017-10-24 19:42:39"
        },
        {
          "id": 135,
          "chassis_id": 53,
          "name": "Cyclone-TR",
          "..."
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 9,
          "count": 5,
          "per_page": 5,
          "current_page": 1,
          "total_pages": 2,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/vehicles?page=2"
          }
        }
      }
    }


Einzelnes Bodenfahrzeug
^^^^^^^^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/vehicles/{Fahrzeug_Name}``

|url_param| Der Name des Fahrzeuges in URL oder Slug enkodierter Form. Zum Beispiel ``Nova+Tank`` order ``nova-tank``


|query_param|

=========  =======      =======================================================================================================================  ==============  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte  Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  ==============  ========  ========  ========
locale     string       Sprache der zurückgegebenen Daten. Ersatzsprache ist en_EN (Englisch) bei fehlender deutscher Übersetzung                de_DE en_EN     Ja        de_DE
=========  =======      =======================================================================================================================  ==============  ========  ========  ========


|api_endpoint| ``/api/vehicles/Cyclone``

.. code-block:: json
    :caption: |caption_response_no_query_params|

    {
      "data": {
        "id": 134,
        "chassis_id": 53,
        "name": "Cyclone",
        "slug": "cyclone",
        "sizes": {
          "length": "6.00",
          "beam": "4.00",
          "height": "2.50"
        },
        "mass": 3022,
        "cargo_capacity": 1,
        "crew": {
          "min": 1,
          "max": 2
        },
        "speed": {
          "scm": 0
        },
        "foci": [
          {
            "en_EN": "Exploration",
            "de_DE": "Erkundung"
          },
          {
            "en_EN": "Recon",
            "de_DE": "Aufklärung"
          }
        ],
        "production_status": {
          "en_EN": "flight-ready",
          "de_DE": "Flugbereit"
        },
        "production_note": {
          "en_EN": "None",
          "de_DE": "Keine"
        },
        "type": {
          "en_EN": "ground",
          "de_DE": "Gelände"
        },
        "description": {
          "en_EN": "With a potent combination of speed, maneuverability, and rugged durability, the Cyclone is a perfect choice for local deliveries and transport between planetside homesteads and outposts."
        },
        "size": {
          "en_EN": "vehicle",
          "de_DE": "Fahrzeug"
        },
        "manufacturer": {
          "code": "TMBL",
          "name": "Tumbril"
        },
        "updated_at": "2017-10-24 19:42:39"
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
      }
    }


|api_endpoint| ``/api/vehicles/Cyclone?locale=de_DE``

.. code-block:: json
    :caption: |caption_response_german_localisation|

    {
      "data": {
        "id": 134,
        "chassis_id": 53,
        "name": "Cyclone",
        "slug": "cyclone",
        "sizes": {
          "length": "6.00",
          "beam": "4.00",
          "height": "2.50"
        },
        "mass": 3022,
        "cargo_capacity": 1,
        "crew": {
          "min": 1,
          "max": 2
        },
        "speed": {
          "scm": 0
        },
        "foci": [
          "Erkundung",
          "Aufklärung"
        ],
        "production_status": "Flugbereit",
        "production_note": "Keine",
        "type": "Gelände",
        "description": "With a potent combination of speed, maneuverability, and rugged durability, the Cyclone is a perfect choice for local deliveries and transport between planetside homesteads and outposts.",
        "size": "Fahrzeug",
        "manufacturer": {
          "code": "TMBL",
          "name": "Tumbril"
        },
        "updated_at": "2017-10-24 19:42:39"
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
      }
    }


|api_endpoint| ``/api/vehicles/Cyclon``

.. code-block:: json
    :caption: |caption_response_404|

    {
      "message": "No Results for Query 'Cyclon'",
      "status_code": 404
    }


Suche
^^^^^
|post|

|api_endpoint| ``/api/vehicles/search``

**Request Body**: ``query``

.. code-block:: php
    :caption: Beispielanfrage:

    $client = new GuzzleHttp\Client([
        'timeout' => 3.0,
        'base_uri' => 'https://api.star-citizen.wiki/api',
        'headers' => [
            'Auth' => 'Bearer <API Key>',
            'Accept' => 'application/x.StarCitizenWikiApi.v1+json',
        ]
    ]);

    $res = $client->request(
        'POST',
        '/ground_search',
        [
            'query' => 'Cyclone'
        ]
    );

.. code-block:: json
    :caption: |caption_response|

    {
      "data": [
        {
          "id": 134,
          "chassis_id": 53,
          "name": "Cyclone",
          "..."
        },
        {
          "id": 135,
          "chassis_id": 53,
          "name": "Cyclone-TR",
          "..."
        },
        {
          "id": 136,
          "chassis_id": 53,
          "name": "Cyclone-RC",
          "..."
        },
        {
          "id": 137,
          "chassis_id": 53,
          "name": "Cyclone-RN",
          "..."
        },
        {
          "id": 138,
          "chassis_id": 53,
          "name": "Cyclone-AA",
          "..."
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 5,
          "count": 5,
          "per_page": 5,
          "current_page": 1,
          "total_pages": 1,
          "links": []
        }
      }
    }


.. code-block:: json
    :caption: |caption_response_404|

    {
      "message": "No Results for Query 'not existent'",
      "status_code": 404
    }



Hersteller
--------------
API zur Abfrage der Hersteller


Alle Hersteller
^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/manufacturers``


|query_param|

=========  =======      =======================================================================================================================  =====================  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte         Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  =====================  ========  ========  ========
page       integer      Seite der Ausgabe. Anzahl der Seiten sowie derzeitige Seite stehen in den Metadaten der Ausgabe                                                 Ja        1         1
limit      integer      Limitiert die Anzahl der Daten auf die angegebene Zahl. Ein Limit von '0' deaktiviert das Limit und gibt alle Daten aus                         Ja        1         10
locale     string       Sprache der zurückgegebenen Daten. Ersatzsprache ist en_EN (Englisch) bei fehlender deutscher Übersetzung                de_DE en_EN            Ja        de_DE
include    string       Komma separierter String mit namen der hinzuzufügenden Relationen                                                        ships vehicles         Ja        ships
=========  =======      =======================================================================================================================  =====================  ========  ========  ========


.. code-block:: json
    :caption: |caption_response_no_query_params|

    {
      "data": [
        {
          "code": "RSI",
          "name": "Roberts Space Industries",
          "known_for": {
            "en_EN": "the Aurora and the Constellation"
          },
          "description": {
            "en_EN": "..."
          }
        },
        {
          "code": "ORIG",
          "name": "Origin Jumpworks GmbH",
          "known_for": {
            "en_EN": "the 300i series"
          },
          "description": {
            "en_EN": "..."
          }
        },
        {
          "code": "ANVL",
          "name": "Anvil Aerospace",
          "..."
        },
        {
          "..."
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "ships",
          "vehicles"
        ],
        "pagination": {
          "total": 16,
          "count": 10,
          "per_page": 10,
          "current_page": 1,
          "total_pages": 2,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/manufacturers?page=2"
          }
        }
      }
    }


Einzelner Hersteller
^^^^^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/manufacturers/{Hersteller_Code}``

|url_param| Der Name des Code des Herstellers. Zum Beispiel ``RSI``


|query_param|

=========  =======      =======================================================================================================================  =====================  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte         Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  =====================  ========  ========  ========
locale     string       Sprache der zurückgegebenen Daten. Ersatzsprache ist en_EN (Englisch) bei fehlender deutscher Übersetzung                de_DE en_EN            Ja        de_DE
include    string       Komma separierter String mit namen der hinzuzufügenden Relationen                                                        ships vehicles         Ja        ships
=========  =======      =======================================================================================================================  =====================  ========  ========  ========


|api_endpoint| ``/api/manufacturers/RSI``

.. code-block:: json
    :caption: Ausgabe ohne Relationen:

    {
      "data": {
        "code": "RSI",
        "name": "Roberts Space Industries",
        "known_for": {
          "en_EN": "the Aurora and the Constellation"
        },
        "description": {
          "en_EN": "..."
        }
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "ships",
          "vehicles"
        ]
      }
    }


|api_endpoint| ``/api/manufacturers/CRSD?include=ships``

.. code-block:: json
    :caption: Ausgabe mit der Relation Raumschiffe:

    {
      "data": {
        "code": "CRSD",
        "name": "Crusader Industries",
        "known_for": {
          "en_EN": "Genesis Starliner"
        },
        "description": {
          "en_EN": "Genesis Starliner"
        },
        "ships": {
          "data": [
            {
              "name": "Genesis Starliner",
              "slug": "genesis-starliner",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/genesis-starliner"
            },
            {
              "name": "C2 Hercules",
              "slug": "c2-hercules",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/c2-hercules"
            },
            {
              "name": "M2 Hercules",
              "slug": "m2-hercules",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/m2-hercules"
            },
            {
              "name": "A2 Hercules",
              "slug": "a2-hercules",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/a2-hercules"
            },
            {
              "name": "Mercury Star Runner",
              "slug": "mercury-star-runner",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/mercury-star-runner"
            }
          ]
        },
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "ships",
          "vehicles"
        ]
      }
    }


|api_endpoint| ``/api/manufacturers/CRSD?include=ships,vehicles``

.. code-block:: json
    :caption: Ausgabe mit der Relation Raumschiffe und Bodenfahrzeuge:

    {
      "data": {
        "code": "CRSD",
        "name": "Crusader Industries",
        "known_for": {
          "en_EN": "Genesis Starliner"
        },
        "description": {
          "en_EN": "Genesis Starliner"
        },
        "ships": {
          "data": [
            {
              "name": "Genesis Starliner",
              "slug": "genesis-starliner",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/genesis-starliner"
            },
            {
              "name": "C2 Hercules",
              "slug": "c2-hercules",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/c2-hercules"
            },
            {
              "name": "M2 Hercules",
              "slug": "m2-hercules",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/m2-hercules"
            },
            {
              "name": "A2 Hercules",
              "slug": "a2-hercules",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/a2-hercules"
            },
            {
              "name": "Mercury Star Runner",
              "slug": "mercury-star-runner",
              "api_url": "https:\/\/api.star-citizen.wiki\/api\/ships\/mercury-star-runner"
            }
          ]
        },
        "vehicles": {
          "data": []
        }
      },
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "ships",
          "vehicles"
        ]
      }
    }


Suche
^^^^^
|post|

|api_endpoint| ``/api/manufacturers/search``

**Request Body**: ``query``

Die Suche kann sowohl nach dem Hersteller ``Code`` als auch dem Hersteller ``Namen`` erfolgen, also sowohl ``RSI`` als auch ``Roberts``


.. code-block:: php
    :caption: Beispielanfrage:

    $client = new GuzzleHttp\Client([
        'timeout' => 3.0,
        'base_uri' => 'https://api.star-citizen.wiki/api',
        'headers' => [
            'Auth' => 'Bearer <API Key>',
            'Accept' => 'application/x.StarCitizenWikiApi.v1+json',
        ]
    ]);

    $res = $client->request(
        'POST',
        '/manufacturers/search',
        [
            'query' => 'Roberts'
        ]
    );

.. code-block:: json
    :caption: |caption_response|

    {
      "data": [
        {
          "code": "RSI",
          "name": "Roberts Space Industries",
          "known_for": {
            "en_EN": "the Aurora and the Constellation"
          },
          "description": {
            "en_EN": "..."
          }
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "ships",
          "vehicles"
        ],
        "pagination": {
          "total": 1,
          "count": 1,
          "per_page": 10,
          "current_page": 1,
          "total_pages": 1,
          "links": []
        }
      }
    }


.. code-block:: json
    :caption: |caption_response_404|

    {
      "message": "No Results for Query 'not existent'",
      "status_code": 404
    }



Comm Links
----------
API zur Abfrage zu Comm Link Metadaten.

Eine Prüfung auf neue Comm Links erfolgt stündlich.

Zusätzlich werden jegliche Bilder der Comm Links von der Star Citizen Wiki API abgespeichert. Links zu den lokal gespeicherten Bildern sind unter dem Schlüssel ``api_url`` zu finden. Beträgt der Wert des Schlüssels ``null``, so ist eine lokale Speicherung noch nicht erfolgt.


Alle Comm Links
^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/comm-links``


|query_param|

=========  =======      =======================================================================================================================  ==============  ========  ========  ========
Parameter  Typ          Beschreibung                                                                                                             Erlaubte Werte  Optional  Beispiel  Standard
=========  =======      =======================================================================================================================  ==============  ========  ========  ========
page       integer      Seite der Ausgabe. Anzahl der Seiten sowie derzeitige Seite stehen in den Metadaten der Ausgabe                                          Ja        1         1
limit      integer      Limitiert die Anzahl der Daten auf die angegebene Zahl. Ein Limit von '0' deaktiviert das Limit und gibt alle Daten aus                  Ja        1         10
include    string       Komma separierter String mit Namen der hinzuzufügenden Relationen                                                        images links    Ja        images
=========  =======      =======================================================================================================================  ==============  ========  ========  ========


.. code-block:: json
    :caption: |caption_response_no_query_params|

    {
      "data": [
        {
          "id": 12705,
          "title": "2610: Tears of Fire",
          "rsi_url": "https:\/\/robertsspaceindustries.com\/comm-link\/spectrum-dispatch\/12705-2610-Tears-Of-Fire",
          "api_url": "https:\/\/api.star-citizen.wiki\/api\/comm-links\/12705",
          "channel": "Lore",
          "category": "Spectrum Dispatch",
          "series": "Time Capsule",
          "images": 2,
          "links": 0,
          "created_at": "2012-09-28"
        },
        {
          "id": "...",
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 4500,
          "count": 15,
          "per_page": 15,
          "current_page": 1,
          "total_pages":400,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/comm-links?page=2"
          }
        }
      }
    }


|api_endpoint| ``/api/comm-links?limit=1``

.. code-block:: json
    :caption: Ausgabe der Anfrage mit Limit Parameter = 1:

    {
      "data": [
        {
          "id": 12705,
          "title": "2610: Tears of Fire",
          "rsi_url": "https:\/\/robertsspaceindustries.com\/comm-link\/spectrum-dispatch\/12705-2610-Tears-Of-Fire",
          "api_url": "https:\/\/api.star-citizen.wiki\/api\/comm-links\/12705",
          "channel": "Lore",
          "category": "Spectrum Dispatch",
          "series": "Time Capsule",
          "images": 2,
          "links": 0,
          "created_at": "2012-09-28"
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "pagination": {
          "total": 4500,
          "count": 1,
          "per_page": 1,
          "current_page": 1,
          "total_pages": 4500,
          "links": {
            "next": "https:\/\/api.star-citizen.wiki\/api\/comm-links?page=2"
          }
        }
      }
    }


|api_endpoint| ``/api/comm-links?include=images``

.. code-block:: json
    :caption: Ausgabe mit der Relation Bilder:

    {
      "data": [
        {
          "id": 13771,
          "title": "Star Citizen raises astronomical $40m",
          "rsi_url": "https:\/\/robertsspaceindustries.com\/comm-link\/SCW\/13771-API",
          "api_url": "https:\/\/api.star-citizen.wiki\/api\/comm-links\/13771",
          "channel": "Undefined",
          "category": "Press",
          "series": "None",
          "images": {
            "data": [
              {
                "rsi_url": "https:\/\/robertsspaceindustries.com\/media\/ry9g91yedn3atr\/source\/10_For_The_Chairman_Embed_6.png",
                "api_url": "https:\/\/api.star-citizen.wiki\/storage\/comm_link_images\/ry9g91yedn3atr\/10_For_The_Chairman_Embed_6.png",
                "alt": "#post-background"
              }
            ]
          },
          "links": 0,
          "created_at": "2014-03-11"
        },
        {
          "id": "...",
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "images",
          "links"
        ]
      }
    }


|api_endpoint| ``/api/comm-links?include=images,links``

.. code-block:: json
    :caption: Ausgabe mit der Relation Bilder und Links:

    {
      "data": [
        {
          "id": 13475,
          "title": "Concept Art: Geddon System",
          "rsi_url": "https:\/\/robertsspaceindustries.com\/comm-link\/engineering\/13475-Concept-Art-Geddon-System",
          "api_url": "https:\/\/api.star-citizen.wiki\/api\/comm-links\/13475",
          "channel": "Development",
          "category": "Engineering",
          "series": "None",
          "images": {
            "data": [
              {
                "rsi_url": "https:\/\/robertsspaceindustries.com\/media\/xgsjydn4r5dcdr\/source\/Geddon-TatKo03low_thumb.jpg",
                "api_url": null,
                "alt": ""
              }
            ]
          },
          "links": {
            "data": [
              {
                "href": "https:\/\/robertsspaceindustries.com\/comm-link\/transmission\/12788-Unlocks-Geddon-System",
                "text": "post"
              }
            ]
          },
          "created_at": "2014-01-13"
        },
        {
          "id": "...",
        }
      ],
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "images",
          "links"
        ]
      }
    }


Einzelner Comm Link
^^^^^^^^^^^^^^^^^^^
|get|

|api_endpoint| ``/api/comm-links/{CommLinkID}``

.. code-block:: json
    :caption: |caption_response|

    {
      "data": {
        "id": 12663,
        "title": "Welcome to the Comm-Link!",
        "rsi_url": "https:\/\/robertsspaceindustries.com\/comm-link\/transmission\/12663-Welcome-To-The-Comm-Link",
        "api_url": "https:\/\/api.star-citizen.wiki\/api\/comm-links\/12663",
        "channel": "General",
        "category": "Transmission",
        "series": "None",
        "images": {
          "data": [
            {
              "rsi_url": "https:\/\/robertsspaceindustries.com\/media\/bluo97w6u7n1ur\/source\/Starshipbridge.jpg",
              "api_url": "https:\/\/api.star-citizen.wiki\/storage\/comm_link_images\/bluo97w6u7n1ur\/Starshipbridge.jpg",
              "alt": ""
            }
          ]
        },
        "links": {
          "data": [
            {
              "href": "http:\/\/robertsspaceindustries.com\/forums\/",
              "text": "forums"
            }
          ]
        },
        "created_at": "2012-09-05"
      }
      "meta": {
        "processed_at": "2018-08-01 00:00:00",
        "valid_relations": [
          "images",
          "links"
        ]
      }
    }






.. |get| replace:: **Anfragetyp**: ``GET``
.. |post| replace:: **Anfragetyp**: ``POST``

.. |url_param| replace:: **URL Parameter**:
.. |query_param| replace:: **Query Parameter**:

.. |api_endpoint| replace:: **API Anfragepunkt**:

.. |caption_response| replace:: Ausgabe der Anfrage:
.. |caption_response_no_query_params| replace:: Ausgabe der Anfrage ohne Query Parameter:
.. |caption_response_german_localisation| replace:: Ausgabe der Anfrage mit deutschen Übersetzungen:
.. |caption_response_404| replace:: Ausgabe einer fehlerhaften Anfrage