
# rag

## 项目介绍
用`RAG`去实现`基于PDF文档的大模型问答`，使用`Ragas评估框架`去评估RAG的性能。

一步步实现：

- 0.ipynb：一篇新闻文章，有一个（问题，答案）对 - 简单RAG - Ragas评估
- 1.ipynb：一份PDF文档，有三个（问题，答案）对 - 简单RAG - Ragas评估
- 2.ipynb：一份PDF文档，有三个（问题，答案）对 - 进阶RAG（检索器优化） - Ragas评估
  - 仅embedding retriever -> bm25 retriever + embedding retriever = ensemble retriever
- 3.ipynb：一份PDF文档，有三个（问题，答案）对 - 进阶RAG（优化后的检索器 + 生成器优化） - Ragas评估
  - 3.1.ipynb：优化后的检索器 + 基于LLMChainExtractor的文本压缩器 = 上下文压缩
  - 3.2.ipynb：优化后的检索器 + 基于BGE Reranker的自定义文本压缩器 = 上下文压缩

所用工具：

- 检索器优化
    - [BGE Embedding](https://huggingface.co/BAAI/bge-large-zh-v1.5)
    - [BM25 Retriever](https://python.langchain.com/docs/modules/data_connection/retrievers/ensemble)
    - [Ensemble Retriever](https://python.langchain.com/docs/modules/data_connection/retrievers/ensemble)
- 生成器优化
    - [Contextual compression](https://python.langchain.com/docs/modules/data_connection/retrievers/contextual_compression)
        - [LLMChainExtractor](https://python.langchain.com/docs/modules/data_connection/retrievers/contextual_compression#adding-contextual-compression-with-an-llmchainextractor)
        - [BGE Reranker](https://huggingface.co/BAAI/bge-reranker-large)
- 评估
  - [Ragas评估框架](https://docs.ragas.io/en/stable/)

## 运行

1、创建虚拟环境并安装依赖
- conda create -n py38_AdvancedRAG python=3.8
- conda activate py38_AdvancedRAG

2、配置环境变量
   - 打开`.env`文件
   - 填写完整该文件中的`OPENAI_API_KEY`、`HTTP_PROXY`、`HTTPS_PROXY`、`HUGGING_FACE_ACCESS_TOKEN`四个环境变量
     - `HUGGING_FACE_ACCESS_TOKEN`获取方式：https://huggingface.co/settings/tokens

    
3、运行 Jupyter Lab
   - 命令行或终端运行`jupyter lab`
     - 浏览器会自动弹出网页：`http://localhost:8888/lab`

4、下载 embedding model
- 运行`test_bge-large-zh-v1.5.ipynb`下载并测试`BAAI/bge-large-zh-v1.5`模型
- 模型 Hugging Face 地址：[https://huggingface.co/BAAI/bge-large-zh-v1.5](https://huggingface.co/BAAI/bge-large-zh-v1.5)

5、下载 reranker model
- 运行`test_bge-reranker-large.ipynb`下载并测试`BAAI/bge-reranker-large`模型
- 模型 Hugging Face 地址：[https://huggingface.co/BAAI/bge-reranker-large](https://huggingface.co/BAAI/bge-reranker-large)

6、运行根目录下几个ipynb文件：0、1、2、3.1、3.2
