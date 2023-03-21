# Finetuning a NLP Model

This is a repo dedicated to my the use of various huggingface and pytorch tools to implement finetuning of a nlp model (BERT) on downstream task sentiment analysis. Here, a "bert-base-cased" model was finetuned to perform yelp review rating (1-5 stars) on the yelp_review_full dataset.

## Model Parameters
A pretrained BERT model was loaded using the transformers library which has 110M trainable parameters. 

The "yelp-review-full" dataset for finetuning was loaded using the datasets library. It consists of randomly sampled 130K training smaples and 10K testing samples. Each review is gets a label of star rating from 1 to 5.Following is one sample extracted from the dataset. 

{
    'label': 0,
    'text': 'I got \'new\' tires from them and within two weeks got a flat. I took my car to a local mechanic to see if i could get the hole patched, but they said the reason I had a flat was because the previous patch had blown - WAIT, WHAT? I just got the tire and never needed to have it patched? This was supposed to be a new tire. \\nI took the tire over to Flynn\'s and they told me that someone punctured my tire, then tried to patch it. So there are resentful tire slashers? I find that very unlikely. After arguing with the guy and telling him that his logic was far fetched he said he\'d give me a new tire \\"this time\\". \\nI will never go back to Flynn\'s b/c of the way this guy treated me and the simple fact that they gave me a used tire!'

Finetuning was done on top of the pretrained weights of BERT by adding a classifier head consisting of 5 output classes on top of the BERT's encoder. The dataset was seeded for 10k random samples and trained for (5+5=10) epochs. 

inference.py was written to demonstrate the use of the model on the review rating (sentiment analysis) task. 

