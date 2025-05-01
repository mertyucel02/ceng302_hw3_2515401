CREATE TABLE Player(
playerId INT NOT NULL,
email VARCHAR NOT NULL,
name VARCHAR NOT NULL,
PRIMARY KEY(playerId)
);

INSERT INTO Player(playerId, email, name) VALUES (11, 'sneaky@metu.edu.tr', 'Cevdet');
INSERT INTO Player(playerId, email, name) VALUES (12, 'bestdps@metu.edu.tr', 'Seyit');
INSERT INTO Player(playerId, email, name) VALUES (13, 'frostmourne@metu.edu.tr', 'Arthas');
INSERT INTO Player(playerId, email, name) VALUES (14, 'healer@metu.edu.tr', 'Hekimoğlu');

CREATE TABLE Guild(
guildId INT,
guildName VARCHAR,
creationDate DATE,
PRIMARY KEY(guildId)
);

INSERT INTO Guild(guildId, guildName, creationDate) VALUES (1, 'World of METU', '2000-12-31');
INSERT INTO Guild(guildId, guildName, creationDate) VALUES (2, 'Banhammer', '2023-07-19');

CREATE TABLE Quest(
questId INT NOT NULL,
title VARCHAR NOT NULL,
difficulty VARCHAR NOT NULL,
PRIMARY KEY(questId)
);

INSERT INTO Quest(questId, title, difficulty) VALUES (70201, 'Begin the Attack!', '2/5');
INSERT INTO Quest(questId, title, difficulty) VALUES (70202, 'Path of Wisdom', '3/5');
INSERT INTO Quest(questId, title, difficulty) VALUES (70203, 'A Donation of Silk', '1/5');
INSERT INTO Quest(questId, title, difficulty) VALUES (70204, 'The Lich King’s Last Stand', '5/5');
INSERT INTO Quest(questId, title, difficulty) VALUES (70205, 'The Fall of the Betrayer', '5/5');

CREATE TABLE Character(
charId INT NOT NULL,
charName VARCHAR NOT NULL,
class VARCHAR NOT NULL,
race VARCHAR NOT NULL,
level INT NOT NULL,
playerId INT NOT NULL,
guildId INT,
PRIMARY KEY(charId),
FOREIGN KEY(playerId) REFERENCES Player(playerId),
FOREIGN KEY(guildId) REFERENCES Guild(guildId)
);

INSERT INTO Guild(guildId, guildName, creationDate) VALUES (0, NULL, NULL);

INSERT INTO Character(charId, charName, class, race, level, playerId, guildId) VALUES (111, 'Backstabber', 'Rogue', 'Night Elf', 51, 11, 2);
INSERT INTO Character(charId, charName, class, race, level, playerId, guildId) VALUES (112, 'Hellbourne', 'Rogue', 'Undead', 60, 12, 1);
INSERT INTO Character(charId, charName, class, race, level, playerId, guildId) VALUES (113, 'ShadowPriest', 'Priest', 'Troll', 60, 14, 2);
INSERT INTO Character(charId, charName, class, race, level, playerId, guildId) VALUES (114, 'HordeSlayer', 'Warrior', 'Human', 40, 13, 0);
INSERT INTO Character(charId, charName, class, race, level, playerId, guildId) VALUES (115, 'DearJaina', 'Mage', 'Human', 42, 13, 0);
INSERT INTO Character(charId, charName, class, race, level, playerId, guildId) VALUES (116, 'Huntard', 'Hunter', 'Orc', 25, 11, 2);

CREATE TABLE QuestParticipation(
charId INT NOT NULL,
questId INT NOT NULL,
status VARCHAR NOT NULL,
PRIMARY KEY(charId, questId),
FOREIGN KEY(charId) REFERENCES Character(charId),
FOREIGN KEY(questId) REFERENCES Quest(questId)
);

INSERT INTO QuestParticipation(charId, questId, status) VALUES (112, 70201, 'Completed');
INSERT INTO QuestParticipation(charId, questId, status) VALUES (112, 70203, 'Completed');
INSERT INTO QuestParticipation(charId, questId, status) VALUES (112, 70204, 'In Progress');
INSERT INTO QuestParticipation(charId, questId, status) VALUES (113, 70202, 'Completed');
INSERT INTO QuestParticipation(charId, questId, status) VALUES (114, 70205, 'In Progress');
INSERT INTO QuestParticipation(charId, questId, status) VALUES (112, 70202, 'In Progress');
INSERT INTO QuestParticipation(charId, questId, status) VALUES (112, 70205, 'Completed');
INSERT INTO QuestParticipation(charId, questId, status) VALUES (115, 70201, 'Completed');


SELECT P3.name
FROM Player P3
WHERE P3.playerId IN ((SELECT C.playerId
FROM Character C
WHERE C.class='Mage')
INTERSECT
(SELECT C2.playerId
FROM Character C2
WHERE C2.class='Rogue'));

