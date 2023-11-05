<template>
  <div>
    <GoogleAll v-if="tabActive === 'all'" :data="result" />
    <GoogleImages v-if="tabActive === 'images'" :data="result"  />
    <GoogleVideos v-if="tabActive === 'videos'" :data="result" />
  </div>
</template>

<script setup>
const props = defineProps(['result'])

const data = [
    {
      "title": "Google",
      "href": "https://www.google.com/",
      "body": "Search the world's information, including webpages, images, videos and more. Google has many special features to help you find exactly what you're looking for."
    },
    {
      "title": "Google - Apps on Google Play",
      "href": "https://play.google.com/store/apps/details?id=com.google.android.googlequicksearchbox",
      "body": "The more you use the Google app, the better it gets. Search and browse: - Nearby shops and restaurants. - Live sports scores and schedules. - Movies times, casts, and reviews. - Videos and images. - News, stock information, and more. - Anything you'd find on the web. Get personalized updates in Discover*:"
    },
    {
      "title": "‎Google on the App Store",
      "href": "https://apps.apple.com/us/app/google/id284815942",
      "body": "The official Google app gives you more ways to search - Use your camera to uncover who painted that artwork, translate a menu on your travels, find out what type of dog that fluffy thing is, shop anything you can see, and solve your homework. Oh, and you can also search for songs by humming. Feature highlights: • Use your camera to identify ..."
    },
    {
      "title": "Make Google your default search provider - Google",
      "href": "https://www.google.com/homepage/search/",
      "body": "In the General tab, find the Search section and click Settings . Select Google . Click Set as default and click Close . Step 1: Open your Search settings. Click on the Search button near the top ..."
    },
    {
      "title": "Google Account",
      "href": "https://myaccount.google.com/",
      "body": "Your Google Account automatically protects your personal information and keeps it private and safe. Every account comes with powerful features like spam filters that block 99.9% of dangerous emails before they ever reach you, and personalized security notifications that alert you of suspicious activity and malicious websites."
    },
    {
      "title": "Google Chrome - The Fast & Secure Web Browser Built to be Yours",
      "href": "https://www.google.com/chrome/",
      "body": "Features. Safety. Support. Download Chrome. Chrome is the official web browser from Google, built to be fast, secure, and customizable. Download now and make it yours."
    },
    {
      "title": "Google - Wikipedia",
      "href": "https://en.wikipedia.org/wiki/Google",
      "body": "In 2015, Google was reorganized as a wholly owned subsidiary of Alphabet Inc. Google is Alphabet's largest subsidiary and is a holding company for Alphabet's internet properties and interests. Sundar Pichai was appointed CEO of Google on October 24, 2015, replacing Larry Page, who became the CEO of Alphabet."
    },
    {
      "title": "Google Photos",
      "href": "https://photos.google.com/",
      "body": "Google Photos is the home for all your photos and videos, automatically organized and easy to share."
    },
    {
      "title": "Google Help",
      "href": "https://support.google.com/?hl=en",
      "body": "If you're having trouble accessing a Google product, there's a chance we're currently experiencing a temporary problem. You can check for outages and downtime on the G Suite Status Dashboard."
    },
    {
      "title": "Download & install Google Chrome - Computer - Google Chrome Help",
      "href": "https://support.google.com/chrome/answer/95346?hl=en&co=GENIE.Platform=Desktop",
      "body": "Download & install Google Chrome. Make Chrome your default browser. Google Chrome is a fast&nbsp;web browser available at no charge. Before you download, you can check if Chrome supports your operating system and you have all the other system requirements. How to ins."
    },
    {
      "title": "Google Scholar",
      "href": "https://scholar.google.com/",
      "body": "Google Scholar provides a simple way to broadly search for scholarly literature. Search across a wide variety of disciplines and sources: articles, theses, books, abstracts and court opinions."
    },
    {
      "title": "Google Cloud",
      "href": "https://cloud.google.com/",
      "body": "Cloud computing, ready for business. Whether you're migrating or already in the cloud, we'll help you modernize and digitally transform your business. Talk to us. Run and build your apps, anywhere. Avoid vendor lock-in and speed up development with Google Cloud's commitment to open source, hybrid, and multicloud."
    },
    {
      "title": "Google Images",
      "href": "https://images.google.com/",
      "body": "Google Images. The most comprehensive image search on the web."
    },
    {
      "title": "Google - YouTube",
      "href": "https://www.youtube.com/google",
      "body": "Celebrate 25 years of Google on our official YouTube channel. Watch videos about our products, technology, company happenings and more. Subscribe to get upda..."
    },
    {
      "title": "Manage your Google Settings - Google Account Help",
      "href": "https://support.google.com/accounts/answer/3118621?hl=en",
      "body": "Account. Tap Manage your Google Account. Scroll to the tab you want. Home. Update basic info in your Google Account. Learn how to change your name and other info. Find your data, activity, and preferences that can make Google services more useful to you. Manage what activity gets saved. Use settings and recommendations to help keep your account ..."
    },
    {
      "title": "Sign in - Google Accounts",
      "href": "https://classroom.google.com/",
      "body": "Not your computer? Use a private browsing window to sign in. Learn more"
    },
    {
      "title": "About - Google Maps",
      "href": "https://maps.google.com/maps/about/#!/",
      "body": "Your Google Assistant is now integrated into Google Maps so you can message, call, listen to music and get hands-free help while driving. Say \"Hey Google\" to get started. Real-time updates for public transportation. Get up-to-the-minute updates on busses and trains, like departure times and how crowded the bus is. You can also see where on ..."
    },
    {
      "title": "Google",
      "href": "https://www.google.com/index.html",
      "body": "Search the world's information, including webpages, images, videos and more. Google has many special features to help you find exactly what you're looking for."
    },
    {
      "title": "Google",
      "href": "https://www.google.com/intl/en/",
      "body": "Search the world's information, including webpages, images, videos and more. Google has many special features to help you find exactly what you're looking for."
    },
    {
      "title": "Google",
      "href": "https://www.google.com/intl/es",
      "body": "Ofrecido por Google en: English Publicidad Todo acerca de Google Google.com in English. © 2023 - Privacidad - CondicionesPrivacidad - Condiciones"
    }
]

const dataI = [
    {
      "title": "Rose Red - Free photo on Pixabay",
      "image": "https://cdn.pixabay.com/photo/2017/10/24/18/17/rose-2885586_960_720.jpg",
      "thumbnail": "https://tse1.mm.bing.net/th?id=OIP.q0Jx0qXAeT82-bMMbXT7LwHaFj&pid=Api",
      "url": "https://pixabay.com/photos/rose-red-red-rose-flower-2885586/",
      "height": 720,
      "width": 960,
      "source": "Bing"
    },
    {
      "title": "File:Beautiful Red Rose.jpg",
      "image": "http://upload.wikimedia.org/wikipedia/commons/9/9f/Beautiful_Red_Rose.jpg",
      "thumbnail": "https://tse1.mm.bing.net/th?id=OIP.EdAZwt9bSWKbNgO_xMJj4AHaE6&pid=Api",
      "url": "http://commons.wikimedia.org/wiki/File:Beautiful_Red_Rose.jpg",
      "height": 1520,
      "width": 2288,
      "source": "Bing"
    },
    {
      "title": "Free photo: Red Rose Photography - Beautiful, Bloom, Blooming - Free ...",
      "image": "https://jooinn.com/images/red-rose-photography-1.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.zs6ycwcSD15SnbzbvFAgRwHaLH&pid=Api",
      "url": "https://jooinn.com/red-rose-photography-2.html",
      "height": 3000,
      "width": 2000,
      "source": "Bing"
    },
    {
      "title": "Top 10 Hybrid Tea Roses",
      "image": "https://www.thespruce.com/thmb/eHrxFkxHrBT5dq1CqEcsR0zcZ78=/5184x3456/filters:fill(auto,1)/Rosa_Peace_1945-5b29cee4ba617700546dd09a.jpg",
      "thumbnail": "https://tse3.mm.bing.net/th?id=OIP.-XGa1Vfpgxt47aFYx1Ja_QHaE8&pid=Api",
      "url": "https://www.thespruce.com/best-hybrid-tea-roses-1403063",
      "height": 3456,
      "width": 5184,
      "source": "Bing"
    },
    {
      "title": "Black Beauty Rose - Hello Hello Plants & Garden Supplies",
      "image": "http://www.thetutuguru.com.au/wp-content/uploads/2013/08/Rose-Black-Beauty.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.h5nDaDYT0FCE3MHWVWoN9gHaHP&pid=Api",
      "url": "http://www.thetutuguru.com.au/shop/black-beauty-rose/",
      "height": 2477,
      "width": 2532,
      "source": "Bing"
    },
    {
      "title": "Most Beautiful Rose Flowers Wallpapers - WallpaperSafari",
      "image": "https://cdn.wallpapersafari.com/45/55/pQLI2h.jpg",
      "thumbnail": "https://tse3.mm.bing.net/th?id=OIP.np0ftWMObLbKR3TkB8kJ2gHaF7&pid=Api",
      "url": "http://wallpapersafari.com/most-beautiful-rose-flowers-wallpapers/",
      "height": 1024,
      "width": 1280,
      "source": "Bing"
    },
    {
      "title": "Flower Picture: Rose Flower Picture # 4",
      "image": "http://1.bp.blogspot.com/-jKe8-s5OklU/Tj1mZfFe5mI/AAAAAAAAFiI/JHheQf6b6Zw/s1600/red-roses-flower-pictures-17.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.iA7w-2-3SHpcb9VrHepOwgHaFj&pid=Api",
      "url": "http://flowers-picture.blogspot.com/2011/08/rose-flower-picture-4.html",
      "height": 1200,
      "width": 1600,
      "source": "Bing"
    },
    {
      "title": "HOW TO GROW THE BLACK ROSE |The Garden of Eaden",
      "image": "http://4.bp.blogspot.com/-X5zjTSMPJv4/UVhr3J5e9LI/AAAAAAAAQ3c/rzV3dsQq4Co/s1600/black+rose.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.YqHVSTiTH9YScsZOhcrlMwHaHa&pid=Api",
      "url": "http://gardenofeaden.blogspot.co.uk/2013/03/the-black-rose.html",
      "height": 1600,
      "width": 1600,
      "source": "Bing"
    },
    {
      "title": "Red Rose Wallpapers High Quality | Download Free",
      "image": "http://yesofcorsa.com/wp-content/uploads/2015/07/1133_red_rose.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.XKHTVo-Qw0BflojaBLgBOAHaEo&pid=Api",
      "url": "http://yesofcorsa.com/red-rose/",
      "height": 1200,
      "width": 1920,
      "source": "Bing"
    },
    {
      "title": "What Is Your Favorite Flower?",
      "image": "http://upload.wikimedia.org/wikipedia/commons/b/b2/Red_Rose.jpg",
      "thumbnail": "https://tse4.mm.bing.net/th?id=OIP.dhkFOFkb2G0fq2FgtW_a0wHaE9&pid=Api",
      "url": "http://www.sodahead.com/fun/what-is-your-favorite-flower/question-1079425/",
      "height": 2592,
      "width": 3872,
      "source": "Bing"
    },
    {
      "title": "GardenZeus Recommendations for Climbing Rose Varieties in California ...",
      "image": "https://www.gardenzeus.com/wp-content/uploads/shutterstock_144180568-1-1362x2048.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.nVbwdWDMFWc3leCYE5JNYQHaLI&pid=Api",
      "url": "https://www.gardenzeus.com/gardenzeus-recommendations-for-climbing-rose-varieties-in-california-zone-15/",
      "height": 2048,
      "width": 1362,
      "source": "Bing"
    },
    {
      "title": "Beautiful rose bush in the garden wallpapers and images - wallpapers ...",
      "image": "http://www.zastavki.com/pictures/originals/2014/Nature___Flowers_Beautiful_rose_bush_in_the_garden_067027_.jpg",
      "thumbnail": "https://tse4.mm.bing.net/th?id=OIP.C7w-j6EyakIX9AGgItp4jAHaFU&pid=Api",
      "url": "http://www.zastavki.com/eng/Nature/Flowers/wallpaper-67027.htm",
      "height": 2848,
      "width": 3964,
      "source": "Bing"
    },
    {
      "title": "Rose Flowers Wallpapers - Real HD Wallpapers",
      "image": "http://4.bp.blogspot.com/-MdAqEy2x1MA/UZKbhRQe0rI/AAAAAAAAAOI/ATFUZ_k8PCU/s1600/rose+flower-2.jpg",
      "thumbnail": "https://tse1.mm.bing.net/th?id=OIP.cyWcFOb00uTN-N8-ff55LQHaFj&pid=Api",
      "url": "http://wallpaperrealhd.blogspot.com/2013/05/rose-flowers-wallpapers.html",
      "height": 1200,
      "width": 1600,
      "source": "Bing"
    },
    {
      "title": "Wallpaper Gallery: Rose Flower Wallpaper -1",
      "image": "http://4.bp.blogspot.com/-Iab8c1gIL6o/T-B1Lq11nsI/AAAAAAAADeM/Z0y0Kaulr7s/s1600/beautiful-hot-pink-red-rose.jpg",
      "thumbnail": "https://tse3.mm.bing.net/th?id=OIP.cDyFxfokxfmqeqnbdLQf2AHaE8&pid=Api",
      "url": "http://wallpapersallin.blogspot.com/2012/06/rose-flower-wallpaper-1.html",
      "height": 1067,
      "width": 1600,
      "source": "Bing"
    },
    {
      "title": "Free picture: flower garden, reddish, roses, blossom, shrub, plant, bud ...",
      "image": "https://pixnio.com/free-images/2019/05/17/2019-05-17-19-44-13.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.wuSgG-MMdPMDVrQw8yYePQHaEH&pid=Api",
      "url": "https://pixnio.com/media/flower-garden-reddish-roses-blossom-shrub",
      "height": 2500,
      "width": 4500,
      "source": "Bing"
    },
    {
      "title": "Pink Rose With Water Drops | Beautiful roses, Rose, Pink roses",
      "image": "https://i.pinimg.com/originals/7e/f5/e7/7ef5e77d3dfe94008214cf173d778201.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP.bccPAIkG0zKHukOPzqnpbwHaJ4&pid=Api",
      "url": "https://www.pinterest.com/pin/395613148487452953/",
      "height": 3264,
      "width": 2448,
      "source": "Bing"
    },
    {
      "title": "Beautiful Red Rose Free Stock Photo - Public Domain Pictures",
      "image": "http://www.publicdomainpictures.net/pictures/40000/velka/beautiful-red-rose.jpg",
      "thumbnail": "https://tse4.mm.bing.net/th?id=OIP.xjpbML6m2HeUjqFp0tBP1AHaE6&pid=Api",
      "url": "http://www.publicdomainpictures.net/view-image.php?image=33515",
      "height": 1272,
      "width": 1920,
      "source": "Bing"
    },
    {
      "title": "Red Rose Desktop Backgrounds Wallpaper HD | PixelsTalk.Net",
      "image": "https://www.pixelstalk.net/wp-content/uploads/2016/04/Rose-Flower-Images-HD-Wallpapers-HD.jpg",
      "thumbnail": "https://tse2.mm.bing.net/th?id=OIP._-zJynAj28OM9Vv9cXnXZAHaEK&pid=Api",
      "url": "https://www.pixelstalk.net/rose-baclgrounds-for-desktop/",
      "height": 1080,
      "width": 1920,
      "source": "Bing"
    },
    {
      "title": "Nature Rose HD Wallpaper",
      "image": "https://images5.alphacoders.com/790/790742.jpg",
      "thumbnail": "https://tse1.mm.bing.net/th?id=OIP.ZvaWWz5TEt9a8rlVTYox6AHaE8&pid=Api",
      "url": "https://wall.alphacoders.com/big.php?i=790742",
      "height": 2425,
      "width": 3637,
      "source": "Bing"
    }
]

const dataV = [
    {
      "content": "https://www.youtube.com/watch?v=kTJczUoc26U",
      "description": "Official video for \"Stay\" by The Kid LAROI & Justin Bieber. Listen & Download \"Stay\" out now: https://thekidlaroi.lnk.to/Stay Amazon Music - https://thekidlaroi.lnk.to/Stay/amazonmusic Apple Music - https://thekidlaroi.lnk.to/Stay/applemusic Audiomack - https://thekidlaroi.lnk.to/Stay/audiomack Deezer - https://thekidlaroi.lnk.to/Stay ...",
      "duration": "2:38",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/kTJczUoc26U?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/kTJczUoc26U?autoplay=1",
      "image_token": "824c832c340352358fc5249df87afc7a05189e9d67d3d22ce8aedd09e603b3d6",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.N_GbnXXmKuMIPr2hHYKUdwHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.N_GbnXXmKuMIPr2hHYKUdwHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM2.oPwl5Owzd-Bnaw_1645376847&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.N_GbnXXmKuMIPr2hHYKUdwHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-07-09T04:00:12.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 816567004
      },
      "title": "The Kid LAROI, Justin Bieber - STAY (Official Video)",
      "uploader": "TheKidLAROIVEVO"
    },
    {
      "content": "https://www.youtube.com/watch?v=h2jvHynuMjI",
      "description": "Watch Official Video: http://stuckwithu.lnk.to/video SB Projects along with longtime clients Ariana Grande and Justin Bieber release \"Stuck with U\" to benefit First Responders Children's Foundation: https://stuckwithu.lnk.to/agjbVD In response to the COVID-19 crisis and to help further bolster relief efforts, all net proceeds from the ...",
      "duration": "3:50",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/h2jvHynuMjI?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/h2jvHynuMjI?autoplay=1",
      "image_token": "28115a8d77c525baa18258dfeda387676229ad985bfb95c836b65aaa22586f6b",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.N4dxbf_LTPwh2TqjH_ax5AHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.N4dxbf_LTPwh2TqjH_ax5AHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.ZdI6L0s_hUC3Nw_1695826440&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.N4dxbf_LTPwh2TqjH_ax5AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2020-05-08T04:00:10.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 198460699
      },
      "title": "Ariana Grande, Justin Bieber - Stuck with U (Lyric Video)",
      "uploader": "JustinBieberVEVO"
    },
    {
      "content": "https://www.youtube.com/watch?v=a59gmGkq_pw",
      "description": "Major Lazer - Cold Water (feat. Justin Bieber & MØ) (Official Lyric Video) WATCH SEASON 1 OF MAJOR LAZER NOW: https://smarturl.it/MLCartoonSeason1 LAY YOUR HEAD ON ME WITH MARCUS MUMFORD OUT NOW https://smarturl.it/LYHOM Subscribe to the Major Lazer YouTube Channel http://majorlazer.fm/YouTube \"I had been trying to link with Benny Blanco and ...",
      "duration": "3:09",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/a59gmGkq_pw?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/a59gmGkq_pw?autoplay=1",
      "image_token": "74472dd297938abc65d946db26288bdca1acd14298acd594bed5a9f5c74247c5",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.8UD2h6YhTXooezOQkNGR0AHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.8UD2h6YhTXooezOQkNGR0AHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.5If6QHagHED_Pw_1694743814&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.8UD2h6YhTXooezOQkNGR0AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2016-07-22T03:57:03.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 1048363489
      },
      "title": "Major Lazer - Cold Water (feat. Justin Bieber & MØ) (Official Lyric Video)",
      "uploader": "Major Lazer Official"
    },
    {
      "content": "https://www.youtube.com/watch?v=gYpvr8lCh7c",
      "description": "Site Oficial: http://bit.ly/Jornada_autodidata Quer falar inglês mas não tem tempo ou dinheiro para frequentar um curso? 👇 Veja como milhares de brasileiros estão alcançando a fluência com músicas e séries👇 Site Oficial: http://bit.ly/Jornada_autodidata Song: Never say never Artist: Justin Bieber feat. Jade Smith Album: Never say ...",
      "duration": "3:47",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/gYpvr8lCh7c?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/gYpvr8lCh7c?autoplay=1",
      "image_token": "52c2c35519d3b5b4f7956ba8e493577d0f86f6b80a45b0ccc9ab2db450d53fc6",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.bRFfZXZxLvdljdQaX29c5wHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.bRFfZXZxLvdljdQaX29c5wHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.el3q7IOh_qYB4w_1695647297&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.bRFfZXZxLvdljdQaX29c5wHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2019-02-13T20:26:39.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 27736231
      },
      "title": "Never say never - Justin Bieber ft. Jaden Smith LYRICS",
      "uploader": "Sing-along"
    },
    {
      "content": "https://www.youtube.com/watch?v=CCSGelSCPGE",
      "description": "The official lyric video for Ed Sheeran & Justin Bieber - I Don't Care Subtract, the new album, out 05.05.2023. Pre-order: https://es.lnk.to/subtract Taken from No.6 Collaborations Project released in 2019, which featured the hit singles 'I Don't Care', 'Cross Me', 'Beautiful People', 'Blow', 'Best Part of Me', 'Antisocial', 'South of the ...",
      "duration": "3:38",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/CCSGelSCPGE?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/CCSGelSCPGE?autoplay=1",
      "image_token": "9e82e0a8f485b58d45179be4eff4447ca152f988933608aa74426471b5e709d0",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.CjXmfobuBZyvxZfB7eKwXgIIEk&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.CjXmfobuBZyvxZfB7eKwXgIIEk&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.vQNxEb_7Wbm7oQ_1697151957&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.CjXmfobuBZyvxZfB7eKwXgIIEk&pid=Api"
      },
      "provider": "Bing",
      "published": "2019-05-10T04:07:42.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 244607674
      },
      "title": "Ed Sheeran & Justin Bieber - I Don't Care [Official Lyric Video]",
      "uploader": "Ed Sheeran"
    },
    {
      "content": "https://www.youtube.com/watch?v=zHzN80iC59I",
      "description": "Bieber Fever! The only cure is to disable the brain. Just ask Lil Wayne. Watch Behind the Scenes HERE! http://www.youtube.com/watch?v=hbnzRBolN3M Subscribe! http://www.youtube.com/subscription_center?add_user=barelypolitical Directed by Tom Small. Lyrics / Vocals by Mark Douglas. Music Reproduction by Jake Chudnow. Bieber: is Jan Uczkowsk ...",
      "duration": "2:53",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/zHzN80iC59I?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/zHzN80iC59I?autoplay=1",
      "image_token": "3b0779cc1f02e3fda18c1af9e1f390f78e89fe735922efd8a25ec1f1087bdca8",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.xy_p6Pk7moaCkRTpLruqJQHgFo&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.xy_p6Pk7moaCkRTpLruqJQHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.MDe2bIUfKfmTfg_1694479792&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.xy_p6Pk7moaCkRTpLruqJQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2010-04-27T23:03:10.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 28328224
      },
      "title": "Justin Bieber ft. Lil Wayne: Bieber Fever! Key of Awesome #19",
      "uploader": "The Key of Awesome"
    },
    {
      "content": "https://www.youtube.com/watch?v=0KXQ9eQxnuU",
      "description": "Justin Bieber performs Cold Water in the Live Lounge for BBC Radio 1 http://vevo.ly/zwmO3A #JustinBieber #ColdWater #Vevo #Pop",
      "duration": "2:48",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/0KXQ9eQxnuU?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/0KXQ9eQxnuU?autoplay=1",
      "image_token": "84380ef9eb08e624d4c1416bc93d45bb2828c69689b397ed2f0b4e3e75bd97c3",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.aINQsIGWfE2T9mpb-wYM8QHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.aINQsIGWfE2T9mpb-wYM8QHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.isp7h7vExsRCcQ_1695189555&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.aINQsIGWfE2T9mpb-wYM8QHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2016-09-07T17:56:53.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 54888765
      },
      "title": "Justin Bieber - Cold Water in the Live Lounge",
      "uploader": "BBCRadio1VEVO"
    },
    {
      "content": "https://www.youtube.com/watch?v=AGpMx0cLBXI",
      "description": "Justin performs \"Mistletoe",
      "duration": "8:26",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/AGpMx0cLBXI?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/AGpMx0cLBXI?autoplay=1",
      "image_token": "b8efe916c5786529d5f070deb73bb7ddb7772c4f7b383e5303b40d77fe7e841d",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.9qM-0ImvgQ9jvKLspdATpAHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.9qM-0ImvgQ9jvKLspdATpAHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.s15iBsBCtJnHug_1694472835&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.9qM-0ImvgQ9jvKLspdATpAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-12-17T17:20:03.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 6584699
      },
      "title": "Justin Bieber - Christmas in Washington 2011 720p HD",
      "uploader": "Bustin Jieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=3jA1shMl4dg",
      "description": "A wedding reception surprise dance by the groom and groomsmen to none other than Justin Bieber's \"Baby\"! A beautiful gift to his beautiful bride... Enjoy! (video by studio 205 films) check out our friend from www.doamore.com! Every engagement and wedding ring from Do Amore either: -Feeds Four Children for a Year or -Gives Clean Water to Two ...",
      "duration": "5:52",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/3jA1shMl4dg?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/3jA1shMl4dg?autoplay=1",
      "image_token": "6b77f2d4abbbf96bfdd53efe617b7669c10d286a5784abec9cddc232d373493f",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.cYJer5l5gkt9moa79kueLwEsDh&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.cYJer5l5gkt9moa79kueLwEsDh&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM1.BCkRo_VN_1bAhw_1635331611&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.cYJer5l5gkt9moa79kueLwEsDh&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-10-27T21:56:40.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 1687349
      },
      "title": "Justin Bieber \"Baby\" groomsmen surprise wedding dance!",
      "uploader": "Aaron Cho"
    },
    {
      "content": "https://www.youtube.com/watch?v=Y7yBhaxJBE8",
      "description": "I make custom car decals and vinyl shirts! check out my insta @NatsCrafts21 Check out my brothers gaming videos! https://www.youtube.com/channel/UCchEytA7igu-x8R2ED7vj6Q EDIT: I know some lyrics are wrong! Few days after I posted it I edited where the real words popped up but it all disappeared and youtube doesn't let you do that feature ...",
      "duration": "3:52",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/Y7yBhaxJBE8?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/Y7yBhaxJBE8?autoplay=1",
      "image_token": "098bebf91f5e49bdd2c2405d365587bcb9d6aeef7d33cec15e3ce00d58831916",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.IIkeS-Qt2CTa1uQklBXz0AHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.IIkeS-Qt2CTa1uQklBXz0AHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.3HDgU62hZqfymQ_1694740689&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.IIkeS-Qt2CTa1uQklBXz0AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2012-06-12T20:46:30.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 73770587
      },
      "title": "As Long As You Love Me - Justin Bieber ft. Big Sean - Official Lyrics",
      "uploader": "Nataly Rodriguez"
    },
    {
      "content": "https://www.youtube.com/watch?v=q8hdSF60U0A",
      "description": "🎵Little Music🎵 Justin Bieber - Baby ft. Ludacris (Lyrics Video) ----------------------------- I do not own anything. All credits go to the right owners. No copyright intended. -- 👍 Hit the thumb hard 💗 Please Subscribe https://goo.gl/zk93pN -- Follow Justin Bieber on.. Facebook : https://www.facebook.com/JustinBieber Instagram ...",
      "duration": "3:31",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/q8hdSF60U0A?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/q8hdSF60U0A?autoplay=1",
      "image_token": "4fd446cd65e37c14a0ffbc10134dfe2e1ed84cb4695177894a791e91d898e512",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.rgDpIncVJ77TpRKDF5c5WQHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.rgDpIncVJ77TpRKDF5c5WQHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.-SVMhEteJUG2vA_1696158191&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.rgDpIncVJ77TpRKDF5c5WQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2019-01-12T04:15:00.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 53934082
      },
      "title": "Justin Bieber - Baby ft. Ludacris (Lyrics Video)",
      "uploader": "Little Music"
    },
    {
      "content": "https://www.youtube.com/watch?v=eYzX05lrgCQ",
      "description": "Go to https://expressvpn.com/kurtistown, to take back your Internet privacy TODAY and find out how you can get 3 months free! WEST COAST TOUR TICKETS https://shop.kurtisconner.com/pages/tour-dates I think it might be too late to say sorry :( Justin Bieber has been doing some very weird things lately, so I decided to go over everything and ...",
      "duration": "22:10",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/eYzX05lrgCQ?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/eYzX05lrgCQ?autoplay=1",
      "image_token": "f139361e79cfbebe744beac54908223a861b2d6bf3be999f94c6b12c25ed2aae",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.qUjybk0kgNUridwvr4021AEsDh&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.qUjybk0kgNUridwvr4021AEsDh&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.tuAyZPtoWC9XWg_1685660321&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.qUjybk0kgNUridwvr4021AEsDh&pid=Api"
      },
      "provider": "Bing",
      "published": "2020-01-17T20:00:04.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 5106359
      },
      "title": "Justin Bieber's Bizarre Desperation",
      "uploader": "Kurtis Conner"
    },
    {
      "content": "https://www.youtube.com/watch?v=JKPp3Kshb7c",
      "description": "Justice the album out now: https://justinbieber.lnk.to/Justice Shop Justice merch: https://JustinBieber.lnk.to/OfficialShop Follow Justin: http://facebook.com/justinbieber http://twitter.com/justinbieber http://instagram.com/justinbieber Sign up for Justin's newsletter: http://justinbiebermusic.com #Justice #JustinBieber",
      "duration": "2:33",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/JKPp3Kshb7c?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/JKPp3Kshb7c?autoplay=1",
      "image_token": "d360c12760c71e2534c0048d5d3c680bb2a1e8d95496533910a9a1e5581a62b5",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.LKtPnixbHxmSVutVOJuZ0AHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.LKtPnixbHxmSVutVOJuZ0AHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.k_NQ8VZ4bHTtgw_1645416028&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.LKtPnixbHxmSVutVOJuZ0AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-03-19T04:00:30.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 12093615
      },
      "title": "Justin Bieber - 2 Much (Visualizer)",
      "uploader": "JustinBieberVEVO"
    },
    {
      "content": "https://www.youtube.com/watch?v=zDj34uJdH40",
      "description": "New video!! I try to post every 2 weeks but it's hard with school so I post this video to make you wait until my new video comes out! Hope you like it! Mashup from : https://www.youtube.com/channel/UCEjb6salkNwX148dUEOv26g",
      "duration": "3:21",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/zDj34uJdH40?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/zDj34uJdH40?autoplay=1",
      "image_token": "03b5fcd2c3932eff8919ea79bd113081c8ff533a0cc6b2f479a2df9c7fdfe6ac",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.oTjsBfqFt3HO3rxGgM07ggHgFo&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.oTjsBfqFt3HO3rxGgM07ggHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.8g4MSh967E8X3g_1694646106&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.oTjsBfqFt3HO3rxGgM07ggHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2017-02-05T19:14:39.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 21413936
      },
      "title": "Selena Gomez and Justin Bieber - Same Old Sorry Mashup (Live Version)",
      "uploader": "Celebrities Videos Manips"
    },
    {
      "content": "https://www.youtube.com/watch?v=V9AxIFs0spc",
      "description": "#JustinBieber",
      "duration": "8:07",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/V9AxIFs0spc?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/V9AxIFs0spc?autoplay=1",
      "image_token": "7682f770258de4b2f1cc00d96a08d59fda8603641fac292b4271a3eb7f2b6080",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.xAO_xq_HmW21P49p3yk56QHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.xAO_xq_HmW21P49p3yk56QHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM1.T9wYF6JhkLK8QQ_1627957098&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.xAO_xq_HmW21P49p3yk56QHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-04-30T02:00:04.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 1289705
      },
      "title": "Justin Bieber In Studio",
      "uploader": "M S"
    },
    {
      "content": "https://www.youtube.com/watch?v=HKMP2Woaf2E",
      "description": "Hold On out now: https://JustinBieber.lnk.to/HoldOn Justice the album out now: https://justinbieber.lnk.to/Justice Shop Justice CDs and merch: https://JustinBieber.lnk.to/OfficialShop Lyric Video Created By: Jessica Severn (@j3ssica7) & Chris Shelley (@create) for Deadhappy Follow Justin: http://facebook.com/justinbieber http://twitter.com ...",
      "duration": "2:51",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/HKMP2Woaf2E?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/HKMP2Woaf2E?autoplay=1",
      "image_token": "9c5d23e36c6133acdad88ad03dca2c675612469dd91447f672098818668b47fe",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP._a9YFYEI_GPtQWLBunTUQAHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP._a9YFYEI_GPtQWLBunTUQAHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.lerLPjjcCwRGYA_1694584672&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP._a9YFYEI_GPtQWLBunTUQAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-03-05T05:00:21.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 25235570
      },
      "title": "Justin Bieber - Hold On (Lyric Video)",
      "uploader": "Justin Bieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=WygKLCyuBu0",
      "description": "",
      "duration": "3:07",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/WygKLCyuBu0?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/WygKLCyuBu0?autoplay=1",
      "image_token": "089592f426b782434fc886f2198c550f60a1240873afdff2850aa4bc750be6eb",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.8dTPOdtef0xr6XMDEkDjDgHgFo&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.8dTPOdtef0xr6XMDEkDjDgHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.RASRgd7PaKRzAA_1695427603&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.8dTPOdtef0xr6XMDEkDjDgHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2012-07-16T12:42:30.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 10965053
      },
      "title": "Justin Bieber singing Never let you go live - Mexico 2012",
      "uploader": "PaulinaSV97"
    },
    {
      "content": "https://www.youtube.com/watch?v=G8PP7_JyYtQ",
      "description": "When you spend as much time on the road as Justin Bieber does, having a place that feels like home to go to after every performance is a welcome refuge. Join us as he shows us around his tour bus that features a steam shower and infrared sauna. GQ's The Monster Logo T-shirt: http://gq.mn/EhpblSJ \"The Redemption of Justin Bieber\" cover story ...",
      "duration": "8:08",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/G8PP7_JyYtQ?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/G8PP7_JyYtQ?autoplay=1",
      "image_token": "34e766ed73b768d3556df5c8118bc4a99b8bcb579f48612f3ae096fd4d9e0f41",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.lKVAkk2sT5Ze0tnDhsb1-gHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.lKVAkk2sT5Ze0tnDhsb1-gHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.BOYUZ3pTAxYbgA_1651966303&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.lKVAkk2sT5Ze0tnDhsb1-gHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-04-13T16:00:03.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 11383220
      },
      "title": "Inside Justin Bieber's Tour Bus | GQ",
      "uploader": "GQ"
    },
    {
      "content": "https://www.youtube.com/watch?v=Ktx5clnnONI",
      "description": "Justin Bieber gives flowers to beautiful girl. Disclaimer: I do not claim to own any of the audio or images used in this video. All rights reserved the their rightful owner. This video is used for entertainment purposes only.",
      "duration": "1:35",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/Ktx5clnnONI?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/Ktx5clnnONI?autoplay=1",
      "image_token": "9adadc0d391bff86adfbe5e63cbe0619a877ede70a76639f6dc0a17b1658ba38",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.g02jClsQ0Yzvh4U1X2qQ-gEsDh&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.g02jClsQ0Yzvh4U1X2qQ-gEsDh&pid=Api",
        "motion": "https://tse4.mm.bing.net/th?id=OM2.zBGek3mgjRh7sQ_1641430215&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.g02jClsQ0Yzvh4U1X2qQ-gEsDh&pid=Api"
      },
      "provider": "Bing",
      "published": "2012-07-27T21:08:23.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 4142277
      },
      "title": "Justin Bieber - One less lonely girl LIVE ( Justin gives flowers to a fan )",
      "uploader": "MediaChannel4u"
    },
    {
      "content": "https://www.youtube.com/watch?v=KNei3xCizPU",
      "description": "Justin Bieber on The Ellen DeGeneres Show",
      "duration": "6:39",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/KNei3xCizPU?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/KNei3xCizPU?autoplay=1",
      "image_token": "aa95c5bd7ee7fb93147469304d23223d59be3b26fb9eb2c0e78b260bb2d8a36d",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.POavPlyKUoYSD9daKygJqQHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.POavPlyKUoYSD9daKygJqQHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.6eyjlIVrF00ZOA_1695713833&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.POavPlyKUoYSD9daKygJqQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-02-09T18:33:52.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 5511461
      },
      "title": "Justin Bieber on Ellen Part 2",
      "uploader": "vipercookie3"
    },
    {
      "content": "https://www.youtube.com/watch?v=aRb0pQaTqog",
      "description": "Big Thank you to the number one Justin Bieber Lookalike: https://youtu.be/-qRPX64du5U Snapchat: @cobypersin http://instagram.com/cobypersin https://twitter.com/coby_persin Security: https://instagram.com/kingobie718 https://instagram.com/danieljean56 https://instagram.com/adriangorbaliuk https://instagram.com/goodvibez.marc https://instagram ...",
      "duration": "10:45",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/aRb0pQaTqog?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/aRb0pQaTqog?autoplay=1",
      "image_token": "cab5855026bb209758942ab32a1ecbe445530312a1d4d7daa8ba98e2894fa1c3",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.RORN9KhGs1jy8dIQbz9K1gHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.RORN9KhGs1jy8dIQbz9K1gHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.ve0PnDgDNJx8vw_1694381302&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.RORN9KhGs1jy8dIQbz9K1gHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2018-12-03T17:58:04.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 17422951
      },
      "title": "Fake Justin Bieber Pranks 10,000 People In New York City!",
      "uploader": "Coby Persin"
    },
    {
      "content": "https://www.youtube.com/watch?v=ox7gSxYZwEU",
      "description": "Justin Bieber - Anyone (Official Live Performance) | Vevo Justin Bieber's new 'Justice' album has arrived after a string of video releases that signaled the pop star's more spiritual and self-reflective concerns. \"Lonely\" pondered the tribulations of a life spent in the spotlight. \"Holy\" magnified Justin's personal faith, comparing ...",
      "duration": "3:16",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/ox7gSxYZwEU?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/ox7gSxYZwEU?autoplay=1",
      "image_token": "c8477769e1fceb5e6dcad3265fab3014da0e30cea89fd5e83fe7b46d3aa63c49",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.2rSynt5nVhXa38TLVUMMbAHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.2rSynt5nVhXa38TLVUMMbAHgFo&pid=Api",
        "motion": "https://tse4.mm.bing.net/th?id=OM2.QPppaVp2cxQ1ag_1640849265&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.2rSynt5nVhXa38TLVUMMbAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-03-26T16:00:28.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 11023012
      },
      "title": "Justin Bieber - Anyone (Official Live Performance) | Vevo",
      "uploader": "JustinBieberVEVO"
    },
    {
      "content": "https://www.youtube.com/watch?v=ntYdrLChiyA",
      "description": "He dressed up as a guard to put Ellen's audience through their paces. Check it out!",
      "duration": "3:57",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/ntYdrLChiyA?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/ntYdrLChiyA?autoplay=1",
      "image_token": "d4ba6d8867e5e283444b43d03f9e63cf3e90a40e68c70e62169fd341ef9dccc6",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.akXC2BxJf2x2Ba9t5uGbCAHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.akXC2BxJf2x2Ba9t5uGbCAHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.eO0Kx0uzs50rvQ_1693358877&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.akXC2BxJf2x2Ba9t5uGbCAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2015-03-19T13:00:03.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 21227804
      },
      "title": "Justin Bieber's Security Guard Prank",
      "uploader": "TheEllenShow"
    },
    {
      "content": "https://www.youtube.com/watch?v=OCqygRWUrxA",
      "description": "Justin Bieber - Kiss and Tell. [Lyrics] No Copyright Intended!! Hope you liked it.",
      "duration": "3:46",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/OCqygRWUrxA?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/OCqygRWUrxA?autoplay=1",
      "image_token": "361ec20ba033cc1acbba6d1782df9864e58374e4e5b5ccdba5d27c8358d27c7e",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.PBliQnBof96TPIxibx2FiwHgFo&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.PBliQnBof96TPIxibx2FiwHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.fDFbDVKCEwxugQ_1695883165&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.PBliQnBof96TPIxibx2FiwHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-05-11T01:18:38.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 10683526
      },
      "title": "Justin Bieber - Kiss And Tell. [Lyrics]",
      "uploader": "BiebLyrics"
    },
    {
      "content": "https://www.youtube.com/watch?v=mFjY5UHM8to",
      "description": "Justin Bieber is trying to do The Nae Nae Dance on Ellen show and he is so good at it!",
      "duration": "0:45",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/mFjY5UHM8to?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/mFjY5UHM8to?autoplay=1",
      "image_token": "4da5b285e9ab6f8a35c015b411f02adb4d2a30002c81247ebcf8c561601b2162",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.4KqKHgBQdNm1umqAYj3PEAHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.4KqKHgBQdNm1umqAYj3PEAHgFo&pid=Api",
        "motion": "https://tse4.mm.bing.net/th?id=OM1.mE3a728nL4X0dA_1653195146&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.4KqKHgBQdNm1umqAYj3PEAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2015-09-15T22:14:19.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 5159355
      },
      "title": "Justin Bieber trying to do The Nae Nae Dance on Ellen show",
      "uploader": "FEEDBACKSHOW"
    },
    {
      "content": "https://www.youtube.com/watch?v=uVyHOc1O-HI",
      "description": "follow me on twitter @ddrewjustin",
      "duration": "3:03",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/uVyHOc1O-HI?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/uVyHOc1O-HI?autoplay=1",
      "image_token": "a640a06166ca8796ed3d8213a16cd658c40476dccef4607171ff9ca379090c12",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.e_fFNvLmhhD7MOQt_ExqtQHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.e_fFNvLmhhD7MOQt_ExqtQHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM2.v9atbSN4UyVf3g_1640503550&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.e_fFNvLmhhD7MOQt_ExqtQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2016-07-20T22:36:12.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 16891609
      },
      "title": "Justin Bieber feat. Jaden Smith - Never Say Never LIVE AT MADISON SQUARE GARDEN (July, 19)",
      "uploader": "ddrewjustin"
    },
    {
      "content": "https://www.youtube.com/watch?v=jzVFfnuZ2Ic",
      "description": "Le recomiendo a todos este GRAN CANAL: https://youtu.be/89d_yxw6xuQ",
      "duration": "3:54",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/jzVFfnuZ2Ic?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/jzVFfnuZ2Ic?autoplay=1",
      "image_token": "86d2f039b750186b13652e4e5bb2a01fe0ac473073a61e00fdeb4b6e876b4547",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.cd5QsoZ8FesfJX7TXkfhAgHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.cd5QsoZ8FesfJX7TXkfhAgHgFo&pid=Api",
        "motion": "https://tse4.mm.bing.net/th?id=OM.WtAVXKJ0NY-Wig_1695643530&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.cd5QsoZ8FesfJX7TXkfhAgHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2018-09-13T19:42:01.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 18539510
      },
      "title": "Love Yourself - Justin Bieber (Traducida al Español)",
      "uploader": "sadsong."
    },
    {
      "content": "https://www.youtube.com/watch?v=gmmH1Xq8G0A",
      "description": "He's Back for more",
      "duration": "4:53",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/gmmH1Xq8G0A?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/gmmH1Xq8G0A?autoplay=1",
      "image_token": "157b0c184eca062266f1b24ca56ca24bbd307bf464b432472fd79ddf87683975",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.nex8X7n2s4r4JRaavUcoOAEsDh&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.nex8X7n2s4r4JRaavUcoOAEsDh&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM1.2KGtN93kjCZSpA_1646215850&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.nex8X7n2s4r4JRaavUcoOAEsDh&pid=Api"
      },
      "provider": "Bing",
      "published": "2015-09-29T12:52:12.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 1076417
      },
      "title": "Justin Bieber LIVE on The X Factor Aust 2015 What Do You Mean",
      "uploader": "marajax"
    },
    {
      "content": "https://www.youtube.com/watch?v=zDycNDqzOqY",
      "description": "",
      "duration": "14:34",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/zDycNDqzOqY?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/zDycNDqzOqY?autoplay=1",
      "image_token": "5f75b6cfcc190d53513bdb3d295e3c491f83ec1fe48316c204bd26448e6ed811",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.S8irdU6IEkeIp4nOFqpw7QHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.S8irdU6IEkeIp4nOFqpw7QHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.MVADJKpXvMnWQg_1694826848&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.S8irdU6IEkeIp4nOFqpw7QHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2015-12-13T16:51:11.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 8918604
      },
      "title": "Justin Bieber - Jingle Ball - Capital FM - 2015 (Live) - Full Concert",
      "uploader": "katherine"
    },
    {
      "content": "https://www.youtube.com/watch?v=A1LvxVqxdLw",
      "description": "SZA's New Album \"SOS\" // Available Everywhere Now! Listen Here // https://sza.lnk.to/SOS Follow SZA: https://szasos.com http://instagram.com/sza http://twitter.com/sza http://facebook.com/sza Watch the Offcial Snooze Music Video Here: https://youtu.be/LDY_XyxBu8A?feature=shared Stream 'Snooze': Apple Music: https://music.apple.com/gb ...",
      "duration": "2:29",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/A1LvxVqxdLw?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/A1LvxVqxdLw?autoplay=1",
      "image_token": "6d55bd1a8fe34337c62a1f496393c84ebe2265218e15e21c5cc58b55f4babab7",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.D-0akoo_SNfDIgQ1B4rhPAEsDh&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.D-0akoo_SNfDIgQ1B4rhPAEsDh&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.98Xo3LMwF85XCA_1686875066&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.D-0akoo_SNfDIgQ1B4rhPAEsDh&pid=Api"
      },
      "provider": "Bing",
      "published": "2022-12-13T02:12:29.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 3984878
      },
      "title": "SZA - Snooze feat. Justin Bieber (Official Music Video)",
      "uploader": "rauhlren"
    },
    {
      "content": "https://www.youtube.com/watch?v=-Wjtt5XmUFA",
      "description": "Hey guys, I made it because i was so bored :D",
      "duration": "5:02",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/-Wjtt5XmUFA?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/-Wjtt5XmUFA?autoplay=1",
      "image_token": "5f803cc95e52c836ad5c472a7d7cae22dee99f99c71a94e32161320348214273",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.eNbR6yJYYfSzqfHtaMglEgHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.eNbR6yJYYfSzqfHtaMglEgHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM1.G9_yoofldkeEzg_1641927093&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.eNbR6yJYYfSzqfHtaMglEgHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-08-12T11:23:19.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 1112026
      },
      "title": "Justin Bieber & Selena Gomez - MMVA",
      "uploader": "xVideoForCelebsx"
    },
    {
      "content": "https://www.youtube.com/watch?v=O3Um41pxFFc",
      "description": "",
      "duration": "3:04",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/O3Um41pxFFc?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/O3Um41pxFFc?autoplay=1",
      "image_token": "47b1be3c198a5f618fabd49e9b0a16b6d8fc745a999883defdca72cf131a74ea",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.k3hS8Dy7rlw5z4X7MGPP4AHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.k3hS8Dy7rlw5z4X7MGPP4AHgFo&pid=Api",
        "motion": "https://tse4.mm.bing.net/th?id=OM.03Xsd69i8rS6eQ_1695167367&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.k3hS8Dy7rlw5z4X7MGPP4AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2012-07-16T15:17:19.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 2497479
      },
      "title": "Justin Bieber - One time acoustic in Mexico",
      "uploader": "JBiebersocute"
    },
    {
      "content": "https://www.youtube.com/watch?v=vbORqkXtNoA",
      "description": "Justin bieber - love me lyrics Lyrics : My friends say I'm a fool to think That you're the one for me I guess I'm just a sucker for love Cause honestly the truth is that You know I'm never leaving Cause you're my angel sent from above Baby you can do no wrong My money is yours Give you little more because I love you, love you With me, girl, is ...",
      "duration": "3:07",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/vbORqkXtNoA?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/vbORqkXtNoA?autoplay=1",
      "image_token": "e80411b437d5acf608b771065497fe94e01ed38373604b6aa77f8adfb2c8272a",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.wGa2-RRdBWLSlzyw-Q_t0AHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.wGa2-RRdBWLSlzyw-Q_t0AHgFo&pid=Api",
        "motion": "https://tse4.mm.bing.net/th?id=OM.Yq--PaF3m1RMZw_1694766254&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.wGa2-RRdBWLSlzyw-Q_t0AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-02-02T21:47:46.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 21307714
      },
      "title": "Love me - Justin Bieber Lyrics",
      "uploader": "Jhon Dyland"
    },
    {
      "content": "https://www.youtube.com/watch?v=YfiDBhe3UhM",
      "description": "Justin Bieber's song Pick Me with lyrics! hope you enjoy! please comment, rate and subscribe! if you give me suggestions i'll post more lyric videos and you're username will be mentioned with a \"thank you for the suggestion\" message!! :)",
      "duration": "3:27",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/YfiDBhe3UhM?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/YfiDBhe3UhM?autoplay=1",
      "image_token": "653debddf93f1b6208c0f5adbf5f616b10fe685029a78f37e2fc1f7cf46c2331",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.ajNapUnJH6oJL-_bjB7-LgHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.ajNapUnJH6oJL-_bjB7-LgHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.numtYbnBLsGN2A_1693696891&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.ajNapUnJH6oJL-_bjB7-LgHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-02-17T22:56:25.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 9230833
      },
      "title": "Justin Bieber-Pick Me (With lyrics on screen)",
      "uploader": "ImBiebersBabe4Ever"
    },
    {
      "content": "https://www.youtube.com/watch?v=qpei-UhStp0",
      "description": "Justin Bieber One Less Lonely Girl Live Montreal 2012 HD 1080P marie-pier outaouais salut",
      "duration": "5:09",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/qpei-UhStp0?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/qpei-UhStp0?autoplay=1",
      "image_token": "2bd6ae08035188f6f897dbe7172cb11d250e9e4f2fc3b943c2b43075386d2cf6",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.uPNzm49hgUFGBerh6vrw6gHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.uPNzm49hgUFGBerh6vrw6gHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.AqTBlp58Rx4-Xw_1694510742&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.uPNzm49hgUFGBerh6vrw6gHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2012-11-28T02:54:56.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 12102767
      },
      "title": "Justin Bieber One Less Lonely Girl Live Montreal 2012 HD 1080P",
      "uploader": "digitaljustinbieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=0n664jRR-xU",
      "description": "Justice (Triple Chucks Deluxe) out now: https://JustinBieber.lnk.to/JusticeTCD Shop Justice merch: https://JustinBieber.lnk.to/OfficialShop Follow Justin: http://facebook.com/justinbieber http://twitter.com/justinbieber http://instagram.com/justinbieber Sign up for Justin's newsletter: http://justinbiebermusic.com #JustinBieber #Justice # ...",
      "duration": "4:02",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/0n664jRR-xU?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/0n664jRR-xU?autoplay=1",
      "image_token": "26072f7dcc961627c73d0dcfec5e396ff018fd15af927430c5062e47f358e3d0",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.rKb_iYWaAF-rFuudEvH1YAHgFo&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.rKb_iYWaAF-rFuudEvH1YAHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM2.eACvgTylpy0FAA_1645117831&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.rKb_iYWaAF-rFuudEvH1YAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-03-26T05:23:16.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 5003814
      },
      "title": "Justin Bieber - Wish You Would (Visualizer) ft. Quavo",
      "uploader": "Justin Bieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=6oDIDLt4aXM",
      "description": "This is my first video, so sorry if it's not good. Follow me on twitter: www.twitter.com/justinbeeb Thankyou and enjoy :)",
      "duration": "3:15",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/6oDIDLt4aXM?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/6oDIDLt4aXM?autoplay=1",
      "image_token": "0eed70de99debf22ccfe8596b89fb7af8928b35ee6d6e3780c19eeaf75a50417",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.lkg3cq79g3pLuU3mM2IZYQHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.lkg3cq79g3pLuU3mM2IZYQHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.gyJ0_53GyaScag_1694772175&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.lkg3cq79g3pLuU3mM2IZYQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2010-03-06T06:53:15.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 17123477
      },
      "title": "One Time - Justin Bieber Lyrics",
      "uploader": "justinbeeb"
    },
    {
      "content": "https://www.youtube.com/watch?v=tbEniex3n_A",
      "description": "https://www.youtube.com/watch?v=1cE9uIv3o6M",
      "duration": "2:58",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/tbEniex3n_A?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/tbEniex3n_A?autoplay=1",
      "image_token": "6c5be562d9685e689212e91574542087ef6b59d4c6e9571c87a3a31f5a643a66",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.pwR48-WyRCwOCgRUx8wKigHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.pwR48-WyRCwOCgRUx8wKigHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.yhvXCOvaR8lWTw_1694447200&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.pwR48-WyRCwOCgRUx8wKigHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2011-12-13T21:15:08.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 14442405
      },
      "title": "Justin Bieber - U Got It Bad / Because of You - LIVE @ This Is Justin Bieber 2011 - HD",
      "uploader": "BieberSupport2"
    },
    {
      "content": "https://www.youtube.com/watch?v=G-4tJ63X5vo",
      "description": "A look inside Hailey and Justin's intimate wedding ceremony in South Carolina (complete with a few surprise guests). As the two finally tie the knot, Justin and those closest to him reflect on just how far he's come—from teenage sensation to world famous popstar to mature, loving husband—and what he's had to do to get there. Justin's new ...",
      "duration": "10:57",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/G-4tJ63X5vo?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/G-4tJ63X5vo?autoplay=1",
      "image_token": "dbe44c51a4ff3790fff413d93f9f70af3166573a5e2b1c2f8c5f534b22b83993",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.5AOhcn9QDtgM3Rrzz9cHUQHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.5AOhcn9QDtgM3Rrzz9cHUQHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.JN_8myOeTnSVYA_1694605089&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.5AOhcn9QDtgM3Rrzz9cHUQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2020-02-12T17:00:04.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 154565256
      },
      "title": "The Wedding: Officially Mr. & Mrs. Bieber - Justin Bieber: Seasons",
      "uploader": "Justin Bieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=ENjrJ_zyeUc",
      "description": "JUSTICE the album out now: https://JustinBieber.lnk.to/Justice Production - Def Jam Recordings, Universal Music France, A&R Studios Executive production - A&R Studios Executive video production - La Blogothèque Creative direction - Nick DeMoura Director - David Ctiborsky Edited by Célidja Pornon Band - We The Band Artist management - SB ...",
      "duration": "2:44",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/ENjrJ_zyeUc?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/ENjrJ_zyeUc?autoplay=1",
      "image_token": "fce5a44352ec350bee313220a46b7a9524fc6b910cfb83f6b9c9255f8ce2fc34",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.rqBbYxCzQKcpEF9cxeAqYAHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.rqBbYxCzQKcpEF9cxeAqYAHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM1.Wckv4uy3hM2KNA_1641793046&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.rqBbYxCzQKcpEF9cxeAqYAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-04-13T23:36:10.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 39089863
      },
      "title": "Justin Bieber - Off My Face (Live from Paris)",
      "uploader": "Justin Bieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=xSG2lz5viQw",
      "description": "Justin Bieber - Sorry (Live In Mumbai 2018) Song - Sorry Singer - Justin Bieber Checkout yash suthar channel https://youtu.be/UH6XRq3qHkE hello everyone. #MumbaiLive #JustinBieber #LiveConcert",
      "duration": "6:52",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/xSG2lz5viQw?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/xSG2lz5viQw?autoplay=1",
      "image_token": "659c47ea384cbd3f04009aedb98894edfe326dcfc9d77be0455478334bd8cffc",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.xX6h5V8DUS6YiotBL35JRQHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.xX6h5V8DUS6YiotBL35JRQHgFo&pid=Api",
        "motion": "https://tse4.mm.bing.net/th?id=OM.Nrk-vO4WpE_mIQ_1645221530&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.xX6h5V8DUS6YiotBL35JRQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2019-04-10T05:21:23.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 1946112
      },
      "title": "Justin Bieber - Sorry (Live In Mumbai 2018)",
      "uploader": "Dixit Chouhan"
    },
    {
      "content": "https://www.youtube.com/watch?v=ftLr7mTD4rA",
      "description": "A dive into all of Justin's lesser known hobbies outside music, including his love of style and the story behind his own fashion label Drew House. Plus, Justin and Hailey head to Bluffton, South Carolina to put the finishing touches on their upcoming wedding. Justin's new album 'Changes' out now: https://justinbieber.lnk.to/ChangesYoutube",
      "duration": "8:30",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/ftLr7mTD4rA?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/ftLr7mTD4rA?autoplay=1",
      "image_token": "e4dac553b85e9e2c485a1e9f582a93bec12a03ea732436e8dc1edbc69928787c",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.Xuc13-DyABRQ5LJCqTkCiQHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.Xuc13-DyABRQ5LJCqTkCiQHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.zLgkG4yCVMfKfQ_1696272805&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.Xuc13-DyABRQ5LJCqTkCiQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2020-02-10T17:00:18.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 35731674
      },
      "title": "Planning The Wedding a Year Later - Justin Bieber: Seasons",
      "uploader": "Justin Bieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=8e4f9f-j-5Y",
      "description": "Official lyric video for Justin Bieber & BloodPop® - Friends Out Now via GENPOP/RBMG/Schoolboy/Def Jam/Republic \"Friends\" out now: https://BieberBloodPop.lnk.to/Friends Directed & Edited by Dan Streit Concept by BloodPop® & Ryan Jackson Producers : Dan Streit, Lindsey Mann, Sean Lopez Photographers : Pizzaslime, Sean Lopez, Lindsey Mann, Adam ...",
      "duration": "3:17",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/8e4f9f-j-5Y?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/8e4f9f-j-5Y?autoplay=1",
      "image_token": "45a0254b09a100c55d4d4ff139510ded51ab61ba2a38e617ba2f2b4054e009bb",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.OQj74Lza_np_eozWveP4BgHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.OQj74Lza_np_eozWveP4BgHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.1YRfUyQWYhLnOA_1696521771&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.OQj74Lza_np_eozWveP4BgHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2017-08-18T16:00:01.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 115275201
      },
      "title": "Justin Bieber, BloodPop® - Friends (Official Lyric Video)",
      "uploader": "BloodPopVEVO"
    },
    {
      "content": "https://www.youtube.com/watch?v=7c49TRyQjfs",
      "description": "Justin Bieber stops by unannounced to play the drums with Reggie Watts and The Late Late Show band. \"Subscribe To \"\"The Late Late Show\"\" Channel HERE: http://bit.ly/CordenYouTube Watch Full Episodes of \"\"The Late Late Show\"\" HERE: http://bit.ly/1ENyPw4 Like \"\"The Late Late Show\"\" on Facebook HERE: http://on.fb.me/19PIHLC Follow \"\"The Late Late ...",
      "duration": "2:13",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/7c49TRyQjfs?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/7c49TRyQjfs?autoplay=1",
      "image_token": "7c2c7e1a8d4d0ccb2eef336d1ba0947513a767f9fc67229fcb2104fb250e17b2",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.GwPf8mwX_SNcsoZN7bR2BgHgFo&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.GwPf8mwX_SNcsoZN7bR2BgHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.4thwpvzFp7q0sA_1693345261&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.GwPf8mwX_SNcsoZN7bR2BgHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2015-05-13T08:35:01.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 6406562
      },
      "title": "Justin Bieber Is the New Late Late Show Drummer",
      "uploader": "The Late Late Show with James Corden"
    },
    {
      "content": "https://www.youtube.com/watch?v=OcnrboRX0lQ",
      "description": "Changes out now: https://justinbieber.lnk.to/Changes Follow Justin: http://facebook.com/justinbieber http://twitter.com/justinbieber http://instagram.com/justinbieber Sign up for Justin's newsletter: http://justinbiebermusic.com #JustinBieber #AllAroundMe #Changes",
      "duration": "2:18",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/OcnrboRX0lQ?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/OcnrboRX0lQ?autoplay=1",
      "image_token": "e001041340baf7fefb11062e85b7fe98afce8d464fbbed059136b5f92d6c8938",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.oMjq6_EqsBTsDng8ooa82AHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.oMjq6_EqsBTsDng8ooa82AHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.HeO5yiOXIw-lhA_1695496695&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.oMjq6_EqsBTsDng8ooa82AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2020-02-14T05:00:36.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 8145603
      },
      "title": "Justin Bieber - All Around Me (Audio)",
      "uploader": "Justin Bieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=1WHPExTeOwg",
      "description": "JUSTICE the album out now: https://JustinBieber.lnk.to/Justice Production - Def Jam Recordings, Universal Music France, A&R Studios Executive production - A&R Studios Executive video production - La Blogothèque Creative direction - Nick DeMoura Director - David Ctiborsky Edited by Célidja Pornon Band - We The Band Artist management - SB ...",
      "duration": "2:57",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/1WHPExTeOwg?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/1WHPExTeOwg?autoplay=1",
      "image_token": "3ac6a02e9f98f6be4745d204161be65ebb73da649c807581bcf60f4bcb8d29d3",
      "images": {
        "large": "https://tse3.mm.bing.net/th?id=OVP.4lTRwz-tFuG3kyr20y464wIIEk&pid=Api",
        "medium": "https://tse3.mm.bing.net/th?id=OVP.4lTRwz-tFuG3kyr20y464wIIEk&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM1.Dj389rvOyj-IXQ_1634740795&pid=Api",
        "small": "https://tse3.mm.bing.net/th?id=OVP.4lTRwz-tFuG3kyr20y464wIIEk&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-04-13T23:36:13.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 58613128
      },
      "title": "Justin Bieber - Hold On (Live from Paris)",
      "uploader": "Justin Bieber"
    },
    {
      "content": "https://www.youtube.com/watch?v=NQ1eqKQJwtw",
      "description": "Justin Bieber - Lonely (Official Live Performance) | Vevo Justin Bieber's new 'Justice' album has arrived after a string of video releases that signaled the pop star's more spiritual and self-reflective concerns. \"Lonely\" pondered the tribulations of a life spent in the spotlight. \"Holy\" magnified Justin's personal faith, comparing ...",
      "duration": "2:48",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/NQ1eqKQJwtw?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/NQ1eqKQJwtw?autoplay=1",
      "image_token": "65b7ff7ab850efacdecfe731b3a49d55ec582310910aa1db39c3885534e71c1b",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.Qe2EpjA4jZeK5aIOMwFRRQHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.Qe2EpjA4jZeK5aIOMwFRRQHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM2.uM3mWdPn6Gvd7A_1645312300&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.Qe2EpjA4jZeK5aIOMwFRRQHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2021-03-30T16:00:21.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 19312698
      },
      "title": "Justin Bieber - Lonely (Official Live Performance) | Vevo",
      "uploader": "JustinBieberVEVO"
    },
    {
      "content": "https://www.youtube.com/watch?v=m64vmqWzCtM",
      "description": "Justin Bieber Performs \"As Long As You Love Me\" LIVE On Dancing With The Stars - 9/25/2012. (IN HD)",
      "duration": "3:51",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/m64vmqWzCtM?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/m64vmqWzCtM?autoplay=1",
      "image_token": "8b88af510cd25bdd5ee564c022d45205f249e000fc89f6b15a374a63e7c578bf",
      "images": {
        "large": "https://tse2.mm.bing.net/th?id=OVP.mfDnlESn1PD1UN2laAVP5QHgFo&pid=Api",
        "medium": "https://tse2.mm.bing.net/th?id=OVP.mfDnlESn1PD1UN2laAVP5QHgFo&pid=Api",
        "motion": "https://tse3.mm.bing.net/th?id=OM.aNN6JvlI7RS7Eg_1694553937&pid=Api",
        "small": "https://tse2.mm.bing.net/th?id=OVP.mfDnlESn1PD1UN2laAVP5QHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2012-09-26T02:29:40.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 14196339
      },
      "title": "Justin Bieber Performs \"As Long As You Love Me\" LIVE On Dancing With The Stars - 9/25/2012 (IN HD)",
      "uploader": "mary rhodes"
    },
    {
      "content": "https://www.youtube.com/watch?v=J8yhsbMULsQ",
      "description": "I do not own the music",
      "duration": "3:27",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/J8yhsbMULsQ?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/J8yhsbMULsQ?autoplay=1",
      "image_token": "8466abf4de59b2e9349c3106d246c1896070b54c58e1d8852ec74555bf9ce85a",
      "images": {
        "large": "https://tse1.mm.bing.net/th?id=OVP.6CalQHrUb8G7KNVZxHfrSAHgFo&pid=Api",
        "medium": "https://tse1.mm.bing.net/th?id=OVP.6CalQHrUb8G7KNVZxHfrSAHgFo&pid=Api",
        "motion": "https://tse2.mm.bing.net/th?id=OM.M2R2ursWtRfR3Q_1695515727&pid=Api",
        "small": "https://tse1.mm.bing.net/th?id=OVP.6CalQHrUb8G7KNVZxHfrSAHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2015-11-17T14:13:37.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 15576422
      },
      "title": "Justin Bieber - Purpose (Lyrics)",
      "uploader": "Mrs Downey"
    },
    {
      "content": "https://www.youtube.com/watch?v=2l75R7ZS-c0",
      "description": "Changes out now: https://justinbieber.lnk.to/Changes Follow Justin: http://facebook.com/justinbieber http://twitter.com/justinbieber http://instagram.com/justinbieber Sign up for Justin's newsletter: http://justinbiebermusic.com #JustinBieber #Changes http://vevo.ly/B40Bl0",
      "duration": "3:46",
      "embed_html": "<iframe width=\"1280\" height=\"720\" src=\"https://www.youtube.com/embed/2l75R7ZS-c0?autoplay=1\" frameborder=\"0\" allowfullscreen></iframe>",
      "embed_url": "https://www.youtube.com/embed/2l75R7ZS-c0?autoplay=1",
      "image_token": "9eaf0470bfc177edf82fe56400f9d373c89aa50cb093298a2c6add4b787c4c42",
      "images": {
        "large": "https://tse4.mm.bing.net/th?id=OVP.5uzx88fsAcKkHoMFk8up4AHgFo&pid=Api",
        "medium": "https://tse4.mm.bing.net/th?id=OVP.5uzx88fsAcKkHoMFk8up4AHgFo&pid=Api",
        "motion": "https://tse1.mm.bing.net/th?id=OM.UZoHrXvMdTFuGQ_1694564961&pid=Api",
        "small": "https://tse4.mm.bing.net/th?id=OVP.5uzx88fsAcKkHoMFk8up4AHgFo&pid=Api"
      },
      "provider": "Bing",
      "published": "2020-02-10T23:43:50.0000000",
      "publisher": "YouTube",
      "statistics": {
        "viewCount": 6519363
      },
      "title": "Justin Bieber - Intentions (Live On Saturday Night Live / 2020)",
      "uploader": "JustinBieberVEVO"
    }
]

const route = useRoute()
const tabActive = computed(() => route.query.tab || 'all')

</script>