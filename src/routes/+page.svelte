<style>
    @import url('https://fonts.googleapis.com/css2?family=Golos+Text&family=Syne:wght@800&display=swap');
body{
    background: #011AFC;
    

}
.bdy{
    background-color: #011AFC;
    height: 1024px;
}
.ec{

/* Ellipse 7 */

position: absolute;
width: 340px;
height: 340px;
left: 650px;
top: 264px;

background: #000000;
filter: blur(200px);

    }
.ecimg{
position: absolute;
top:60px;
left:650px ;
width:340px;
}
.botname{
width: 517px;
height: 100px;


font-family: 'Syne';
font-style: normal;
font-weight: 800;
font-size: 100px;
line-height: 100%;
/* identical to box height, or 100px */

text-align: center;

color: #FFFFFF;


}
.botdesc{
width: 581px;
height: 52px;
font-family: 'Golos Text', sans-serif;
font-style: normal;
font-weight: 400;
font-size: 27px;
line-height: 26px;
/* or 96% */

/*margin-top: -80px;*/
color: rgba(255, 255, 255, 0.7);

}
.botbtn{
margin-top: 40px;
border-style: none;
font-family: 'Golos Text', sans-serif;
display: flex;
flex-direction: row;
justify-content: center;
align-items: center;
padding: 16px 44px;
gap: 10px;

left: 9.24%;
right: 66.94%;
top: 57.42%;
bottom: 37.3%;
width:220px;
background: #FFFFFF;
box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
border-radius: 8px;
color:#000000;
}
.usrtxt{
font-family: 'Golos Text', sans-serif;
color:white;
margin-top: 30px;
}
.lft{
margin-left: 80px;
}
.profile{
display: inline-block;
width: 50px;
height: 50px;
}
.navbar{
width: 100%;
display: block;
padding: 20px;
color:white;
margin-bottom: 50px;

}
.navlogo{
width:175px;
margin-left: 70px;
font-family: 'Golos Text', sans-serif;
display: inline-block;
}
a{
text-decoration: none;
font-family: 'Golos Text', sans-serif;
margin-left:36px;
margin-top:-10px;
}
.wabtn{
padding: 10px;
margin-top: -5px;
background-color: #000000;
color:white;
border: none;
width:247px;
font-family: 'Golos Text', sans-serif;
font-weight: 100px;
border-radius: 10px;
float: right;
margin-right:30px;
display: inline-block;
}

.users{
    margin-bottom: 100px;
    margin-top: 10px;
}

</style>
<div class="bdy">
<div class="navbar">
    <img class="navlogo" src="logo.png">
    <a href="">About</a>
    <a href="">Privacy Policy</a>
    <button class="wabtn">Chat on Whatsapp</button>

</div>
<div class="lft">
<div >
<p class="botname">KABIR</p>
<p class="botdesc">Knowledgeable Artificial Intelligence Bot for Investigating and Resolving cybercrimes</p>
<a href="/chat"><button class="botbtn">GET STARTED</button></a>
</div>
<div>
<p class="usrtxt">Already helped more than 1000+ users 💙</p>
<div>
    <div class="users" ><img class="profile"src="dp.png">
        <img class="profile"src="dp.png">
        <img class="profile"src="dp.png">
        <img class="profile"src="dp.png">
        <img class="profile"src="dp.png">
        <img class="profile"src="dp.png">
    </div>
</div>

</div>
</div>

<div>
<!-- svelte-ignore a11y-missing-attribute -->
<img class="ecimg" src="kabir.png">
<div class="ec">
</div>
</div>

</div>
