# YouTube Video Summarizer

An end-to-end web application built inside a Jupyter Notebook environment to extract and summarize YouTube video transcripts. The project features a robust **FastAPI** backend that loads a transformer model to process text, paired with an interactive **Streamlit** frontend interface for a clean user experience. A secure public tunnel via **pyngrok** links the two components together, allowing you to interact with the application directly from your browser.

---

## Features

*   **Automated Transcript Fetching:** Extracts English captions directly from public YouTube URLs using the YouTube Transcript API.
*   **Smart Link Parsing:** Automatically searches for the special `v` parameter (`v=`) in standard YouTube URLs to extract the unique video ID, while also handling short-form links (`youtu.be/`) seamlessly.
*   **Local Transformers Inference:** Runs the `facebook/bart-large-cnn` model natively within the notebook environment to generate precise, abstractive summaries.
*   **Decoupled Backend Architecture:** Runs a FastAPI server securely in a background thread to manage model inference.
*   **Interactive Web UI:** Provides an intuitive Streamlit interface to input video links and view summarized results instantly.

---

## Technologies Used

*   **Backend Framework:** FastAPI, Uvicorn
*   **Frontend Interface:** Streamlit, Requests
*   **Machine Learning Ecosystem:** Hugging Face Transformers, PyTorch
*   **APIs & Utilities:** `youtube-transcript-api`, `pyngrok`, Python native `threading`

---

## Steps to Run on Kaggle:

1.  **Upload the Notebook:** 
    *   Go to your Kaggle dashboard and click **"New Notebook"**.
    *   In the menu bar, navigate to `File -> Upload notebook` and select this `.ipynb` file.

2.  **Configure Notebook Settings:**
    *   In the right-hand panel under **Settings**, toggle **Internet** to **On** (required to download dependencies and model weights).
    *   Under **Accelerator**, select a GPU option (e.g., **GPU T4 x2**) to ensure fast summary generation.

3.  **Insert Authentication Tokens:**
    *   Locate the cell defining the configuration variables.
    *   Replace the placeholder `NGROK_TOKEN` with your personal tunnel token from your free ngrok dashboard to prevent session disconnects.

4.  **Execute the Code:**
    *   Click **"Run All"** in the top toolbar to execute all cells sequentially.
    *   Cell 1 through 3 will install dependencies and start the background API server.
    *   Cell 4 and 5 will generate the frontend application and launch the secure tunnel interface.

5.  **Open the Web UI:**
    *   Scroll to the output of the final cell. Look for a line that reads:
        `Click here to open the Streamlit UI: https://xxxx-xxxx.ngrok-free.dev`
    *   Click the generated link to open the functional YouTube Summarizer web page in a new browser tab.
