<script>
	import Markdown from "../components/Markdown.svelte";
	import Sidebar from "../components/Sidebar.svelte";
	import Window from "../components/Window.svelte";
	import TabItem from "../components/TabItem.svelte";
</script>

<style>
	::-webkit-scrollbar-corner { background: rgba(0,0,0,0); }

	::-webkit-scrollbar-track {
		border-radius: 10px;
		background-color: transparent;
	}

	::-webkit-scrollbar {
		width: 8px;
		background-color: transparent;
	}
</style>

<div class="[ bg-cover bg-[url('https://www.ytechb.com/wp-content/uploads/2025/06/macOS-Tahoe-26-Dark-Wallpaper-Thumb.webp')] ] 
			[ flex flex-col h-screen justify-center items-center ]">
	<Window>
		<div class="flex overflow-hidden">
			<Sidebar class="">
				<div class="mb-8 traffic-lights flex px-4 pt-4 align-top justify-start">
					<!--svelte-ignore a11y_consider_explicit_label-->
					<button class="traffic-light traffic-light-close" id="close"></button>
					<!--svelte-ignore a11y_consider_explicit_label-->
					<button class="traffic-light traffic-light-minimize" id="minimize"></button>
					<!--svelte-ignore a11y_consider_explicit_label-->
					<button class="traffic-light traffic-light-maximize" id="maximize"></button>
				</div>
				<TabItem class="text-white/55 font-semibold flex px-6 text-sm">
					Page 1
				</TabItem>
				<TabItem class="text-white/55 font-semibold flex px-6 text-sm">
					Page 2
				</TabItem>
				<TabItem class="text-white/55 font-semibold flex px-6 text-sm">
					Page 3
				</TabItem>
			</Sidebar>
			<div class="border-l-2 border-[#171616]/100 flex flex-col w-[85vw]">
				<div class="bg-[#3d383e] flex items-center text-white/95 p-4 overflow-hidden h-[48px] border-b-[#171616]/100 border-b-2">
					<div class="align-middle items-center inline-flex rounded-md py-2">
						<svg class="w-4 h-4 fill-white/95 mr-1.5 mb-1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free 6.7.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2025 Fonticons, Inc.--><path d="M410.3 231l11.3-11.3-33.9-33.9-62.1-62.1L291.7 89.8l-11.3 11.3-22.6 22.6L58.6 322.9c-10.4 10.4-18 23.3-22.2 37.4L1 480.7c-2.5 8.4-.2 17.5 6.1 23.7s15.3 8.5 23.7 6.1l120.3-35.4c14.1-4.2 27-11.8 37.4-22.2L387.7 253.7 410.3 231zM160 399.4l-9.1 22.7c-4 3.1-8.5 5.4-13.3 6.9L59.4 452l23-78.1c1.4-4.9 3.8-9.4 6.9-13.3l22.7-9.1 0 32c0 8.8 7.2 16 16 16l32 0zM362.7 18.7L348.3 33.2 325.7 55.8 314.3 67.1l33.9 33.9 62.1 62.1 33.9 33.9 11.3-11.3 22.6-22.6 14.5-14.5c25-25 25-65.5 0-90.5L453.3 18.7c-25-25-65.5-25-90.5 0zm-47.4 168l-144 144c-6.2 6.2-16.4 6.2-22.6 0s-6.2-16.4 0-22.6l144-144c6.2-6.2 16.4-6.2 22.6 0s6.2 16.4 0 22.6z"/></svg>
						Test Page
					</div>
				</div>
				<div class="relative flex flex-col w-full overflow-hidden h-full bg-[#1e1e1e]">
					<div class="flex-1 overflow-y-auto">
						<Markdown class="py-2 px-4">
							# H1
							## H2
							### H3

							My list:
							- item 1
							- item 2

							~~strike~~
							**Bold**

							https://www.makeuseof.com/tag/10-tips-get-apple-notes-os-x/

							This is the first blog page I have made

							[Here](https://www.makeuseof.com/tag/10-tips-get-apple-notes-os-x/)

							```js
								let a = 100;
								print(a);
							```

							stuffssdkj
							skdjutituiutjksjdfoisuf
							kasjfosidutioeprjtklejt
							ads
							sdad
							adsasd
							asd
							ds
							sdad
							adsasd
							asdds
							sdad
							adsasd
							asd
						</Markdown>
					</div>
					<!--svelte-ignore element_invalid_self_closing_tag-->
					<div class="absolute bottom-0 left-0 right-0 h-12 bg-gradient-to-t from-[#171616] from-0% to-transparent to-45% pointer-events-none"/>
				</div>
			</div>
		</div>
	</Window>
</div>