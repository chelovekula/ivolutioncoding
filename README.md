
<h1 align="center"><img src="img/logo.png" alt="IVolution Autocompleter"/><p>IVolution Autocompleter</p></h1>



> An autocompleter for code editors based on [OpenAI GPT-2](https://github.com/openai/gpt-2).

### 🏠 [Homepage](https://ivolution.ai/)

**Ivolution** is an auto code completer for code editors (or any text editor) based on [OpenAI GPT-2](https://github.com/openai/gpt-2). It is trained (finetuned) on a curated list of approximately 45K Python (~470MB) files gathered from the Github. Currently, it just works properly on Python but not bad at other languages (thanks to GPT-2's power). 


![Ivolution demo GIF](img/python1.gif)
## Installation

### With Docker

Clone the repository:
```sh
git clone https://github.com/chelovekula/ivolutioncoding
```

Download the latest model from releases and uncompress it into the directory:
```sh
curl -SL https://github.com/chelovekula/ivolutioncoding/releases/latest/download/model.tar.xz | tar -xJC ./ivolutioncoding

```
Install dependencies:
```sh
pip3 install -r requirements.txt
```
P.S.: Be sure that you have tensorflow version >= 1.13

Run the autocompleter:
```sh
python3 main.py
```

## Usage
Currently, there are no extensions for code editors. You can use it through HTTP. When you run the `main.py`, it will serve an HTTP (flask) server. Then you can easily make a POST request to the http://localhost:3030/ with the some `JSON` body like the following:

```sh
{text: "your python code goes here"}
```

An example curl command:

```sh
curl -X POST \
  http://localhost:3030/autocomplete \
  -H 'Content-Type: application/json' \
  -d '{"text":"import os\nimport sys\n# Count lines of codes in the given directory, separated by file extension.\ndef main(directory):\n  line_count = {}\n  for filename in os.listdir(directory):\n    _, ext = os.path.splitext(filename)\n    if ext not"}'
  ```


## Finetuning The Model
Even you can finetune (re-train over) the model with/for your code files. Just follow the `Max Woolf's` [gpt-2-simple](https://github.com/minimaxir/gpt-2-simple) or `Neil Shepperd's` [gpt-2](https://github.com/nshepperd/gpt-2) repositories with **`345M`** version. But don't forget to replace checkpoint (model) with the one in this repository.
