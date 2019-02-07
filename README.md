# data-NZZ-gothic-ground-truth

This is a small documentation of the creation of a ground truth for Gothic letter. The OCR of Gothic letter is still error-prone. In order to be able to assess the OCR quality of newspapers (and also in order to be able to train new models to improve the OCR), it is necessary to have a ground truth at one's disposal. The Neue Zürcher Zeitung (NZZ) has been publishing in black letter from its very first issue in 1780 until 1947. The variation in font, as well as the paper quality of the scans rendered mediocre OCR quality at best, while some of the content is entirely illegible.

The current version of the ground truth is licensed under a Creative Commons license as specified in the file LICENSE.txt. This ground truth can be used for academic purposes. 

<WORK'S NAME> (c) by <AUTHOR'S NAME>

<WORK'S NAME> is licensed under a
Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) License.

You should have received a copy of the license along with this
work. If not, see <https://creativecommons.org/licenses/by-nc/3.0/legalcode.txt>.

<b>If you use it, please indicate the source as "A, B and C, D. 2019. A Ground Truth for 18th Century until 20th Century Newspaper Texts from the Neue Zürcher Zeitung." University of Zurich, Zurich.</b>

## content
This NZZ ground truth contains several files:
 - <b>NZZ_orig</b>: The original text files provided by the NZZ. The NZZ text stems from 2005. They newspaper pages were OCR-ised with ABBYY FineReader XIX, a specialised version from ABBYY for gothic letter.
 - <b>NZZ_ABBYY</b>: A version produced from Transkribus-internal (see below) ABBYY FineReader Engine 11.
 - <b>NZZ_correct</b>: Our final version of the ground truth.
   - the finished ground truth contains 290,048 words and 40,986 lines.

## sampling
From 1780 to 1947 we randomly sampled one title page per year, which gives us a total of 167 pages. We chose title pages to make sure not to sample pages containing advertisements or stock information. Since the NZZ had been published several times a day during certain periods, and since there were sometimes supplements, it is not guaranteed that all title pages are from the very first issue of the day. There were also title pages from supplements which have been sampled.

## ground truth production
In order to speed up the process of the ground truth production, we uploaded the 167 images to Transkribus (<url>https://transkribus.eu/Transkribus/</url>) and extracted the text with the internal ABBYY FineReader Engine 11. We then continued to use Transkribus to correct the text.

When the transcription of about 120 pages was done, we had the Transkribus team train a HTR model with which we extracted the text from the pages which had not been transcribed at that point in time. This significantly speeded up the process.

### guidelines
Here some guidelines:

 - *punctuation*
   - the old writing styles use the equality sign "=" to split words over two lines. We transcribed this as "-", like we would use it today.
   - special symbols were only rarely transcribed (sometimes the newspaper used a symbole like a triangle, a dagger or a cross to mark a specific canton or author)
   - there are inconsistencies in the transcription of quotation marks. In some cases, we used the curly quotation marks (for quotation marks on the baseline (Anführungszeichen), whereas in others, the straight quotation marks were used (to mark the end of quotation (Schlusszeichen)).

 - *spelling*
   - in black letter, there is no distinction between capital "I" and capital "J". We decided to transcribe the words starting with either letter in the way current spelling rules would require it, e.g.: we would write "Jakob" instead of "Iakob", and "Insekt" instead of "Jnsekt".
   - the ligature "sz" is kept and transcribed as "ß"
   - spaced letters (Sperrschrift) are fused using the merge tool of transkribus
   - sometimes, hyphenated words contain spaces, e.g. "Landboten - Korrespondent". We adopted the current spelling "Landboten-Korrespondent" for such cases.
   - the occurrence "N°" was always transcribed as "Nr."
   - the long "s" has always been transcribed as normal "s".

 - *regions*
   - in Transkribus, it is possible to either transcribe word based or line based. Our standard is not consistent. We have a line based transcription for all pages. Word based transcriptions are only available for the following pages: **Word-based transcription for years:**
1780-1895, 1898, 1900, 1905, 1908, 1910, 1913, 1915, 1918, 1920, 1923, 1925, 1930, 1933, 1935, 1938, 1940, 1943, 1945, 1946
TOTAL: 134 years --> the word boxes for these years should also be right.
   - we corrected all baselines, so the ground truth can be used to train HTR models in Transkribus
   - moreover, we corrected the text regions where necessary
   - for the pages where we detected the text with the HTR model, we straightened the line boxes
 
 ## additionsl remarks
 there are pages which have been slightly cut at the right-hand side. this stems from the digitisation process by the NZZ. for future versions, we should replace these pages.
 

## transcribors:
 - Isabelle Meraner
 - Camille Watter
 - Simon Clematide siclemat@ifi.uzh.ch - in case of questions
 - Phillip Ströbel pstroebel@cl.uzh.ch - in case of questions
