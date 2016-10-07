# jwt-explained

Le Json Web Token est un mécanisme qui permet d'échanger

# L'anatomie d'un token

Un token JWT est une enveloppe qui se compose de 3 parties. 

Un header qui contient les informations techniques relative à la vérification de l'authenticité de celui-ci. Le body qui contient les données que vous souhaitez transférer, et la partie de signature qui permet de vérifier que les données contenues sont conformes à celles générées par le serveur.

Il faut bien comprendre qu'un token dont on ne ferait qu'utiliser les données du body sans vérifier que la signature est valide, ne présenterai AUCUN interet en terme de sécurité.

# alg

L'alghoritme de signature utilisé par l'émetteur

# jku

Json Key Url qui pointe vers une Json Web Key, TLS obligatoire

    {"jwk":
      [
        {"alg":"EC",
         "crv":"P-256",
         "x":"MKBCTNIcKUSDii11ySs3526iDZ8AiTo7Tu6KPAqv7D4",
         "y":"4Etl6SRW2YiLUrN5vfvVHuhp7x8PxltmWWlbbM4IFyM",
         "use":"enc",
         "kid":"1"},

        {"alg":"RSA",
         "mod": "0vx7agoebGcQSuuPiLJXZptN9nndrQmbXEps2aiAFbWhM78LhWx
    4cbbfAAtVT86zwu1RK7aPFFxuhDR1L6tSoc_BJECPebWKRXjBZCiFV4n3oknjhMs
    tn64tZ_2W-5JsGY4Hc5n9yBXArwl93lqt7_RN5w6Cf0h4QyQ5v-65YGjQR0_FDW2
    QvzqY368QQMicAtaSqzs8KJZgnYb9c7d0zgdAZHzu6qMQvRL5hajrn1n91CbOpbI
    SD08qNLyrdkt-bFTWhAI4vMQFh6WeZu0fM4lFd2NcRwr3XPksINHaQ-G_xBniIqb
    w0Ls1jF44-csFCur-kEgU8awapJzKnqDKgw",
         "exp":"AQAB",
         "kid":"2011-04-29"}
      ]
    }

# jwk

La Json Web Key directement inliné dans le message

# kid

Key Identifier est le nom de la clé qui a servi a signer. 

# x5u

L'url pour récupérer la clé publique du certificat X509 qui a servi à générer la signture, TLS obligatoire

# x5c

La chaine de certificat. Le 1er est le certificat qui a signé, les suivants sont ceux qui permettent de valider le certificat de signature

# x5t

Le thumbprint +/- hash du  certificat x509 utilisé pour signé (sha1)

# x5t#S256

idem mais avec sha256

# typ

Content type

JWT: plain json
JOSE Compact

# cty

content type, hum...

JWS Signature
JWE Encrypt

# crit

Claims a valider impérativement

ex: 

     {"alg":"ES256",
      "crit":["exp"],
      "exp":1363284000
     }
