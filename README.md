# Interwoven
A personal branding website
<!DOCTYPE html>


<html lang="en">


 <head>


  <meta charset="utf-8"/>


  <link href="https://media.base44.com/images/public/6af970535004c2d0e44e7415/fe4d85c40_logo.png/v1/fit/w_180,h_180/fe4d85c40_logo.png" rel="icon" type="image/svg+xml"/>


  <meta content="width=device-width, initial-scale=1.0" name="viewport"/>


  <link href="/manifest.json" rel="manifest"/>


  <title>


   interwoven — a student portfolio


  </title>


  <meta content="interwoven — the projects, essays, internships and college years of a computer science student, threaded together." name="description"/>


  <meta content="interwoven — a student portfolio" property="og:title"/>


  <meta content="Projects, essays, internships and the years between — a college journey, threaded together." property="og:description"/>


  <meta content="website" property="og:type"/>


  <script crossorigin="" src="/assets/index-wMp5Fije.js" type="module">


  </script>


  <link crossorigin="" href="/assets/index-Dcc2TtZ0.css" rel="stylesheet"/>


  <script type="module">


   if (window.self === window.top) {


  let lastPath = "";


  // The visitor's analytics_storage choice from window.__b44Consent; null until one is known.


  let consentGranted = null;


  function getPageNameFromPath(path) {


    const segments = path.split("/").filter(Boolean);


    return segments[0] || null;


  }


  // Same rules as @base44/sdk analytics. Read on every send: the server sets the meta.


  function analyticsMode() {


    const meta = document.querySelector('meta[name="base44-analytics"]');


    return meta ? meta.getAttribute("content") : null;


  }


  function deniedBefore() {


    try {


      return window.localStorage.getItem("base44_analytics_denied") === "1";


    } catch (e) {


      return false;


    }


  }


  function mayTrack() {


    const mode = analyticsMode();


    if (mode === "off") return false;


    if (mode === "consent") return consentGranted === true;


    if (mode === "on") return consentGranted === null ? !deniedBefore() : consentGranted;


    return true;


  }


  function trackPageView() {


    if (!mayTrack()) return;


    const path = window.location.pathname;


    if (path === lastPath) return;


    lastPath = path;


    const pageName = getPageNameFromPath(path) || "home";


    const appId = "6af970535004c2d0e44e7415";


    if (!appId) return;


    fetch(/api/app-logs/${appId}/log-user-in-app/${pageName}, {


      method: "POST",


    }).catch(() => {});


  }


  const originalPushState = history.pushState.bind(history);


  history.pushState = function (...args) {


    originalPushState(...args);


    trackPageView();


  };


  const originalReplaceState = history.replaceState.bind(history);


  history.replaceState = function (...args) {


    originalReplaceState(...args);


    trackPageView();


  };


  window.addEventListener("popstate", trackPageView);


  // A module script runs after the head's classic scripts, so the listener exists by now.


  // Without it, "consent" never sends and "on" relies on the saved Decline only.


  try {


    if (window.__b44Consent) {


      window.__b44Consent.on(


        "analytics_storage",


        function () {


          consentGranted = true;


          trackPageView();


        },


        function () {


          consentGranted = false;


          // A later grant sends the page the visitor is on, even one they saw before.


          lastPath = "";


        }


      );


    }


  } catch (e) {}


  trackPageView();


}


  </script>


  <meta content="on" name="base44-analytics"/>


  <script id="b44-consent-listener">


   (function () {


  if (window.__b44Consent) return;


  var state = {};


  var listeners = [];


  function notify(listener) {


    try {


      (state[listener.category] === "granted" ? listener.grant : listener.revoke)();


    } catch (e) {}


  }


  function read(entry) {


    if (!entry || entry[0] !== "consent" || entry[1] !== "update" || !entry[2]) return;


    for (var category in entry[2]) {


      state[category] = entry[2][category];


      for (var i = 0; i < listeners.length; i++) {


        if (listeners[i].category === category) notify(listeners[i]);


      }


    }


  }


  var dataLayer = (window.dataLayer = window.dataLayer || []);


  // The banner may have restored the visitor's saved choice before this script ran.


  for (var i = 0; i < dataLayer.length; i++) read(dataLayer[i]);


  var push = dataLayer.push;


  dataLayer.push = function () {


    var result = push.apply(dataLayer, arguments);


    for (var j = 0; j < arguments.length; j++) read(arguments[j]);


    return result;


  };


  window.__b44Consent = {


    on: function (category, grant, revoke) {


      var listener = { category: category, grant: grant, revoke: revoke };


      listeners.push(listener);


      if (category in state) notify(listener);


    },


  };


})();


  </script>


  <meta content="on" data-source="default" name="base44-visitor-tracking"/>


  <script id="b44-visitor-tracking">


   (function () {


  try {


    if (window.top !== window) return;


    var CONSENT_CATEGORY = "analytics_storage";


    var attributes = "; Path=/; Secure; SameSite=Lax";


    var keep = "; Max-Age=2592000" + attributes;


    // Read now: the app's router may drop ?ref= before the visitor consents.


    var referrerId = new URLSearchParams(window.location.search).get("ref");


    var referrerOrigin = document.referrer && new URL(document.referrer).origin;


    function write() {


      if (referrerId && /^[0-9a-f]{24}$/i.test(referrerId)) {


        document.cookie = "base44_referrer_id=" + referrerId + keep;


      }


      // First touch: a return from a sign-in or checkout page must not replace who sent the visitor.


      var hasOrigin = /(?:^|;\s*)base44_referrer_origin=/.test(document.cookie);


      if (!hasOrigin && /^https?:\/\//.test(referrerOrigin) && referrerOrigin !== window.location.origin) {


        document.cookie = "base44_referrer_origin=" + referrerOrigin + keep;


      }


    }


    function clear() {


      document.cookie = "base44_referrer_id=; Max-Age=0" + attributes;


      document.cookie = "base44_referrer_origin=; Max-Age=0" + attributes;


    }


    var meta = document.querySelector('meta[name="base44-visitor-tracking"]');


    var signal = navigator.globalPrivacyControl;


    // Global Privacy Control opts the visitor out of tracking Base44 turned on by default.


    var optOut = meta && meta.getAttribute("data-source") === "default" && signal;


    if (meta && meta.getAttribute("data-privacy-signals") === "honor") {


      optOut = signal || navigator.doNotTrack === "1";


    }


    if (optOut) {


      clear();


    } else if (meta && meta.content === "consent") {


      window.__b44Consent.on(CONSENT_CATEGORY, write, clear);


    } else {


      write();


    }


  } catch (e) {}


})();


  </script>


  <meta content="yes" name="mobile-web-app-capable"/>


  <meta content="black" name="apple-mobile-web-app-status-bar-style"/>


  <meta content="interwoven" name="apple-mobile-web-app-title"/>


  <script async="true" data-app-id="6af970535004c2d0e44e7415" data-platform-url="https://app.base44.com" src="/static/js/badge.js">


  </script>


 </head>


 <body>


  <div id="root">


  </div>


 </body>


</html>
