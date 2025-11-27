## Hi there 👋
SELECT
    s.SID,
    s.SERIAL#,
    s.USERNAME,
    s.EVENT,
    s.MACHINE,
    s.STATE,
    s.SQL_ID,
    q.SQL_FULLTEXT AS SQL_TEXT,
    s.SECONDS_IN_WAIT AS SEC_WAITED,
    s.LAST_CALL_ET AS LAST_CALL_SEC
FROM
    V$SESSION s,
    V$SQL q
WHERE
    s.STATUS = 'ACTIVE'
    AND s.TYPE != 'BACKGROUND'
    AND s.SQL_ID = q.SQL_ID (+) -- Using (+) for a LEFT JOIN to ensure sessions without a current SQL_ID (like 'waiting for message') are still listed.
ORDER BY
    s.SECONDS_IN_WAIT DESC;





SELECT s.SID, s.SERIAL#, s.USERNAME, s.EVENT, s.MACHINE, s.STATE, s.SQL_ID, REPLACE(TRIM(s.SQL_TEXT), CHR(10), ' ') AS SQL, -- Using s.SQL_TEXT (from V$SQL/V$SESSION) or s.PREV_SQL_ID depending on the exact source s.SECONDS_IN_WAIT AS SECONDS_WAITED, -- Or just 'WAITING' state time.s.LAST_CALL_ET AS LAST_CALL FROM V$SESSION s WHERE s.STATUS = 'ACTIVE' AND s.TYPE != 'BACKGROUND' ORDER BY s.SECONDS_IN_WAIT DESC;


SELECT
    s.SID,
    s.SERIAL#,
    s.USERNAME,
    s.EVENT,
    s.MACHINE,
    s.STATE,
    s.SQL_ID,
    REPLACE(TRIM(s.SQL_TEXT), CHR(10), ' ') AS SQL, -- Using s.SQL_TEXT (from V$SQL/V$SESSION) or s.PREV_SQL_ID depending on the exact source
    s.SECONDS_IN_WAIT AS SECONDS_WAITED, -- Or just 'WAITING' state time
    s.LAST_CALL_ET AS LAST_CALL
FROM
    V$SESSION s
WHERE
    s.STATUS = 'ACTIVE'
    AND s.TYPE != 'BACKGROUND'
ORDER BY
    s.SECONDS_IN_WAIT DESC;




Subject: Coordination of Patching Schedule with AWS Cutover

Hi [Recipient’s Name],

As discussed over Teams, we noticed that the planned patching window overlaps with our AWS cutover night. Since the patching will be executed in a rolling fashion and only results in a partial outage, there is no expected impact to our activities.

To help streamline both efforts, we kindly request if the patching can be initiated around 11:30 PM. This timing will allow our cutover activities to commence at 9:00 PM as scheduled, and by then we should be completed with the critical database activities.

Please confirm if this adjustment can be accommodated. Your confirmation will help us align both change windows seamlessly.

Thank you for your support and collaboration.

Best regards,
[Your Name]



<!--
**sethni/sethni** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
We successfully implemented an innovative framework in our development environment for the first time within a TEF project. This marks a key step in enhancing our development process. As a developer, the new framework improves code efficiency, streamlines debugging, and fosters better maintainability—ultimately allowing us to deliver features faster and with higher quality
-->
