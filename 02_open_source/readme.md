# Introduction to open source llm usage:

* I'm going to do it in a detached way, without a proper gpu since i cannot connect to google collab and i dont want to use aturn cloud or vm's in gcp

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
    * 


