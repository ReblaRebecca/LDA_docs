# Preprocessing lists: Swedish parliamentary motions on education

Word lists used to preprocess Swedish parliamentary motions referred to the Committee on Education
(Utbildningsutskottet, UbU), sessions 1985/86–2025/26, before topic modelling with LDA.
They belong to the project report *Tracing Thematic Change in Swedish Parliamentary Motions on Education,
1986–2026* (Rebecca Lagerkvist, Stockholm University, LIS070, autumn 2026).

## Files

| File | Entries | Used for |
|---|---|---|
| `boilerplate_phrases.txt` | 467 words and phrases | Political boilerplate, scanning artifacts and time expressions, removed from the text |
| `lemma_corrections.txt` | 36 corrections | Known errors of the Stanza lemmatizer, corrected after lemmatization |
| `stopwords_supplementary.txt` | 135 words (129 not in NLTK) | Added to NLTK's Swedish stopword list (114 words) |

Each file explains its format in its header; lines starting with `#` are comments.

## Order of the steps

1. **Lemmatization** with Stanza's Swedish model (Qi et al., 2020).
2. **Boilerplate removal** (`boilerplate_phrases.txt`), matched on the original word forms of body text and title,
   and **lemma corrections** (`lemma_corrections.txt`); a wrong lemma marked with `*` is also corrected at the
   end of a compound.
3. **Normalization:** digits removed, punctuation inside words turned into spaces, single characters dropped.
4. **Stopword removal:** NLTK's Swedish list (`nltk.corpus.stopwords.words('swedish')`, 114 words, not copied
   here) plus `stopwords_supplementary.txt`, applied to the lemmatized, normalized text, so most entries are
   lemma forms.

Boilerplate is parliamentary and domain-specific language; stopwords are general Swedish words. Keeping them
apart lets the stopword list be reused for other Swedish texts.

## References

- Bird, S., Klein, E. and Loper, E. (2009). *Natural Language Processing with Python.* O'Reilly. (NLTK)
- Qi, P., Zhang, Y., Zhang, Y., Bolton, J. and Manning, C. D. (2020). Stanza: A Python Natural Language
  Processing Toolkit for Many Human Languages. *ACL 2020: System Demonstrations.*

## License

Licensed under the MIT License; see `LICENSE`.
