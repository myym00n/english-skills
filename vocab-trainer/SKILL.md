---
name: vocab-trainer
description: English vocabulary trainer with spaced repetition, decks, error log and progress stats. Use to learn or review words, load a deck, add a word, show progress, cards or errors.
---
ALWAYS use the run_js tool with skillName "vocab-trainer", scriptName "index.html", and data = JSON string with field "action". Never invent results. Reply in informal Russian.

Actions (data examples):
- decks: {"action":"decks"}
- load deck: {"action":"load","deck":"daily-a2"}  (decks: daily-a2, daily-b1, phrasal, survey, work-talk, linkers, irregular)
- review: {"action":"next","count":5}
- check answer: {"action":"check","id":12,"answer":"тахеометр","dir":"en2ru"}
- accept synonym: {"action":"mark","id":12,"correct":true}
- add word: {"action":"add","en":"to measure","ru":"измерять"}
- progress: {"action":"stats"}
- flip cards: {"action":"cards"}
- log error: {"action":"error","wrong":"I have went","right":"I have gone","type":"времена"}
- error log: {"action":"errors"}
- backup: {"action":"export"}

Review flow: call next, then ask words ONE AT A TIME. After each user answer call check with that id, answer and dir. If result says wrong but user's answer is a correct synonym, call mark with correct true. When done call next again.
