# Multi-Model-Document-Retrieval-System

## Overview
This project is a multi-modal document retrieval system that integrates text, audio, image, and video data. The system leverages various machine learning models and libraries to process, store, and retrieve multi-modal data efficiently. The project is designed to handle large datasets and provides functionalities to query and retrieve relevant documents based on user input.

I will try to implementing here:

- Audio Retrieval with Contrastive Language-Audio Pretraining models for text to audio and audio to audio retrieval.
- Image Retrieval with Contrastive Language-Image Pretraining models for text to image and image to image retrieval.
- Text Retrieval with standard text embeddings for text to text retrieval.
- Video Retrieval through some clever workarounds to maintain temporal information across frames
- Running the retrieved text, image, and video information through an LLM to get some insights, and finish our RAG loop. 

## Project Structure
The project is structured into several key components:

1. `Data Loading and Preprocessing:` Loading datasets from various sources (e.g., ESC50 for audio, StockImages-CC0 for images, Wikipedia for text, StockVideos-CC0 for videos). Preprocessing data (e.g., resampling audio, extracting frames from videos).

2. `Embedding Generation:` Generating embeddings for text, audio, images, and video frames using models like CLAP, OpenCLIP, and SentenceTransformer.

3. `Data Storage:` Storing embeddings and metadata in a ChromaDB collection for efficient retrieval.

4. `Query and Retrieval:` Querying the ChromaDB collections to retrieve relevant documents based on user input. Displaying retrieved documents (text, audio, images, videos) in an interactive manner.

5. `Integration with LLaVA Model:` Using the LLaVA model to generate responses based on retrieved documents and user queries.


## Key Components

### 1. Data Loading and Preprocessing

#### Audio Data
- **Dataset:** ESC50
- **Preprocessing:**
   - Load audio files.
   - Resample audio to a target sample rate.
   - Save processed audio files to a specified directory.

#### Image Data
- **Dataset:** StockImages-CC0
- **Preprocessing:**
   - Load images.
   - Save images to a specified directory.


#### Text Data
- **Dataset:** Wikipedia-example-data
- **Preprocessing:**
    - Load text documents.
    - Generate embeddings using SentenceTransformer.

#### Video Data
- **Dataset:** StockVideos-CC0
- **Preprocessing:**
    - Extract frames from videos at specified intervals.
    - Save frames to a specified directory.

### 2. Embedding Generation

#### Audio Embeddings
- **Model:** CLAP (Contrastive Language-Audio Pretraining)
- **Functionality:**
    - Encode audio waveforms into embeddings.


#### Image Embeddings
- **Model:** OpenCLIP
- **Functionality:**
    - Encode images into embeddings.


#### Text Embeddings
- **Model:** SentenceTransformer
- Functionality:
    - Encode text documents into embeddings.

### 3. Data Storage

#### ChromaDB Collections

**Collections:**

- `audio_collection:` Stores audio embeddings and metadata.
- `image_collection:` Stores image embeddings and metadata.
- `text_collection:` Stores text embeddings and metadata.
- `video_collection:` Stores video frame embeddings and metadata.


### 4. Query and Retrieval

#### Querying Collections

**Functionality:**
- Query collections based on user input.
- Retrieve and display relevant documents (text, audio, images, videos).


### 5. Integration with LLaVA Model

#### LLaVA Model

- **Model:** LLaVA-1.5-7B-HF
- **Functionality:**
    - Generate responses based on retrieved documents and user queries.

## Usage

### Running the Project

#### 1. Install Dependencies:
Ensure all required libraries are installed. You can install them using pip:
```
pip install torch transformers sentence-transformers chromadb soundfile datasets opencv-python IPython
```

#### 2. Load Datasets:
Load the necessary datasets (ESC50, StockImages-CC0, Wikipedia-example-data, StockVideos-CC0).

#### 3. Preprocess Data:
Preprocess the data (resample audio, extract frames from videos, etc.).

#### 4. Generate Embeddings:
Generate embeddings for text, audio, images, and video frames.

#### 5. Store Data in ChromaDB:
Store the embeddings and metadata in ChromaDB collections.

#### 6. Query and Retrieve Documents:
Query the collections based on user input and retrieve relevant documents.

#### 7. Generate Responses with LLaVA:
Use the LLaVA model to generate responses based on retrieved documents and user queries.

### Example Queries
- **Text Retrieval:**
   ```
   display_text_documents("San Francisco", max_distance=1.0)
   ```

- **Audio Retrieval:**
   ```
   display_audio_files("water droplet", max_distance=1.5)
   ```

- **Image Retrieval:**
   ```
   display_images("water droplet", max_distance=1.5)
   ```

- **Video Retrieval:**
   ```
   display_videos("Trees", max_distance=1.55)
   ```

- **LLaVA Response:**
   ```
   San Francisco, officially known as the City and County of San Francisco, is a major commercial, financial, and cultural hub in Northern California. It is the fourth most populous city in California and the 17th in the United States, with a population of 815,201 as of 2021. The city is located at the end of the San Francisco Peninsula and is known for its high population density, being the second most densely populated large U.S. city after New York City.
   
   San Francisco is colloquially known by several nicknames, including "SF," "San Fran," "The City," "Frisco," and "Baghdad by the Bay." The city is also notable for its high per capita income, ranking first among U.S. cities with over 250,000 residents.
   
   The San Francisco 49ers, a professional American football team, are based in the San Francisco Bay Area. They compete in the NFL and play their home games at Levi's Stadium in Santa Clara, California.
   
   Silicon Valley, located in the southern part of the San Francisco Bay Area, is a global center for high technology and innovation. Major cities in Silicon Valley include San Jose, Sunnyvale, Santa Clara, and Palo Alto. San Jose is the largest city in Northern California by both population and area, with a population of 1,013,240 as of 2020.
   
   The San Francisco Bay Area, often referred to as the Bay Area, includes nine counties: Alameda, Contra Costa, Marin, Napa, San Mateo, Santa Clara, Solano, Sonoma, and San Francisco. The core cities of the Bay Area are San Francisco, San Jose, and Oakland.
   
   The first image shows a scenic view of San Francisco with the Bay Bridge in the background and a person rowing a boat in the foreground. The second image is a frame from a video showing a vibrant cityscape at night, with illuminated buildings and a bridge, likely representing the bustling urban environment of the Bay Area.
   ```

## Conclusion
This multi-modal document retrieval system provides a comprehensive solution for handling and retrieving text, audio, image, and video data. By leveraging advanced machine learning models and efficient data storage solutions, the system offers powerful querying capabilities and interactive document retrieval. The integration with the LLaVA model further enhances the system's ability to generate meaningful responses based on retrieved documents.



