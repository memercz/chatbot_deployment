# Thesis Chatbot Deployment Guide

## Installation Guide

**1. Install Python**

   - Install Python version 3.8
```   
python -m pip uninstall pip
```

<br>

```
python -m ensurepip
```

<br>

```
python -m pip install -U pip
```



**2. Install Rasa**
```
pip install rasa
```


**3. Install Dependencies for spaCy**
```
pip3 install 'rasa[spacy]'
```
```
python3 -m spacy download en_core_web_md
```


**4. Install Dependencies for Transformer**
```
pip3 install "rasa[transformers]"
```

**5. Optional: Install All Additional Dependencies**

If some dependencies are not met when running Rasa:
```
pip3 install 'rasa[full]'
```


## Running the chatbot (Rasa) Guide

**1. Copy the files from the GitHub link.**

**2. Make sure the directory is within that file.**

**3. In the terminal, run:**

```
rasa train --domain data/domain --data data/nlu data/stories --config myInitialconfig.yml
```

A model with its path will be created when the training is done. <br>
Example model path: `models\20240507-113555-immense-distance.tar.gz`.

Sample image:
![image](https://github.com/memercz/chatbot_deployment/assets/161113570/b1c0f114-fd46-430e-832c-2ce086acf586)



**4. Next, run the following command in the terminal:**

```
rasa run --enable-api --cors "*" --debug --endpoints endpoints.yml -m [path of the model] -p 6006
```
Sample command:
```
rasa run --enable-api --cors "*" --debug --endpoints endpoints.yml -m models\20240507-113555-immense-distance.tar.gz -p 6006
```

Here, `p` is the port of the REST/webhook where Rasa can connect.

**5. Additionally, in `index.html`, on line 176, change the port as needed**<br>

![image](https://github.com/memercz/chatbot_deployment/assets/161113570/21f3987f-bffc-4269-9e2d-0bfe3195b24d)


**6. To open Rasa in the local server, you can choose either of the following options:**

**- Option 1:**

   On new terminal, type:

  ```
  python -m http.server 8000
  ```

  Then open `localhost:8000` in your browser.

**- Option 2:**

  Copy the path of `index.html`.

.
