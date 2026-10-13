# Morphological Tagger: UD Hindi HDTB Only

## 1. Source
- Model: `google/muril-base-cased` fine-tuned with four task heads.
- 128-dim morphology embedding via learned projection.

## 2. Training Data
- **UD Hindi HDTB:** 13306 train sentences.
- **Dev:** 1659 sentences.
- **Test:** 1684 sentences.
- LDC2010T24 and IndicCorpus were not used.

## 3. Inference-Time Procedure
At each decoding step, the tagger receives the caption prefix, predicts POS/Gender/Number/Case for the next token, and produces a 128-dim embedding `m_i` fed to MAA. No gold tags are required at test time.

## 4. Independent Evaluation (UD Hindi test split)
### upos
```
              precision    recall  f1-score   support

         ADJ     0.8918    0.8985    0.8952      2129
         ADP     0.9600    0.6439    0.7708      7464
         ADV     0.7335    0.9507    0.8281       304
         AUX     0.9354    0.9925    0.9631      2392
       CCONJ     0.9694    0.9969    0.9829       635
         DET     0.9657    0.9812    0.9734       745
        NOUN     0.7173    0.5556    0.6262      8036
         NUM     0.9829    0.9971    0.9900       693
        PART     0.9446    0.9823    0.9631       677
        PRON     0.9937    0.9249    0.9581      1372
       PROPN     0.4424    0.8740    0.5874      4438
       PUNCT     0.9841    1.0000    0.9920      2420
       SCONJ     0.9718    0.9985    0.9849       655
        VERB     0.9945    0.8916    0.9403      3461
           X     0.2083    0.5556    0.3030         9

    accuracy                         0.7869     35430
   macro avg     0.8464    0.8829    0.8506     35430
weighted avg     0.8392    0.7869    0.7948     35430

```

### Gender
```
              precision    recall  f1-score   support

         Fem     0.9546    0.9791    0.9667      5686
        Masc     0.9298    0.9639    0.9465     13253
           O     0.9789    0.9414    0.9598     16491

    accuracy                         0.9559     35430
   macro avg     0.9544    0.9615    0.9577     35430
weighted avg     0.9566    0.9559    0.9559     35430

```

### Number
```
              precision    recall  f1-score   support

           O     0.9479    0.9703    0.9590     13370
        Plur     0.9076    0.9543    0.9303      2932
        Sing     0.9767    0.9529    0.9647     19128

    accuracy                         0.9596     35430
   macro avg     0.9441    0.9592    0.9513     35430
weighted avg     0.9601    0.9596    0.9597     35430

```

### Case
```
              precision    recall  f1-score   support

         Acc     0.8051    0.6306    0.7072     10138
     Acc,Dat     0.7895    1.0000    0.8824       120
     Acc,Erg     0.9935    1.0000    0.9968       154
     Acc,Gen     0.2794    0.9929    0.4361       280
     Acc,Ine     1.0000    1.0000    1.0000        41
     Acc,Ins     0.6964    1.0000    0.8211        39
         Nom     0.5692    0.8113    0.6690      8437
           O     0.8850    0.7673    0.8220     16221

    accuracy                         0.7428     35430
   macro avg     0.7523    0.9003    0.7918     35430
weighted avg     0.7822    0.7428    0.7508     35430

```

