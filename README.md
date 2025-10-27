![LangChain Academy](https://cdn.prod.website-files.com/65b8cd72835ceeacd4449a53/66e9eba1020525eea7873f96_LCA-big-green%20(2).svg)

## Introduction

Welcome to LangChain Academy, Introduction to LangGraph! 
This is a growing set of modules focused on foundational concepts within the LangChain ecosystem. 
Module 0 is basic setup and Modules 1 - 5 focus on building in LangGraph, progressively adding more advanced themes.  Module 6 addresses deploying your agents. 
In each module folder, you'll see a set of notebooks. A link to the LangChain Academy lesson is at the top of each notebook to guide you through the topic. Each module also has a `studio` subdirectory, with a set of relevant graphs that we will explore using the LangGraph API and Studio.

> 我下一步计划看[官方视频教程--项目：使用 LangGraph 的深度代理](https://academy.langchain.com/courses/take/deep-agents-with-langgraph/lessons/68193153-welcome)

## Setup

### ✅Python version

To get the most out of this course, please ensure you're using Python 3.11 or later. 
This version is required for optimal compatibility with LangGraph. If you're on an older version, 
upgrading will ensure everything runs smoothly.【我的python版本是：Python 3.13.6】
```
python3 --version
```

### ✅Clone repo
```
git clone https://github.com/langchain-ai/langchain-academy.git
$ cd langchain-academy
```
Or, if you prefer, you can download a zip file [here](https://github.com/langchain-ai/langchain-academy/archive/refs/heads/main.zip).

### Create an environment and install dependencies
#### Mac/Linux/WSL
```
$ python3 -m venv lc-academy-env
$ source lc-academy-env/bin/activate
$ pip install -r requirements.txt
```
#### ✅Windows Powershell
```
PS> python3 -m venv lc-academy-env
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
PS> lc-academy-env\scripts\activate
PS> pip install -r requirements.txt
```

### Running notebooks【我用cursor提供的插件，在编辑器中调试】
If you don't have Jupyter set up, follow the installation instructions [here](https://jupyter.org/install).
```
$ jupyter notebook
```

### Setting up env variables
Briefly going over how to set up environment variables. 
#### Mac/Linux/WSL
```
$ export API_ENV_VAR="your-api-key-here"
```
#### Windows Powershell
```
PS> $env:API_ENV_VAR = "your-api-key-here"
```

### Set OpenAI API key
* If you don't have an OpenAI API key, you can sign up [here](https://openai.com/index/openai-api/).
*  Set `OPENAI_API_KEY` in your environment 

### Sign up and Set LangSmith API
* Sign up for LangSmith [here](https://docs.langchain.com/langsmith/create-account-api-key#create-an-account-and-api-key), find out more about LangSmith and how to use it within your workflow [here](https://www.langchain.com/langsmith). 
*  Set `LANGSMITH_API_KEY`, `LANGSMITH_TRACING_V2=true` `LANGSMITH_PROJECT="langchain-academy"`in your environment 
*  If you are on the EU instance also set `LANGSMITH_ENDPOINT`="https://eu.api.smith.langchain.com" as well.

### Set up Tavily API for web search

* Tavily Search API is a search engine optimized for LLMs and RAG, aimed at efficient, 
quick, and persistent search results. 
* You can sign up for an API key [here](https://tavily.com/). 
It's easy to sign up and offers a very generous free tier. Some lessons (in Module 4) will use Tavily. 

* Set `TAVILY_API_KEY` in your environment.

### Set up Studio 完整启动指令
因为你用的是虚拟环境，因此需要在虚拟环境激活后，方可使用全局命令，否则就会出现 “无法将“langgraph”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。”

如果你使用了虚拟环境（如venv等），需要确保已激活该环境，激活后，命令行前缀会显示环境名称（如(lc-academy-env)），此时再尝试运行langgraph dev。
```
cd lc-academy-env\Scripts
.\activate

# 回到主目录，在这个终端中正常执行命令即可
cd ../../
```

```
cd module-1/studio
langgraph dev
```

### Set up Studio

* Studio is a custom IDE for viewing and testing agents.
* Studio can be run locally and opened in your browser on Mac, Windows, and Linux.
* See documentation [here](https://docs.langchain.com/langsmith/studio#local-development-server) on the local Studio development server. 
* Graphs for LangGraph Studio are in the `module-x/studio/` folders for module 1-5.
* To start the local development server, run the following command in your terminal in the `/studio` directory in each module:

```
langgraph dev
```

You should see the following output:
```
- 🚀 API: http://127.0.0.1:2024
- 🎨 Studio UI: https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024
- 📚 API Docs: http://127.0.0.1:2024/docs
```

Open your browser and navigate to the Studio UI: `https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024`.

* To use Studio, you will need to create a .env file with the relevant API keys
* Run this from the command line to create these files for module 1 to 5, as an example:
```
for i in {1..5}; do
  cp module-$i/studio/.env.example module-$i/studio/.env
  echo "OPENAI_API_KEY=\"$OPENAI_API_KEY\"" > module-$i/studio/.env
done
echo "TAVILY_API_KEY=\"$TAVILY_API_KEY\"" >> module-4/studio/.env
```
