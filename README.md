Static Generation<br>
-Pre-generate a page (with data prepared on the server-side during build time)<br>
-Pages prepared ahead of time and can be cached by the server / CDN serving the app<br>
-Can use static generation for data and then also use useEffect to update any new data. The user straight away is shown the old data with the new data uploading in the background. Or...<br>
-Can utilise incremental static generation; continuously updated after deployment without you re-deploying it. Pre-generate page, then re-generate it on every request, at most every X seconds. This serves the 'old' page if re-gen is not needed yet or serves latest page otherwise. On going pre-rendering on the server for incoming requests; revalidate on getStaticProps props object. If site is highly dynamic, have a shorter revalidate time, if less dynamic a longer revalidate time<br>
-When you have dynamically generated url page, default behaviour is to not statically generate that page as you will technically have multiple different possible pages; would have different data.
-Need pre-generated paths for case above; [id] values. Multiple concrete [id] page instances (e.g. id = 1, id = 2 etc.) are pr-generated

- export async function getStaticPaths() {something something}
  <br><br>
  Server-side rendering<br>
  -Sometimes need to pre-render for every request or you need access to the request object (e.g. for cookies)
