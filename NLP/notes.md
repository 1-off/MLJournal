# Vector space models
- capture relationship between the words
- understanding the context regardless of the words used

# Word2Vec
Word2Vec is an algorithm used for generating word embeddings, which are vector representations of words that capture the meaning and context of the word. Word embeddings are useful for a variety of natural language processing tasks such as language translation, sentiment analysis, and text classification.

The basic idea behind Word2Vec is to train a neural network to predict the context of a word based on the surrounding words in a text corpus. For example, consider the sentence "The cat sat on the mat." The Word2Vec algorithm would process this sentence and generate a vector representation for each word in the sentence, such as:
 ```     
    Vector representation of "cat" = [0.2, 0.8, 0.5]
    Vector representation of "sat" = [0.6, 0.3, 0.9]
    Vector representation of "on" = [0.1, 0.4, 0.7]
    Vector representation of "the" = [0.8, 0.1, 0.4]
    Vector representation of "mat" = [0.5, 0.7, 0.2]
```
These vector representations capture the semantic and syntactic relationships between the words in the sentence. For example, the vectors for "cat" and "mat" are more similar to each other than they are to the vectors for "on" and "the", reflecting the fact that "cat" and "mat" are more closely related in meaning than "on" and "the".

Once the Word2Vec algorithm has generated these vector representations for each word in the corpus, they can be used as input to other neural network models for various natural language processing tasks.

Overall, Word2Vec is a powerful algorithm for generating high-quality word embeddings that capture the meaning and context of words in a text corpus, and is widely used in modern natural language processing applications.

## Vectors
#### Counterclockwise Rotation
If you want to rotate a vector rr with coordinates (xx, yy) and angle αα counterclockwise over an angle ββ to get vector r’r’ with coordinates (x’x’, y’y’) then the following holds:
```
x=r∗cos(α)x=r∗cos(α)

y=r∗sin(α)y=r∗sin(α)

x’=r’∗cos(α+β)x’=r’∗cos(α+β)

y’=r’∗sin(α+β)y’=r’∗sin(α+β)
```
#### Trigonometric addition gives us:
```
cos(α+β)=cos(α)cos(β)−sin(α)sin(β)cos(α+β)=cos(α)cos(β)−sin(α)sin(β)

sin(α+β)=cos(α)sin(β)+sin(α)cos(β)sin(α+β)=cos(α)sin(β)+sin(α)cos(β)
```
