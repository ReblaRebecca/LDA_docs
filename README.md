# Swedish parliamentary motions on education: preprocessing lists and topic chain explorer

Word lists used to preprocess Swedish parliamentary motions referred to the Committee on Education
(Utbildningsutskottet, UbU), sessions 1985/86–2025/26, before topic modelling with LDA, and the explorer of
the resulting topic chains. They belong to the project report *Tracing Thematic Change Reproducibly in
Swedish Parliamentary Motions on Education, 1985/86–2025/26* (Rebecca Lagerkvist, Stockholm University,
LIS070, autumn 2026).

## Files

| File | Entries | Used for |
|---|---|---|
| `boilerplate_phrases.txt` | 467 words and phrases | Political boilerplate, scanning artifacts and time expressions, removed from the text |
| `lemma_corrections.txt` | 36 corrections | Known errors of the Stanza lemmatizer, corrected after lemmatization |
| `stopwords_supplementary.txt` | 135 words (129 not in NLTK) | Added to NLTK's Swedish stopword list (114 words) |

| `period_explorer.html` | 8 chains × 4 time bins | The topic chain explorer (see below) |

Each list explains its format in its header; lines starting with `#` are comments.

## Topic chain explorer

`period_explorer.html` shows the LDA models of the four time bins (8 topics each) as eight topic chains, in
the order of the report's chain figure. For each topic: a word cloud of its 20 most relevant words, its share
of the bin's motions and its seed stability (in how many of 4 other seed models it is found again). A weak
link (cosine similarity below 0.50) is marked with its cosine.

**Open it as a web page:** https://reblarebecca.github.io/LDA_docs/period_explorer.html

(GitHub's file view shows the file as source code, not as a page. The page is self-contained, so the file can
also be downloaded and opened in a browser; an internet connection is needed only for the fonts.)

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
