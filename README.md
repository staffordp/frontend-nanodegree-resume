<div id="readme" class="blob instapaper_body">
    <article class="markdown-body entry-content" itemprop="mainContentOfPage"><h2><a id="user-content-how-do-i-complete-this-project" class="anchor" href="#how-do-i-complete-this-project" aria-hidden="true"><span class="octicon octicon-link"></span></a>How do I complete this project?</h2>

<ol>
<li>Go to the <a href="https://www.udacity.com/course/ud804">Javascript Basics course</a> and select "View Course Materials."</li>
<li>Go through the videos and assignments in this course to learn the JavaScript necessary to build your resume.</li>
<li>Review your work against the Project Rubric (on the next page).</li>
<li>When you are satisfied with your project, submit it according to the Submission Instructions on the next page.</li>
</ol>

<h3><a id="user-content-by-the-end" class="anchor" href="#by-the-end" aria-hidden="true"><span class="octicon octicon-link"></span></a>By the end:</h3>

<p>Your resume will look something like this
<a href="https://camo.githubusercontent.com/f4c154444bc91d29cab9f120a480277f673015f5/687474703a2f2f692e696d6775722e636f6d2f7057553158626c2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/f4c154444bc91d29cab9f120a480277f673015f5/687474703a2f2f692e696d6775722e636f6d2f7057553158626c2e706e67" alt="" data-canonical-src="http://i.imgur.com/pWU1Xbl.png" style="max-width:100%;"></a></p>

<p>And your repository will include the following files:</p>

<ul>
<li><strong>index.html</strong>: The main HTML document. Contains links to all of the CSS and JS resources needed to render the resume, including resumeBuilder.js.</li>
<li><strong>js/helper.js</strong>: Contains helper code needed to format the resume and build the map. It also has a few function shells for additional functionality. More on helper.js further down.</li>
<li><strong>js/resumeBuilder.js</strong>: This file is empty. You should write your code here.</li>
<li><strong>js/jQuery.js</strong>: The jQuery library.</li>
<li><strong>css/style.css</strong>: Contains all of the CSS needed to style the page.</li>
<li><strong>README.md</strong>: 
The GitHub readme file.</li>
<li>and some images in the images directory.</li>
</ul>

<h2><a id="user-content-your-starting-point" class="anchor" href="#your-starting-point" aria-hidden="true"><span class="octicon octicon-link"></span></a>Your starting point...</h2>

<h3><a id="user-content-jshelperjs" class="anchor" href="#jshelperjs" aria-hidden="true"><span class="octicon octicon-link"></span></a>js/helper.js</h3>

<p>Within helper.js, you’ll find a large collection of strings containing snippets of HTML. Within many snippets, you’ll find placeholder data in the form of <code>%data%</code> or <code>%contact%</code>.</p>

<p>Each string has a title that describes how it should be used. For instance, <code>HTMLworkStart</code> should be the first <code>&lt;div&gt;</code> in the Work section of the resume. <code>HTMLschoolLocation</code> contains a <code>%data%</code> placeholder which should be replaced with the location of one of your schools.</p>

<h3><a id="user-content-your-process" class="anchor" href="#your-process" aria-hidden="true"><span class="octicon octicon-link"></span></a>Your process:</h3>

<p>The resume has four distinct sections: work, education, projects and a header with biographical information. You’ll need to:</p>

<ol>
<li><p>Build four JSONs, each one representing a different resume section. The objects that you create need to follow the names within the schema below exactly. Make sure your JSONs are formatted correctly using <a href="http://jsonlint.com/" target="_blank">JSONlint.com</a>.</p></li>
</ol>

<ul>
<li><p><code>bio</code> contains:</p>

<pre><code>    name : string
    role : string
    contacts : an object with
          mobile: string
          email: string 
          github: string
          twitter: string 
          location: string
    welcomeMessage: string 
    skills: array of strings
    biopic: url
    display: function taking no parameters
</code></pre></li>
<li><p><code>education</code> contains:</p>

<pre><code>    schools: array of objects with
         name: string
         location: string
         degree: string
         majors: array of strings
         dates: integer (graduation date)
         url: string
    onlineCourses: array with
         title: string
         school: string
         date: integer (date finished)
         url: string
    display: function taking no parameters
</code></pre></li>
<li><p><code>work</code> contains</p>

<pre><code>    jobs: array of objects with
         employer: string 
         title: string 
         location: string 
         dates: string (works with a hyphen between them)
         description: string 
    display: function taking no parameters
</code></pre></li>
<li><p><code>projects</code> contains:</p>

<pre><code>    projects: array of objects with
          title: string 
          dates: string (works with a hyphen between them)
          description: string
          images: array with string urls
    display: function taking no parameters
</code></pre></li>
</ul>

<ol>
<li>Iterate through each JSON and append its information to index.html in the correct section.

<ul>
<li>First off, you’ll be using jQuery’s <code>selector.append()</code> and <code>selector.prepend()</code> functions to modify index.html. <code>selector.append()</code> makes an element appear at the end of a selected section. <code>selector.prepend()</code> makes an element appear at the beginning of a selected section.

<ul>
<li>Pay close attention to the ids of the <code>&lt;div&gt;</code>s in index.html and the HTML snippets in helper.js. They’ll be very useful as jQuery selectors for <code>selector.append()</code> and <code>selector.prepend()</code></li>
</ul></li>
</ul></li>
<li>You’ll also be using the JavaScript method <code>string.replace(old, new)</code> to swap out all the placeholder text (e.g. <code>%data%</code>) for data from your resume JSONs.</li>
<li>Here’s an example of some code that would add the location of one your companies to the page:

<ul>
<li><code>var formattedLocation = HTMLworkLocation.replace("%data%", work.jobs[job].location);</code></li>
<li><code>$(".work-entry:last").append(formattedLocation);</code></li>
<li>Use the mockup at the page of this document as a guide for the order in which you should append elements to the page.</li>
</ul></li>
<li>The resume includes an interactive map. To add it, append the googleMap string to <code>&lt;div id=”mapDiv”&gt;</code>.</li>
<li>All of your code for adding elements to the resume should be within functions. And all of your functions should be encapsulated within the same objects containing your resume data. For instance, your functions for appending work experience elements to the page should be found within the same object containing data about your work experience.</li>
<li>Your resume should also <code>console.log()</code> information about click locations. On line 90 in helper.js, you’ll find a jQuery onclick handler that you’ll need to modify to work with the <code>logClicks(x,y)</code> function above it.</li>
<li>It’s possible to make additional information show up when you click on the pins in the map. Check out line 174 in helper.js and the Google Maps API to get started.</li>
