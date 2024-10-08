## Como construir un  Chatbot Multi-modal RAG

Muchos documentos contienen una mezcla de tipos de contenido, incluidos texto e imágenes.
Sin embargo, la información capturada en las imágenes se pierde en la mayoría de las aplicaciones RAG.
Con la aparición de modelos de lenguaje multimodal, como GPT-4V, ¿Vale la pena considerar cómo utilizar las imágenes en RAG?

`¿Qué haremos hoy?`

* Usar un modelo de lemguaje multimodal ([GPT-4V](https://openai.com/research/gpt-4v-system-card),  para generar resumenes de images.
* Recuperar y embeber esos resumenes con una referencia al archivo original.
* Recuperar contenido original y respuesta a una pregunta realizada.


`¿Qué tecnologías se usarán?`

* Usaremos [Unstructured](https://unstructured.io/) para analizar imágenes, texto y tablas de documentos (PDFs).
* Utilizaremos el [multi-vector retriever](https://python.langchain.com/docs/modules/data_connection/retrievers/multi_vector) con [Chroma](https://www.trychroma.com/) para almacenar el texto e imágenes junto con sus resúmenes para su posterior recuperación.
* Usaremos GPT-4V/GPT-4o tanto para la generación de resúmenes de imágenes (para su recuperación) como para la síntesis final de respuestas a partir del análisis conjunto de imágenes y textos (o tablas).


`Antes de empezar`

Además de los paquetes pip mencionados a continuación, también necesitarás instalar `poppler` ([instrucciones de instalación](https://pdf2image.readthedocs.io/en/latest/installation.html)) y `tesseract` ([instrucciones de instalación](https://tesseract-ocr.github.io/tessdoc/Installation.html)) en tu sistema.

![rag-architecture.png](https://github.com/omairapalacios/rag-multimodal/blob/main/rag-architecture.drawio.png)
