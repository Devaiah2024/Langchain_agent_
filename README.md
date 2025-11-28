# Langchain_agent_

LangChain Pandas DataFrame Agent

This project demonstrates how to build intelligent agents using LangChain that can interact with one or multiple Pandas DataFrames using natural-language queries. The notebook shows examples of:

Loading and preparing datasets

Cleaning data (e.g., filling missing values)

Creating single- and multi-DataFrame LangChain agents

Asking questions about the data via an LLM (OpenAI)

 Features
 1. Load and Clean Data

The project works with the Titanic dataset and performs operations such as copying a DataFrame and filling missing values:

df1 = df.copy()        # :contentReference[oaicite:0]{index=0}
df1["Age"] = df1["Age"].fillna(df1["Age"].mean())   # :contentReference[oaicite:1]{index=1}

 2. Create a LangChain Agent for a Single DataFrame
llm = OpenAI()     # :contentReference[oaicite:2]{index=2}
agent = create_pandas_dataframe_agent(llm, df, verbose=True)

 3. Multi-DataFrame Agent Support

You can combine multiple DataFrames and let the agent reason across all of them:

agent = create_pandas_dataframe_agent(llm, [df, df1], verbose=True)   # :contentReference[oaicite:3]{index=3}


Later, a third DataFrame (df2) is added:

agent = create_pandas_dataframe_agent(llm, [df, df1, df2], verbose=True)   # :contentReference[oaicite:4]{index=4}



 Requirements

Install dependencies:

pip install langchain openai pandas python-dotenv


Also ensure you set your OpenAI key:

export OPENAI_API_KEY="your_api_key"


(or place it in a .env file)

 How to Run

Open the notebook (Langchain_Agents.html / .ipynb)

Load your datasets into Pandas

Run the cells to:

Clean/prepare data

Initialize the LLM

Create the agent

Ask questions like:

"Which passenger had the highest fare?"
"Show me the average age grouped by class."


The agent will automatically generate the required Pandas code and return results.

 Example Queries
"List passengers older than 50."
"Compare the mean fare between df and df1."
"Show rows where Age > 35."
