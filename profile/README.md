## Sign Master

## About This Project
Sign Master is an innovative application designed to support the deaf and mute community, their families, and close connections. It addresses key challenges such as the limited resources and limited communication opportunities. By leveraging AI-powered tools for gesture recognition and interactive learning modules, Sign Master enables smooth conversations between deaf individuals and their loved ones, fostering stronger bonds and breaking communication barriers. This ensures the community feels empowered, supported, and included.

The app also caters to two additional groups: individuals learning sign language for personal growth and professionals such as educators or customer service representatives who need it for their careers. With structured modules, gamified quizzes, and certifications, Sign Master makes the learning process engaging and effective. By bridging communication gaps and promoting inclusivity, the app helps foster societal understanding and respect for the deaf community.

## Team Member C242-PS363
<div align="center">

| Bangkit ID | Name | Learning Path | LinkedIn Profile | Status |
|:----------:|------|:------------:|:-------|------------------|
| M008B4KY2566 | Mohammad Fajar Maulid | Machine Learning | [LinkedIn](https://www.linkedin.com/in/fajar-maulid-2665b81b1/) | Active |
| M008B4KY2883 | Muhammad Hariish Hafiiz | Machine Learning | [LinkedIn](https://www.linkedin.com/in/muhammad-hariish-hafiiz-84b15b2a5/) | Active |
| M008B4KY4525 | Yazid Rizki Kurniawan | Machine Learning | [LinkedIn](https://www.linkedin.com/in/yazid-rizki-kurniawan-521237154/) | Active |
| C008B4KY1542 | Fitriansyah Eka Putra | Cloud Computing | [LinkedIn](https://www.linkedin.com/in/fitriansyah-eka-putra-417049199/) | Active |
| C008B4KY3671 | Rakyan Pangrukti Wibana | Cloud Computing | [LinkedIn](https://www.linkedin.com/in/rakyanwibana/) | Active |
| A529B4KY0766 | Aziz Nur Ashidiq | Mobile Development | [LinkedIn](https://www.linkedin.com/in/aziz-nur-ashidiq-466b39218/) | Active |
| A529B4KY2683 | Muhammad Adira Zaidan Putra Pratama | Mobile Development | [LinkedIn](https://www.linkedin.com/in/adira-zaidan-b457082b5/) | Active |

</div>

 ## Project Architecture 
```mermaid
graph LR
    subgraph "Development Environment"
        ML[ML Engineer Workstation]
    end

    subgraph "Google Cloud Platform"
        subgraph "Storage"
            GCS[("Google Cloud Storage")]
            subgraph "Buckets"
                Dataset[bucket-asl-data]
                Model[bucket-tomotion]
                ImageBucket[bucket-news-image]
            end
        end

        subgraph "Database"
            SQL["PostgreSQL"]
        end

        subgraph "Services"
            CR1["Cloud Run<br/>Auth Service"]
            CR2["Cloud Run<br/>Inference Service"]
            CR3["Cloud Run<br/>Material and Quiz Service"]
            CR6["Cloud Run<br/>Text to Motion Service"]
            CR7["Cloud Run<br/>News Service"]
            CR8["Cloud Run<br/>Certificate Generator"]
        end
    end

    subgraph "Client Applications"
        Mobile["Mobile App"]
    end

    %% Development Flow
    ML -->|"Upload Dataset"| Dataset
    
    %% Model & Dataset Access
    Dataset -->|"Access material and quiz data"| CR3
    Dataset -->|"Access motion data"| CR6
    ImageBucket -->|"Access news image"| CR7
    CR6 -->|"Store Generated motion"| Dataset
    Model --> |"Store Generated Certificates"| CR8

    %% Database Connections
    CR1 -->|"DB Operations"| SQL
    CR3 -->|"DB Operations"| SQL
    CR6 -->|"DB Operations"| SQL
    CR7 -->|"DB Operations"| SQL

    %% Service Communications
    CR1 -->|"Token Validation"| CR3

    %% Client Communications
    Mobile -->|"HTTPS API Calls"| CR1
    Mobile -->|"HTTPS API Calls"| CR2
    Mobile -->|"HTTPS API Calls"| CR3
    Mobile -->|"HTTPS API Calls"| CR6
    Mobile -->|"HTTPS API Calls"| CR7
    CR3 -->|"Generates Certificate"| CR8

    classDef gcpService fill:#4285f4,stroke:#1a73e8,color:white;
    classDef storage fill:#fad2d2,stroke:#e06666;
    classDef client fill:#fff,stroke:#333;
    classDef bucket fill:#ffe6cc,stroke:#d79b00;
    classDef database fill:#67AB9F,stroke:#008975,color:white;

    class GCS storage;
    class Dataset,Model,ImageBucket,NewsBucket bucket;
    class CR1,CR2,CR3,CR6,CR7,CR8 gcpService;
    class Mobile client;
    class SQL database;
```

## Machine Learning
TODO

## Cloud Computing
[Inference Service](https://github.com/Bangkit-Capstone-Project-C242-PS363/service-toMotion.git)

[Auth Service](https://github.com/Bangkit-Capstone-Project-C242-PS363/service-auth.git)

[Material and Quiz Service](https://github.com/Bangkit-Capstone-Project-C242-PS363/service-material-quiz)

[Text to Motion Service](https://github.com/Bangkit-Capstone-Project-C242-PS363/service-toMotion.git)

[News Service](https://github.com/Bangkit-Capstone-Project-C242-PS363/service-news)


## Mobile Development
TODO
