pnpm i 

then run
pnpm dev

this will load the link to launch click on the link and launch.




One benefit of using layouts in Next.js is that on navigation, only the page components update while the layout won't re-render. This is called partial rendering which preserves client-side React state in the layout when transitioning between pages.


export default function RootLayout({});

This is called a root layout and is required in every Next.js application. Any UI you add to the root layout will be shared across all pages in your application. You can use the root layout to modify your <html> and <body> tags, and add metadata (you'll learn more about metadata in a later chapter).




/app/ui/dashboard/nav-links.tsx

className={clsx(
              'flex h-[48px] grow items-center justify-center gap-2 rounded-md bg-gray-50 p-3 text-sm font-medium hover:bg-sky-100 hover:text-blue-600 md:flex-none md:justify-start md:p-2 md:px-3',
              {
                'bg-sky-100 text-blue-600': pathname === link.href,
              },
            )}


This make the active link highlighted in blue in dashboard page




partial prerendering - next js - not good for production

to implement - 

go to next.config.ts

add line in nextConfig block

  experimental: {
    ppr: 'incremental'
  }

then go to layout page of dashboard where you want to implement and add 

export const experimental_ppr = true;

thats it.
The great thing about Partial Prerendering is that you don't need to change your code to use it. As long as you're using Suspense to wrap the dynamic parts of your route, Next.js will know which parts of your route are static and which are dynamic.



 Next.js APIs: useSearchParams, usePathname, and useRouter.