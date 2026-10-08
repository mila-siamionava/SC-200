Generative AI, and technologies that implement it are increasingly in the public consciousness – even among people who don't work in technology roles or have a background in computer science or machine learning. The futurist and novelist Arthur C. Clarke is quoted as observing that "any sufficiently advanced technology is indistinguishable from magic". In the case of generative AI, it does seem to have an almost miraculous ability to produce human-like original content, including poetry, prose, and even computer code.

However, there's no wizardry involved in generative AI – just the application of mathematical techniques incrementally discovered and refined over many years of research into statistics, data science, and machine learning. You can gain a high-level understanding of how the magic trick is done by learning the core concepts and principles explored in this module. As you learn more about the generative AI technologies we have today, and how it powers a new generation of AI agents; you can help society imagine new possibilities for AI tomorrow.


# Large language models (LLMs)


At the core of generative AI, large language models (LLMs) - and their more compact relations, small language models (SLMs) - encapsulate the linguistic and semantic relationships between the words and phrases in a vocabulary. The model can use these relationships to reason over natural language input and generate meaningful and relevant responses.

Fundamentally, LLMs are trained ==to generate _completions_ based on _prompts_.== Think of them as being super-powerful examples of the predictive text feature on many cellphones. A prompt starts a sequence of text predictions that results in a semantically correct completion. The trick is that the model understands the relationships between words and it can identify which words in the sequence so far are most likely to influence the next one; and use that to predict the most probable continuation of the sequence.

For example, consider the following sentence:

> _I heard a dog bark loudly at a cat_

Now, suppose you only heard the first few words: _"I heard a dog ..."_. You know that some of these words are more helpful clues as to what the next word might be than others. You know that "heard" and "dog" are strong indicators of what comes next, and that helps you narrow down the probabilities. You know that there's a good chance the sentence will continue as _"I heard a dog **bark**"_.

You're able to guess the next word because:

- You have a large vocabulary of words to draw from.
- You've learned common linguistic structures, so you know how words relate to one another in meaningful sentences.
- You have an understanding of semantic concepts associated with words - you know that something you _heard_ must be a sound of some kind, and you know that there are specific sounds that are made by a _dog_.

So how do we train a model to have these same abilities?

## Tokenization

The first step is to provide the model with a large vocabulary of words and phrases; and we do mean _large_. The latest generation of LLMs have vocabularies that consist of hundreds of thousands of tokens, based on large volumes of training data from across the Internet and other sources.

Wait a minute. _Tokens_?

While we tend to think of language in terms of _words_, LLMs break down their vocabulary into _tokens_. ==Tokens== include words, but ==also _sub_-words== (like the "un" in "unbelievable" and "unlikely"), ==punctuation, and other commonly used sequences of characters==. The first step in training a large language model therefore is to break down the training text into its distinct tokens, and assign a unique integer identifier to each one, like this:

- I (1)
- heard (2)
- a (3)
- dog (4)
- bark (5)
- loudly (6)
- at (7)
- a (3) _already assigned_
- cat (8)

and so on.

As you add more training data, more tokens will be added to the vocabulary and assigned identifiers; so you might end up with tokens for words like _puppy_, _skateboard_, _car_, and others.

 Note

In this simple example, we've tokenized the example text based on _words_. In reality there would also be sub-words, punctuation, and other tokens.

## Transforming tokens with a _transformer_

Now that we have a set of tokens with unique IDs, we need to find a way to relate them to one another. To do this, we assign each token a ==_vector_== (an array of multiple numeric values, like [1, 23, 45]). Each vector has multiple numeric _elements_ or _dimensions_, and we can use these to encode linguistic and semantic attributes of the token to help provide a great deal of information about what the token _means_ and how it relates to other tokens, in an efficient format.

We need to transform the initial vector representations of the tokens into new vectors with linguistic and semantic characteristics embedded in them, based on the contexts in which they appear in the training data. Because the new vectors have semantic values embedded in them, we call them ==_embeddings_==.

To accomplish this task, we use a [[_transformer_]] model. This kind of model consists of two "blocks":
ENCODER → understanding
The encoder reads the input and builds useful contextual representations.
DECODER → generation
The decoder predicts the next token.
- An [[_encoder_]] block that creates the embeddings by applying a technique called _[[attention]]_. The attention layer examines each token in turn, and determines how it's influenced by the tokens around it. To make the encoding process more efficient, [[_multi-head_]] attention is used to evaluate multiple elements of the token in parallel and assign weights that can be used to calculate the new vector element values. The results of the attention layer are fed into a fully connected neural network to find the best vector representation of the embedding.
- A [[_decoder_]] layer that uses the embeddings calculated by the encoder to determine the next most probable token in a sequence started by a prompt. The decoder also uses attention and a feed-forward neural network to make its predictions.
**Tokenization = turn language into pieces.**

**Token ID = give each piece a number.**

**Vector = represent each piece using many numbers.**

**Embedding = a vector whose position carries learned meaning.**

**Attention = determine which other tokens matter for understanding this token.**

**Multi-head attention = examine several types of relationships simultaneously.**

**Transformer = repeatedly use attention + neural networks to build contextual understanding.**

**Decoder = use that understanding to predict what token should come next.**

![Diagram of the Transformer architecture with the encoding and decoding layers.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/simplified-transformer-architecture.png)

 Note

We've greatly simplified the transformer architecture and process in the description and diagram. Don't worry too much about the specific details of how attention works - the key point is that it helps capture linguistic and semantic characteristics of each token based on the contexts in which it's used. If you want a deeper dive into the transformer architecture and how it uses attention, you can read the original _[Attention is all you need](https://arxiv.org/abs/1706.03762)_ paper.

### Initial vectors and positional encoding

Initially, the token vector values are assigned randomly, before being fed through the transformer to create embedding vectors. The token vectors are fed into the transformer along with a _positional encoding_ that indicates where the token appears in the sequence of training text (we need to do this because the order in which tokens appear in the sequence is relevant to how they relate to one another). For example, our tokens might start off looking like this:

|Token|Token ID|Position|Vector|
|---|---|---|---|
|I|1|1|[3, 7, 10]|
|heard|2|2|[2, 15, 1]|
|a|3|3|[9, 11, 1]|
|dog|4|4|[2, 7, 11]|
|bark|5|5|[9, 12, 0]|
|loudly|6|6|[3, 8, 13]|
|at|7|7|[5, 7, 10]|
|a|3|8|[9, 11, 1]|
|cat|8|9|[8, -6, 9 ]|
|...|...|...|...|
|puppy|127|45|[7, 7, -2 ]|
|car|128|56|[5, -5, 1 ]|
|skateboard|129|67|[4, 7, 14]|

 Note

We've kept things simple by using vectors with only three elements (which will help us visualize them in three-dimensions later). In reality, the vectors have thousands of elements.

### Attention and embeddings

To determine the vector representations of tokens that include embedded contextual information, the transformer uses _attention_ layers. An attention layer considers each token in turn, within the context of the sequence of tokens in which it appears. The tokens around the current one are weighted to reflect their influence and the weights are used to calculate the element values for the current token's embedding vector. For example, when considering the token "bark" in the context of "I heard a dog bark", the tokens for "heard" and "dog" will be assigned more weight than "I" or "a", since they're stronger indicators for "bark".

Initially, the model doesn't "know" which tokens influence others; but as it's exposed to larger volumes of text, it can iteratively learn which tokens commonly appear together, and start to find patterns that help assign values to the vector elements that reflect the linguistic and semantic characteristics of the tokens, based on their proximity and frequency of use together. The process is made more efficient by using _multi-head_ attention to consider different elements of the vectors in parallel.

The result of the encoding process is a set of embeddings; vectors that include contextual information about how the tokens in the vocabulary relate to one another. A real transformer produces embeddings that include thousands of elements, but to keep things simple, let's stick to vectors with only three vectors in our example. The result of the encoding process for our vocabulary might look something like this:

|Token|Token ID|Embedding|
|---|---|---|
|I|1|[2, 0, -1 ]|
|heard|2|[-2, 2, 4 ]|
|a|3|[-3, 5, 5 ]|
|dog|4|[10, 3, 2 ]|
|bark|5|[9, 2, 10 ]|
|loudly|6|[-3, 8, 3 ]|
|at|7|[-5, -1, 1]|
|cat|8|[10, 3, 1]|
|puppy|127|[5, 3, 2 ]|
|car|128|[-2, -2, 1 ]|
|skateboard|129|[-3, -2, 2 ]|

We can think of the elements of the embeddings as dimensions in a multi-dimensional vector-space. In our simple example, our embeddings only have three elements, so we can visualize them as vectors in three-dimensional space, like this:

![Diagram of embedding vectors for tokens in three-dimensions.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/embed-example.png)

Because the dimensions are calculated based on how the tokens relate linguistically to one another, tokens that are used in similar contexts (and therefore have similar meanings) result in vectors with similar directions. For example, the embeddings for "dog" and "puppy" point in more or less the same direction, which isn't too different from the embedding for "cat"; but very different from the embedding for "skateboard" or "car". We can measure how close tokens are to one another semantically by calculating the _cosine similarity_ (**how similar two vectors are by comparing the direction they point in**, rather than their absolute size) of their vectors.

## Predicting completions from prompts

Now that we have a set of embeddings that encapsulate the contextual relationship between tokens, we can use the _decoder_ block of a transformer to iteratively predict the next word in a sequence based on a starting _prompt_.

Once again, _attention_ is used to consider each token in context; but this time the context to be considered can only include the tokens that _precede_ the token we're trying to predict. The decoder model is trained, using data for which we already have the full sequence, by applying a technique called _masked attention_; in which the tokens after the current t==oken are ignored==. Since we already know the next token during training, the transformer can compare it to the predicted token and adjust the learned weights in later training iterations to reduce the error in the model.

When predicting a new completion, for which the next tokens are unknown, the attention layers calculate possible vectors for the next token and the feed-forward network is used to help determine the most probable candidate. The predicted value is then added to the sequence, and the whole process repeats to predict the _next_ token; and so on, until the decoder predicts that the sequence has ended.

For example, given the sequence "_When my dog was a ..._", the model will evaluate the tokens in the sequence so far, use _attention_ to assign weights, and predict that the next most probable token is "_puppy_" rather than, say, "_cat_" or "_skateboard_".

# Prompts
A _prompt_ is simply the input you give to an LLM to get a response. It might be a question or a command, or just a casual comment to start a conversation. The model responds to a prompt with a _completion_.

## Types of prompt

There are ==two main types of prompts==:

-[[ **System prompts**]] that set the behavior and tone of the model, and any constraints it should adhere to. For example, "_You're a helpful assistant that responds in a cheerful, friendly manner._". ==System prompts determine constraints and styles for the model's responses==.
- [[**User prompts** ]]that elicit a response to a specific question or instruction. For example, "_Summarize the key considerations for adopting generative AI described in GenAI_Considerations.docx for a corporate executive. Format the summary as no more than six bullet points with a professional tone._".

![Diagram of a system and user prompt.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/system-prompt.png)

Usually, the system prompt is set by the application that uses the model. User prompts can be entered by a human user in a chat application; or in some cases generated by the application on the user’s behalf. The model responds to user prompts while obeying the overall guidance in the system prompt.

## Conversation history

To keep a conversation consistent and relevant, generative AI apps often keep track of the conversation history; and include summarized versions of it in subsequent prompts. This ensures there’s an ongoing context for the conversation that the model can build on.

![Diagram of a conversation with multiple prompts and completions.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/conversation-history.png)

For example, suppose the model responds to the system and user prompts described previously with the following completion:

> _Key considerations for adopting Generative AI include:_
> 
> - _Establish Clear Governance and Responsible AI Policies_
> - _Prioritize High-Value Use Cases Across Corporate Functions_
> - _Mitigate Risks Around Privacy, Security, and Compliance_
> - _Foster Organizational Readiness and Cultural Adaptation_
> - _Measure Impact and Build Accountability_
> - _Stay Ahead of Strategic and Competitive Shifts_

You could respond with a follow-up question, such as "_What are common privacy-related risks?_. The prompt would include the new question, but also the previous prompts and responses; providing context to the model so that it understands the question in relation to Generative AI adoption.

## Retrieval augmented generation (RAG)=technique that lets an AI **look up relevant information first, then use that information to answer**.
 To add even more context, generative AI applications can use a technique called[[ _retrieval augmented generation (RAG)_]]. This approach involves retrieving information, like documents or emails, and using it to augment the prompt with relevant data. The response generated by the model is then _grounded_ in the information that was provided.

For example, suppose you submit a prompt like "_What's the maximum I can claim for travel expenses on a business trip?_". With no other information, a model will respond with a generic answer - probably telling you to consult your organization's expenses policy documentation. A better solution would be to build an expenses assistant app that initially queries the organization's expenses policy documentation, retrieving sections related to "travel expenses"; and then includes the retrieved information in the prompt that is sent to the model, along with your original question. Now the model can use the expenses policy information in the prompt to provide context, and respond with a more relevant answer.

![Diagram of a retrieval augmented generation being used to provide context in a prompt.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/retrieval-augmented-generation.png)

## Tips for better prompts

The quality of responses from generative AI assistants not only depends on the language model used, but on the prompts you submit to it.

![Diagram of a clear and specific prompt with context, examples, and a request for structure.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/writing-prompts.png)

To get better results from your prompts:

- Be **clear** and **specific** – prompts with explicit instructions or questions work better than vague language.
- Add **context** - mention the topic, audience, or format you want.
- Use **examples**, If you want a certain style, provide an example of what you mean.
- Ask for **structure**, Like bullet points, tables, or numbered lists.

Using well-designed prompts can make a huge difference to the results you’ll get from your generative AI model.


# AI agents
Imagine having a digital assistant that doesn’t just answer questions, but actually gets things done! Welcome to the world of AI agents.

==Agents== are ==software applications== built on generative AI that ==can reason over and generate natural language==, automate tasks by using tools, and respond to contextual conditions to take appropriate action.

## Components of an AI agent

![Diagram of an agent with a model, instructions, and tools.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/agent.png)

AI agents have three key elements:

- **A large language model**: This is the agent's brain; using generative AI for language understanding and reasoning.
- **Instructions**: A system prompt that defines the agent’s role and behavior. Think of it as the agent’s job description.
- **Tools**: These are what the agent uses to interact with the world. Tools can include:
    - _Knowledge_ tools that provide access to information, like search engines or databases.
    - _Action_ tools that enable the agent to perform tasks, such as sending emails, updating calendars, or controlling devices.

With these capabilities, AI agents can take on the role of digital assistants that intelligently automate tasks and collaborate with you to work smarter and more efficiently.

## Multi-agent systems

Agents can also work with one another, in multi-agent systems. Instead of one agent doing everything, multiple agents can collaborate—each with its own specialty. One might gather data, another might analyze it, and a third might take action. Together, they form an AI-powered workforce that can handle complex workflows, just like a human team.

![Diagram of a multi-agent system.](https://learn.microsoft.com/en-gb/training/wwl-data-ai/fundamentals-generative-ai/media/multiple-agents.png)

Agents communicate with each other through prompts, using generative AI to determine what tasks are required and which agents are responsible for completing them.

Agentic AI is set to be the next advance in how we use technology to find information and get work done.
# Exercise - Explore generative AI
![[Pasted image 20260824070146.png]]
![[Pasted image 20260824070209.png]]![[Pasted image 20260824070227.png]]

