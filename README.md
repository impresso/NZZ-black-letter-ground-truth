# data-NZZ-gothic-ground-truth

This is a small documentation of the creation of a ground truth for gothic letter. The OCR of gothic letter is still error-prone. In order to be able to assess the OCR quality of newspapers (and also in order to be able to train new models to improve the OCR), it is necessary to have a ground truth at one's disposal. The Neue Zürcher Zeitung (NZZ) has been publishing in black letter from its very first issue in 1780 until 1947.

All the data, which includes .xml and image files, in this repository is licensed under a Creative Commons license as specified in the file LICENSE.txt. This ground truth can be used for academic purposes. 

<WORK'S NAME> (c) by <AUTHOR'S NAME>

<WORK'S NAME> is licensed under a
Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) License.

You should have received a copy of the license along with this
work. If not, see <https://creativecommons.org/licenses/by-nc/4.0/legalcode.txt>.

<b>If you use it, please indicate the source as "A, B and C, D. 2019. A Ground Truth for 18th Century until 20th Century Newspaper Texts from the Neue Zürcher Zeitung." University of Zurich, Zurich.</b>

## content
This NZZ ground truth contains several directories:
 - `ABBYY_FineReader_XIX`: The original text provided by the NZZ from 2005. We extracted the images as well as the text with TET PDFLib an saved it as .tif files and .tetml files, respectively.The newspaper pages were OCR-ised with ABBYY FineReader XIX, a specialised version from ABBYY for gothic letter. 
 - `ABBYY_FineReader_Server11`: A version produced from Transkribus-internal (see below) ABBYY FineReader Engine 11.
 - `NZZ_groundtruth`: the manually corrected texts from the 167 seven pages of the NZZ.
   - the ground truth contains 304,268 words and 43,151 lines.
 - `img`: The images we extracted from the PDF files we received from the nzz.

## sampling
From 1780 to 1947 we randomly sampled one title page per year, which gives us a total of 167 pages. We chose title pages to make sure not to sample pages containing advertisements or stock information. Since the NZZ had been published several times a day during certain periods, and since there were sometimes supplements, it is not guaranteed that all title pages are from the very first issue of the day. There were also title pages from supplements which have been sampled.

## ground truth production
In order to speed up the process of the ground truth production, we uploaded the 167 images to Transkribus (<url>https://transkribus.eu/Transkribus/</url>) and extracted the text with the internal ABBYY FineReader Server 11. We then continued to use Transkribus to manually correct the text.

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
   - in Transkribus, it is possible to either transcribe word-based or line-based. Generally, our ground truth is line-based. We have a line-based transcription for all pages. For the following pages, we also provide word-based transcriptions: **Word-based transcription for years:**
1780-1895, 1898, 1900, 1905, 1908, 1910, 1913, 1915, 1918, 1920, 1923, 1925, 1930, 1933, 1935, 1938, 1940, 1943, 1945, 1946
TOTAL: 134 years --> the word boxes for these years should also be right.
   - we corrected all baselines, so the ground truth can be used to train HTR models in Transkribus
   - moreover, we corrected the text regions where necessary
   - for the pages where we detected the text with the HTR model, we straightened the line boxes
 
 ## Additional remarks
There are pages which have been slightly cut at the right-hand side. this stems from the digitisation process by the NZZ. for future versions, we should replace these pages.
 
 ## Training and test data for Transkribus HTR model
 Our paper about Transkribus HTR for improving the OCR of black letter in newspaper texts can be found here <INSERT LINK>. We used the text in the following years for testing:
 1780, 1790, 1800, 1810, 1820, 1830, 1840, 1850, 1860, 1870, 1880, 1890, 1904, 1910, 1915, 1929, 1939
 
## transcribors:
 - Isabelle Meraner
 - Camille Watter
 - Simon Clematide siclemat@ifi.uzh.ch - in case of questions
 - Phillip Ströbel pstroebel@cl.uzh.ch - in case of questions
