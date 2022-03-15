# liveProject
TTA Live Project Creating Site for UC Construction

<h1> Overview: </h1>

During the end of my UI/UX Design boot camp at The Tech Academy, I took part in a Live Project in which a team member and I collaborated designs and created a web page for a construction company. In the two week span of the project, I created a logo, wireframes, mockups, prototypes, and a working home page that was viewable in mobile, tablet, and desktop. During this time, I was able to work in Azure DevOps and coordinate with a team member and instructor in Scrum Meetings. I experienced what it was like to work on a team and coordinate design elements such as which logo and font families to use, nav and footer layouts, and overall feel of the designs. (Note: The logo we decided to use in our designs was created by my partner, Rob Corpus.)
![UC Desktop](https://user-images.githubusercontent.com/96311253/158440821-1cb15276-f532-481a-b90e-14043dcfbc54.png)


<h1> Problem Solving: </h1>

I was having trouble getting the nav to stick to the top on the mobile and tablet version. I had set the position to fixed and top to 0, but it was still scrolling past the top of the nav before sticking in place. After working with my instructor a little, I found the error was that some of my elements were sized over 100% width which was causing this issue. 

```
/*====================
    Mobile Header
====================*/
img#mhHeaderBGImg {
    width: 100%; <------------------ This was set to 110% 
    height: auto;
    position: absolute;
    z-index: 0;
}

/*========================
  HAMBURGER NAV Mobile
========================*/
.mhNavbar {
    top: 0;
    position: fixed;
    z-index: 2;
    background-color: white;
    width: 100%;
}

.mhTopNav {
    overflow: hidden;
    position: fixed;
    z-index: 2;
    display: block;
    top: 0;
    left: -1em;
    width: 400px;
    height: 800px;
}
```


After changing this, my first section was being overlapped by the header banner and couldn’t be moved. It was as if the two elements were stuck together. I picked at my code for an hour before reaching out to my instructor. After not being able to find the error, we collectively decided it would be best for me to revert to the version of code I had started with at the beginning of the day and start making changes from there, testing along the way. I took a break and came back to it the next morning. I realized that by setting the position  of the section to absolute I could fix this without sacrificing all of my hard work. I thought it wasn’t going to work previously, as the header banner completely disappeared when doing so. I figured out that the section wasn’t disappearing, but rather just being moved up above the page. I quickly changed my margins and got everything working correctly. 


```
.mhRow {
    text-align: center;
    position: absolute; <--------------This was set to relative causing it to  stick to the header banner
}
```


<h1> Challenges: </h1>

I designed the nav to be more of a triangular shape to fit with the flow of the page. I was not sure how to do this in CSS so after quickly researching I learned how to set the clip-path for a polygon and got our nav to look the way I wanted.

```
 #mhLinks {
    display: none;
    text-align: left;
    position: absolute;
    z-index: 2;
    text-decoration: none;
    color:#0E4456;
    top: 3em;
    left:0;
    width: 100%;
    height: 30em;
    padding: 0.5em 0 0 2em;
    background-color: #fffffffa;
     clip-path: polygon(0 0, 0 100%, 80% 0);
}
    
```

![UC Mobile Nav](https://user-images.githubusercontent.com/96311253/158442865-706911ff-eab8-4d95-b8dc-c923295cda15.png)


I wanted to have a text overlay that faded in and out on hover for some of the images as if they were links to other pages on the site. I had done this in a previous course, but had some issues doing so. I was able to quickly figure it out that I needed to do a transformation changing the opacity of the overlay from 0 to 1. 

```
.mhTextBox {
    width: 200px;
    height: 200px;
    margin-left: .8em;
    margin-top: -12.3em;
    opacity: 0;
    position: absolute;
    z-index: 3;
    color: white;
    background-color: #00000069;
}

.mhTextBox:hover{
    transition: opacity 1s ease-in-out;
    opacity: 1;
}
```
