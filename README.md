<h1>Draft Stars - Model<h1>

<h3>Creates, trains and exports a model which predicts the outcome of Brawl Stars matches.</h3>
<h4>Created with PyTorch</h4>



---


<h3>Input</h3>

To run this program, you need a dataset of Brawl Stars matches. You can collect one yourself with another repo of mine: <a href="https://github.com/mcmckinley/DraftStarsDataCollection">DraftStarsDataCollection</a>

<br>

Each match in the dataset contains the following values:
* IDs for all six brawlers<sub>1</sub>
  * There are six players in each match (3 versus 3). The first three IDs for each match refer to the left (or blue) team. The last three refer to the right (or red) team.
  * Very important note: there are no brawlers with indices 33 and 55. This is because the official brawler list, when requested from Supercell's API, does not include brawlers at these indices.
* Which team won
  * This column is titled 'did_blue_team_win'. 1 means yes and a 0 means no (the team on right, or red team, won.)
* Trophy counts of each player on that brawler
  * This is useful for weighing the statistical significance of any given match. When a low skill team wins, we assume that their team composition was superior.

<br>

I would strongly recommmend initializing the brawler and map embedding layers with manually chosen values. With Google Colab this notebook is already set up  to import spreadsheets of initialization values that I have created myself. If you wish to run these locally, you should download my spreadsheets or make your own (would not recommend, it takes a while.)


<p>Brawler Data Spreadsheet:

* <a href="https://docs.google.com/spreadsheets/d/17hqBX-6XEA4nGCOcQizNGTZt8ZNelkg0OEtDC4DR1hE/edit?gid=0#gid=0">View</a>

* <a href="https://docs.google.com/spreadsheets/d/e/  2PACX-1vRZXNyNjU1csRxyikhZ-GbnLrt-99bX0FCvxnBKzobXtXpWmvJl8gtNfb46CDIZ50LLHWoY9JU-U4A2/pub?output=csv">Download as CSV</a>
</p>

<p>Map Data Spreadsheet:

* <a href="https://docs.google.com/spreadsheets/d/1eU8GuR_vp8UZdf4gPxDEHrkjTeGk_PDUlVAdkedardA/edit?usp=sharing">View</a>

* <a href="https://docs.google.com/spreadsheets/d/e/ 1eU8GuR_vp8UZdf4gPxDEHrkjTeGk_PDUlVAdkedardA/pub?output=csv">Download as CSV</a>


---
<h3>Output</h3>

* The pytorch model
* Embedding layers for the brawlers and maps, in CSV format
  * Why CSV? For one, it's readable. It's interesting to see how the model takes the initialization data and tweaks it. More importantly however is the fact that we can alter it ourselves.
* A list of maps, in the order than the model interprets them. Without this the backend won't know which map is selected.

