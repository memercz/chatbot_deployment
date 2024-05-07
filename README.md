# Thesis Chatbot Deployment Tutorial

## How to Install

**1. Install Python**

   - Install Python version 3.8
```   
`python -m pip uninstall pip`
```
<br>
```
`python -m ensurepip`
```
<br>
```
`python -m pip install -U pip`
```
<br>


**2. Install Rasa**
```
`pip install rasa`
```


**3. Install Dependencies for spaCy**
```
`pip3 install 'rasa[spacy]'`
```
```
`python3 -m spacy download en_core_web_md`
```


**4. Install Dependencies for Transformer**
```
`pip3 install "rasa[transformers]"`
```

**5. Optional: Install Additional Dependencies**

If some dependencies are not met when running Rasa:
```
`pip3 install 'rasa[full]'`
```


## Running Rasa

**1. Copy the files from the GitHub link.**

**2. Make sure the directory is within that file.**

**3. In the terminal, run:**

```
`rasa train --domain data/domain --data data/nlu data/stories --config myInitialconfig.yml`
```

**A model with its path will be created when the training is done. 
Example model path: `models\20240507-113555-immense-distance.tar.gz`.**

**4. Next, run the following command in the terminal:**

```
`rasa run --enable-api --cors "*" --debug --endpoints endpoints.yml -m [path of the model] -p 6006`
```


Here, `p` is the port of the REST/webhook where Rasa can connect.

**5. To open Rasa in the local server, you can choose either of the following options:**

**- Option 1:**

  ```
  `python -m http.server 8000`
  ```

  Then open `localhost:8000` in your browser.

**- Option 2:**

  Copy the path of `index.html`.

6. Additionally, in `index.html`, on line 176, change the port as needed.
