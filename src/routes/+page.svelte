<script>
	import 'aos/dist/aos.css';
	// @ts-ignore
	import AOS from 'aos';

	import { onMount } from 'svelte';
	/*
  ___  _                    _  _
 / __|| |_   ___  _ _  _ _ | || |
| (__ |   \ / -_)| '_|| '_| \_. |
 \___||_||_|\___||_|  |_|   |__/
	*/

	console.log('%c  ___  _                    _  _ \n / __|| |_   ___  _ _  _ _ | || |\n| (__ |   \\ / -_)| \'_|| \'_| \\_. |\n \\___||_||_|\\___||_|  |_|   |__/ \n \nCh$rry network | https://cherrybot.xyz | https://discord.gg/aTGSF4U6f4', 'color: #e06c75');
	console.log('%cWait! it seems like you\'re a developer. Check out: \n|- API: https://docs.cherrybot.xyz \n|- Bot Dev: https://www.github.com/clapann\n|- Site Dev: https://www.github.com/forloopcodes'
		, 'color: #bada55');
	$: screenWidth = 0;
	$: size0 = screenWidth <= 800 && screenWidth > 0
	$: size1 = screenWidth <= 1250 && screenWidth > 800
	$: size3 = screenWidth <= 3000 && screenWidth > 2000
	let pagescrollY = 0;
	let elementOneMarginX = 0;
    let MouseX = 0;
    let MouseY = 0;
	let finalStyleOfMouseFollower = [
		'w-44',
		'h-44', 'opacity-5',
		'from-neutral-400', 'to-neutral-500',
		'rounded-full',
		'animate-pulse'
	]
		.join(' ');
	let initStyleOfMouseFollower = [
		'w-40',
		'h-40', 'opacity-10',
		'from-neutral-100',
		'to-neutral-300',]
		.join(' ');
	onMount(() => {
		AOS.init();
		window.addEventListener('scroll', () => {
			pagescrollY = window.scrollY;
			if (pagescrollY < 1833) {
				elementOneMarginX = 10;
			} else {
				elementOneMarginX = size0 ? 200 - (pagescrollY - 1833) / 10 : 100 - (pagescrollY - 1833) / 15;
					//140 - (pagescrollY - 1833) / 10;
			}
		});
        window.addEventListener('mousemove', (e) => {
            MouseX = e.clientX;
            MouseY = e.clientY;
        });
		screenWidth = window.innerWidth;
		size0 = screenWidth <= 800 && screenWidth > 0
		size1 = screenWidth <= 1250 && screenWidth > 800
		size3 = screenWidth <= 3000 && screenWidth > 2000
		window.addEventListener('resize', () => {
			screenWidth = window.innerWidth;
			size0 = screenWidth <= 800 && screenWidth > 0
			size1 = screenWidth <= 1250 && screenWidth > 800
			size3 = screenWidth <= 3000 && screenWidth > 2000
		});
		// when hover .card and buttons, change style of .mouseFollower
		const elements = [...document.querySelectorAll('.card'), ...document.querySelectorAll('a'), ...document.querySelectorAll('.commanditem'), ...document.querySelectorAll('button')];
		const mouseFollower = document.querySelector('.mouseFollower');
		elements.forEach((element) => {
			element.addEventListener('mouseenter', () => {
				mouseFollower.classList.remove(...initStyleOfMouseFollower.split(' '));
				mouseFollower.classList.add(...finalStyleOfMouseFollower.split(' '));
			});
			element.addEventListener('mouseleave', () => {
				mouseFollower.classList.remove(...finalStyleOfMouseFollower.split(' '));
				mouseFollower.classList.add(...initStyleOfMouseFollower.split(' '));
			});
		});
	});
	let arrayOfFeatures = [
		{
			name: 'Utilities.',
			style: 'from-red-800 to-orange-300',
			description:
					'Ch$rry is a multi-purpose Discord bot with tons of utilities like moderation, AI, economy, and more.'
		},
		{
			name: 'Moderation.',
			style: 'from-pink-500 to-violet-500',
			description:
					"Ch$rry's advanced moderation tools help you keep your server safe and clean without any hassle."
		},
		{
			name: 'ChatGPT.',
			style: 'from-yellow-500 to-pink-500',
			description: "Ch$rry's ChatGPT feature allows you to ask questions and talk to ChatGPT directly through your server."
		},
		{
			name: 'AI tools.',
			style: 'from-green-500 to-blue-500',
			description:
					'Ch$rry has tons of AI features that generate images, texts, and more with different options.'
		},
		{
			name: 'Games.',
			style: 'from-cyan-500 to-blue-500',
			description: "Ch$rry's awesome games are fun and helps make your server more interactive and fun."
		},
		{
			name: 'Economy.',
			style: 'from-violet-500 to-purple-500',
			description:
					'Ch$rry includes a crypto system linked to real-life crypto coins. No money? Gamble it!'
		}
	];
	let liveText = '';
	let num = 0;
	let index = 0;
	setInterval(() => {
		if (index < arrayOfFeatures[num].name.length) {
			liveText = liveText + arrayOfFeatures[num].name[index];
			index++;
		} else {
			liveText = arrayOfFeatures[num].name;
		}
	}, 100);
	setInterval(
		() => {
			liveText = '';
			index = 0;
			num++;
			if (num >= arrayOfFeatures.length) num = 0;
		},
		7000,
		num
	);
</script>
<div class="mouseFollower {size0 && 'hidden'} fixed blur-3xl bg-gradient-to-r z-50 pointer-events-none {initStyleOfMouseFollower}" style="top: {MouseY}px; left: {MouseX}px; transform: translate(-50%, -50%); border-radius: 50%; transition: 0.1s linear"></div>
<header
	class="w-full h-16 p-5 {size0 ? 'pl-0 justify-center' : size1? 'pl-0 justify-center' : 'pl-56'} text-sm fixed z-10 text-neutral-400 flex justify-start items-center backdrop-blur-3xl"
	style="background-color: rgba(0,0,0,0.1)"
>
	<a class="mx-4 hover:text-neutral-200" href="/">
		<img
			alt="logo"
			class="h-8 w-8"
			src="https://cdn.discordapp.com/app-icons/775604826448592927/abf5192ec4fb13ae82986820d4731a42.webp?size=128"
		/>
	</a>
	<a
			class="mx-4 hover:text-neutral-200 hover-underline-animation bg-clip-text text-transparent bg-gradient-to-r from-red-700 to-amber-900 font-extrabold after:scale-x-100 after:origin-bottom-left after:bg-gradient-to-r after:from-red-700 after:to-amber-900"
			href="/vote"
	>
		Vote for Ch$rry
	</a>
	<a
		class="mx-4 hover:text-neutral-200 {size0 && 'hidden'} hover-underline-animation"
		href="/invite"
	>
		Invite
	</a>
	<a
		class="mx-4 hover:text-neutral-200 {size0 && 'hidden'} hover-underline-animation"
		href="/discord"
	>
		Support
	</a>
	<a
		class="mx-4 hover:text-neutral-200 {size0 && 'hidden'} hover-underline-animation"
		href="/api"
	>
		API for developers
	</a>
</header>

<section class="{size0 ? 'pt-16' : size1 ? 'pt-20' : size3 ? 'pt-64' : 'pt-24'} flex justify-start items-center flex-col text-center px-10">
	<h2
		class="{size0 ? 'text-lg' : 'text-2xl'} text-neutral-500 font-bold tracking-normal mt-32 bg-clip-text text-transparent bg-gradient-to-b from-neutral-100 to-neutral-400"
	>
		Upgrade your server with the
	</h2>
	<h1
		class="{size0 ? 'text-5xl leading-28' : size1 ? 'text-7xl' : 'text-8xl'} w-11/12 tracking-tighter font-extrabold mt-8 bg-clip-text text-transparent bg-gradient-to-b from-neutral-100 to-neutral-400"
		style="font-family: 'Inter', monospace"
	>
		Power of
		<span class="divider">
			{#if size0 || size1}
				<br/>
			{/if}
		</span>
		<span
			class="bg-clip-text pr-0.5 tracking-tighter text-transparent bg-gradient-to-r {arrayOfFeatures[
				num
			].style}"
			id="writer"
		>
			{liveText}
			<span
				style="animation: blink 2s linear infinite"
				class="bg-clip-text text-transparent bg-gradient-to-b from-neutral-200 to-neutral-400"
			>
				|
			</span>
		</span>
	</h1>
	<h2
		class="{size0 ? 'w-10/12 text-sm leading-5' : size1 ? 'w-6/12 text-xl leading-8' : 'w-4/12 text-xl leading-8'} text-neutral-500 tracking-wide mt-10"
		style="animation: blink1 7s linear infinite"
	>
		{arrayOfFeatures[num].description}
	</h2>
	<div class="mt-14 flex">
		<a
			class="text-white relative mx-3
		 rounded-lg z-1 bg-gradient-to-r from-neutral-100 to-neutral-300"
			href="/discord"
			style="padding: 1px"
		>
			<div
				class="flex tracking-wide text-sm justify-center z-1 rounded-lg items-center bg-neutral-700 w-full h-full px-8 py-2.5 relative hover:bg-transparent hover:text-neutral-950"
			>
				Join Discord
			</div>
		</a>
		<a
			class="text-white relative mx-3
		 rounded-lg z-1 bg-gradient-to-r {arrayOfFeatures[num].style}"
			href="/invite"
			style="padding: 1px"
		>
			<div
				class="absolute left-1/4 rounded-lg blur-xl opacity-30 w-16 h-16 bg-gradient-to-r {arrayOfFeatures[
					num
				].style}"
				style="z-index: 0; animation: spin 20s linear infinite; top: -14px;"
			/>
			<div
				class="flex tracking-wide text-sm justify-center z-1 rounded-lg items-center bg-neutral-950 w-full h-full px-8 py-2.5 relative hover:bg-transparent hover:text-neutral-950"
			>
				Invite Ch$rry
			</div>
		</a>
	</div>
</section>
<section class="{size0 ? 'mt-20' : size1 ? 'mt-16' : 'mt-24'} flex justify-center flex-col items-center">
	<div class="{size0 ? 'mt-2 text-sm' : size1 ? 'mt-20' : 'mt-24'} mb-80 text-neutral-500">👇 Start exploring Ch$rry!</div>
	<div class="grid {size0 ? 'grid-cols-1' : size1 ? 'grid-cols-2' : 'grid-cols-3'} w-max text-center">
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style={size0 ? "margin-top: -15rem" : "margin-top: -10rem"}
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-green-500 to-teal-500"
			>
				Trust and Support.
			</p>
			<p class="desc-text">
				Trusted by over 200 servers and has a dedicated support team that is always ready to help
				asap.
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card mt-28"
			style="background: linear-gradient(180deg, rgba(255,255,255,4%), rgba(255,255,255,3%));"
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-orange-500 to-blue-500"
			>
				99% Uptime.
			</p>
			<p class="desc-text">
				Ch$rry would never go down, it's always there for your server, 24/7, 365 days a year!
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style="margin-top: -10rem; opacity:0;{size0 || size1 ? 'display: none' : 'display: auto'}"
		/>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style={size0 ? "" : "margin-top: -10rem"}
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-violet-500 to-cyan-500"
			>
				AI Powered.
			</p>
			<p class="desc-text">
				Ch$rry is powered by AI, ask ChatGPT, Generate Images, and not limited to only that much!
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card mt-28"
			style="background: linear-gradient(180deg, rgba(255,255,255,4%), rgba(255,255,255,3%));"
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-pink-500 to-red-500"
			>
				Advanced Moderation.
			</p>
			<p class="desc-text">
				Ch$rry has advanced moderation tools to keep your server safe and clean without any hassle.
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style={size0 ? "" : "margin-top: -10rem"}
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-slate-500 to-pink-500"
			>
				Fun Utilities.
			</p>
			<p class="desc-text">
				Ch$rry has tons of fun utilities like games, memes, and more to make your server more
				interactive and fun.
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style="{size0 || size1 ? '' : 'margin-top: -10rem;'}"
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-teal-500 to-slate-500"
			>
				Economy.
			</p>
			<p class="desc-text">
				Ch$rry includes a crypto system linked to real-life crypto coins. Gamble, Work, or Beg to
				earn more!
			</p>
		</div>
	</div>
</section>

<section
	class="flex justify-start flex-col items-center"
	data-aos={size0 ? 'none' : 'fade-up'}
	data-aos-anchor-placement="none"
	data-aos-duration="500"
>
	<h2
		class="text-2xl text-neutral-500 font-bold tracking-normal mt-56 bg-clip-text text-transparent bg-gradient-to-r from-neutral-100 to-slate-400"
	>
		Ch$rry is not limited to this...
	</h2>
	<div
		class="mt-60 overflow-hidden text-white spacefont w-full flex flex-col justify-center items-start hidescrollbar"
		style={size0 && "width: 100vw !important; overflow-x:scroll!important;"}
	>
		<ul
			class="flex my-3"
			style={'padding-left:' + elementOneMarginX * 0.4 + '% !important'}
			data-aos="fade-left"
			data-aos-anchor-placement="bottom-bottom"
			data-aos-duration="1000"
		>
			<li class="commanditem">/Alter balance<li>
			<li class="commanditem">/Alter reset<li>
			<li class="commanditem">/Alter blacklist<li>
			<li class="commanditem">/Alter unblacklist<li>
			<li class="commanditem">/Alter premium<li>
			<li class="commanditem">/Alter inventory<li>
			<li class="commanditem">/Developermode<li>
			<li class="commanditem">/Eval<li>
			<li class="commanditem">/Outages report<li>
			<li class="commanditem">/Outages update<li>
			<li class="commanditem">/Balance<li>
			<li class="commanditem">/Beg<li>
			<li class="commanditem">/Crypto buy<li>
			<li class="commanditem">/Crypto sell<li>
			<li class="commanditem">/Crypto assets<li>
			<li class="commanditem">/Crypto charts<li>
			<li class="commanditem">/Dig<li>
			<li class="commanditem">/Fish<li>
			<li class="commanditem">/Gamble dice<li>
			<li class="commanditem">/Gamble slots<li>
			<li class="commanditem">/Gamble roulette<li>
			<li class="commanditem">/Gamble coinflip<li>
			<li class="commanditem">/Instagram user<li>
		</ul>
		<ul
			class="flex my-3"
			style={'padding-left:' + elementOneMarginX * 0.5 + '% !important'}
			data-aos="fade-left"
			data-aos-anchor-placement="bottom-bottom"
			data-aos-duration="1000"
		>
			<li class="commanditem">/Gamble minesweeper<li>
			<li class="commanditem">/Hunt<li>
			<li class="commanditem">/Inventory<li>
			<li class="commanditem">/Job list<li>
			<li class="commanditem">/Job apply<li>
			<li class="commanditem">/Job resign<li>
			<li class="commanditem">/Job work<li>
			<li class="commanditem">/Leaderboard server<li>
			<li class="commanditem">/Leaderboard global<li>
			<li class="commanditem">/Lottery next<li>
			<li class="commanditem">/Marriage marry<li>
			<li class="commanditem">/Marriage divorce<li>
			<li class="commanditem">/Marriage view<li>
			<li class="commanditem">/Pet buy<li>
			<li class="commanditem">/Pet disown<li>
			<li class="commanditem">/Postmeme<li>
			<li class="commanditem">/Profile<li>
			<li class="commanditem">/Rewards daily<li>
			<li class="commanditem">/Rewards weekly<li>
			<li class="commanditem">/Rewards monthly<li>
			<li class="commanditem">/Search<li>
			<li class="commanditem">/Settings guild autotts<li>
		</ul>
		<ul
			class="flex my-3"
			style={'padding-left:' + elementOneMarginX * 0.5 + '% !important'}
			data-aos="fade-left"
			data-aos-anchor-placement="bottom-bottom"
			data-aos-duration="1000"
		>
			<li class="commanditem">/Shop buy<li>
			<li class="commanditem">/Shop sell<li>
			<li class="commanditem">/Shop sellall<li>
			<li class="commanditem">/Stats<li>
			<li class="commanditem">/Transfer deposit<li>
			<li class="commanditem">/Transfer withdraw<li>
			<li class="commanditem">/Transfer pay<li>
			<li class="commanditem">/8ball<li>
			<li class="commanditem">/Advice<li>
			<li class="commanditem">/Aki<li>
			<li class="commanditem">/Ben<li>
			<li class="commanditem">/Draw<li>
			<li class="commanditem">/Fortunecookie<li>
			<li class="commanditem">/Image get<li>
			<li class="commanditem">/Image generate<li>
			<li class="commanditem">/Rates gay<li>
			<li class="commanditem">/Rates iq<li>
			<li class="commanditem">/Rates thot<li>
			<li class="commanditem">/Rates pp<li>
			<li class="commanditem">/Ship<li>
			<li class="commanditem">/Botinfo<li>
			<li class="commanditem">/Devices<li>
			<li class="commanditem">/Tiktok<li>
			<li class="commanditem">/Translate<li>
			<li class="commanditem">/Enlarge<li>
			<li class="commanditem">/Instagram download<li>
		</ul>
		<ul
			class="flex my-3"
			style={'padding-left:' + elementOneMarginX * 0.8 + '% !important'}
			data-aos="fade-left"
			data-aos-anchor-placement="bottom-bottom"
			data-aos-duration="1000"
		>
			<li class="commanditem">/Ping<li>
			<li class="commanditem">/Serverinfo<li>
			<li class="commanditem">/Uptime<li>
			<li class="commanditem">/Whois<li>
			<li class="commanditem">/Lastfm connect<li>
			<li class="commanditem">/Lastfm disconnect<li>
			<li class="commanditem">/Lastfm nowplaying<li>
			<li class="commanditem">/Lastfm recent<li>
			<li class="commanditem">/Lastfm albums<li>
			<li class="commanditem">/Lastfm artists<li>
			<li class="commanditem">/Lastfm songs<li>
			<li class="commanditem">/Levels rank<li>
			<li class="commanditem">/Levels leaderboard<li>
			<li class="commanditem">/Avatar<li>
			<li class="commanditem">/Badges<li>
			<li class="commanditem">/Banner<li>
			<li class="commanditem">/Discrim<li>
			<li class="commanditem">/Help<li>
			<li class="commanditem">/Hypesquad<li>
			<li class="commanditem">/Serveravatar<li>
			<li class="commanditem">/Snipe deleted<li>
			<li class="commanditem">/Snipe edited<li>
			<li class="commanditem">/Steal<li>
		</ul>
		<ul
			class="flex my-3"
			style={'padding-left:' + elementOneMarginX * 0.5 + '% !important'}
			data-aos="fade-left"
			data-aos-anchor-placement="bottom-bottom"
			data-aos-duration="1000"
		>
			<li class="commanditem">/Suggest<li>
			<li class="commanditem">/Urban word<li>
			<li class="commanditem">/Urban random<li>
			<li class="commanditem">/Nuke<li>
			<li class="commanditem">/Punish warn<li>
			<li class="commanditem">/Punish timeout<li>
			<li class="commanditem">/Punish untimeout<li>
			<li class="commanditem">/Punish kick<li>
			<li class="commanditem">/Punish ban<li>
			<li class="commanditem">/Punish banid<li>
			<li class="commanditem">/Punish unban<li>
			<li class="commanditem">/Punishments view<li>
			<li class="commanditem">/Punishments clear<li>
			<li class="commanditem">/Purge messages<li>
			<li class="commanditem">/Purge user<li>
			<li class="commanditem">/Purge bots<li>
			<li class="commanditem">/Purge match<li>
			<li class="commanditem">/Purge includes<li>
			<li class="commanditem">/Purge links<li>
			<li class="commanditem">/Settings user autolottery<li>
			<li class="commanditem">/Settings guild view<li>
		</ul>
		<ul
			class="flex my-3"
			style={'padding-left:' + elementOneMarginX * 0.7 + '% !important'}
			data-aos="fade-left"
			data-aos-anchor-placement="bottom-bottom"
			data-aos-duration="1000"
		>
			<li class="commanditem">/Settings guild booster<li>
			<li class="commanditem">/Settings guild chatbot<li>
			<li class="commanditem">/Settings guild grabify<li>
			<li class="commanditem">/Settings guild invites<li>
			<li class="commanditem">/Settings guild joinlog<li>
			<li class="commanditem">/Settings guild leveling<li>
			<li class="commanditem">/Settings guild logs<li>
			<li class="commanditem">/Settings guild membercount<li>
			<li class="commanditem">/Settings guild addbutton<li>
			<li class="commanditem">/Settings guild colors<li>
			<li class="commanditem">/Setup<li>
			<li class="commanditem">/Tickets setup<li>
			<li class="commanditem">/Tickets add<li>
			<li class="commanditem">/Chatgpt ask<li>
			<li class="commanditem">/Chatgpt followup<li>
			<li class="commanditem">/Color<li>
			<li class="commanditem">/Embed<li>
		</ul>
	</div>
</section>

<section class="{size0 ? 'mt-20' : size1 ? 'mt-16' : 'mt-24'} flex justify-center flex-col items-center">
	<div class="{size0 ? 'mt-2 text-sm' : size1 ? 'mt-20' : 'mt-24'} mb-80 text-neutral-500">Not yet, there's even more!</div>
	<div class="grid {size0 ? 'grid-cols-1' : size1 ? 'grid-cols-2' : 'grid-cols-3'} w-max text-center">
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style={size0 ? "margin-top: -15rem" : "margin-top: -10rem"}
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-amber-500 to-teal-500"
			>
				Instagram / TikTok
			</p>
			<p class="desc-text">
				Download Instagram and TikTok videos and images with just a single command, directly within
				your server!
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card mt-28"
			style="background: linear-gradient(180deg, rgba(255,255,255,4%), rgba(255,255,255,3%));"
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-orange-500 to-indigo-500"
			>
				Faster Responses.
			</p>
			<p class="desc-text">
				Ch$rry is hosted on a powerful server, so your server never has to wait for a response from
				Ch$rry.
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style="margin-top: -10rem; opacity:0;{size0 || size1 ? 'display: none' : 'display: auto'}"
		/>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style={size0 ? "" : "margin-top: -10rem"}
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-violet-500 to-red-500"
			>
				Leveling.
			</p>
			<p class="desc-text">
				Ch$rry has a leveling system that allows you to level up by chatting. The more you chat, the
				more you level up!
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card mt-28"
			style="background: linear-gradient(180deg, rgba(255,255,255,4%), rgba(255,255,255,3%));"
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-pink-500 to-teal-500"
			>
				Akinator.
			</p>
			<p class="desc-text">
				Bored? Play Akinator with your friends and see who can guess the character first!
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style={size0 ? "" : "margin-top: -10rem"}
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-slate-500 to-yellow-500"
			>
				LastFM.
			</p>
			<p class="desc-text">
				Ch$rry has a LastFM feature that allows you to connect your LastFM account and get your
				music stats.
			</p>
		</div>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style="margin-top: -10rem; opacity:0;{size0 || size1 ? 'display: none' : 'display: auto'}"
		/>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card mt-28"
			style="margin-top: -10rem; opacity:0;{size0 || size1 ? 'display: none' : 'display: auto'}"
		/>
		<div
			data-aos={size0 ? 'none' : 'fade-up'}
			data-aos-anchor-placement={size0 ? 'none' : size1 ? 'center-bottom' : 'bottom-bottom'}
			data-aos-duration="500"
			class="card"
			style={size0 ? "" : size1 ? "margin-top: 3rem" : "margin-top: -10rem"}
		>
			<p
				class="text-4xl tracking-tighter my-5 font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-cyan-500 to-emerald-500"
			>
				Lmfao.
			</p>
			<p class="desc-text">
				Some really suspicious commands that you can use to troll your friends.
			</p>
		</div>
	</div>
</section>
<section
	class="flex justify-start flex-col items-center px-5 text-center"
	data-aos={size0 ? 'none' : 'fade-up'}
	data-aos-anchor-placement="none"
	data-aos-duration="500"
>
	<div class="mt-16 mb-56 text-neutral-500">
		...and the list still goes on. Invite Ch$rry for more unexpected features!
	</div>
	<h2
		class="text-3xl text-neutral-500 font-bold tracking-normal mt-0 bg-clip-text text-transparent bg-gradient-to-b from-white to-neutral-400"
	>
		You're just one click away!
	</h2>

	<div class="mt-14 flex"
		 data-aos={size0 ? 'none' : 'fade-up'}
		 data-aos-anchor-placement="bottom-bottom"
		 data-aos-duration="500">
		<a
			class="text-white relative mx-3
		 rounded-lg z-1 bg-gradient-to-r from-neutral-100 to-neutral-300"
			href="/invite"
			style="padding: 1px"
		>
			<div
				class="absolute left-1/4 rounded-lg blur-xl opacity-30 w-16 h-16 bg-gradient-to-r from-neutral-100 to-neutral-300"
				style="z-index: 0; animation: spin 20s linear infinite; top: -14px;"
			/>
			<div
				class="flex tracking-wide text-sm justify-center z-1 rounded-lg items-center bg-neutral-950 w-full h-full px-8 py-2.5 relative hover:bg-transparent hover:text-neutral-950"
			>
				Invite Ch$rry
			</div>
		</a>
	</div>
	<div class="mt-14 flex">
		<div
				data-aos={size0 ? 'none' : 'fade-up'}
				data-aos-anchor-placement="bottom-bottom"
				data-aos-duration="500"
			class="card flex flex-col justify-center items-center text-white relative"
			style="background: linear-gradient(180deg, rgba(255,115,90,0.64), rgba(255,0,0,0.83)); border: 0px solid rgba(255,255,255,0.5) !important; padding:1px !important;"
		>
			<div class="p-12 rounded-xl w-full h-full flex flex-col justify-center items-center text-white relative bg-gradient-to-b from-neutral-900 to-neutral-900">
				<h2
					class="text-3xl w-full text-center text-neutral-500 font-bold tracking-normal bg-clip-text text-transparent bg-gradient-to-r from-red-900 to-amber-500"
				>
					Buy Ch$rry Premium!
				</h2>
				<ul class="mt-10 list-disc text-neutral-300 text-left">
					<li>More Economy commands!</li>
					<li>More Premium features coming soon!</li>
				</ul>
				<p class="mt-8 text-neutral-500">Join server for getting Premium access!</p>
			</div>
		</div>
	</div>
</section>
<section
	class="flex justify-start flex-col items-center border-t-neutral-700 border-t mt-36 p-5 bg-neutral-800"
>
	<p class="text-neutral-400 text-xs tracking-wide leading-8">
		2023 © Ch$rry Network. All rights reserved. Made with ❤️ by <a
			class="hover-underline-animation"
			href="https://www.github.com/clapann">Clapan</a
		>, Site by
		<a class="hover-underline-animation" href="https://www.github.com/forloopcodes">Forloop</a>
	</p>
</section>
<!-- LINE 750 | Never gonna give you up | LOL | 🍒🍒🍒🍒🍒🍒🍒🍒🍒🍒-->