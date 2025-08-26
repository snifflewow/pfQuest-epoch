# How to contribute

# Table of Contents
- [Introduction](#introduction)
- [Macros](#macros)
- [Example](#example)
- [via issue](#issue)
- [via pull request](#issue)

---

## Introduction {#introduction}

The database format in use, is similar to the existing pfQuest databases.
You might want to also look into the "pfQuest-tbc" databases to learn how entries could be removed or manipulated.

Demo quest commit: [Do Slavers Keep Records?
](https://github.com/snifflwow/pfQuest-epoch/commit/39abc567413a0c004ea22ec38fed4eb2e486e9d6)

## Macros {#macros}

Your Current Cords:
`/script SetMapToCurrentZone() local x,y=GetPlayerMapPosition("player") DEFAULT_CHAT_FRAME:AddMessage(format("%s, %s: %.1f, %.1f",GetZoneText(),GetSubZoneText(),x*100,y*100))`
[Zone IDs](https://github.com/Bennylavaa/wowchat-epoch/blob/main/src/main/resources/pre_cata_areas.csv)

Targeted Unit Information:
`/run local guid = UnitGUID("target"); local npcId = tonumber(string.sub(guid, 8, 12), 16); local npcName = UnitName("target"); print("NPC ID:", npcId, "NPC Name:", npcName)`

Selected QuestLog Data:
`/run local t, l, _, _, _, _, _, _, i = GetQuestLogTitle(GetQuestLogSelection()); print("\nID:"..i.."\nLevel:"..l.."\n[\"T\"] "..t.."\n[\"O\"] "..QuestInfoObjectivesText:GetText().."\n[\"D\"] "..QuestInfoDescriptionText:GetText())`

Hover Over Item ID:
`/run local _, link = GameTooltip:GetItem(); if link then local itemID = tonumber(link:match("item:(%d+):")); if itemID then print("Item ID:", itemID) end end`

Object ID:
No Possible way to get this info currently

## Example {#example}

## Issue {#issue}

##  Pull request {#pull-request}
If you wish to add more content, feel free to contribute and send [Pull Requests](https://github.com/snifflewow/pfQuest-epoch/pulls).

notes:
macros
coordinates
structure
example
pr or issue with update
