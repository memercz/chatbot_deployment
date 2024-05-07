# chatbot_deployment

# How to install

**Install python**
  install python == 3.8
  
  python -m pip uninstall pip
  python -m ensurepip
  python -m pip install -U pip

**Install rasa**
  pip install rasa

**Install dependencies for spaCy**
  pip3 install 'rasa[spacy]'
  python3 -m spacy download en_core_web_md

**Install dependencies for transformer**
  pip3 install "rasa[transformers]"

**Optional. For additional dependencies (if some dependencies are note met when running rasa)**
  pip3 install 'rasa[full]'

**Running rasa**

1. Copy the files in the github link:
2. Make sure the directory is within that file
3. in the terminal:
    rasa train --domain data/domain --data data/nlu data/stories --config myInitialconfig.yml
4. A model with its path are created when done training the model. Example of model with its path:
   models\20240507-113555-immense-distance.tar.gz
   
6. Next step is to run this in the terminal:
    rasa run --enable-api --cors "*" --debug --endpoints endpoints.yml -m [path of the model] -p 6006
 Where p is the port of the rest/webhook the rasa can conenct
8. What i do to open the rasa in the local server:
   Option 1:
     python -m http.server 8000
   
     Then open localhost:8000
   
   Option 2:
     Copy the path of index.html
9. Moreover in index.html, in line 176
      Change the port kung asa need
  
   
