<script lang="ts">
	import { isMobileMenu } from '$lib/stores/App';
	import { LOGO } from '$lib/constants';

	const login = '/login';

	// Example : { label: 'contact-us', href: '/contact-us' }
	const links = [];

	function openMenu(): void {
		$isMobileMenu = true;
	}

	function closeMenu(): void {
		$isMobileMenu = false;
	}
</script>

<svg
	class="hidden lg:block absolute right-0 inset-y-0 h-full w-48 text-background transform translate-x-1/2"
	fill="currentColor"
	viewBox="0 0 100 100"
	preserveAspectRatio="none"
	aria-hidden="true"
>
	<polygon points="50,0 100,0 50,100 0,100" />
</svg>

<div>
	<div class="relative h-auto pt-6 px-4 sm:px-6 lg:px-8">
		<nav
			class="relative h-auto flex items-center justify-between sm:h-10 lg:justify-start"
			aria-label="Global"
		>
			<div class="flex items-center flex-grow flex-shrink-0">
				<div class="flex items-center justify-between w-full md:w-auto">
					<a href={LOGO.href}>
						<span class="sr-only">{LOGO.label}</span>
						<img alt={LOGO.img.alt} class="w-14 h-auto max-w-none" src={LOGO.img.src} />
					</a>
					<div class="-mr-2 flex items-center md:hidden">
						<button
							on:click|preventDefault={openMenu}
							type="button"
							class="bg-background rounded-md p-2 inline-flex items-center justify-center text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-primary-500"
							aria-expanded="false"
						>
							<span class="sr-only">Open main menu</span>
							<!-- Heroicon name: outline/menu -->
							<svg
								class="h-6 w-6"
								xmlns="http://www.w3.org/2000/svg"
								fill="none"
								viewBox="0 0 24 24"
								stroke-width="2"
								stroke="currentColor"
								aria-hidden="true"
							>
								<path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
							</svg>
						</button>
					</div>
				</div>
			</div>
			<div class="hidden md:block md:ml-10 md:pr-4 md:space-x-8">
				{#each links as { label, href }}
					<a {href} class="font-medium text-gray-500 hover:text-gray-900 capitalize">{label}</a>
				{/each}

				<a
					href={login}
					class="inline-flex items-center justify-center px-4 py-2 border border-transparent rounded-md shadow-sm text-base font-medium text-background bg-gradient-to-r from-secondary-500 to-secondary-600 hover:from-secondary-400 hover:to-secondary-500"
					>Log in</a
				>
			</div>
		</nav>
	</div>

	<!-- Mobile Menu -->
	<div
		class="absolute {$isMobileMenu
			? 'expo-in opacity-100 translate-x-0 z-20'
			: 'expo-out opacity-75 translate-x-full -z-10'} top-0 inset-x-0 p-2 transition transform origin-top-right duration-500 md:hidden"
	>
		<div
			class="rounded-lg shadow-md bg-background ring-1 ring-black ring-opacity-5 overflow-hidden"
		>
			<div class="px-5 pt-4 flex items-center justify-between">
				<div>
					<img class="h-8 w-auto" src={LOGO.img.src} alt={LOGO.img.alt} />
				</div>
				<div class="-mr-2">
					<button
						on:click|preventDefault={closeMenu}
						type="button"
						class="bg-background rounded-md p-2 inline-flex items-center justify-center text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-primary-500"
					>
						<span class="sr-only">Close main menu</span>
						<!-- Heroicon name: outline/x -->
						<svg
							class="h-6 w-6"
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="2"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
						</svg>
					</button>
				</div>
			</div>
			<div class="px-2 pt-2 pb-3 space-y-1">
				{#each links as { label, href }}
					<a
						{href}
						class="block px-3 py-2 rounded-md capitalize text-base font-medium text-gray-700 hover:text-gray-900 hover:bg-gray-50 "
						>{label}</a
					>
				{/each}
			</div>
			<a
				href={login}
				class="block w-full px-5 py-3 text-center font-medium capitalize text-background bg-gradient-to-r from-secondary-500 to-secondary-600 hover:from-secondary-400 hover:to-secondary-500"
			>
				Log in
			</a>
		</div>
	</div>
</div>
