# Project Structure
```
├── src/ 
│ ├── routes/
│ │ ├── pets.routes.js
│ │ ├── clinics.routes.js
│ │ └── articles.routes.js
│ ├── middlewares/
│ │ └── validation.middleware.js
│ ├── controllers/
│ │ ├── pets.controller.js
│ │ ├── clinics.controller.js
│ │ └── articles.controller.js
│ ├── data/
│ │ ├── petsData.js
│ │ ├── clinicsData.js
│ │ └── articlesData.js
│ ├── helpers/
│ ├── app.js
│ └── server.js
├── .env
├── .gitignore
└── package.json
```
--------------------------------------------------------------------------------------------

# Libraries

Express.js, dotenv, morgan, nodemon
--------------------------------------------------------------------------------------------

# Random Pets Data
```
Pets = [
    {
      "id": 1,
      "name": "max",
      "type": "dog",
      "age": 3,
      "location": "Roma",
      "image": "dog.png",
      "description": ".......",
      available: true
    },
    {
      "id": 2,
      "name": "sona",
      "type": "cat",
      "age": 2,
      "location": "Milano",
      "image": "cat.png",
      "description": ".......",
      available: true
    },
    {
      "id": 3,
      "name": "bobby",
      "type": "dog",
      "age": 4,
      "location": "Paris",
      "image": "dog.png",
      "description": ".......",
      available: false
    }
  ]
```
--------------------------------------------------------------------------------------------

# Random clinics Data
```
clinics = [
    {
      "id": 1,
      "name": "Emergency Vet Clinic"
      "location": "Roma",
      "isOpen": true,
      "emergencyServices": yes,
      "rating": 5 stars,
      "phoneNumber": 732687293 
    },
    {
      "id": 2,
      "name": "EVC"
      "location": "Milano",
      "isOpen": true,
      "emergencyServices": False,
      "rating": 4 stars,
      "phoneNumber": 8237941836
    }
  ]
```
--------------------------------------------------------------------------------------------

# Random Articles Data
```
articles = [
  {
    "id": 1,
    "title": "Top 5 Tips for Caring for Your Indoor Cat",
    "content": "Here are some essential tips to keep your cat happy and healthy",
    "petType": "cat",
    "category": "care",
    "author": "Dr. Sarah Ahmed",
    "datePublished": "2023-10-26T14:30:00Z",
    "image": "cat_care_tips.jpg"
  },
  {
    "id": 2,
    "title": "Puppy Training: A Beginner's Guide",
    "content": "Learn how to train your puppy in obedience and basic skills...",
    "petType": "dog",
    "category": "training",
    "author": "The Experts Team",
    "datePublished": "2023-10-20T10:00:00Z",
    "image": "puppy_training.jpg"
  },
  {
    "id": 3,
    "title": "How to Choose the Best Food for Your Cat",
    "content": "Tips on choosing the right food for your cat to maintain their health...",
    "petType": "cat",
    "category": "nutrition",
    "author": "Dr. Ali Hassan",
    "datePublished": "2023-10-15T16:00:00Z",
    "image": "cat_food_tips.jpg"
  },
  {
    "id": 4,
    "title": "Caring for Your Dog's Dental Health",
    "content": "The importance of cleaning your dog's teeth and preventing gum disease...",
    "petType": "dog",
    "category": "health",
    "author": "Dr. Layla Mahmoud",
    "datePublished": "2023-10-10T11:00:00Z",
    "image": "dog_dental_care.jpg"
  }
]
```
--------------------------------------------------------------------------------------------

# Searching Available Pets
```
├── Users need to see a list of available pets
├── Results should be filterable by city
└── Complete information about each pet should be displayed
```

* in available key we use the value for show/hide the adoption button. if the value is true; the btn appears and the pet is available for adoption. otherwise; it's not available 

Get All pets:

* if there is data:
```
- Get: '/api/pets'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "type": string,
      "location": string
    }
  ]
}
```
ex: 
```
- Get: '/api/pets'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "max",
      "type": "dog",
      "location": "Roma"
    },
    {
      "name": "sona",
      "type": "cat",
      "location": "Milano"
    },
    {
      "name": "bobby",
      "type": "dog",
      "location": "Paris"
    }
  ]
}
```
--------------------------------------------------------------------------------------------

* if there is no data:
```
- Get: '/api/pets'
- response: {
  message: "get successfully",
  data: null | There isn't any data
}
```
--------------------------------------------------------------------------------------------

Get one pet:
* if there is data:
```
- Get: '/api/pets/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "type": string,
      "age": numder,
      "location": string,
      "image": string,
      "description": "......."
    }
  ]
}
```
ex: 
```
- Get: '/api/pets/2'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "sona",
      "type": "cat",
      "age": 2,
      "location": "Milano",
      "image": "cat.png",
      "description": "......."
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Get All available pets:

* if there is data:
```
- Get: '/api/pets/available'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "type": string,
      "location": string
    }
  ]
}
```
ex: 
```
- Get: '/api/pets/available'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "max",
      "type": "dog",
      "location": "Roma"
    },
    {
      "name": "sona",
      "type": "cat",
      "location": "Milano"
    }
  ]
}
```
--------------------------------------------------------------------------------------------

* if there is no data:
```
- Get: '/api/pets/available'
- response: {
  message: "get successfully",
  data: null | There isn't any available pet
}
```
--------------------------------------------------------------------------------------------

Get one available pet:
* if there is data:
```
- Get: '/api/pets/available/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "type": string,
      "age": numder,
      "location": string,
      "image": string,
      "description": "......."
    }
  ]
}
```
ex: 
```
- Get: '/api/pets/available/2'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "sona",
      "type": "cat",
      "age": 2,
      "location": "Milano",
      "image": "cat.png",
      "description": "......."
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on pets by city & type:

* if there is data:
```
- Get: '/api/pets?city={city}&type={animal_type}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "type": string,
      "location": string
    }
  ]
}
```
ex: 
```
- Get: '/api/pets?city=Roma&type=dog'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "max",
      "type": "dog",
      "location": "Roma"
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on pets by city & type with id:

* if there is data:
```
- Get: '/api/pets?city={city}&type={animal_type}/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "type": string,
      "age": numder,
      "location": string,
      "image": string,
      "description": "......."
    }
  ]
}
```
ex: 
```
- Get: '/api/pets?city=Roma&type=dog/1'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "max",
      "type": "dog",
      "age": 3,
      "location": "Roma",
      "image": "dog.png",
      "description": "......."
    }
  ]
}
```
--------------------------------------------------------------------------------------------

* Pets API Errors
```
├── Attempting to display pets in a non-existent id
├── Attempting to display available pets in a non-existent id
├── Attempting to display pets in a non-existent city or type
└── Attempting to display pets in a non-existent city or type by id
```
```
- Get: '/api/pets?city={city}&type={animal_type}'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value
}
```
ex: 
```
- Get: '/api/pets?city=Roma&type=cat'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/pets?city={city}&type={animal_type}/{id}'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value
}
```
ex: 
```
- Get: '/api/pets?city=Roma&type=dog/8'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value 
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/pets/{id}'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value
}
```
ex: 
```
- Get: '/api/pets/4'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/pets/available/{id}'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value
}
```
ex: 
```
- Get: '/api/pets/available/4'
- response: {
  message: "failed",
  data: 404 | No pets fits with the search value
}
```
--------------------------------------------------------------------------------------------

# Finding Veterinary Clinics
```
├── Clinics near the user's location should be shown
├── Emergency status should be supported
└── Contact information and ratings should be displayed
```

Get All Clinics:

* if there is data:
```
- Get: '/api/clinics'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "location": string,
      "isOpen": boolean,
      "phoneNumber": number
    }
  ]
}
```
ex: 
```
- Get:'/api/clinics'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "Emergency Vet Clinic"
      "location": "Roma",
      "isOpen": true,
    },
    {
      "name": "EVC"
      "location": "Milano",
      "isOpen": true,
    }
  ]
}
```
--------------------------------------------------------------------------------------------

* if there is no data:
```
- Get: '/api/clinics'
- response: {
  message: "get successfully",
  data: null | There isn't any data
}
```
--------------------------------------------------------------------------------------------

Get one clinic:
* if there is data:
```
- Get: '/api/clinics/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "location": string,
      "isOpen": boolean,
      "emergencyServices": boolean,
      "rating": string,
      "phoneNumber": number
    }
  ]
}
```
ex: 
```
- Get:'/api/clinics/1'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "Emergency Vet Clinic"
      "location": "Roma",
      "isOpen": true,
      "emergencyServices": true,
      "rating": 5 stars,
      "phoneNumber": 732687293
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on clinics by city:

* if there is data:
```
- Get: '/api/clinics?city={city}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "location": string,
      "isOpen": boolean,
      "emergencyServices": boolean,
      "rating": string,
      "phoneNumber": number
    }
  ]
}
```
ex: 
```
- Get: '/api/clinics?city=Roma'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "Emergency Vet Clinic"
      "location": "Roma",
      "isOpen": true,
      "emergencyServices": true,
      "rating": 5 stars,
      "phoneNumber": 732687293
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on clinics by city with id:

* if there is data:
```
- Get: '/api/clinics?city={city}/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "location": string,
      "isOpen": boolean,
      "emergencyServices": boolean,
      "rating": string
    }
  ]
}
```
ex: 
```
- Get: '/api/clinics?city=Roma/1'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "Emergency Vet Clinic"
      "location": "Roma",
      "isOpen": true,
      "emergencyServices": true,
      "rating": 5 stars,
      "phoneNumber": 732687293
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on emergency clinics by city:

* if there is data:
```
- Get: '/api/clinics?emergency=true&isOpenNow=true&city={city}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "location": string,
      "isOpen": boolean,
      "emergencyServices": boolean,
      "rating": string,
      "phoneNumber": number
    }
  ]
}
```
ex: 
```
- Get:'/api/clinics?emergency=true&isOpenNow=true&city=Roma'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "Emergency Vet Clinic"
      "location": "Roma",
      "isOpen": true,
      "emergencyServices": true,
      "rating": 5 stars,
      "phoneNumber": 732687293
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on emergency clinics by city with id:

* if there is data:
```
- Get: '/api/clinics?emergency=true&isOpenNow=true&city={city}/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "name": string,
      "location": string,
      "isOpen": boolean,
      "emergencyServices": boolean,
      "rating": string,
      "phoneNumber": number
    }
  ]
}
```
ex: 
```
- Get: '/api/clinics?emergency=true&isOpenNow=true&city=Roma/1'
- response: {
  message: "get successfully",
  data: [
    {
      "name": "Emergency Vet Clinic"
      "location": "Roma",
      "isOpen": true,
      "emergencyServices": true,
      "rating": 5 stars
    }
  ]
}
```
--------------------------------------------------------------------------------------------

* Clinics API Errors
```
├── Attempting to display clinics in a non-existent id
├── Attempting to display clinics in a non-existent emergency clinics in the city
└── Attempting to display clinics in a non-existent city
```
```
- Get: '/api/clinics?city={city}'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
ex: 
```
- Get: '/api/clinics?city=latakia'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/clinics?city={city}/{id}'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
ex: 
```
- Get:'/api/clinics?city=Roma/8'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/clinics?emergency=true&isOpenNow=true&city={city}'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
ex: 
```
- Get: '/api/clinics?emergency=true&isOpenNow=true&city=Milano'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/clinics?emergency=true&isOpenNow=true&city={city}/{id}'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
ex: 
```
- Get: '/api/clinics?emergency=true&isOpenNow=true&city=Roma/99'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/clinics/{id}'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```
ex: 
```
- Get: '/api/clinics/6'
- response: {
  message: "failed",
  data: 404 | No clinics fits with the search value
}
```

** also we can use lan & lng instead of city **
--------------------------------------------------------------------------------------------

# Reading Articles
```
├── Content should be organized by animal type
├── Search and filtering should be supported
└── Details of each article should be displayed
```

Get All Articles:

* if there is data:
```
- Get: '/api/articles'
- response: {
  message: "get successfully",
  data: [
    {
      "title": string,
      "petType": string,
      "author": string,
      "image": string
    }
  ]
}
```
ex: 
```
- Get: '/api/articles'
- response: {
  message: "get successfully",
  data: [
      {
      "title": "Top 5 Tips for Caring for Your Indoor Cat",
      "petType": "cat",
      "author": "Dr. Sarah Ahmed",
      "image": "cat_care_tips.jpg"
    },
    {
      "title": "Puppy Training: A Beginner's Guide",
      "petType": "dog",
      "author": "The Experts Team",
      "image": "puppy_training.jpg"
    },
    {
      "title": "How to Choose the Best Food for Your Cat",
      "petType": "cat",
      "author": "Dr. Ali Hassan",
      "image": "cat_food_tips.jpg"
    },
    {
      "title": "Caring for Your Dog's Dental Health",
      "petType": "dog",
      "author": "Dr. Layla Mahmoud",
      "image": "dog_dental_care.jpg"
    }
  ]
}
```
--------------------------------------------------------------------------------------------

* if there is no data:
```
- Get: '/api/articles'
- response: {
  message: "get successfully",
  data: null | There isn't any data
}
```
--------------------------------------------------------------------------------------------

Get one article:
* if there is data:
```
- Get: '/api/articles/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "title": string,
      "content": string
      "petType": string,
      "category": string,
      "author": string,
      "datePublished": date
      "image": string
    }
  ]
}
```
ex: 
```
- Get:'/api/articles/4'
- response: {
  message: "get successfully",
  data: [
    {
      "title": "Caring for Your Dog's Dental Health",
      "content": "The importance of cleaning your dog's teeth and preventing gum disease...",
      "petType": "dog",
      "category": "health",
      "author": "Dr. Layla Mahmoud",
      "datePublished": "2023-10-10T11:00:00Z",
      "image": "dog_dental_care.jpg"
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on articles by petType:

* if there is data:
```
- Get: '/api/articles?petType={animal_type}'
- response: {
  message: "get successfully",
  data: [
    {
      "title": string,
      "petType": string,
      "author": string,
      "image": string
    }
  ]
}
```
ex: 
```
- Get: '/api/articles?petType=dog'
- response: {
  message: "get successfully",
  data: [
    {
      "title": "Puppy Training: A Beginner's Guide",
      "petType": "dog",
      "author": "The Experts Team",
      "image": "puppy_training.jpg"
    },
    {
      "title": "Caring for Your Dog's Dental Health",
      "petType": "dog",
      "author": "Dr. Layla Mahmoud",
      "image": "dog_dental_care.jpg"
    }
  ]
}
```
--------------------------------------------------------------------------------------------

Search on pets by petType with id:

* if there is data:
```
- Get: '/api/articles?petType={animal_type}/{id}'
- response: {
  message: "get successfully",
  data: [
    {
      "title": string,
      "content": string
      "petType": string,
      "category": string,
      "author": string,
      "datePublished": date
      "image": string
    }
  ]
}
```
ex: 
```
- Get: '/api/articles?petType=dog/2'
- response: {
  message: "get successfully",
  data: [
    {
      "title": "Puppy Training: A Beginner's Guide",
      "content": "Learn how to train your puppy in obedience and basic skills...",
      "petType": "dog",
      "category": "training",
      "author": "The Experts Team",
      "datePublished": "2023-10-20T10:00:00Z",
      "image": "puppy_training.jpg"
    }
  ]
}
```
--------------------------------------------------------------------------------------------

* articles API Errors
```
├── Attempting to display articles in a non-existent id
├── Attempting to display articles in a non-existent type
└── Attempting to display articles in a non-existent type by id
```
```
- Get: '/api/articles?petType={animal_type}'
- response: {
  message: "failed",
  data: 404 | No articles fits with the search value
}
```
ex: 
```
- Get: '/api/articles?city=Roma&type=cat'
- response: {
  message: "failed",
  data: 404 | No articles fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/articles?petType={animal_type}/{id}'
- response: {
  message: "failed",
  data: 404 | No articles fits with the search value
}
```
ex: 
```
- Get: '/api/articles?petType=dog/8'
- response: {
  message: "failed",
  data: 404 | No articles fits with the search value
}
```
--------------------------------------------------------------------------------------------
```
- Get: '/api/articles/{id}'
- response: {
  message: "failed",
  data: 404 | No articles fits with the search value
}
```
ex: 
```
- Get: '/api/articles/8'
- response: {
  message: "failed",
  data: 404 | No articles fits with the search value
}
```
--------------------------------------------------------------------------------------------
