Các bước deploy
Test Code => Optimize Code => Build App for Production => Upload Production Code to Server => Configure Server

Lazy Loading - Tải Code chỉ khi cần
const Component = React.lazy(() => import('...'))
<Suspense fallback={JSX Code}>...</Suspense> - JSX Code trong fallback prop sẽ là Content được hiển thị khi Code cần thiết chưa hoàn thành tải xuống

npm run build - Build App for Production => Build Folder
React SPA là "Static Website"

Server-side Routing vs Client-side Routing - Configure Server để luôn trả về một Response với mọi path và để React Code đảm nhiệm việc render Content với từng path
