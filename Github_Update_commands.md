Jab local folder pehle se hi GitHub repository se connected ho, toh updated code push karne ke liye pehle ussi folder mein right click karke Git Bash kholte hai, phir usmein yeh standard commands type karte hai:

### 1. Changes stage karein

Saari nayi aur modified files ko stage karne ke liye:

```bash
git add .
```

* **Verify karne ke liye:** `git status` chalayein. Modified files green color mein dikhni chahiye.

### 2. Changes commit karein

Apne updates ke saath ek descriptive message likh kar commit karein:

```bash
git commit -m "Update message"
```

* **Verify karne ke liye:** Terminal par `[branch-name commit-hash] Update message` jaisa output aayega.

### 3. Code GitHub par push karein

Code ko remote repository par bhejane ke liye:

```bash
git push origin main
```

* **Verify karne ke liye:** Output mein `Writing objects: 100%` aur branch update hone ka message aayega. Uske baad GitHub repository ke webpage ko refresh karke latest commit check kar sakte hain.

### Useful Tip (Merge Conflict se bachne ke liye)

Agar repository par kisi aur ne ya aapne kisi doosre device se commit kiya hai, toh hamesha `push` karne se pehle latest code pull kar lena chahiye:

```bash
git pull origin main
```