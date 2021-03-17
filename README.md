Static Generation<br>
-Pre-generate a page (with data prepared on the server-side during build time)<br>
-Pages prepared ahead of time and can be cached by the server / CDN serving the app<br>
-Can use static generation for data and then also use useEffect to update any new data. The user straight away is shown the old data with the new data uploading in the background. Or...<br>
-Can utilise incremental static generation; continuously updated after deployment without you re-deploying it. Pre-generate page, then re-generate it on every request, at most every X seconds. This serves the 'old' page if re-gen is not needed yet or serves latest page otherwise. On going pre-rendering on the server for incoming requests; revalidate on getStaticProps props object. If site is highly dynamic, have a shorter revalidate time, if less dynamic a longer revalidate time<br>
-When you have dynamically generated url page, default behaviour is to not statically generate that page as you will technically have multiple different possible pages; would have different data.
-Need pre-generated paths for case above; [id] values. Multiple concrete [id] page instances (e.g. id = 1, id = 2 etc.) are pr-generated
-Export async function getStaticPaths() {something something}<br>
<br>

Server-side rendering<br>
-Sometimes need to pre-render for every request or you need access to the request object (e.g. for cookies, authentication)
-NextJS allows you to run 'real server-side code' as well; export async function getServerSideProps() {something something}<br>
-Get access to params, req & res through context. Also re-renders on request from the user.
-Dynamic routes work without getStaticPaths as it runs on the server anyway - no pre-generated pages mean it doesn't need to know which pages to pre-generate<br>
<br>

Client-side Data Fetching<br>
-Some data doesn't need to be pre-rendered:<br>
-Data changing with high frequency (e.g. stock data)<br>
-Highly user-specific data (e.g. last orders in an online shop)<br>
-Partial data (e.g. data that's only used on a part of an page)<br>
-At this point traditional react code might make more sense; client-side data fetching (e.g. useEFfect() with fetch() is fine)
-Could also use SWR hook; has caching, auto revalidation & retries on error
-Could combine pre-fetching with client-side fetching; use getStaticProps or getServerSideProps and put into initial state, then use client-side fetching to fetch latest data
