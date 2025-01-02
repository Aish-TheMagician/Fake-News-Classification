### Dataset Overview | [Link to Dataset](https://drive.google.com/drive/folders/1V5cqA-cthmVbMvjg0lesgSS6N35-7fnY?usp=sharing)

The dataset comprises news articles with attributes that provide valuable insights for fake news detection. Below is a detailed description of each attribute and its relevance to the analysis:

---

#### **1. Title**
- **Description**: The headline of the article, crafted to grab attention. Titles often convey the overall intent or tone, such as neutral, biased, or sensational.
- **Example**:  
  *"Ex-CIA head says Trump remarks on Russia interfere with democracy."*
- **Analysis**:  
  Features like sentiment, keyword frequency, and length (short and impactful vs. long and descriptive) are analyzed to aid classification.

---

#### **2. Text**
- **Description**: The main content or body of the article, providing detailed information. Articles can vary in length and depth, ranging from factual reporting to opinionated, exaggerated, or false claims.
- **Example**:  
  *"Former CIA director John Brennan criticized Trump's remarks, stating they undermine democratic principles."*
- **Techniques Used**:  
  - Tokenization  
  - Sentiment Analysis  
  - Topic Modeling  
These techniques extract meaningful patterns to assist classification.

---

#### **3. Subject**
- **Description**: A categorical attribute representing the general theme or topic of the article (e.g., politics, news, government affairs).  
- **Example Categories**:  
  - *politicsNews*  
  - *Government News*  
  - *left-news*  
- **Relevance**:  
  Subject labels may highlight biases in coverage, as certain themes are more prone to polarizing or fabricated content.

---

#### **4. Date**
- **Description**: The publication date of the article. Temporal patterns, such as surges in fake news during elections or major events, can provide context for misinformation trends.

---

#### **5. Annotations**
- **Labels**: Binary labels indicating whether an article is fake or real.
  - `0`: Fake News  
  - `1`: Real News  
- **Example**:  
  An article labeled `1` is considered real, while one labeled `0` is fake.
- **Purpose**:  
  These labels serve as the ground truth for training and testing the classification models.

---

This dataset offers a diverse range of attributes that are pivotal for exploring patterns in fake news and training robust classification models.


Here is a table summarizing the attributes and their descriptions for the dataset:

| **Attribute**  | **Description**                                                                 | **Example**                                               | **Relevance/Techniques**                                                                 |
|----------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|-----------------------------------------------------------------------------------------|
| **Title**      | The headline of the article, designed to grab attention. It can convey tone or intent, e.g., neutral, biased, or sensational. | *"Ex-CIA head says Trump remarks on Russia interfere with democracy."* | Sentiment analysis, keyword frequency, length analysis, tone classification.            |
| **Text**       | The main content of the article, which may range from factual to exaggerated or false claims. | *"Former CIA director John Brennan criticized Trump's remarks, stating they undermine democratic principles."* | Tokenization, sentiment analysis, topic modeling for content pattern extraction.       |
| **Subject**    | A categorical label representing the general theme or topic of the article (e.g., politics, news, government affairs). | *politicsNews*, *Government News*, *left-news*            | Reveals potential biases in article coverage; useful for pattern recognition and classification. |
| **Date**       | The publication date of the article, providing temporal context for trends and misinformation. | *2024-01-01*                                             | Temporal analysis to detect trends, e.g., fake news spikes during elections or events.   |
| **Annotations**| Binary labels indicating whether an article is fake or real.                       | `0` (Fake News), `1` (Real News)                          | Ground truth labels for training and evaluating classification models.                  |

This table summarizes the key attributes and their roles in fake news detection.
