!pip install -q langchain langchain-google-genai

import os
from langchain_core.prompts import ChatPromptTemplate
from langchain_google_genai import ChatGoogleGenerativeAI

os.environ["GOOGLE_API_KEY"]="Gemini_API"

#3.Initialize
llm=ChatGoogleGenerativeAI(model="gemini-2.5-flash",temperature=0.7)

#4.define the  prompt
prompt=ChatPromptTemplate.from_messages([
    ("system","you are a senior software architect specializing in AI."),
    ("user","Explain concept of {topic} in exactly two sentences")
])

#5.create langchain
chain = prompt|llm

#6.invoke the chain and print theresult

response=chain.invoke({"topic":"ML"})
print(response.content)
