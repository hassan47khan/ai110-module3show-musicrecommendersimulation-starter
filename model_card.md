# 🎧 Model Card: Music Recommender Simulation

## 1. Model Name  

Give your model a short, descriptive name.  
Example: **VibeFinder 1.0**  

---

## 2. Intended Use  

Describe what your recommender is designed to do and who it is for. 

Prompts:  

- What kind of recommendations does it generate  
- What assumptions does it make about the user  
- Is this for real users or classroom exploration  

---

## 3. How the Model Works

The recommender works like a judge handing out points. Every song in the catalog starts at zero, and we go through a short checklist for each one, adding points when the song matches what the listener said they wanted.

**What we look at for every song:** its genre (pop, rock, lofi, etc.), its mood (happy, chill, intense, etc.), and a few numeric "vibe" measurements between 0 and 1 — how energetic it is, how danceable it is, and how acoustic it is.

**What the listener tells us:** a favorite genre, a favorite mood, and (optionally) a target energy level — basically "I'm in a happy pop mood and I want something upbeat."

**How the points are awarded:**

- If the song's genre matches the listener's pick exactly, it gets **+2 points**. Genre is the strongest signal, so it carries the most weight.
- If the mood matches, it gets another **+1 point**.
- For each numeric vibe (energy, danceability, acousticness) the listener specified, we measure how close the song's value is to the listener's target. A perfect match is worth close to a full point, and the reward shrinks the farther apart they are. A song that is way off on energy gets zero for that category instead of a negative penalty, so no single mismatch wrecks a song that's otherwise a good fit.

Once every song has a score, we sort them from highest to lowest and show the top five. Alongside each pick, we also show the specific reasons it scored well — "genre match", "mood match", "energy proximity" — so the listener can see *why* the system thought this one belonged on the list, not just that it does.

The main change from the starter code: the starter just returned the first five songs in the file regardless of preference. Now the ranking actually responds to the listener, and every recommendation comes with a plain-language explanation.

---

## 4. Data  

Describe the dataset the model uses.  

Prompts:  

- How many songs are in the catalog  
- What genres or moods are represented  
- Did you add or remove data  
- Are there parts of musical taste missing in the dataset  

---

## 5. Strengths  

Where does your system seem to work well  

Prompts:  

- User types for which it gives reasonable results  
- Any patterns you think your scoring captures correctly  
- Cases where the recommendations matched your intuition  

---

## 6. Limitations and Bias 

Where the system struggles or behaves unfairly. 

Prompts:  

- Features it does not consider  
- Genres or moods that are underrepresented  
- Cases where the system overfits to one preference  
- Ways the scoring might unintentionally favor some users  

---

## 7. Evaluation  

How you checked whether the recommender behaved as expected. 

Prompts:  

- Which user profiles you tested  
- What you looked for in the recommendations  
- What surprised you  
- Any simple tests or comparisons you ran  

No need for numeric metrics unless you created some.

---

## 8. Future Work  

Ideas for how you would improve the model next.  

Prompts:  

- Additional features or preferences  
- Better ways to explain recommendations  
- Improving diversity among the top results  
- Handling more complex user tastes  

---

## 9. Personal Reflection  

A few sentences about your experience.  

Prompts:  

- What you learned about recommender systems  
- Something unexpected or interesting you discovered  
- How this changed the way you think about music recommendation apps  
