# Reactdesignapp
Zinc is an app designed to help people with interior design, built using React

Chapter 1: Why did we develop this app?

Opportunity
2020 has been a tough year for retail. One of the very few categories that is performing is hardware and paints, showing a 12% increase in sales, compared to -13% for retail overall (Coffey et al, 2020). Lockdowns have left us spending more time at home and more money on our homes, while restrictions on store openings have created a tipping point for e-commerce adoption among consumers.
All three team members are social science graduates, so having identified the commercial opportunity we did some research.

Consumer Behaviour
First, we conducted three 30 minute observational studies at Woodies DIY at The Blanchardstown Centre. Behaviours observed here confirmed the role mobile phone applications play in the path to purchase for home decorators. 
We witnessed shoppers using several apps before making a purchase - calculator to work out quantities required, notes app to refer to the measurements they had taken, camera to take pictures for future reference, social media to find the images that had initially inspired them and texts and calls to partners at home to confirm dimensions and approve the products being selected.
The observed behaviours were distilled into two user personas (Appendix A), to ensure the user was at the heart of the development process. Shannon the Stylista is a trend-led, commitment-free digital native. Fintan the Family Man is a convenience-led, time-pressed dad of four. This created simple decision-making criteria for features during the development process: Would it hold Shannon’s attention; Would it make life easier for Fintan?

Consumer Attitudes
We conducted an online survey (Appendix B), receiving over 350 responses, to assess consumer attitudes towards a home decorating application. 78% of respondents were open to using an app for their home decorating projects, with the three main pain points identified as: 
Assessing quantity of materials needed (85%)
Interior design (82%)
Budgeting (76%)


Chapter 2: How did you design the app? 

All three team members had worked in sectors badly affected by the pandemic. The project gave us the perfect chance to combine our pre-COVID work experience with what we had learned on the course. 

Conor had run his own online travel company, so he became our developer. Paula’s photography career had given her the Photoshop skills to work on our graphics and become our designer while Ian’s retail strategy experience led him to focus on product selection and UX - a great combination of skills that made task allocation easy (Appendix C).

Wireframe

Informed by the user requirements identified by our research, we started by creating a wireframe (Appendix D) to use as a blueprint for the course of the project. We devised a three point process - MEASURE - BUDGET - SELECT - that meets the customer pain points and is easy to understand. 

The mobile phone is a high-distraction environment (Al-Nuaim and Al-Harigy, 2015), so the process is short and numbered. The user knows where they are at all times, what is coming next and therefore less likely to abandon the process midway.

Home page

We opted for a large, bold sans-serif font (montserrat) for our logo, in keeping with the trend seen everywhere from luxury brands like Burberry and Saint Laurent to our own Maynooth University. Sans-serif fonts are popular for brand logos because they render sharply in different screen sizes (Livni, 2018), a useful quality given that Peter Mooney chose to teach us React in part because of its ability to adapt to different screen sizes.

Our three step process is made clear through the use of bold vector images and large numbers, while supporting text is designed to ensure the customer feels in control and unintimidated - “ Home Decorating Made Easy”, “We’ll do the math”, “Plan with confidence” and “You decide!”

The button, as with all buttons throughout the app, displays a clear call to action, rather than a generic ‘next’, so that the customer is invited to participate and knows what is going to happen when they press.

1. Measure Your Wall

The page header, as is the case on each page, lets the user know where they are in the process and what they need to do on this page.

The page has minimal text and a clear graphic to illustrate the measurements required. The input boxes are wide, spanning the entire screen, and centered in the middle of the page, where touch response is most accurate (Hoober, 2017). 

Numeric input is favoured over a dropdown given the precision required. The dimensions of the room are not likely to change during the selection process.

Here and throughout the app, the button to proceed to the next page is only made available through conditional rendering once a suitable input has been received by the user.

2. Set Your Budget

Here sliders are used, rather than numeric input, as the user’s thoughts on budget could change quickly and frequently. The slider affords an easy flexibility that re-entering numbers into a box would not, especially given that 75% of smartphone users navigate the screen with one thumb (Hoober, 2017). Setting both a minimum and a maximum budget will lead to a more concise selection of products on the results page. 

3. Select A Finish

Hick’s Law (Oxford Reference) suggests that the more options the customer is shown, the longer it will take them to make a decision. To help the user with their decision-making, we’ve created a selection process that prevents them from feeling overwhelmed.

We firstly offer the choice between paint or wallpaper. When that decision has been made, a submenu appears, offering a choice between four distinct styles: Bold, Pastel, Rich and Neutral for paint; Classic, Floral, Retro and Graphic for wallpaper. The image-led, grid format is inspired by a Buzzfeed quiz (Perpetua, 2017), easy and fun.

The categories and large visuals encourage the user to think about the mood they would like to set in the home, provide design inspiration and a more realistic product representation than a small colour card.

Results page

At the end of the process, you are presented with a selection of products that meet your style and budget criteria, alongside a calculation of how many units of that product you will need for the measurements entered and the total cost.

Hyperlinks can take you to the product page of the affiliated retailer to purchase the product. We also suggest some accessories you may require to complete your home decoration project, either undercoat, brushes and rollers or wallpaper paste and tools.

Chapter 3: How did you implement the functionality in the app?
Our app was coded using CodeSandbox and the functionality was implemented by calling classes in the main app function.

Using conditional rendering controlled by boolean values in this.state on the App.js page, we controlled which page the user was currently on. Data was passed from the child components via a callback using this.props, on each button click. The button clicks provided multiple operations, controlling the boolean values for conditional rendering, and verifying that user-input was correct using a disabled/enabled boolean.

We used a form text box to take user-input for the height and width, using functions to handle the changes of state, and declared the variable inside the render to calculate the area. The area is then sent to App.js using this.state and the callback function. The button will not appear until the user has inputted both a height and a width in numeric form- as it’s based on an area containing a number larger than 0.

We used a slider to set the user’s budget, with conditional rendering to display an error message if the maximum price was set at lower than the minimum price.The state was again controlled in two functions, value 1 and value 2, and both states were passed via another callback to App.js. We imported the Slider function from the React Semantic UI Range (NPM, 2020)


The selection choice of both the finish (Paint or Wallpaper) and the style was achieved by using conditional rendering and an onClick inside each <img> tag.  The user’s selection is saved and passed from each image click to App.js, where the choices made are rendered below. The button is disabled until both the style and finish variables are greater than 0, and using boolean values, it is impossible for the user to pick a wallpaper finish with paint, or vice versa. 


On the results page, the Json library was imported from Github using async. Each of the user inputs (The area, max and min slider values, and the finish and style selection) were sent to App.js from their respective components, and from App.js passed to the results component. The data were then entered into a filter function and a formula, with the results rendered on a table. The filter function accepted user inputs for the following;
Area
Budget - maximum and minimum spend
Finish selection
Style selection



An additional products table was displayed, with the contents depending on your previous selections. This was done by conditional rendering, based on the this.props.style selection. The details of your selections are also displayed on the bottom of the page. A ‘return to start’ button was included on the final page that reset the state of each variable, and returns you to the home screen.


We used Bootstrap and CSS in our app. Bootstrap was used for our buttons, input fields, images and table rendering. CSS was used for our font.













Pages were tested individually for their core functionality before being brought together in CodeSandbox







Chapter 4: Overall evaluation – An honest appraisal of the app. 

The project was a success! We met the technical brief of three working functions (user input, selection and calculation) while addressing the need our research identified for a tool that helps with budgeting, quantities and interior design. 

The timeframe didn’t allow for us to build every feature from our wireframe, so these would be the first elements to improve, along with some stretch projects like AR and chat-app functionality.
Design
We have endeavoured to keep the user interface simple and uniform with the same font colours throughout. We also kept the UI simple with the user in mind. In the context of having more time and resources, we would continue to build on this, e.g. having the min-max budget settings on one shared slider or highlighting the images that have been selected. We would conduct user testing, taking the feedback to improve the aesthetic and user experience.
User Login
Enabled by Firebase, having a user login would then afford the ability to retain previous searches and favourites.
Favourites
Most of us use apps on the go so if interrupted or unsure about what choices to make, being able to favourite previously accessed options would be ideal to save time the next time the user is accessing the app.
Augmented Reality capabilities
React has AR capabilities we would like to explore to make it even easier for our users to visualise their space before purchasing. On the Shopify ecommerce platform, product pages with AR functionality show a 94% higher conversion rate than those without (Papagiannis, 2020). 
Online chat function with an interior designer
Online chat with an interior designer is a feature that would be worth considering, given that interior design advice is one of the main pain points we have identified from our survey. 
New product categories
The 3 step functionality we’ve created could also be easily applied to other DIY categories - flooring, tiling… everything but the kitchen Zinc!



Bibliography
Al-Nuaim H, Al-Harigy L, 2015, User Interface Context of Use Guidelines for Mobile Apps, Available from:   <https://www.cscjournals.org/manuscript/Journals/IJHCI/Volume6/Issue3/IJHCI-120.pdf> [accessed 12 October 2020]
Brugnoli, G n.d., Connecting the Dots of User Experience, Journal of Information Architecture [online], 1(1), pp 6-15. Available from:  <http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.178.207&rep=rep1&type=pdf> [accessed 12 October 2020]
Coffey C, Doorley K, O’Toole C, Roantree, B, (2020) The effect of the Covid-19 Pandemic on consumption and indirect tax in Ireland, ESRI Budget Perspectives 2021, Paper 3, Available from: <https://www.esri.ie/system/files/publications/BP202103.pdf> [accessed 01 November 2020] 
Hoober, S. (2017), Mobile Matters: Design for Fingers, Touch and People – Part 1, UX Matters, Available from: <https://www.uxmatters.com/mt/archives/2017/03/design-for-fingers-touch-and-people-part-1.php> [accessed 01 December 2020]
Kjelsdov, J n.d., Chapter 9: Mobile Computing, The Encyclopedia of Human-Computer Interaction 2nd.ed [online] Available from: <https://www.interaction-design.org/literature/book/the-encyclopedia-of-human-computer-interaction-2nd-ed/mobile-computing> [accessed 28 November 2020]
Livni, E. (2018), You aren’t imagining it – every brand logo looks the same now, Quartz, Available from:<https://qz.com/quartzy/1507040/every-brand-logo-looks-the-same-now/> [accessed 31 October 2020]
NPM React Semantic UI Range, computer software, downloaded 10 December 2020 <https://www.npmjs.com/package/react-semantic-ui-range>
Oxford Reference (2020) Hick’s Law, Oxford Reference, Available from: <https://www.oxfordreference.com/view/10.1093/oi/authority.20110803095935267> [accessed 12 November 2020]
Papagiannis, H. (2020) How AR Is Redefining Retail in the Pandemic, Harvard Business Review [online]. Available from: <https://hbr-org.cdn.ampproject.org/c/s/hbr.org/amp/2020/10/how-ar-is-redefining-retail-in-the-pandemic> [accessed 01 November 2020].
Perpetua, M (2017)Your Taste In Home Decor WIll Reveal Your Personality Type, Buzzfeed, Available from: <https://www.buzzfeed.com/perpetua/decor> [accessed 16 November 2020]

















Appendix D - Wireframe



