# fusion retrieval
Fusion Retrieval in Document Search

Overview:

This code implements a Fusion Retrieval system that combines vector-based similarity search with keyword-based BM25 retrieval. The approach aims to leverage the strengths of both methods to improve the overall quality and relevance of document retrieval.

Motivation:
Traditional retrieval methods often rely on either semantic understanding (vector-based) or keyword matching (BM25). Each approach has its strengths and weaknesses. Fusion retrieval aims to combine these methods to create a more robust and accurate retrieval system that can handle a wider range of queries effectively.

Key Components:
PDF processing and text chunking.

Vector store creation using FAISS and huggingface embeddings.

BM25 index creation for keyword-based retrieval.

Custom fusion retrieval function that combines both methods.

Method Details:
Document Preprocessing
1. The PDF is loaded and split into chunks using RecursiveCharacterTextSplitter.

2. Chunks are cleaned by replacing 't' with spaces (likely addressing a specific formatting issue).

Vector Store Creation:
Huggingface embeddings are used to create vector representations of the text chunks.

A FAISS vector store is created from these embeddings for efficient similarity search.

BM25 Index Creation:
1. A BM25 index is created from the same text chunks used for the vector store.

2. This allows for keyword-based retrieval alongside the vector-based method.

Fusion Retrieval Function:
The fusion_retrieval function is the core of this implementation:

1. It takes a query and performs both vector-based and BM25-based retrieval.
 
2. Scores from both methods are normalized to a common scale.

3. A weighted combination of these scores is computed (controlled by the alpha parameter).

4. Documents are ranked based on the combined scores, and the top-k results are returned.

Benefits of this Approach.
1. Improved Retrieval Quality: By combining semantic and keyword-based search, the system can capture both conceptual similarity and exact keyword matches.

2. Flexibility: The alpha parameter allows for adjusting the balance between vector and keyword search based on specific use cases or query types.

3. Robustness: The combined approach can handle a wider range of queries effectively, mitigating weaknesses of individual methods.

4. Customizability: The system can be easily adapted to use different vector stores or keyword-based retrieval methods.

Conclusion:
Fusion retrieval represents a powerful approach to document search that combines the strengths of semantic understanding and keyword matching. By leveraging both vector-based and BM25 retrieval methods, it offers a more comprehensive and flexible solution for information retrieval tasks. This approach has potential applications in various fields where both conceptual similarity and keyword relevance are important, such as academic research, legal document search, or general-purpose search engines.
