<script>
    export default {

    }
</script>
<template>


	<div>
        <input type="checkbox" id="slide" name="" value="" />
        <div class="container">
		<label for="slide" class="toggle">☰</label>
		<nav class="sidebar"> 
			<ul>
				<li><a href="#"> Home </a></li>
				<li><a href="#"> Nav2 </a></li>
				<li><a href="#"> Nav3 </a></li>
				<li><a href="#"> Nav4 </a></li>
				<li><a href="#"> Nav5 </a></li>
			</ul>
		</nav>
	</div>
    </div>

</template>

<style>


html, body {
margin: 0;
padding: 0; }


.toggle {
text-decoration: none;
font-size: 2em;
color: rgba(0, 0, 0, 0.61);
-webkit-transition: all 0.15s ease-out 0;
-moz-transition: all 0.15s ease-out 0;
transition: all 0.45s ease-out 0;
position: fixed;
top: 20px;
left: 20px;
z-index: 10;
cursor: pointer;
}

.sidebar {
position: fixed;
top: 0px;
bottom: 0px;
left: -190px;
z-index: 4;
-webkit-transition: all 0.15s ease-out 0;
-moz-transition: all 0.15s ease-out 0;
transition: all 0.15s ease-out 0;
width: 8rem;
padding: 1.5em;
background: #19C4BC; 
}

.sidebar ul {
list-style: none;
margin: 0;
padding: 0; 
}

.sidebar li a {
color: #fff;

font-size: 1.2em;
margin: 0;
margin-bottom: 16px;
cursor: pointer;
text-decoration: none;
line-height: 200%;
}

.sidebar a:hover {
  color: rgba(0, 0, 0, 0.61); 
}

#slide:checked + .container .sidebar {
left: 0px;
 }

#slide:checked + .container .toggle {
left: 200px;
 }


#slide {
display: none; 
}


</style>