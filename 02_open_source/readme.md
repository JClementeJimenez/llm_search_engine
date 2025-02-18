# Introduction to open source llm usage:

* I'm going to do it in a detached way, without a proper gpu since i cannot connect to google collab and i dont want to use saturn cloud or vm's in gcp

## HUGGING FACE AND GOOGLE FLAN

* ```Import model from HF hub```

* ```pip install -U transformers accelerate bitsand```

* In the example they use google flan t5 xl. There are examples to use it on CPU. 
    * the tokenizer transforms the text into tokens that the generator uses, thats the model
    * It downloads the files from HF. If there is no room, we have to set the HF_HOME env variable to point out to a location
    * send tokens and process to cuda
    * after using everything we can send it to the class that we had

* phi3 from microsoft:
    * more similar to openai interface of use

* Mistral 7B from HF
    * it uses the generic example from HF. it uses parameters from the transformers library from HF
    * Some models need to accept certain conditions and add a token to acces to models:
        ```
        from huggingface_hub import login 
        login(token = ...)
        ```
    * [LLM tutorial from HF](https://huggingface.co/docs/transformers/en/llm_tutorial)
    * It is a completetion model, so it doesn't like large model. using a pipeline to group generator and tokenizer
    * Looking for model in the leadebords from HF. 7B or 8B to run in open gpu's.

## Ollama and CPU run

* Ollama is an opensource library that allows to run models without gpu locally. For models that are supported by ollama check repo
* We can use it as a drop in replacement for a api, like open ai. it supports mistral
* ollama puts the models where it can be modifyed in the .ollama folder
* Example of use:
        Aqui puedo modificar la URL a la que apunta el codigo, en lugar de a la de mistral api, a la del puerto desde el que se puede acceder a ollama. No necesitaria una key porque mi puerto esta abierto sino que tendria que apuntar a la aplicacion ollama para que se ejecute. luego podria pedirle un modelo de ollama, en este caso podria usar mistral 7b en lugar de mistral small latest.


        1. hay que hacer ollama serve para que se habra la url 
        2. luego hay que hacer ollama pull para que descargue el modelo
        3. a partir de ahi se pude usar
* we can run it also in docker
    ```
    docker run -it \
    -v ollama:/root/.ollama \
    -p 11434:11434 \
    --name ollama \
    ollama/ollama

    docker exec -it ollama bash
    ollama pull phi3
    ```

* or with a python client [(ollama py github)](https://github.com/ollama/ollama-python)

* docker compose to use a docker with elastic search and ollama in another docker

