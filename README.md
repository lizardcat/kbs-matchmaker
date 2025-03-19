# Matchmaking Knowledge-Based System Overview

Our project focuses on developing a matchmaking knowledge-based system designed to connect users based on shared preferences and compatibility factors. We designed the system with a Kenyan context in mind, incorporating locations and professions relevant to Kenyan users.

The platform allows users to create profiles, customize the importance of various matching attributes, and find compatible matches based on a weighted scoring system.

The user interface, built with the `ipywidgets` library in a Jupyter Notebook environment, has two main sections: **Profile Management** and **Matchmaking**.

### User Capabilities
When using the system, users can:
- Create or update their profiles
- Adjust attribute weightings to prioritize what matters most to them
- Find matches based on personalized preferences

This design ensures that users are not limited to a one-size-fits-all approach but can instead refine the matchmaking process according to their unique relationship goals and lifestyle preferences.

---

# Description of Rules and Scoring Logic

Our matchmaking system considers **8 attributes** to determine compatibility between users:

1. **Age** – The user’s age is factored into compatibility, with a penalty applied if the age difference is significant.
2. **Gender & Preferred Gender** – Users specify their gender and the gender they prefer in a match. If preferences are not aligned, compatibility is zero.
3. **Location** – Users with the same location are given a higher compatibility score, as proximity is often an important factor in relationships.
4. **Interests** – Shared interests are crucial. A user with common hobbies, passions, or pastimes with another will have a higher compatibility score.
5. **Education Level** – Having a similar education level contributes to compatibility since it often reflects shared values and intellectual compatibility.
6. **Occupation** – Matches with the same profession or within similar fields may score higher, as they might better understand each other’s lifestyles.
7. **Relationship Goals** – Users indicate their goals, such as looking for a casual relationship, a long-term commitment, or marriage. Misalignment reduces compatibility.
8. **Lifestyle** – Lifestyle choices like smoking status or activity level also impact compatibility. Users with matching lifestyles score higher.

---

## Scoring Mechanism
The matchmaking process uses a set of predefined rules and a **weighted scoring system**. The system compares these attributes between the user and other profiles in the database, calculating a compatibility score based on both similarity and user-defined weightings.

### Scoring Rules:
- **Age Difference**: Max +20 points, Min 0 points. If the age gap is within 10 years, a proportional score is awarded. The smaller the gap, the higher the score.
- **Shared Interests**: Max +30 points. A Jaccard similarity index measures overlap. Example: 3 out of 6 shared interests = +15 points.
- **Same City**: +15 points. Living in the same city grants +10 points.
- **Education Match**: +10 points.
- **Same Occupation**: +10 points.
- **Lifestyle Match**: +15 points.
- **Gender Preference Alignment**: Automatic disqualification if preferences do not align.

Each attribute’s score is **multiplied by its weight** and summed to produce a final compatibility score. The system ranks matches based on this score, presenting users with the most compatible profiles.

Users can **adjust the weight** of each attribute within the Profile Management tab. For instance, a user who values shared interests more than location can increase the interest weight and decrease the location weight to tailor the matchmaking process.

---

# Screenshots of Matchmaking Results
## 1. **Profile Management Tab**
![Profile Management Tab](/assets/kbs_dating_1.png)

## 2. **Adjust Matchmaking Weights**
![Adjust Matchmaking Weights](/assets/kbs_dating_3.png)

## 3. **Matchmaking Tab**
![Matchmaking Tab](/assets/kbs_dating_4.png)

---

# Reflection on Limitations and Future Improvements

While our current implementation successfully connects users based on defined rules and custom preferences, several limitations exist:

- The system relies solely on **user-inputted data** and rule-based matching, which lacks adaptability and nuance.
- There is **no mechanism** to account for evolving user preferences or behavior patterns beyond the initial profile setup.

### Planned Improvements:
- Implement a **dynamic input system** allowing users to describe their ideal match in free text.
- Use **Natural Language Processing (NLP)** to process user input by removing stop words, normalizing text, and extracting key phrases.
- Match extracted keywords against profiles to factor in both explicit preferences and implicit compatibility indicators.
- Transition from `ipywidgets` to a **web-based platform like Streamlit**, enabling deployment as an interactive web application.

This deployment would make the system more accessible, facilitate user feedback, and support continuous improvement.

