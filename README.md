<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>صفحة بدون إنترنت</title>
    <link rel="icon" href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAJ0lEQVR42mNkYGD4z0ABYBSMDIwMQzBQOgohCrgGVQEqmBqJQgDKgwL0cTBrwAAAABJRU5ErkJggg==" />
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            text-align: center;
            background-color: #f9f9f9;
        }
        h1 {
            color: #333;
        }
        p {
            color: #555;
        }
    </style>
</head>
<body>
    <h1>مرحبًا بك في صفحتي التي تعمل بدون إنترنت</h1>
    <p>يمكنك رؤية هذه الصفحة حتى بدون اتصال بالشبكة.</p>

    <script>
        // إعداد الكاش
        const CACHE_NAME = 'offline-cache-v1';
        const FILES_TO_CACHE = [
            window.location.href // رابط الصفحة نفسها
        ];

        // تثبيت Service Worker وتخزين الملفات
        self.addEventListener('install', (event) => {
            event.waitUntil(
                caches.open(CACHE_NAME).then((cache) => {
                    return cache.addAll(FILES_TO_CACHE);
                })
            );
        });

        // خدمة الملفات من الكاش عند الطلب
        self.addEventListener('fetch', (event) => {
            event.respondWith(
                caches.match(event.request).then((response) => {
                    return response || fetch(event.request);
                })
            );
        });

        // تسجيل Service Worker
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register(window.location.href)
                .then((registration) => {
                    console.log('Service Worker مسجل بنجاح:', registration);
                })
                .catch((error) => {
                    console.error('فشل تسجيل Service Worker:', error);
                });
        }
    </script>
</body>
</html>
