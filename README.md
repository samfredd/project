
Mini Unsplash Clone

A responsive, feature-rich web application replicating the core functionalities of Unsplash. Built with Vue.js, this project enables users to search and browse high-quality photos seamlessly. Leveraging the Unsplash API, it presents images in a dynamic, staggered grid layout with smooth interactions and user-friendly features.

Table of Contents

	•	Demo
	•	Features
	•	Technologies
	•	Installation
	•	Usage
	•	API Configuration
	•	Project Structure
	•	Future Enhancements
	•	Contact

Demo

Live Demo

Features

	•	Responsive Staggered Grid Layout: Displays photos in a masonry-like grid, adapting to various screen sizes.
	•	Search Functionality: Users can search for photos using keywords.
	•	Author & Location Information: Displays the photographer’s name and location for each photo.
	•	Tint Overlay: Ensures text readability over images with varying backgrounds.
	•	Loading Placeholders: Provides visual feedback while images are being fetched.
	•	Image Modal: View any image in larger resolution within a modal by clicking on it.
	•	Infinite Scrolling: Automatically loads more images as the user scrolls down.
	•	Accessible Design: Fully keyboard navigable and screen reader friendly.
	•	Vue.js Integration: Utilizes Vue.js for reactive, component-based architecture.

Technologies

	•	Frontend: Vue.js (v3), Vue Router, Axios for HTTP requests
	•	Styling: CSS3, Flexbox, CSS Grid, Animations & Transitions
	•	API: Unsplash API
	•	Build Tools: Vue CLI

Installation

Prerequisites

	•	Node.js (v14 or later)
	•	npm or Yarn

Steps

	1.	Clone the Repository

git clone https://github.com/samfredd/project.git


	2.	Install Dependencies
Using npm:

npm install

Or using Yarn:

yarn install


	3.	Obtain Unsplash API Access Key
	•	Sign up or log in to Unsplash Developers.
	•	Create a new application to get your Access Key.
	4.	Configure Environment Variables
	•	Create a .env file in the project root.
	•	Add your Unsplash Access Key:

VUE_UNSPLASH_ACCESS_KEY=your_unsplash_access_key_here


	5.	Run the Development Server
Using npm:

npm run dev

Or using Yarn:

yarn dev

The application should now be running at http://localhost:3000 (or the port specified by Vite).

Usage

	1.	Search for Photos
	•	Enter a keyword into the search bar and press “Enter” or click the “Search” button.
	•	The grid will update with photos matching your search query.
	2.	Browse Photos
	•	Scroll through the grid to view a variety of photos.
	•	Infinite scrolling will load more images as you reach the bottom of the page.
	3.	View Photo Details
	•	Hover over any photo to see the photographer’s name and location.
	•	Click on a photo to open it in a modal for a larger view.
	4.	Close Modal
	•	Click the close button (×) at the top-right corner of the modal.
	•	Alternatively, click outside the image to close the modal.

Project Structure

mini-unsplash-clone/
│
├── public/
│   └── index.html          
│
├── src/
│   ├── assets/           
│   ├── components/         
│   │   ├── ImageGrid.vue
│   │   ├── ImageCard.vue
│   │   ├── SearchBar.vue
│   │   └── ImageModal.vue
│   ├── views/              
│   │   └── Home.vue
│   ├── store/              
│   ├── router/             
│   ├── App.vue             
│   ├── main.js             
│   └── styles/             
│       └── main.css
│
├── .env                    
├── .gitignore             
├── package.json          
├── README.md             

Future Enhancements

	•	User Authentication: Allow users to create accounts and save favorite images.
	•	Image Uploading: Enable users to upload their own photos.
	•	Advanced Filters: Add filters for image orientation, color, etc.
	•	Performance Optimizations: Implement lazy loading and optimize image sizes for faster load times.

Contact

	•	Email: solugbenga393@gmail.com
	•	LinkedIn: LinkedIn Profile
	•	GitHub: GitHub Profile

Feel free to reach out with any questions, suggestions, or feedback. Happy browsing!