# Build Your Own Custom Chatbot
In this project, we will implement RAG on a chosen dataset to provide the relevant context to an LLM so that the LLM responses are accurate (as per the dataset) and reflective of the latest developments.

## Project Details
We intend to utilize an LLM for question answering task related to the major events that happened in the year 2023. The LLM selected for this project is OpenAI ['gpt-3.5-turbo-instruct'](https://platform.openai.com/docs/models/gpt-3-5-turbo) but its training data is only up to September 2021 and hence, it is not aware of the 2023 events. To provide this relevant 2023 context to our chosen LLM, we utilize [2023 Wikipedia page](https://en.wikipedia.org/wiki/2023) and we access this data via [Wikipedia API](https://www.mediawiki.org/wiki/API:Main_page). This Wiki page contains brief extracts of most major events that happened in 2023 which makes it highly relevant for our intended purpose. 

The [conda environment file](Chat_RAG.yml) is provided for installing the relevant packages needed to run the [notebook](custom_chatbot.ipynb). A valid [OpenAI API](https://platform.openai.com/) will also be required to run the OpenAI models utilized in the project. 

## Baseline vs Custom comparison
Below we show the comparison of LLM responses with and without performing RAG on relevant data.
```
Q1: How many people were killed in 2023 Hawaii wildfires?

Original Answer: I'm sorry, I cannot answer this question as it is currently the year 2021 and it has not yet reached 2023. Additionally, I do not have access to information about potential future events.
Custom Answer:   At least 101 people were killed in the 2023 Hawaii wildfires.

Q2: When did Tharman become president of Singapore?
Original Answer: Tharman Shanmugaratnam has never been the president of Singapore. He has held various ministerial positions, including Deputy Prime Minister and Minister for Finance, but not the presidency. The current president of Singapore is Halimah Yacob, who has been in office since September 2017.
Custom Answer:   September 1, 2023
```

## Limitations
- The developed custom chatbot does not have a memory element. This can be implemented in a future version via relevant utilities from [LangChain](https://www.langchain.com/]) along with a suitable Vector database.
- The retrieval mechanism is simple because the relevant context for each question is present in a single chunk of data and all the chunks are more or less independent. 
