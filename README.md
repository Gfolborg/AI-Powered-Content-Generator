<p align="center">
<img src="https://i.imgur.com/vt44gaX.png" height="40%" width="40%" alt="AI Automation Project Logo"/>
</p>

<h1>AI-Powered Content Generation Engine</h1>
<p>
This Intelligent Automation (IA) workflow is designed for Marketing Managers at the simulated Texas Cardiology Clinic of Houston. The system achieves hands-off, timely content creation tailored to the healthcare industry. It orchestrates multiple AI agents and APIs for research, drafting, and asset generation, enforcing strict Human-in-the-Loop (HITL) controls to ensure brand safety and quality before social publication.
</p>

<h2>Environments and Technologies Used</h2>

<ul>
    <li>n8n (Workflow Automation/Orchestration)</li>
    <li>Google Sheets (Approval Gate/Data Logging)</li>
    <li>Gemini AI (Research, Drafting, Image Prompt Generation, Iteration)</li>
    <li>Google Trends API (Real-time Topic Research)</li>
    <li>Nano Banana Image Generator (Image Asset Creation)</li>
    <li>Facebook API (Final Publication/End-to-End Delivery)</li>
</ul>

<h2>High-Level Deployment and Configuration Steps</h2>

<ul>
    <li>Configure the scheduled trigger for trend analysis and initial content draft creation.</li>
    <li>Implement immediate email notification for Human-in-the-Loop (HITL) review.</li>
    <li>Design the fast-polling regeneration loop for denied content, ensuring rapid iteration.</li>
    <li>Set up the final AI agent for image prompt optimization and asset generation.</li>
    <li>Build the final publishing module with robust, AI prompted error handling and success notifications.</li>
</ul>

<h2>Facebook Post Examples:</h2>
<p>
<img src="https://i.imgur.com/wt0WKqC.png" height="80%" width="80%" alt="Facebook Example 1"/>
<img src="https://i.imgur.com/VUBHWzB.png" height="80%" width="80%" alt="Facebook Example 2"/>
<img src="https://i.imgur.com/9Gh905A.png" height="80%" width="80%" alt="Facebook Example 3"/>
</p>


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/YnkCqhS.png" height="80%" width="80%" alt="Miro Workflow Design Diagram"/>
</p>
<p>
The workflow was meticulously mapped out using Miro to manage the complex, multi-agent branching logic, ensuring flawless data transfer and control flow across all modules.
</p>
<br />

<h3>Step 1: Scheduled Trend Analysis, Initial Draft, and Notification</h3>
<p>
<img src="https://i.imgur.com/BY5PtvY.png" height="80%" width="80%" alt="n8n Triggers"/>
</p>
<p>
<p> A weekly scheduled trigger initiates the process. </p>
<img src="https://i.imgur.com/lrqWVY9.png" height="30%" width="30%" alt="Close up triggers"/>
<img src="https://i.imgur.com/yYCmS8q.png" height="80%" width="80%" alt="Close up Trend Search"/>

The Content Creation Agent analyzes Google Trends for the top 3 trending topics according to the target keywords (e.g., "heart health"), drafts the social media post, and logs all data to Google Sheets. An email is immediately sent to the recipient notifying them that the content is ready for review and approval/denial.
<p>
    <img src="https://i.imgur.com/uixEqF2.png" height="40%" width="40%" alt="AI Content Creation"/>
</p>
<p>
    <img src="https://i.imgur.com/AHB5xSM.png" height="50%" width="50%" alt="Approval Email Example"/>
</p>


</p>
<br />

<h3>Step 2: Human-in-the-Loop (HITL) Fast Polling and Filtering</h3>
<table>
  <tr>
    <td><img src="https://i.imgur.com/8H792Y5.png" width="400" alt="Human-in-the-Loop Approval Filter"/></td>
    <td><img src="https://i.imgur.com/XePiogG.png" width="400" alt="Human-in-the-Loop Approval Filter"/></td>
  </tr>
</table>

<p>
A separate, high-frequency trigger polls the Google Sheet every minute looking for content marked 'No' in the Approval row and a written reason in the Denial Reason field. This ensures rapid detection of necessary changes, initiating the regeneration loop.
</p>
<br />

<h3>Step 3: Conditional AI Regeneration Loop</h3>
<p>
<img src="https://i.imgur.com/W3x1u64.png" height="40%" width="40%" alt="Regeneration Agent"/>
</p>
<p>
<img src="https://i.imgur.com/xdMlrqa.png" height="100%" width="100%" alt="Google Sheets Example"/>
</p>
<p>
The denied content is processed by a dedicated Regeneration Agent. This agent is specifically prompted to integrate the human-provided Denial Reason to create a new, optimized draft.</p>
<p>
<img src="https://i.imgur.com/ENU6yWg.png" height="80%" width="80%" alt="Google Sheets Example"/>
</p>
</p>
 <p>The Google Sheet row is updated with the revised content, and a new email is sent for pending approval, minimizing iteration time.
 <p>
     <img src="https://i.imgur.com/8Tmilvd.png" height="80%" width="80%" alt="Google Sheets Example"/>
 </p>
  
</p>
<br />

<h3>Step 4: Image Prompt Optimization and Asset Generation</h3>
<p>
    <img src="https://i.imgur.com/IF03bUm.png" height="100%" width="100%" alt="Image Generation Workflow"/>
</p>
<p>
The image generator workflow trigger polls Google Sheets row for new the row that needs an image and is approved.
<p>
    <img src="https://i.imgur.com/oW8eknt.png" height="30%" width="30%" alt="Image Workflow trigger"/>
</p>
<p>Once content is approved, a Gemini AI agent processes the final draft, generating a refined, high-quality prompt for Gemini's Nano Banana Image Generator. This step ensures the final image asset is perfectly aligned with the approved social media copy.
<p>
    <img src="https://i.imgur.com/6s57EP7.png" height="40%" width="40%" alt="AI Image Generator "/>
</p>
</p>
<br />

<h3>Step 5: Final Publishing and Robust AI Error Handling</h3>
<table>
  <tr>
    <td><img src="https://i.imgur.com/LsXrARc.png" width="400" alt="Image Turned into a link"/></td>
    <td><img src="https://i.imgur.com/0Y98pro.png" width="400" alt="AI Agent Post Content to Facebook"/></td>
  </tr>
</table>
<p>
The final content and image are posted to Facebook via the API. This module features robust, AI-driven error handling.
<p>If the post fails, an email is sent immediately to the recipient, including an AI generated analysis of the error and a suggested fix. 
</p>
<br/>
<p>
<img src="https://i.imgur.com/kRYgxA9.png" height="80%" width="80%" alt="Error email notification"/>
</p>
<p>
     <img src="https://i.imgur.com/gutzSP7.png" height="50%" width="50%" alt="Google Sheets Example"/>
 </p>
<br />
<p>If successful, a separate success notification confirms the post is live.</p>
<br/>
<p>
<img src="https://i.imgur.com/ZmXUV9Z.png" height="40%" width="40%" alt="Error email notification 1"/>
<img src="https://i.imgur.com/ow2JGRg.png" height="40%" width="40%" alt="Error email notification 2"/>
</p>
