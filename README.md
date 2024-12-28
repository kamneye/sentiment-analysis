# sentiment-analysis
import pandas as pd
import numpy as np
from textblob import TextBlob

# Sample data (you can replace this with your dataset)
data = {
    'text': [
        "I love this product, it works amazing!",
        "Horrible service, will not buy again.",
        "It's okay, not great but not bad.",
        "I am so happy with my purchase!",
        "This is the worst experience I've ever had!"
    ]
}

# Create DataFrame from the data
df = pd.DataFrame(data)

# Function to perform sentiment analysis
def analyze_sentiment(text):
    # Create a TextBlob object
    blob = TextBlob(text)
    # Get the sentiment polarity (-1 to 1 scale)
    polarity = blob.sentiment.polarity
    # Determine if sentiment is Positive, Neutral, or Negative based on polarity
    if polarity > 0:
        return 'Positive'
    elif polarity == 0:
        return 'Neutral'
    else:
        return 'Negative'

# Apply sentiment analysis to each text in the DataFrame
df['sentiment'] = df['text'].apply(analyze_sentiment)

# Print out the DataFrame with sentiments
print(df)
