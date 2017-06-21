# curlMaster

Simple curl wrapper. At the moment only method GET.

## Usage

```php
use peterkahl\curlMaster\curlMaster;

$curlm = new curlMaster;

# Specify location of CA certificate file
$curlm->ca_file = '/srv/certs/ca-bundle.crt';

$curlm->useragent = 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10.12; rv:56.0) Gecko/20100101 Firefox/56.0';

# Optional forced caching
$curlm->CacheResponse = true;

$curlm->CacheMaxAge   = 180;

$response = $curlm->get_curl('https://github.com/');

$headers  = $response['headers'];
$body     = $response['body'];
$status   = $response['status'];
$filename = $response['filename'];

if ($status != '200') {
  throw new Exception('HTTP request failed with status '.$status);
}

var_dump($response);

/*
array(4) {
  ["headers"]=>
  array(23) {
    ["status"]=>
    string(15) "HTTP/1.1 200 OK"
    ["date"]=>
    string(29) "Wed, 21 Jun 2017 22:06:16 GMT"
    ["content-type"]=>
    string(24) "text/html; charset=utf-8"
    ["transfer-encoding"]=>
    string(7) "chunked"
    ["server"]=>
    string(10) "GitHub.com"
    ["status-1"]=>
    string(6) "200 OK"
    ["cache-control"]=>
    string(8) "no-cache"
    ["vary"]=>
    string(6) "X-PJAX"
    ["x-ua-compatible"]=>
    string(16) "IE=Edge,chrome=1"
    ["set-cookie"]=>
    string(99) "logged_in=no; domain=.github.com; path=/; expires=Sun, 21 Jun 2037 22:06:16 -0000; secure; HttpOnly"
    ["set-cookie-2"]=>
    string(277) "_gh_sess=eyJzZXNzaW9uX2lkIjoiY2FmNmY3MTc1MTI4ZTA2YWNkNDk4NGNmY2IyYjgzNzciLCJsYXN0X3JlYWRfZnJvbV9yZXBsaWNhcyI6MTQ5ODA4Mjc3NjYwNiwiX2NzcmZfdG9rZW4iOiJwYTd4T0ttVlV2V1U5azl2TjlHRUI5ZjBjVDh6NVFPRktqWEE1elRMVUk4PSJ9--488b029d77b0c43014e35c88315ac352af7363e0; path=/; secure; HttpOnly"
    ["x-request-id"]=>
    string(32) "ea4f2ee585eaa5910f070c14e4b1d085"
    ["x-runtime"]=>
    string(8) "0.058459"
    ["content-security-policy"]=>
    string(770) "default-src 'none'; base-uri 'self'; child-src render.githubusercontent.com; connect-src 'self' uploads.github.com status.github.com collector.githubapp.com api.github.com www.google-analytics.com github-cloud.s3.amazonaws.com github-production-repository-file-5c1aeb.s3.amazonaws.com github-production-upload-manifest-file-7fdce7.s3.amazonaws.com github-production-user-asset-6210df.s3.amazonaws.com wss://live.github.com; font-src assets-cdn.github.com; form-action 'self' github.com gist.github.com; frame-ancestors 'none'; img-src 'self' data: assets-cdn.github.com identicons.github.com collector.githubapp.com github-cloud.s3.amazonaws.com *.githubusercontent.com; media-src 'none'; script-src assets-cdn.github.com; style-src 'unsafe-inline' assets-cdn.github.com"
    ["strict-transport-security"]=>
    string(44) "max-age=31536000; includeSubdomains; preload"
    ["public-key-pins"]=>
    string(447) "max-age=5184000; pin-sha256="WoiWRyIOVNa9ihaBciRSC7XHjliYS9VwUGOIud4PB18="; pin-sha256="RRM1dGqnDFsCJXBTHky16vi1obOlCgFFn/yOhI/y+ho="; pin-sha256="k2v657xBsOVe1PQRwOsHsw3bsGT2VzIqz5K+59sNQws="; pin-sha256="K87oWBWM9UZfyddvDfoxL+8lpNyoUB2ptGtn0fv6G2Q="; pin-sha256="IQBnNBEiFuhj+8x6X8XLgh01V9Ic5/V3IRQLNFFc7v4="; pin-sha256="iie1VXtL7HzAMF+/PVPR9xzT80kQxdZeJ+zduCB3uj0="; pin-sha256="LvRiGEjRqfzurezaWuj8Wie2gyHMrW5Q06LspMnox7A="; includeSubDomains"
    ["x-content-type-options"]=>
    string(7) "nosniff"
    ["x-frame-options"]=>
    string(4) "deny"
    ["x-xss-protection"]=>
    string(13) "1; mode=block"
    ["x-runtime-rack"]=>
    string(8) "0.063833"
    ["content-encoding"]=>
    string(4) "gzip"
    ["vary-3"]=>
    string(15) "Accept-Encoding"
    ["x-github-request-id"]=>
    string(32) "4330:28EE6:E60E7:16289C:594AEDD8"
  }
  ["body"]=>
  string(98940) "<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
  <link rel="dns-prefetch" href="https://assets-cdn.github.com">
  <link rel="dns-prefetch" href="https://avatars0.githubusercontent.com">
  <link rel="dns-prefetch" href="https://avatars1.githubusercontent.com">
  <link rel="dns-prefetch" href="https://avatars2.githubusercontent.com">
  <link rel="dns-prefetch" href="https://avatars3.githubusercontent.com">
  <link rel="dns-prefetch" href="https://github-cloud.s3.amazonaws.com">
  <link rel="dns-prefetch" href="https://user-images.githubusercontent.com/">

<meta content="origin-when-cross-origin" name="referrer" />

  <link crossorigin="anonymous" href="https://assets-cdn.github.com/assets/frameworks-4ba00b1aa0227e4b7a7961544c3b7938afb2720757a471735991ec4475c829e0.css" integrity="sha256-S6ALGqAifkt6eWFUTDt5OK+ycgdXpHFzWZHsRHXIKeA=" media="all" rel="stylesheet" />
  <link crossorigin="anonymous" href="https://assets-cdn.github.com/assets/github-81684fd7510dbd0631cf199316b86c30d3741f8600001e7998ec8ec766d6423c.css" integrity="sha256-gWhP11ENvQYxzxmTFrhsMNN0H4YAAB55mOyOx2bWQjw=" media="all" rel="stylesheet" />


  <link crossorigin="anonymous" href="https://assets-cdn.github.com/assets/site-1cec6e19c02a09d6c96a57a213c77436a5533e7b570074ed409b636f3b67a57b.css" integrity="sha256-HOxuGcAqCdbJaleiE8d0NqVTPntXAHTtQJtjbztnpXs=" media="all" rel="stylesheet" />


  <meta name="viewport" content="width=device-width">

  <title>The world&#39;s leading software development platform · GitHub</title>
  <link rel="search" type="application/opensearchdescription+xml" href="/opensearch.xml" title="GitHub">
  <link rel="fluid-icon" href="https://github.com/fluidicon.png" title="GitHub">
  <meta property="fb:app_id" content="1401488693436528">

    <meta property="og:url" content="https://github.com">
    <meta property="og:site_name" content="GitHub">
    <meta property="og:title" content="Build software better, together">
    <meta property="og:description" content="GitHub is where people build software. More than 22 million people use GitHub to discover, fork, and contribute to over 61 million projects.">
    <meta property="og:image" content="https://assets-cdn.github.com/images/modules/open_graph/github-logo.png">
    <meta property="og:image:type" content="image/png">
    <meta property="og:image:width" content="1200">
    <meta property="og:image:height" content="1200">
    <meta property="og:image" content="https://assets-cdn.github.com/images/modules/open_graph/github-mark.png">
    <meta property="og:image:type" content="image/png">
    <meta property="og:image:width" content="1200">
    <meta property="og:image:height" content="620">
    <meta property="og:image" content="https://assets-cdn.github.com/images/modules/open_graph/github-octocat.png">
    <meta property="og:image:type" content="image/png">
    <meta property="og:image:width" content="1200">
    <meta property="og:image:height" content="620">


  <link rel="assets" href="https://assets-cdn.github.com/">

  <meta name="pjax-timeout" content="1000">

  <meta name="request-id" content="4330:28EE6:E60E7:16289C:594AEDD8" data-pjax-transient>


  <meta name="selected-link" value="/" data-pjax-transient>

  <meta name="google-site-verification" content="KT5gs8h0wvaagLKAVWq8bbeNwnZZK1r1XQysX3xurLU">
<meta name="google-site-verification" content="ZzhVyEFwb7w3e0-uOTltm8Jsck2F5StVihD0exw2fsA">
    <meta name="google-analytics" content="UA-3769691-2">

<meta content="collector.githubapp.com" name="octolytics-host" /><meta content="github" name="octolytics-app-id" /><meta content="https://collector.githubapp.com/github-external/browser_event" name="octolytics-event-url" /><meta content="4330:28EE6:E60E7:16289C:594AEDD8" name="octolytics-dimension-request_id" /><meta content="sea" name="octolytics-dimension-region_edge" /><meta content="iad" name="octolytics-dimension-region_render" />





  <meta class="js-ga-set" name="dimension1" content="Logged Out">




      <meta name="hostname" content="github.com">
  <meta name="user-login" content="">

      <meta name="expected-hostname" content="github.com">
    <meta name="js-proxy-site-detection-payload" content="MGRhNWQ4NzU2NWY0MmU5YWJmZDBjOTQ1YjM3NmU1MGUxZTk1YzA2N2ZjOGFlODIxOGNmMWIzNzc3YWQwZjBjY3x7InJlbW90ZV9hZGRyZXNzIjoiMTI4LjE5OS44OS4xODUiLCJyZXF1ZXN0X2lkIjoiNDMzMDoyOEVFNjpFNjBFNzoxNjI4OUM6NTk0QUVERDgiLCJ0aW1lc3RhbXAiOjE0OTgwODI3NzYsImhvc3QiOiJnaXRodWIuY29tIn0=">


  <meta name="html-safe-nonce" content="4b4031cfa352a6d93ed84da5158f8eb466c8ee9b">

  <meta http-equiv="x-pjax-version" content="161b9919cc8adfb2f2f97c7941696b2c">


      <meta name="viewport" content="width=device-width">
  <link crossorigin="anonymous" href="https://assets-cdn.github.com/assets/site-1cec6e19c02a09d6c96a57a213c77436a5533e7b570074ed409b636f3b67a57b.css" integrity="sha256-HOxuGcAqCdbJaleiE8d0NqVTPntXAHTtQJtjbztnpXs=" media="all" rel="stylesheet" />


    <link rel="canonical" href="https://github.com/" data-pjax-transient>


  <meta name="browser-stats-url" content="https://api.github.com/_private/browser/stats">

  <meta name="browser-errors-url" content="https://api.github.com/_private/browser/errors">

  <link rel="mask-icon" href="https://assets-cdn.github.com/pinned-octocat.svg" color="#000000">
  <link rel="icon" type="image/x-icon" href="https://assets-cdn.github.com/favicon.ico">

<meta name="theme-color" content="#1e2327">



  </head>

  <body class="logged-out env-production emoji-size-boost page-responsive min-width-0 f4 site-header-dark">




  <div class="position-relative js-header-wrapper ">
    <a href="#start-of-content" tabindex="1" class="px-2 py-4 show-on-focus js-skip-to-content">Skip to content</a>
    <div id="js-pjax-loader-bar" class="pjax-loader-bar"><div class="progress"></div></div>







          <header class="site-header js-details-container Details" role="banner">
  <div class="site-nav-container">
    <a class="header-logo-invertocat" href="https://github.com/" aria-label="Homepage" data-ga-click="(Logged out) Header, go to homepage, icon:logo-wordmark">
      <svg aria-hidden="true" class="octicon octicon-mark-github" height="32" version="1.1" viewBox="0 0 16 16" width="32"><path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>
    </a>

    <button class="btn-link float-right site-header-toggle js-details-target" type="button" aria-label="Toggle navigation" aria-expanded="false">
      <svg aria-hidden="true" class="octicon octicon-three-bars" height="24" version="1.1" viewBox="0 0 12 16" width="18"><path fill-rule="evenodd" d="M11.41 9H.59C0 9 0 8.59 0 8c0-.59 0-1 .59-1H11.4c.59 0 .59.41.59 1 0 .59 0 1-.59 1h.01zm0-4H.59C0 5 0 4.59 0 4c0-.59 0-1 .59-1H11.4c.59 0 .59.41.59 1 0 .59 0 1-.59 1h.01zM.59 11H11.4c.59 0 .59.41.59 1 0 .59 0 1-.59 1H.59C0 13 0 12.59 0 12c0-.59 0-1 .59-1z"/></svg>
    </button>

    <div class="site-header-menu">
      <nav class="site-header-nav">
        <a href="/features" class="js-selected-navigation-item nav-item" data-ga-click="Header, click, Nav menu - item:features" data-selected-links="/features /features/code-review /features/project-management /features/integrations /features">
          Features
</a>        <a href="/business" class="js-selected-navigation-item nav-item" data-ga-click="Header, click, Nav menu - item:business" data-selected-links="/business /business/security /business/customers /business">
          Business
</a>        <a href="/explore" class="js-selected-navigation-item nav-item" data-ga-click="Header, click, Nav menu - item:explore" data-selected-links="/explore /trending /trending/developers /integrations /integrations/feature/code /integrations/feature/collaborate /integrations/feature/ship /showcases /explore">
          Explore
</a>            <a href="/marketplace" class="js-selected-navigation-item nav-item" data-ga-click="Header, click, Nav menu - item:marketplace" data-selected-links=" /marketplace">
              Marketplace
</a>        <a href="/pricing" class="js-selected-navigation-item nav-item" data-ga-click="Header, click, Nav menu - item:pricing" data-selected-links="/pricing /pricing/developer /pricing/team /pricing/business-hosted /pricing/business-enterprise /pricing">
          Pricing
</a>      </nav>

      <div class="site-header-actions">
          <div class="header-search   js-site-search" role="search">
  <!-- '"` --><!-- </textarea></xmp> --></option></form><form accept-charset="UTF-8" action="/search" class="js-site-search-form" data-unscoped-search-url="/search" method="get"><div style="margin:0;padding:0;display:inline"><input name="utf8" type="hidden" value="&#x2713;" /></div>
    <label class="form-control header-search-wrapper js-chromeless-input-container">
        <a href="/dashboard" class="header-search-scope no-underline">/dashboard</a>
      <input type="text"
        class="form-control header-search-input js-site-search-focus "
        data-hotkey="s"
        name="q"
        value=""
        placeholder="Search GitHub"
        aria-label="Search GitHub"
        data-unscoped-placeholder="Search GitHub"
        data-scoped-placeholder="Search"
        autocapitalize="off">
        <input type="hidden" class="js-site-search-type-field" name="type" >
    </label>
</form></div>


          <a class="text-bold site-header-link" href="/login" data-ga-click="(Logged out) Header, clicked Sign in, text:sign-in">Sign in</a>
            <span class="text-gray">or</span>
            <a class="text-bold site-header-link" href="/join?source=header-home" data-ga-click="(Logged out) Header, clicked Sign up, text:sign-up">Sign up</a>
      </div>
    </div>
  </div>
</header>



  </div>

  <div id="start-of-content" class="show-on-focus"></div>

    <div id="js-flash-container">
</div>



  <div role="main">


<div class="jumbotron jumbotron-codelines">
  <div class="container-lg p-responsive position-relative">
    <div class="d-md-flex flex-items-center gutter-md-spacious">
      <div class="col-md-7 text-md-left ">
        <h1 class="alt-h0 text-white lh-condensed-ultra mb-3">Built for developers</h1>
        <p class="alt-lead mb-4">
          GitHub is a development platform inspired by the way you work. From <a href="/open-source" class="text-white jumbotron-link">open source</a> to <a href="/business" class="text-white jumbotron-link">business</a>, you can host and review code, manage projects, and build software alongside millions of other developers.
        </p>
      </div>
        <div class="mx-auto col-sm-8 col-md-5 hide-sm rounded-1 bg-gray-light pt-4 pb-5">
          <!-- '"` --><!-- </textarea></xmp> --></option></form><form accept-charset="UTF-8" action="/join" autocomplete="off" class="home-hero-signup js-signup-form" method="post"><div style="margin:0;padding:0;display:inline"><input name="utf8" type="hidden" value="&#x2713;" /><input name="authenticity_token" type="hidden" value="Jl1CDB0sP9rORtLjKfpK+p9GVnCKwXl2KEJ0cc2Deb32FolcC/9hbzpnRIO7YoA9g/Z6FEsnNZmoGBK5BAWITg==" /></div>            <dl class="form">
              <dd>
                <label class="form-label text-gray f5" for="user[login]">Username</label>
                <input type="text" name="user[login]" id="user[login]" class="form-control form-control-lg input-block" placeholder="Pick a username" data-autocheck-url="/signup_check/username" data-autocheck-authenticity-token="fkbR9C2SAa3lM63yKdyq5jfclc0fb44UZTTs4v/fBrb+lfvCjsNzjeLbeCUp6+gKTIxosGIkaKxtZv48NBsOxA==" autofocus>
              </dd>
            </dl>
            <dl class="form">
              <dd>
                <label class="form-label text-gray f5" for="user[email]">Email</label>
                <input type="text" name="user[email]" id="user[email]" class="form-control form-control-lg input-block js-email-notice-trigger" placeholder="Your email address" data-autocheck-url="/signup_check/email" data-autocheck-authenticity-token="LgbNPt14BHIr9gDdhcwkK7CfLs0CbJMhgr9J5bh9VD+qU+0HrrCTfEtR7kRL1J5uyy37m3ywGAmLfIt3S7ND4w==">
              </dd>
            </dl>
            <dl class="form">
              <dd>
                <label class="form-label text-gray f5" for="user[password]">Password</label>
                <input type="password" name="user[password]" id="user[password]" class="form-control form-control-lg input-block" placeholder="Create a password" data-autocheck-url="/signup_check/password" data-autocheck-authenticity-token="/B0vs6D5S9QwRn5JBcCqVjJZbzyc0PCCiOjOYgpayh5IFrQBi7jlElJMsTmCtudiYlFZWLRSnoSGcOxx9sWL1Q==">
              </dd>
              <p class="form-control-note">Use at least one letter, one numeral, and seven characters.</p>
            </dl>
            <input type="hidden" name="source" class="js-signup-source" value="form-home">
            <input class="form-control" name="timestamp" type="hidden" value="1498082776585" />
<input class="form-control" name="timestamp_secret" type="hidden" value="ce570381d95481c43478087a6f240c54dda9f838e919c037be93d475a0a04bd5" />

            <button class="btn btn-primary btn-large f4 btn-block" type="submit">Sign up for GitHub</button>
            <p class="form-control-note text-center">
              By clicking "Sign up for GitHub", you agree to our
              <a class="" href="https://help.github.com/terms" target="_blank">terms of service</a> and
              <a class="" href="https://help.github.com/privacy" target="_blank">privacy policy</a>. <span class="js-email-notice">We’ll occasionally send you account related emails.</span>
            </p>
</form>        </div>
        <div class="d-sm-none text-center">
          <a href="/join?source=button-home" class="btn btn-primary btn-large border-0" rel="nofollow">Sign up for GitHub</a>
        </div>
    </div>
  </div>
</div>

<div class="bg-gray-dark border-bottom py-4 py-md-2">
  <div class="px-4 mx-auto clearfix container-lg p-responsive">
    <div class="d-block d-md-flex flex-items-center">
      <div class="mb-4 my-2 mr-md-4 ml-md-n6 text-center">
        <svg xmlns="http://www.w3.org/2000/svg" id="Layer_1" data-name="Layer 1" viewBox="0 0 349.65 253.23" class="" width="220"><title>platform</title><path d="M176.42,165.13H153.58a1.7,1.7,0,0,1,0-3.39h22.84A1.71,1.71,0,0,1,176.42,165.13Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M26.53,165.13H3.68a1.7,1.7,0,0,1,0-3.39H26.52A1.7,1.7,0,0,1,26.53,165.13Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M43.51,163.44" transform="translate(-0.13 0.01)" style="fill:none;stroke:#2f363d;stroke-linecap:round;stroke-linejoin:round;stroke-width:3.393686056137085px"></path><path d="M140.81,163.44" transform="translate(-0.13 0.01)" style="fill:none;stroke:#2f363d;stroke-linecap:round;stroke-linejoin:round;stroke-width:3.393686056137085px"></path><path d="M139.35,192.84H88.52a1.7,1.7,0,0,1,0-3.39h50.83A1.7,1.7,0,0,1,139.35,192.84Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M71.54,192.84H1.7a1.7,1.7,0,0,1,0-3.39H71.55A1.7,1.7,0,0,1,71.54,192.84Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M316.09,192.84H278.26a1.7,1.7,0,0,1,0-3.39h37.83A1.7,1.7,0,0,1,316.09,192.84Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M261.31,137.45H228.19a1.7,1.7,0,0,1,0-3.39h33.12a1.7,1.7,0,1,1,.26,3.39h-0.26Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M212.69,137.45H165.15a1.7,1.7,0,0,1,0-3.39h47.54A1.7,1.7,0,0,1,212.69,137.45Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M285.07,165.13H193.4a1.7,1.7,0,0,1-.26-3.39h91.93A1.7,1.7,0,0,1,285.07,165.13Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M260.56,192.84H156.39a1.7,1.7,0,0,1,0-3.39H260.56a1.7,1.7,0,1,1,.26,3.39h-0.26Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M336.1,165.13H298.28a1.7,1.7,0,0,1,0-3.39h37.83A1.7,1.7,0,0,1,336.1,165.13Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M348,220.53H251.44a1.7,1.7,0,0,1,0-3.39H348a1.7,1.7,0,0,1,.26,3.39H348Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M323.88,137H278.19a1.7,1.7,0,0,1,0-3.39h45.69A1.7,1.7,0,0,1,323.88,137Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M329.81,109.3H292.5a1.7,1.7,0,1,1-.26-3.39h37.57a1.7,1.7,0,1,1,.26,3.39h-0.26Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M162.21,79.88H143.37a20,20,0,0,1-20-20V38.61a1.7,1.7,0,0,1,3.39,0V59.85a16.65,16.65,0,0,0,16.63,16.63h18.82a1.7,1.7,0,1,1,0,3.4h0Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M80,143.24a1.7,1.7,0,0,1-1.7-1.7h0c0-14,11-24.13,26.13-24.13h2.25a16.65,16.65,0,0,0,16.63-16.63V57.29a1.7,1.7,0,0,1,3.39,0v43.49a20,20,0,0,1-20,20h-2.25c-13.18,0-22.74,8.72-22.74,20.74a1.7,1.7,0,0,1-1.68,1.72h0Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M80,239a1.7,1.7,0,0,1-1.7-1.7h0V184.93a1.7,1.7,0,1,1,3.39,0v52.34A1.7,1.7,0,0,1,80,239Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M35,182.65" transform="translate(-0.13 0.01)" style="fill:none;stroke:#59616a;stroke-linecap:round;stroke-linejoin:round;stroke-width:3.393686056137085px"></path><path d="M184.91,179.25a1.7,1.7,0,0,1-1.7-1.7h0V144.24a1.7,1.7,0,0,1,3.39,0v33.31A1.7,1.7,0,0,1,184.91,179.25Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M184.91,129a1.7,1.7,0,0,1-1.7-1.7h0V102.58a1.7,1.7,0,0,1,3.39,0v24.68A1.7,1.7,0,0,1,184.91,129Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M228.58,165.13a1.69,1.69,0,0,1-1.2-.5l-27.7-27.7a1.7,1.7,0,0,1,2.4-2.4l27.7,27.7A1.7,1.7,0,0,1,228.58,165.13Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M334.1,218.83" transform="translate(-0.13 0.01)" style="fill:none;stroke:#2f363d;stroke-linecap:round;stroke-linejoin:round;stroke-width:3.393686056137085px"></path><path d="M139.26,31.82H110.81a1.7,1.7,0,0,1-1.7-1.7h0V1.69a1.7,1.7,0,0,1,1.7-1.7h28.43a1.7,1.7,0,0,1,1.7,1.7h0V30.13A1.7,1.7,0,0,1,139.26,31.82Zm-26.73-3.39h25v-25h-25v25Z" transform="translate(-0.13 0.01)" style="fill:#6b4fa0"></path><path d="M221.34,253.22H200.09a8.21,8.21,0,0,1-8.2-8.2V210.35a1.7,1.7,0,0,1,2.81-1.28l9.73,8.47h16.9a8.21,8.21,0,0,1,8.2,8.2V245A8.21,8.21,0,0,1,221.34,253.22Zm-26.05-39.09v30.94a4.81,4.81,0,0,0,4.81,4.81h21.24a4.81,4.81,0,0,0,4.81-4.81V225.75a4.81,4.81,0,0,0-4.81-4.81H203.81a1.69,1.69,0,0,1-1.11-.42Z" transform="translate(-0.13 0.01)" style="fill:#f26b21"></path><path d="M174.18,239H160.29a6,6,0,0,1-6-6v-12.6a6,6,0,0,1,6-6h10.83l6.2-5.4a1.7,1.7,0,0,1,2.81,1.28v22.67a6,6,0,0,1-5.95,6h0Zm-13.89-21.1a2.56,2.56,0,0,0-2.56,2.56V233a2.56,2.56,0,0,0,2.56,2.56h13.89a2.56,2.56,0,0,0,2.56-2.56V214.08l-3.87,3.37a1.69,1.69,0,0,1-1.11.42H160.29Z" transform="translate(-0.13 0.01)" style="fill:#ffd23e"></path><circle cx="184.78" cy="191.15" r="8.55" style="fill:#24292e"></circle><path d="M184.91,201.39a10.25,10.25,0,1,1,10.25-10.26A10.25,10.25,0,0,1,184.91,201.39Zm0-17.11a6.86,6.86,0,1,0,6.9,6.85,6.86,6.86,0,0,0-6.9-6.85h0Z" transform="translate(-0.13 0.01)" style="fill:#f26b21"></path><path d="M183.37,83a1.69,1.69,0,0,1-1.2-.5l-3.26-3.26a1.7,1.7,0,0,1,2.26-2.54l0.14,0.14,2.06,2.06,5.13-5.13a1.7,1.7,0,0,1,2.4,2.4l-6.33,6.33A1.69,1.69,0,0,1,183.37,83Z" transform="translate(-0.13 0.01)" style="fill:#3567b0"></path><path d="M269.06,243.33a1.7,1.7,0,0,1-1.7-1.7h0V226.48a1.7,1.7,0,1,1,3.39,0v15.15A1.7,1.7,0,0,1,269.06,243.33Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M269.06,211.2a1.7,1.7,0,0,1-1.7-1.7h0V171.93a1.7,1.7,0,0,1,3.39,0V209.5A1.7,1.7,0,0,1,269.06,211.2Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M269.06,156.65a1.7,1.7,0,0,1-1.7-1.7h0V96.51a16.65,16.65,0,0,0-16.63-16.63H207.61a1.7,1.7,0,1,1-.26-3.39h43.38a20,20,0,0,1,20,20v58.45A1.7,1.7,0,0,1,269.06,156.65Z" transform="translate(-0.13 0.01)" style="fill:#59616a"></path><path d="M199.12,94.13H170.7a1.7,1.7,0,0,1-1.7-1.7h0V64a1.7,1.7,0,0,1,1.7-1.7h28.43a1.7,1.7,0,0,1,1.7,1.7h0V92.4a1.7,1.7,0,0,1-1.67,1.73h0Zm-26.73-3.39h25v-25h-25v25Z" transform="translate(-0.13 0.01)" style="fill:#3567b0"></path><path d="M125,23.13a1.7,1.7,0,0,1-1.7-1.7h0v-11a1.7,1.7,0,0,1,3.39,0v11A1.7,1.7,0,0,1,125,23.13Z" transform="translate(-0.13 0.01)" style="fill:#6b4fa0"></path><path d="M130.54,17.6h-11a1.7,1.7,0,0,1,0-3.39h11a1.7,1.7,0,1,1,.26,3.39h-0.26Z" transform="translate(-0.13 0.01)" style="fill:#6b4fa0"></path><path d="M132.69,165.13h-70a1.7,1.7,0,0,1,0-3.39h70A1.7,1.7,0,0,1,132.69,165.13Z" transform="translate(-0.13 0.01)" style="fill:#2f363d"></path><path d="M147.37,179.34H34.07a1.7,1.7,0,0,1-1.7-1.7h0V149.21a1.7,1.7,0,0,1,1.7-1.7h113.3a1.7,1.7,0,0,1,1.7,1.7h0v28.43a1.7,1.7,0,0,1-1.7,1.7h0Zm-111.56-3.4h109.9v-25H35.81v25Z" transform="translate(-0.13 0.01)" style="fill:#27a74a"></path><path d="M99.41,165.13H62.74a1.7,1.7,0,0,1,0-3.39H99.41A1.7,1.7,0,0,1,99.41,165.13Z" transform="translate(-0.13 0.01)" style="fill:#27a74a"></path><path d="M47.09,168.29a1.69,1.69,0,0,1-1.2-.5l-3.26-3.26a1.7,1.7,0,0,1,2.4-2.4l2.06,2.06,5.13-5.13a1.7,1.7,0,0,1,2.4,2.4l-6.33,6.33A1.69,1.69,0,0,1,47.09,168.29Z" transform="translate(-0.13 0.01)" style="fill:#27a74a"></path></svg>

      </div>
      <div class="flex-column text-center text-md-left">
        <h4 class="alt-h3 text-white">Platform updates</h4>
        <p class="mb-3" style="color:#939393;">
          Extend your workflow with GitHub Marketplace, GitHub GraphQL API, and more.
        </p>
        <p class="mb-1">
          <a href="/updates" aria-label="Read recent GitHub product updates" class="btn btn-transparent">See recent updates</a>
        </p>
      </div>
    </div>
  </div>
</div>

<div class="featurette">
  <div class="container-lg p-responsive">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 66.2 59.33" class="d-block mx-auto mb-2" width="64"><title>teams</title><path d="M5.49 47.04h-.14a1 1 0 0 1-.86-1.12 9.61 9.61 0 0 1 16.82-4.87 1 1 0 1 1-1.52 1.3 7.61 7.61 0 0 0-13.31 3.84 1 1 0 0 1-.99.85z" fill="#79b8ff"></path><path d="M13.99 39.67a7.12 7.12 0 1 1 7.12-7.12 7.13 7.13 0 0 1-7.12 7.12zm0-12.24a5.12 5.12 0 1 0 5.12 5.12 5.12 5.12 0 0 0-5.12-5.11zm46.24 19.61a1 1 0 0 1-1-.87 7.61 7.61 0 0 0-13.31-3.84 1 1 0 1 1-1.52-1.3 9.61 9.61 0 0 1 16.82 4.87 1 1 0 0 1-.86 1.13h-.14z" fill="#79b8ff"></path><path d="M51.71 39.67a7.12 7.12 0 1 1 7.12-7.12 7.13 7.13 0 0 1-7.12 7.12zm0-12.24a5.12 5.12 0 1 0 5.12 5.12 5.12 5.12 0 0 0-5.12-5.11z" fill="#79b8ff"></path><path d="M43.62 59.34a1 1 0 0 1-1-.89 9.73 9.73 0 0 0-9.78-8.59 9.87 9.87 0 0 0-9.79 8.47 1.01 1.01 0 1 1-2-.27 11.88 11.88 0 0 1 11.77-10.21 11.73 11.73 0 0 1 11.79 10.39 1 1 0 0 1-.89 1.1h-.11z" fill="#2088ff"></path><path d="M32.84 49.85a8.76 8.76 0 1 1 8.76-8.76 8.77 8.77 0 0 1-8.76 8.76zm0-15.52a6.76 6.76 0 1 0 6.76 6.76 6.77 6.77 0 0 0-6.76-6.75z" fill="#2088ff"></path><path d="M32.84 25.47a7.12 7.12 0 1 1 7.12-7.12 7.13 7.13 0 0 1-7.12 7.12zm0-12.24a5.12 5.12 0 1 0 5.12 5.12 5.12 5.12 0 0 0-5.12-5.11z" fill="#79b8ff"></path><path d="M39.86 29.08a1 1 0 0 1-.82-.42 7.61 7.61 0 0 0-12.39 0 1 1 0 0 1-1.63-1.16 9.61 9.61 0 0 1 15.65 0 1 1 0 0 1-.81 1.58z" fill="#79b8ff"></path><path d="M47.35 22.33a1 1 0 0 1-1-1V5.8a5.81 5.81 0 0 1 5.8-5.8h8.24a5.81 5.81 0 0 1 5.8 5.8v5.05c0 4-2.48 6.35-6.64 6.35h-6.67l-4.83 4.83a1 1 0 0 1-.7.3zm4.8-20.32a3.8 3.8 0 0 0-3.8 3.8v13.11l3.41-3.41a1 1 0 0 1 .71-.29h7.08c3.08 0 4.64-1.46 4.64-4.35V5.82a3.8 3.8 0 0 0-3.8-3.8h-8.24zM18.84 22.33a1 1 0 0 1-.71-.29l-4.83-4.8H6.63c-4.16 0-6.64-2.37-6.64-6.35V5.84a5.81 5.81 0 0 1 5.8-5.8h8.24a5.81 5.81 0 0 1 5.8 5.8v15.52a1 1 0 0 1-.99.97zm-13-20.32a3.8 3.8 0 0 0-3.8 3.8v5.05c0 2.88 1.56 4.35 4.64 4.35h7.03a1 1 0 0 1 .71.29l3.41 3.41V5.8a3.81 3.81 0 0 0-3.8-3.8H5.79z" fill="#2088ff"></path><circle cx="53.75" cy="8.66" r="1.41" fill="#2088ff"></circle><circle cx="59.11" cy="8.66" r="1.41" fill="#2088ff"></circle><circle cx="7.24" cy="8.66" r="1.41" fill="#2088ff"></circle><circle cx="12.6" cy="8.66" r="1.41" fill="#2088ff"></circle></svg>

    <h6 class="alt-h4 text-normal text-gray text-center">
      GitHub for teams
    </h6>
    <h2 class="alt-h1 lh-condensed mt-3 mb-2 text-center">
      A better way to work together
    </h2>
    <p class="lead text-center col-md-8 mx-auto">
      GitHub brings teams together to work through problems, move ideas forward, and learn from each other along the way.
    </p>
    <div class="text-center">
        <a href="/join?plan=business&amp;setup_organization=true&amp;source=business-page" class="btn btn-large btn-outline">Sign up your team</a>
    </div>

    <div class="d-md-flex flex-items-center flex-row-reverse my-5">
      <div class="col-sm-8 col-md-6 mx-auto text-center p-5">
        <img src="https://assets-cdn.github.com/images/modules/site/home-illo-conversation.svg" alt="" width="360" class="d-block width-fit mx-auto">
      </div>
      <div class="col-sm-8 col-md-6 mx-auto text-center text-md-left pr-md-5">
        <h3 class="alt-h3 mb-1">Write better code</h3>
        <p class="">
          Collaboration makes perfect. The conversations and code reviews that happen in Pull Requests help your team share the weight of your work and improve the software you build.
        </p>
        <p>
          <a class="mt-3" href="/features/code-review">Learn about code review on <span class="no-wrap">GitHub<svg aria-hidden="true" class="octicon octicon-chevron-right ml-2 v-align-text-bottom" height="16" version="1.1" viewBox="0 0 8 16" width="8"><path fill-rule="evenodd" d="M7.5 8l-5 5L1 11.5 4.75 8 1 4.5 2.5 3z"/></svg></span></a>
        </p>
      </div>
    </div>

    <div class="d-md-flex flex-items-center my-5">
      <div class="col-sm-8 col-md-6 mx-auto text-center p-5">
        <img src="https://assets-cdn.github.com/images/modules/site/home-illo-chaos.svg" alt="" class="d-block width-fit mx-auto">
      </div>
      <div class="col-sm-8 col-md-6 mx-auto text-center text-md-left pl-md-5">
        <h3 class="alt-h3 mb-1">Manage your chaos</h3>
        <p class="">
          Take a deep breath. On GitHub, project management happens in Issues and Projects, right alongside your code. All you have to do is mention a teammate to get them involved.
        </p>
        <p>
          <a class="mt-3" href="/features/project-management">Learn about project management on <span class="no-wrap">GitHub<svg aria-hidden="true" class="octicon octicon-chevron-right ml-2 v-align-text-bottom" height="16" version="1.1" viewBox="0 0 8 16" width="8"><path fill-rule="evenodd" d="M7.5 8l-5 5L1 11.5 4.75 8 1 4.5 2.5 3z"/></svg></span></a>
        </p>
      </div>
    </div>
  </div>
</div>

<div class="featurette">
  <div class="container-lg p-responsive">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64.1 59.57" class="d-block mx-auto mb-2" width="64"><title>security-admin</title><path d="M34.27 51.67H3a3 3 0 0 1-3-3V3a3 3 0 0 1 3-3h48.3a3 3 0 0 1 3 3v22.11a1 1 0 0 1-2 0V3a1 1 0 0 0-1-1H3a1 1 0 0 0-1 1v45.67a1 1 0 0 0 1 1h31.27a1 1 0 1 1 0 2z" fill="#79b8ff"></path><path d="M11.1 16.85a1 1 0 0 1-.71-.29l-2.85-2.85a1 1 0 0 1 1.41-1.41l2.14 2.14 5-5a1 1 0 0 1 1.42 1.4l-5.66 5.75a1.2 1.2 0 0 1-.75.26zM62.1 59.57H44.3a2.08 2.08 0 0 1-2-2v-13.8a1.93 1.93 0 0 1 2-2h17.8a1.93 1.93 0 0 1 2 2v13.8a1.93 1.93 0 0 1-2 2zm-17.8-2.06l17.8.06v-13.8H44.3v13.74z" fill="#2088ff"></path><path d="M59.9 43.07h-2v-4.3a4.8 4.8 0 0 0-9.6 0v4.3h-2v-4.3a6.8 6.8 0 0 1 13.6 0v4.3z" fill="#2088ff"></path><circle cx="53.3" cy="49.67" r="2.2" fill="#2088ff"></circle><path d="M53.3 54.57a1 1 0 0 1-1-1v-2.9a1 1 0 0 1 2 0v2.9a1 1 0 0 1-1 1z" fill="#2088ff"></path><path d="M43.18 11.48H23.92a1 1 0 1 1 0-2h19.27a1 1 0 0 1-.01 2zM34.27 17.1H23.92a1 1 0 1 1 0-2h10.36a1 1 0 1 1-.01 2z" fill="#79b8ff"></path><path d="M11.1 41.77a1 1 0 0 1-.71-.29l-2.85-2.85a1 1 0 0 1 1.41-1.41l2.14 2.14 5-5a1 1 0 0 1 1.42 1.4l-5.66 5.75a1.14 1.14 0 0 1-.75.26z" fill="#2088ff"></path><path d="M34.27 36.4H23.92a1 1 0 1 1 0-2h10.36a1 1 0 1 1-.01 2zM34.27 42.02H23.92a1 1 0 1 1 0-2h10.36a1 1 0 1 1-.01 2zM43.4 26.83H1.48a1 1 0 0 1 0-2H43.4a1 1 0 0 1 0 2z" fill="#79b8ff"></path></svg>

    <h6 class="alt-h4 text-normal text-gray text-center">
      Security and administration
    </h6>
    <h2 class="alt-h1 mt-3 mb-2 text-center">
      Boxes? Check.
    </h2>
    <p class="lead text-center mb-2 pb-md-4 col-md-8 mx-auto">
      We worried about your administrative and security needs so you don’t have to. From flexible hosting to authentication options, GitHub can help you meet your team’s requirements.
    </p>

    <p class="text-center mb-5">
      <a href="/business" class="btn btn-large btn-outline mx-auto">
        Learn about GitHub for Business
      </a>
    </p>

    <div class="d-md-flex flex-items-center flex-row-reverse my-5">
      <div class="col-sm-8 col-md-6 mx-auto px-5 pr-md-0 text-center">
        <img src="https://assets-cdn.github.com/images/modules/site/home-illo-business.svg" alt="" class="d-block width-fit mx-auto mb-4">
      </div>
      <div class="col-sm-8 col-md-6 mx-auto text-center text-md-left">
        <h3 class="alt-h3 mb-1">Code security</h3>
        <p class="mb-3 mb-md-5">
          Prevent problems before they happen. Protected branches, signed commits, and required status checks protect your work and help you maintain a high standard for your code.
        </p>

        <h3 class="alt-h3 mb-1">Access controlled</h3>
        <p class="mb-3 mb-md-5">
          Encourage teams to work together while limiting access to those who need it with granular permissions and authentication through SAML/SSO and LDAP.
        </p>

        <h3 class="alt-h3 mb-1">Hosted where you need it</h3>
        <p class="mb-3 mb-md-4">
          Securely and reliably host your work on GitHub.com. Or, deploy GitHub Enterprise on your own servers or in a private cloud using Amazon Web Services, Azure or Google Cloud Platform.
        </p>
      </div>
    </div>
  </div>
</div>

<div class="featurette">
  <div class="container-lg p-responsive text-center py-md-6">
    <div class="col-md-8 py-md-6 mx-auto">
      <svg xmlns="http://www.w3.org/2000/svg" data-name="Layer 1" viewBox="0 0 58.5 58.7" class="d-block mx-auto mb-2" width="72"><title>integrations</title><path d="M41.6 15.6l-1.4-1.4a1 1 0 1 0-1.4 1.4l1.4 1.4a1 1 0 0 0 1.4 0 1 1 0 0 0 0-1.4zM33.9 7.9a1 1 0 1 0-1.4 1.4l1.4 1.4a1 1 0 0 0 1.4 0 1 1 0 0 0 0-1.4zM27.9 26.6a1 1 0 0 0-1.4 1.4l1.4 1.4a1 1 0 0 0 1.4 0 1 1 0 0 0 0-1.4zM21.6 20.2a1 1 0 0 0-1.4 1.4l1.4 1.4a1 1 0 0 0 1.4 0 1 1 0 0 0 0-1.4zM15.4 38.7a1 1 0 0 0-1.4 1.4l1.4 1.4a1 1 0 0 0 1.4 0 1 1 0 0 0 0-1.4zM9.3 32.7a1 1 0 1 0-1.4 1.4l1.4 1.4a1 1 0 0 0 1.4 0 1 1 0 0 0 0-1.4z" fill="#6bbcff"></path><path d="M26.6 13.4V1a.94.94 0 0 0-1-1H1a.94.94 0 0 0-1 1v24.8a.94.94 0 0 0 1 1h12.4a.94.94 0 0 0 1-1V14.4h11.2a1.08 1.08 0 0 0 1-1zm-2-1H13.4a.94.94 0 0 0-1 1v11.4H2V2h22.6v10.4zM58.2 19.9a.91.91 0 0 0-.7-.3H45.1a.94.94 0 0 0-1 1v11.3H33.9a1.9 1.9 0 0 0-1.9 1.9v10.6H21.5a1.9 1.9 0 0 0-1.9 1.9v10.5a1.9 1.9 0 0 0 1.9 1.9h36a.94.94 0 0 0 1-1V20.6a.91.91 0 0 0-.3-.7zm-1.7 1.7v22.8H46.1V21.7zM44.1 34v21.1L33.9 44.9 33.8 34h10.3zM21.5 46.4h11l10.4 10.4H21.5V46.4zm24.6 10.3V46.4h10.4v10.4z" fill="#008fff"></path></svg>

      <h6 class="alt-h4 text-normal text-gray">
        Integrations
      </h6>
      <h2 class="alt-h1 lh-condensed mt-3 mb-2">
        Build on GitHub
      </h2>
      <p class="lead mb-2 pb-md-4 px-md-3">
        Customize your process with GitHub apps and an intuitive API. Integrate the tools you already use or discover new favorites to create a happier, more efficient way of working.
      </p>
      <p class="f4 text-center mb-6">
        <a href="/features/integrations" class="btn btn-large btn-outline mx-auto">Learn about integrations</a>
      </p>
    </div>

    <div class="apps-cluster d-flex flex-wrap flex-justify-center pb-6">
      <div class="CircleBadge CircleBadge--medium CircleBadge--feature tooltipped tooltipped-s tooltipped-no-delay" style="background-color: #553958;" aria-label="Slack"><img src="https://assets-cdn.github.com/images/modules/site/integrators/slackhq.png" alt="" class="CircleBadge-icon"></div>
      <div class="CircleBadge CircleBadge--medium CircleBadge--feature tooltipped tooltipped-s tooltipped-no-delay" style="background-color: #364e98;" aria-label="ZenHub"><img src="https://assets-cdn.github.com/images/modules/site/integrators/zenhubio.png" alt="" class="CircleBadge-icon"></div>
      <div class="CircleBadge CircleBadge--medium CircleBadge--feature tooltipped tooltipped-s tooltipped-no-delay" style="background-color: #eff9f9;" aria-label="Travis CI"><img src="https://assets-cdn.github.com/images/modules/site/integrators/travis-ci.png" alt="" class="CircleBadge-icon"></div>
      <div class="CircleBadge CircleBadge--medium CircleBadge--feature tooltipped tooltipped-s tooltipped-no-delay" style="background-color: #5fb57d;" aria-label="Atom"><img src="https://assets-cdn.github.com/images/modules/site/integrators/atom.png" alt="" class="CircleBadge-icon"></div>
      <div class="CircleBadge CircleBadge--medium CircleBadge--feature tooltipped tooltipped-s tooltipped-no-delay" style="background-color: #022531;" aria-label="Circle CI"><img src="https://assets-cdn.github.com/images/modules/site/integrators/circleci.png" alt="" class="CircleBadge-icon"></div>
      <div class="CircleBadge CircleBadge--medium CircleBadge--feature tooltipped tooltipped-s tooltipped-no-delay" style="background-color: #f3f6fb;" aria-label="Codeship"><img src="https://assets-cdn.github.com/images/modules/site/integrators/codeship.png" alt="" class="CircleBadge-icon"></div>
      <div class="CircleBadge CircleBadge--medium CircleBadge--feature hide-sm tooltipped tooltipped-s tooltipped-no-delay" style="background-color: #303030;" aria-label="Code Climate"><img src="https://assets-cdn.github.com/images/modules/site/integrators/codeclimate.png" alt="" class="CircleBadge-icon"></div>
    </div>

    <div class="col-md-8 py-md-6 mx-auto">
      <p class="my-2 alt-text-small col-sm-8 col-md-6 mx-auto">
        Sometimes, there’s more than one tool for the job. Why not try something new?
      </p>
      <p>
        <a href="/marketplace">Browse GitHub <span class="no-wrap">Marketplace<svg aria-hidden="true" class="octicon octicon-chevron-right ml-2 v-align-text-bottom" height="16" version="1.1" viewBox="0 0 8 16" width="8"><path fill-rule="evenodd" d="M7.5 8l-5 5L1 11.5 4.75 8 1 4.5 2.5 3z"/></svg></span></a>
      </p>
    </div>
  </div>
</div>

<div class="featurette overflow-hidden">
  <div class="container-lg p-responsive position-relative">
    <svg xmlns="http://www.w3.org/2000/svg" data-name="Layer 1" viewBox="0 0 69.41 57.98" class="d-block mx-auto mb-2" width="72"><title>open-source</title><path d="M25.21 56.35a1 1 0 0 1-.93-1.33 3.51 3.51 0 0 0 .22-1.26 4.52 4.52 0 0 0-4.09-4.48 1 1 0 0 1-.9-1v-4.1a5.78 5.78 0 0 0-.51-2.53 1.002 1.002 0 0 1 1.81-.86 7.76 7.76 0 0 1 .74 3.35v3.29a6.5 6.5 0 0 1 5 6.31 5.46 5.46 0 0 1-.36 2 1 1 0 0 1-.98.61zM49.35 6.26a1 1 0 0 1-.53-.12 26.91 26.91 0 0 0-22.43-2.86 1.001 1.001 0 0 1-.6-1.91 28.92 28.92 0 0 1 24.09 3 1 1 0 0 1-.53 1.89z" fill="#79b8ff"></path><path d="M25.21 56.35a1 1 0 0 1-.34-.06 29.61 29.61 0 0 1-11.11-7.15 1 1 0 1 1 1.44-1.39 27.59 27.59 0 0 0 10.35 6.69 1 1 0 0 1-.34 1.91zM6.7 27.48h-.09a1 1 0 0 1-.9-1.09 28.62 28.62 0 0 1 .76-4.42 1 1 0 0 1 1.94.49 26.65 26.65 0 0 0-.71 4.11 1 1 0 0 1-1 .91zM49.59 53.56a1 1 0 0 1-.59-1.84 26.93 26.93 0 0 0 11.81-16.7 1.024 1.024 0 0 1 2 .44 29 29 0 0 1-12.7 17.91 1 1 0 0 1-.52.19zM62.45 28.89a1 1 0 0 1-1-1 26.9 26.9 0 0 0-.78-5.47 1 1 0 1 1 1.94-.49 28.88 28.88 0 0 1 .84 5.88 1 1 0 0 1-1 1v.08z" fill="#79b8ff"></path><path d="M61.78 36.28h-.19a1 1 0 0 1-.79-1.14 32 32 0 0 0 .66-6v-1.2a1 1 0 1 1 2 0v1.08a34 34 0 0 1-.69 6.43 1 1 0 0 1-.99.83zM34.52 58.02a28.67 28.67 0 0 1-9.74-1.69 1 1 0 0 1 .55-1.92h.12a26.93 26.93 0 0 0 23.6-2.68 1 1 0 1 1 1.06 1.67 28.75 28.75 0 0 1-15.59 4.62zM19 29.65a1 1 0 0 1-.8-1.63 8 8 0 0 0 1.91-5.21 1 1 0 0 1 2 0 10.09 10.09 0 0 1-2.36 6.49 1 1 0 0 1-.75.35z" fill="#79b8ff"></path><path d="M62.45 28.89h-8a8.27 8.27 0 0 1-4.54-1.34h-5.6a4.36 4.36 0 0 1 0-8.72h2a8.25 8.25 0 0 1 1.8-3.69 1 1 0 1 1 1.53 1.29 6.22 6.22 0 0 0-1.46 3.48 1 1 0 0 1-1 .91h-2.87a2.36 2.36 0 0 0 0 4.72h6a1 1 0 0 1 .6.2 6.14 6.14 0 0 0 3.62 1.14h8a1.006 1.006 0 0 1-.08 2.01zM49.59 53.56a1 1 0 0 1-.74-.32 7.79 7.79 0 0 1-2.09-5.29v-.93h-.43a8 8 0 0 1 0-16h9.5a8 8 0 0 1 6.8 3.83 1 1 0 0 1-1.7 1 6 6 0 0 0-5.1-2.83h-9.5a6 6 0 0 0 0 12h1.44a1 1 0 0 1 1 1v1.92a5.79 5.79 0 0 0 1.56 3.93 1 1 0 0 1-.74 1.69z" fill="#79b8ff"></path><path d="M14.69 45.59a7.25 7.25 0 0 1-6.58-3.67H2.74A2.82 2.82 0 0 1 0 39.09v-6.53a2.57 2.57 0 0 1 .68-1.93 2.76 2.76 0 0 1 2.05-.9h11.53A2.75 2.75 0 0 1 17 32.5v6.58a2.82 2.82 0 0 1-2.73 2.83h-.55c.43 1.57 1.32 1.62 1.75 1.64a1 1 0 0 1 0 2 6.35 6.35 0 0 1-.78.04zM2.74 31.74a.75.75 0 0 0-.57.24.63.63 0 0 0-.16.49v6.63a.82.82 0 0 0 .73.83h6a1 1 0 0 1 .92.61A4.7 4.7 0 0 0 12 43.02a7.7 7.7 0 0 1-.44-2 1 1 0 0 1 .91-1.09h1.82a.82.82 0 0 0 .71-.82v-6.55a.75.75 0 0 0-.68-.82H2.74zM54.75 21.62H54a1 1 0 0 1 0-2c.38 0 1.28-.13 1.71-1.75h-.6a2.73 2.73 0 0 1-2.68-2.73V8.69a2.77 2.77 0 0 1 2.68-2.8h11.38a3 3 0 0 1 2.92 2.71v6.54a2.73 2.73 0 0 1-2.73 2.73h-5.23a7.42 7.42 0 0 1-6.7 3.75zm.36-13.73a.79.79 0 0 0-.73.81v6.44a.72.72 0 0 0 .71.73h1.75a1 1 0 0 1 1 1v.09a7.76 7.76 0 0 1-.47 2.12 4.87 4.87 0 0 0 2.49-2.6 1 1 0 0 1 .92-.61h5.86a.72.72 0 0 0 .76-.68v-6.5a1 1 0 0 0-.92-.81H55.11zM18 9.61a1.52 1.52 0 0 0-1.5-1.54 1.48 1.48 0 0 0-1.44 1c0 .1-.1.1-.19 0a1.48 1.48 0 0 0-1.44-1 1.52 1.52 0 0 0-1.54 1.5c0 1.63 1.73 3.07 2.59 3.74a.72.72 0 0 0 .86 0c.89-.54 2.66-2.07 2.66-3.7z" fill="#2088ff"></path><path d="M63.11 12.88h-4.47a1 1 0 0 1 0-2h4.47a1 1 0 1 1 0 2zM10.71 36.73H5.8a1 1 0 0 1 0-2h4.91a1 1 0 0 1 0 2zM14.79 22.27a1 1 0 0 1-.9-.64l-1.52-3.89H9.32a2.81 2.81 0 0 1-2.73-2.81v-9a2.73 2.73 0 0 1 2.67-2.79h11.39a2.73 2.73 0 0 1 2.73 2.73v9a2.81 2.81 0 0 1-2.73 2.81h-3.11l-1.84 4a1 1 0 0 1-.91.59zM9.32 5.14a.72.72 0 0 0-.73.71v9a.79.79 0 0 0 .73.81h3.79a1 1 0 0 1 .93.64l.89 2.32L16 16.25a1 1 0 0 1 1-.58h3.74a.79.79 0 0 0 .73-.81v-9a.72.72 0 0 0-.72-.72H9.32z" fill="#2088ff"></path></svg>

    <h6 class="alt-h4 text-normal text-gray text-center">
      Community
    </h6>
    <h2 class="alt-h1 mt-3 mb-2 lh-condensed text-center">
      Welcome home, developers
    </h2>
    <p class="lead text-center col-md-8 mx-auto pb-md-6">
      GitHub is home to the world’s largest community of developers and their projects. Whether you’re making your first commit or sending a Rover to Mars, there’s room for you here, too.
    </p>

    <div class="d-flex flex-wrap gutter-md mt-6 py-6">
      <a href="/personal" class="p-4 flex-md-item-equal mx-auto mx-md-3 mb-4 no-underline bg-white border box-shadow rounded-1 home-community-developers">
        <p class="mt-1 mb-1 text-gray-dark">
          <span class="alt-h2 text-bold d-block lh-condensed-ultra">22M</span>
          <span class="f3">Developers worldwide</span>
        </p>
        <p class="f5 text-gray-dark">
          Developers use GitHub for personal projects, from experimenting with new programming languages to hosting their life’s work.
        </p>
        <p class="text-blue f5 text-bold mb-0">See how developers use <span class="no-wrap">GitHub<svg aria-hidden="true" class="octicon octicon-chevron-right ml-2 v-align-text-bottom" height="16" version="1.1" viewBox="0 0 8 16" width="8"><path fill-rule="evenodd" d="M7.5 8l-5 5L1 11.5 4.75 8 1 4.5 2.5 3z"/></svg></span></p>
      </a>

      <a href="/open-source" class="p-4 flex-md-item-equal mx-auto mx-md-3 mb-4 no-underline bg-white border box-shadow rounded-1 home-community-repositories">
        <p class="mt-1 mb-1 text-gray-dark">
          <span class="alt-h2 text-bold d-block lh-condensed-ultra">61M</span>
          <span class="f3">Repositories worldwide</span>
        </p>
        <p class="f5 text-gray-dark">
          GitHub’s users create and maintain influential technologies alongside the world's largest open source community.
        </p>
        <p class="text-orange-light f5 text-bold mb-0">Learn about open <span class="no-wrap">source<svg aria-hidden="true" class="octicon octicon-chevron-right ml-2 v-align-text-bottom" height="16" version="1.1" viewBox="0 0 8 16" width="8"><path fill-rule="evenodd" d="M7.5 8l-5 5L1 11.5 4.75 8 1 4.5 2.5 3z"/></svg></span></p>
      </a>

      <a href="/business" class="p-4 flex-md-item-equal mx-auto mx-md-3 mb-4 no-underline bg-white border box-shadow rounded-1 home-community-teams">
        <p class="mt-1 mb-1 text-gray-dark">
          <span class="alt-h2 text-bold d-block lh-condensed-ultra">117K</span>
          <span class="f3">Businesses worldwide</span>
        </p>
        <p class="f5 text-gray-dark">
          Businesses of all sizes use GitHub to support their development process and to securely build software.
        </p>
        <p class="text-purple f5 text-bold">See how businesses use <span class="no-wrap">GitHub<svg aria-hidden="true" class="octicon octicon-chevron-right ml-2 v-align-text-bottom" height="16" version="1.1" viewBox="0 0 8 16" width="8"><path fill-rule="evenodd" d="M7.5 8l-5 5L1 11.5 4.75 8 1 4.5 2.5 3z"/></svg></span></p>
      </a>

      <div class="mt-5 col-10 col-md-12 flex-shrink-0 mx-auto home-community-svg">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1055.96 472.75">
  <defs>
    <style>
    .cls-1{isolation:isolate;}
    .cls-2{opacity:0.1;}
    .cls-3,.cls-4,.community-svg-orange,.community-svg-purple,.community-svg-blue{fill:none;stroke-linecap:round;stroke-miterlimit:10;stroke-width:4.45px;}
    .cls-3{stroke:#929497;}
    .cls-4{stroke:#6e7074;}
    .community-svg-orange{stroke:#f66a0a;}
    .community-svg-orange,.community-svg-purple,.community-svg-blue{mix-blend-mode:multiply;}
    .community-svg-purple{stroke:#6f42c1;}
    .community-svg-blue{stroke:#006eeb;}
    </style>
  </defs>

    <title>home-illo-community</title>
    <g class="cls-1">
    <g id="Layer_1" data-name="Layer 1">
    <g class="cls-2">
    <line class="cls-3" x1="382.18" y1="2.22" x2="417.53" y2="2.22"></line>
    <line class="cls-3" x1="249.64" y1="11.06" x2="284.99" y2="11.06"></line>
    <line class="cls-3" x1="399.86" y1="11.06" x2="435.2" y2="11.06"></line>
    <line class="cls-3" x1="293.82" y1="11.06" x2="311.49" y2="11.06"></line><line class="cls-3" x1="346.84" y1="11.06" x2="391.02" y2="11.06"></line><line class="cls-3" x1="223.13" y1="19.89" x2="461.71" y2="19.89"></line><line class="cls-3" x1="620.76" y1="19.89" x2="629.6" y2="19.89"></line><line class="cls-3" x1="664.94" y1="19.89" x2="673.78" y2="19.89"></line><line class="cls-3" x1="779.81" y1="19.89" x2="779.81" y2="19.89"></line><line class="cls-3" x1="302.66" y1="28.73" x2="444.04" y2="28.73"></line><line class="cls-3" x1="214.29" y1="28.73" x2="284.99" y2="28.73"></line><line class="cls-3" x1="223.13" y1="37.57" x2="267.31" y2="37.57"></line><line class="cls-3" x1="187.79" y1="37.57" x2="205.46" y2="37.57"></line><line class="cls-3" x1="240.8" y1="46.4" x2="258.48" y2="46.4"></line><line class="cls-3" x1="125.93" y1="81.75" x2="187.79" y2="81.75"></line><line class="cls-3" x1="152.44" y1="90.56" x2="223.13" y2="90.56"></line><line class="cls-3" x1="178.95" y1="99.4" x2="249.64" y2="99.4"></line><line class="cls-3" x1="205.46" y1="81.75" x2="214.29" y2="81.75"></line><line class="cls-3" x1="267.31" y1="125.93" x2="276.15" y2="125.93"></line><line class="cls-3" x1="293.82" y1="125.93" x2="302.66" y2="125.93"></line><line class="cls-3" x1="28.73" y1="81.75" x2="37.57" y2="81.75"></line><line class="cls-3" x1="19.9" y1="90.59" x2="81.75" y2="90.59"></line><line class="cls-3" x1="2.22" y1="99.42" x2="152.44" y2="99.42"></line><line class="cls-3" x1="2.22" y1="108.26" x2="249.64" y2="108.26"></line><line class="cls-3" x1="2.22" y1="117.09" x2="249.64" y2="117.09"></line><line class="cls-3" x1="11.06" y1="125.93" x2="223.13" y2="125.93"></line><line class="cls-3" x1="11.06" y1="134.73" x2="214.29" y2="134.73"></line><line class="cls-3" x1="231.97" y1="81.75" x2="284.99" y2="81.75"></line><line class="cls-3" x1="240.79" y1="90.57" x2="293.81" y2="90.57"></line><line class="cls-3" x1="284.99" y1="99.42" x2="302.66" y2="99.42"></line><line class="cls-3" x1="284.99" y1="108.26" x2="311.49" y2="108.26"></line><line class="cls-3" x1="267.31" y1="117.09" x2="302.66" y2="117.09"></line><line class="cls-3" x1="231.97" y1="64.08" x2="258.48" y2="64.08"></line><line class="cls-3" x1="125.93" y1="72.91" x2="152.44" y2="72.91"></line><line class="cls-3" x1="108.26" y1="90.59" x2="134.77" y2="90.59"></line><line class="cls-3" x1="178.95" y1="72.91" x2="258.48" y2="72.91"></line><line class="cls-3" x1="223.13" y1="55.23" x2="231.97" y2="55.23"></line><line class="cls-3" x1="143.61" y1="46.4" x2="170.11" y2="46.4"></line><line class="cls-3" x1="134.77" y1="55.23" x2="205.46" y2="55.23"></line><line class="cls-3" x1="196.62" y1="28.73" x2="196.62" y2="28.73"></line><line class="cls-3" x1="170.11" y1="37.57" x2="170.11" y2="37.57"></line><line class="cls-3" x1="214.29" y1="46.4" x2="214.29" y2="46.4"></line><line class="cls-3" x1="161.28" y1="64.05" x2="161.28" y2="64.05"></line><line class="cls-3" x1="267.3" y1="99.4" x2="267.3" y2="99.4"></line><line class="cls-3" x1="249.64" y1="125.93" x2="249.64" y2="125.93"></line><line class="cls-3" x1="187.79" y1="46.39" x2="187.79" y2="46.39"></line><line class="cls-3" x1="134.77" y1="64.08" x2="134.77" y2="64.08"></line><line class="cls-3" x1="284.99" y1="37.56" x2="435.2" y2="37.56"></line><line class="cls-3" x1="284.99" y1="46.39" x2="435.2" y2="46.39"></line><line class="cls-3" x1="550.07" y1="28.73" x2="576.58" y2="28.73"></line><line class="cls-3" x1="656.11" y1="28.73" x2="691.45" y2="28.73"></line><line class="cls-3" x1="770.98" y1="28.73" x2="788.65" y2="28.73"></line><line class="cls-3" x1="629.6" y1="28.73" x2="638.44" y2="28.73"></line><line class="cls-3" x1="532.4" y1="37.56" x2="558.91" y2="37.56"></line><line class="cls-3" x1="779.81" y1="37.56" x2="806.32" y2="37.56"></line><line class="cls-3" x1="541.24" y1="46.39" x2="550.07" y2="46.39"></line><line class="cls-3" x1="797.49" y1="46.39" x2="806.33" y2="46.39"></line><line class="cls-3" x1="567.75" y1="46.39" x2="567.75" y2="46.39"></line><line class="cls-3" x1="293.82" y1="55.23" x2="435.2" y2="55.23"></line><line class="cls-3" x1="329.17" y1="64.06" x2="435.2" y2="64.06"></line><line class="cls-3" x1="338" y1="72.9" x2="426.37" y2="72.9"></line><line class="cls-3" x1="338" y1="81.73" x2="426.37" y2="81.73"></line><line class="cls-3" x1="338" y1="90.56" x2="426.36" y2="90.56"></line><line class="cls-3" x1="770.98" y1="55.23" x2="832.83" y2="55.23"></line><line class="cls-3" x1="673.78" y1="55.23" x2="700.29" y2="55.23"></line><line class="cls-3" x1="753.31" y1="64.06" x2="832.83" y2="64.06"></line><line class="cls-3" x1="664.94" y1="64.06" x2="673.78" y2="64.06"></line><line class="cls-3" x1="700.29" y1="72.9" x2="877.01" y2="72.9"></line><line class="cls-3" x1="656.11" y1="72.9" x2="664.94" y2="72.9"></line><line class="cls-3" x1="903.52" y1="55.23" x2="921.19" y2="55.23"></line><line class="cls-3" x1="903.52" y1="64.06" x2="938.87" y2="64.06"></line><line class="cls-3" x1="912.36" y1="72.9" x2="921.19" y2="72.9"></line><line class="cls-3" x1="691.45" y1="81.73" x2="947.7" y2="81.73"></line><line class="cls-3" x1="576.58" y1="81.73" x2="585.42" y2="81.73"></line><line class="cls-3" x1="647.27" y1="81.73" x2="664.94" y2="81.73"></line><line class="cls-3" x1="1027.23" y1="81.73" x2="1036.07" y2="81.73"></line><line class="cls-3" x1="1044.9" y1="117.09" x2="1044.9" y2="117.09"></line><line class="cls-3" x1="673.78" y1="90.56" x2="1018.39" y2="90.56"></line><line class="cls-3" x1="541.24" y1="99.4" x2="1036.07" y2="99.4"></line><line class="cls-3" x1="532.4" y1="108.23" x2="1053.74" y2="108.23"></line><line class="cls-3" x1="523.56" y1="117.07" x2="1027.23" y2="117.07"></line><line class="cls-3" x1="558.91" y1="125.9" x2="1027.23" y2="125.9"></line><line class="cls-3" x1="514.73" y1="125.9" x2="541.24" y2="125.9"></line><line class="cls-3" x1="514.73" y1="134.73" x2="550.07" y2="134.73"></line><line class="cls-3" x1="488.22" y1="134.73" x2="497.06" y2="134.73"></line><line class="cls-3" x1="514.73" y1="143.57" x2="541.24" y2="143.57"></line><line class="cls-3" x1="479.38" y1="143.57" x2="488.22" y2="143.57"></line><line class="cls-3" x1="541.24" y1="152.4" x2="541.24" y2="152.4"></line><line class="cls-3" x1="523.56" y1="152.4" x2="523.56" y2="152.4"></line><line class="cls-3" x1="470.55" y1="152.44" x2="488.22" y2="152.44"></line><line class="cls-3" x1="974.22" y1="134.73" x2="1000.72" y2="134.73"></line><line class="cls-3" x1="567.74" y1="134.73" x2="956.53" y2="134.73"></line><line class="cls-3" x1="550.07" y1="90.56" x2="585.42" y2="90.56"></line><line class="cls-3" x1="638.43" y1="90.56" x2="638.43" y2="90.56"></line><line class="cls-3" x1="338" y1="99.4" x2="408.69" y2="99.4"></line><line class="cls-3" x1="338" y1="108.23" x2="391.02" y2="108.23"></line><line class="cls-3" x1="426.37" y1="108.23" x2="444.04" y2="108.23"></line><line class="cls-3" x1="347.06" y1="117.07" x2="373.35" y2="117.07"></line><line class="cls-3" x1="426.37" y1="117.07" x2="435.2" y2="117.07"></line><line class="cls-3" x1="346.84" y1="125.9" x2="373.35" y2="125.9"></line><line class="cls-3" x1="470.55" y1="125.9" x2="470.55" y2="125.9"></line><line class="cls-3" x1="355.68" y1="134.73" x2="364.51" y2="134.73"></line><line class="cls-3" x1="267.31" y1="134.73" x2="284.98" y2="134.73"></line><line class="cls-3" x1="90.59" y1="143.6" x2="223.13" y2="143.6"></line><line class="cls-3" x1="19.9" y1="143.6" x2="46.41" y2="143.6"></line><line class="cls-3" x1="267.31" y1="143.6" x2="302.66" y2="143.6"></line><line class="cls-3" x1="99.42" y1="152.47" x2="231.97" y2="152.47"></line><line class="cls-3" x1="19.9" y1="152.47" x2="37.57" y2="152.47"></line><line class="cls-3" x1="276.62" y1="152.47" x2="311.49" y2="152.47"></line><line class="cls-3" x1="99.42" y1="161.34" x2="249.64" y2="161.34"></line><line class="cls-3" x1="267.31" y1="161.34" x2="320.33" y2="161.34"></line><line class="cls-3" x1="2.22" y1="161.34" x2="19.9" y2="161.34"></line><line class="cls-3" x1="2.22" y1="170.11" x2="2.22" y2="170.11"></line><line class="cls-3" x1="117.1" y1="170.21" x2="249.64" y2="170.21"></line><line class="cls-3" x1="117.1" y1="178.95" x2="294.05" y2="178.95"></line><line class="cls-3" x1="267.31" y1="170.21" x2="329.16" y2="170.21"></line><line class="cls-3" x1="329.16" y1="178.95" x2="329.16" y2="178.95"></line><line class="cls-3" x1="134.77" y1="187.69" x2="302.66" y2="187.69"></line><line class="cls-3" x1="134.77" y1="196.62" x2="311.49" y2="196.62"></line><line class="cls-3" x1="134.77" y1="205.45" x2="284.98" y2="205.45"></line><line class="cls-3" x1="134.77" y1="214.28" x2="276.15" y2="214.28"></line><line class="cls-3" x1="134.77" y1="223.12" x2="267.31" y2="223.12"></line><line class="cls-3" x1="143.61" y1="231.95" x2="267.31" y2="231.95"></line><line class="cls-3" x1="152.44" y1="240.78" x2="258.48" y2="240.78"></line><line class="cls-3" x1="161.28" y1="249.61" x2="258.48" y2="249.61"></line><line class="cls-3" x1="161.28" y1="258.44" x2="205.57" y2="258.44"></line><line class="cls-3" x1="258.48" y1="258.44" x2="258.48" y2="258.44"></line><line class="cls-3" x1="170.11" y1="267.28" x2="205.46" y2="267.28"></line><line class="cls-3" x1="187.79" y1="276.11" x2="205.57" y2="276.11"></line><line class="cls-3" x1="231.91" y1="276.11" x2="240.81" y2="276.11"></line><line class="cls-3" x1="258.48" y1="276.11" x2="284.98" y2="276.11"></line><line class="cls-3" x1="187.79" y1="284.98" x2="231.97" y2="284.98"></line><line class="cls-3" x1="205.53" y1="293.82" x2="249.64" y2="293.82"></line><line class="cls-3" x1="231.82" y1="302.66" x2="249.61" y2="302.66"></line><line class="cls-3" x1="284.98" y1="302.66" x2="284.98" y2="302.66"></line><line class="cls-3" x1="240.81" y1="311.49" x2="311.49" y2="311.49"></line><line class="cls-3" x1="258.48" y1="320.33" x2="320.33" y2="320.33"></line><line class="cls-3" x1="267.31" y1="329.08" x2="346.84" y2="329.08"></line><line class="cls-3" x1="258.48" y1="337.92" x2="346.84" y2="337.92"></line><line class="cls-3" x1="258.48" y1="346.76" x2="364.51" y2="346.76"></line><line class="cls-3" x1="258.48" y1="355.6" x2="391.02" y2="355.6"></line><line class="cls-3" x1="267.31" y1="364.44" x2="391.02" y2="364.44"></line><line class="cls-3" x1="267.31" y1="373.28" x2="381.95" y2="373.28"></line><line class="cls-3" x1="276.15" y1="382.12" x2="381.95" y2="382.12"></line><line class="cls-3" x1="284.98" y1="390.96" x2="381.95" y2="390.96"></line><line class="cls-3" x1="293.82" y1="399.8" x2="373.35" y2="399.8"></line><line class="cls-3" x1="293.82" y1="408.64" x2="373.35" y2="408.64"></line><line class="cls-3" x1="293.82" y1="417.48" x2="355.68" y2="417.48"></line><line class="cls-3" x1="284.98" y1="426.32" x2="346.84" y2="426.32"></line><line class="cls-3" x1="284.98" y1="435.16" x2="346.84" y2="435.16"></line><line class="cls-3" x1="284.98" y1="444" x2="338" y2="444"></line><line class="cls-3" x1="284.98" y1="452.84" x2="329.16" y2="452.84"></line><line class="cls-3" x1="284.98" y1="461.68" x2="320.33" y2="461.68"></line><line class="cls-3" x1="276.15" y1="470.52" x2="311.49" y2="470.52"></line><line class="cls-3" x1="267.31" y1="284.98" x2="302.66" y2="284.98"></line><line class="cls-3" x1="338" y1="187.69" x2="320.33" y2="187.69"></line><line class="cls-3" x1="567.75" y1="143.57" x2="912.36" y2="143.57"></line><line class="cls-3" x1="558.91" y1="152.4" x2="903.52" y2="152.4"></line><line class="cls-3" x1="523.43" y1="161.24" x2="912.36" y2="161.24"></line><line class="cls-3" x1="461.71" y1="161.24" x2="497.06" y2="161.24"></line><line class="cls-3" x1="479.38" y1="170.21" x2="488.22" y2="170.21"></line><line class="cls-3" x1="965.37" y1="143.57" x2="974.21" y2="143.57"></line><line class="cls-3" x1="965.38" y1="152.44" x2="974.21" y2="152.44"></line><line class="cls-3" x1="956.54" y1="161.24" x2="974.21" y2="161.24"></line><line class="cls-3" x1="965.37" y1="170.21" x2="965.37" y2="170.21"></line><line class="cls-3" x1="505.89" y1="170.07" x2="921.19" y2="170.07"></line><line class="cls-3" x1="497.06" y1="178.9" x2="921.19" y2="178.9"></line><line class="cls-3" x1="479.38" y1="187.74" x2="921.19" y2="187.74"></line><line class="cls-3" x1="497.06" y1="196.57" x2="921.19" y2="196.57"></line><line class="cls-3" x1="620.76" y1="205.41" x2="894.69" y2="205.41"></line><line class="cls-3" x1="470.55" y1="205.41" x2="532.4" y2="205.41"></line><line class="cls-3" x1="550.07" y1="205.41" x2="576.58" y2="205.41"></line><line class="cls-3" x1="558.91" y1="214.24" x2="877.01" y2="214.24"></line><line class="cls-3" x1="558.91" y1="223.07" x2="850.5" y2="223.07"></line><line class="cls-3" x1="470.54" y1="214.24" x2="497.06" y2="214.24"></line><line class="cls-3" x1="523.56" y1="214.24" x2="523.56" y2="214.24"></line><line class="cls-3" x1="541.24" y1="214.24" x2="541.24" y2="214.24"></line><line class="cls-3" x1="470.54" y1="223.07" x2="488.22" y2="223.07"></line><line class="cls-3" x1="532.4" y1="223.07" x2="541.24" y2="223.07"></line><line class="cls-3" x1="912.36" y1="205.41" x2="921.19" y2="205.41"></line><line class="cls-3" x1="912.36" y1="214.24" x2="912.36" y2="214.24"></line><line class="cls-3" x1="903.52" y1="223.07" x2="912.36" y2="223.07"></line><line class="cls-3" x1="868.18" y1="223.07" x2="877.01" y2="223.07"></line><line class="cls-3" x1="594.25" y1="231.91" x2="850.5" y2="231.91"></line><line class="cls-3" x1="479.38" y1="231.91" x2="523.56" y2="231.91"></line><line class="cls-3" x1="470.54" y1="240.8" x2="532.4" y2="240.8"></line><line class="cls-3" x1="558.91" y1="240.8" x2="567.74" y2="240.8"></line><line class="cls-3" x1="877.01" y1="231.91" x2="912.36" y2="231.91"></line><line class="cls-3" x1="885.85" y1="240.74" x2="885.85" y2="240.74"></line><line class="cls-3" x1="885.85" y1="249.58" x2="885.85" y2="249.58"></line><line class="cls-3" x1="877.01" y1="258.41" x2="877.01" y2="258.41"></line><line class="cls-3" x1="603.09" y1="240.74" x2="850.5" y2="240.74"></line><line class="cls-3" x1="470.54" y1="249.58" x2="850.5" y2="249.58"></line><line class="cls-3" x1="461.71" y1="258.41" x2="638.43" y2="258.41"></line><line class="cls-3" x1="656.11" y1="258.41" x2="850.5" y2="258.41"></line><line class="cls-3" x1="611.93" y1="267.24" x2="647.27" y2="267.24"></line><line class="cls-3" x1="452.87" y1="267.24" x2="594.26" y2="267.24"></line><line class="cls-3" x1="700.29" y1="267.24" x2="850.5" y2="267.24"></line><line class="cls-3" x1="700.29" y1="276.08" x2="824" y2="276.08"></line><line class="cls-3" x1="717.96" y1="284.91" x2="744.47" y2="284.91"></line><line class="cls-3" x1="779.81" y1="284.91" x2="806.32" y2="284.91"></line><line class="cls-3" x1="850.5" y1="284.91" x2="859.34" y2="284.91"></line><line class="cls-3" x1="824" y1="284.91" x2="824" y2="284.91"></line><line class="cls-3" x1="850.51" y1="293.75" x2="859.34" y2="293.75"></line><line class="cls-3" x1="788.66" y1="293.75" x2="815.15" y2="293.75"></line><line class="cls-3" x1="717.96" y1="293.75" x2="735.64" y2="293.75"></line><line class="cls-3" x1="850.51" y1="302.58" x2="868.18" y2="302.58"></line><line class="cls-3" x1="788.64" y1="302.58" x2="815.15" y2="302.58"></line><line class="cls-3" x1="717.89" y1="302.58" x2="735.63" y2="302.58"></line><line class="cls-3" x1="726.8" y1="311.41" x2="726.8" y2="311.41"></line><line class="cls-3" x1="788.66" y1="311.41" x2="788.66" y2="311.41"></line><line class="cls-3" x1="806.32" y1="311.41" x2="806.32" y2="311.41"></line><line class="cls-3" x1="868.18" y1="311.41" x2="859.34" y2="311.41"></line><line class="cls-3" x1="788.64" y1="320.25" x2="797.49" y2="320.25"></line><line class="cls-3" x1="735.64" y1="320.25" x2="735.64" y2="320.25"></line><line class="cls-3" x1="859.34" y1="320.25" x2="868.19" y2="320.25"></line><line class="cls-3" x1="841.68" y1="320.25" x2="841.68" y2="320.25"></line><line class="cls-3" x1="779.81" y1="329.08" x2="806.32" y2="329.08"></line><line class="cls-3" x1="832.83" y1="329.08" x2="841.67" y2="329.08"></line><line class="cls-3" x1="823.99" y1="337.92" x2="877.01" y2="337.92"></line><line class="cls-3" x1="788.64" y1="337.92" x2="806.34" y2="337.92"></line><line class="cls-3" x1="823.99" y1="346.75" x2="912.36" y2="346.75"></line><line class="cls-3" x1="894.68" y1="355.59" x2="947.7" y2="355.59"></line><line class="cls-3" x1="850.51" y1="355.59" x2="868.17" y2="355.59"></line><line class="cls-3" x1="806.32" y1="355.59" x2="815.16" y2="355.59"></line><line class="cls-3" x1="956.53" y1="364.42" x2="965.37" y2="364.42"></line><line class="cls-3" x1="885.85" y1="364.42" x2="930.03" y2="364.42"></line><line class="cls-3" x1="815.15" y1="364.42" x2="868.19" y2="364.42"></line><line class="cls-3" x1="850.5" y1="373.25" x2="859.34" y2="373.25"></line><line class="cls-3" x1="885.85" y1="373.25" x2="885.85" y2="373.25"></line><line class="cls-3" x1="938.87" y1="373.25" x2="938.87" y2="373.25"></line><line class="cls-3" x1="868.17" y1="382.09" x2="894.68" y2="382.09"></line><line class="cls-3" x1="921.19" y1="382.09" x2="921.19" y2="382.09"></line><line class="cls-3" x1="850.5" y1="390.92" x2="930.03" y2="390.92"></line><line class="cls-3" x1="850.5" y1="399.76" x2="930.03" y2="399.76"></line><line class="cls-3" x1="832.83" y1="408.59" x2="938.87" y2="408.59"></line><line class="cls-3" x1="983.05" y1="399.76" x2="991.89" y2="399.76"></line><line class="cls-3" x1="983.05" y1="408.59" x2="991.89" y2="408.59"></line><line class="cls-3" x1="832.83" y1="417.42" x2="947.7" y2="417.42"></line><line class="cls-3" x1="832.83" y1="426.26" x2="947.7" y2="426.26"></line><line class="cls-3" x1="841.68" y1="435.09" x2="947.7" y2="435.09"></line><line class="cls-3" x1="894.68" y1="443.93" x2="938.87" y2="443.93"></line><line class="cls-3" x1="841.68" y1="443.93" x2="859.33" y2="443.93"></line><line class="cls-3" x1="1009.56" y1="443.93" x2="1009.56" y2="443.93"></line><line class="cls-3" x1="912.36" y1="452.76" x2="938.87" y2="452.76"></line><line class="cls-3" x1="930.03" y1="461.59" x2="921.19" y2="461.59"></line><line class="cls-3" x1="1009.56" y1="452.76" x2="1018.39" y2="452.76"></line><line class="cls-3" x1="1027.23" y1="461.59" x2="1009.56" y2="461.59"></line><line class="cls-3" x1="1009.56" y1="470.43" x2="1018.39" y2="470.43"></line><line class="cls-3" x1="930.03" y1="470.43" x2="930.03" y2="470.43"></line><line class="cls-3" x1="797.49" y1="346.75" x2="806.34" y2="346.75"></line><line class="cls-3" x1="444.04" y1="276.08" x2="664.94" y2="276.08"></line><line class="cls-3" x1="620.77" y1="284.91" x2="656.11" y2="284.91"></line><line class="cls-3" x1="452.87" y1="284.91" x2="603.08" y2="284.91"></line><line class="cls-3" x1="629.6" y1="293.75" x2="647.27" y2="293.75"></line><line class="cls-3" x1="452.87" y1="293.75" x2="611.92" y2="293.75"></line><line class="cls-3" x1="629.6" y1="302.58" x2="452.87" y2="302.58"></line><line class="cls-3" x1="461.71" y1="311.41" x2="647.27" y2="311.41"></line><line class="cls-3" x1="461.71" y1="320.25" x2="647.27" y2="320.25"></line><line class="cls-3" x1="523.56" y1="329.08" x2="629.6" y2="329.08"></line><line class="cls-3" x1="470.54" y1="329.08" x2="479.38" y2="329.08"></line><line class="cls-3" x1="523.56" y1="337.92" x2="620.76" y2="337.92"></line><line class="cls-3" x1="611.92" y1="346.75" x2="523.56" y2="346.75"></line><line class="cls-3" x1="611.92" y1="355.59" x2="532.4" y2="355.59"></line><line class="cls-3" x1="611.92" y1="364.42" x2="541.24" y2="364.42"></line><line class="cls-3" x1="611.92" y1="373.25" x2="541.24" y2="373.25"></line><line class="cls-3" x1="611.92" y1="382.09" x2="532.4" y2="382.09"></line><line class="cls-3" x1="611.92" y1="390.92" x2="532.4" y2="390.92"></line><line class="cls-3" x1="603.09" y1="399.76" x2="541.24" y2="399.76"></line><line class="cls-3" x1="603.09" y1="408.59" x2="541.24" y2="408.59"></line><line class="cls-3" x1="603.09" y1="417.42" x2="541.24" y2="417.42"></line><line class="cls-3" x1="647.27" y1="382.09" x2="638.43" y2="382.09"></line><line class="cls-3" x1="629.6" y1="390.92" x2="638.43" y2="390.92"></line><line class="cls-3" x1="629.6" y1="399.76" x2="638.43" y2="399.76"></line><line class="cls-3" x1="629.6" y1="408.59" x2="638.43" y2="408.59"></line><line class="cls-3" x1="629.6" y1="417.42" x2="629.6" y2="417.42"></line><line class="cls-3" x1="585.42" y1="426.26" x2="550.07" y2="426.26"></line><line class="cls-3" x1="585.42" y1="435.09" x2="550.07" y2="435.09"></line><line class="cls-3" x1="576.58" y1="443.93" x2="550.07" y2="443.93"></line><line class="cls-4" x1="267.31" y1="19.89" x2="284.99" y2="19.89"></line><line class="cls-4" x1="322.82" y1="19.9" x2="364.51" y2="19.9"></line><line class="cls-4" x1="355.68" y1="28.73" x2="397.37" y2="28.73"></line><line class="cls-4" x1="417.53" y1="19.89" x2="417.53" y2="19.89"></line><line class="cls-4" x1="249.64" y1="28.73" x2="276.15" y2="28.73"></line><line class="cls-4" x1="426.37" y1="28.73" x2="444.04" y2="28.73"></line><line class="cls-4" x1="311.49" y1="37.57" x2="338" y2="37.57"></line><line class="cls-4" x1="373.35" y1="37.56" x2="426.36" y2="37.56"></line><line class="cls-4" x1="249.64" y1="37.57" x2="223.13" y2="37.57"></line><line class="cls-4" x1="170.11" y1="55.23" x2="187.79" y2="55.23"></line><line class="cls-4" x1="399.85" y1="46.39" x2="435.2" y2="46.39"></line><line class="cls-4" x1="329.16" y1="46.4" x2="355.68" y2="46.4"></line><line class="cls-4" x1="293.82" y1="55.23" x2="320.33" y2="55.23"></line><line class="cls-4" x1="373.35" y1="55.23" x2="408.69" y2="55.23"></line><line class="cls-4" x1="435.2" y1="64.06" x2="399.86" y2="64.06"></line><line class="cls-4" x1="347.06" y1="64.06" x2="355.68" y2="64.08"></line><line class="cls-4" x1="214.3" y1="72.91" x2="240.81" y2="72.91"></line><line class="cls-4" x1="143.61" y1="81.73" x2="178.95" y2="81.73"></line><line class="cls-4" x1="382.18" y1="72.91" x2="408.69" y2="72.91"></line><line class="cls-4" x1="338" y1="81.73" x2="364.51" y2="81.73"></line><line class="cls-4" x1="399.86" y1="81.75" x2="417.53" y2="81.75"></line><line class="cls-4" x1="355.68" y1="90.56" x2="391.02" y2="90.56"></line><line class="cls-4" x1="382.18" y1="99.4" x2="399.86" y2="99.4"></line><line class="cls-4" x1="19.9" y1="99.4" x2="55.24" y2="99.4"></line><line class="cls-4" x1="108.26" y1="99.4" x2="117.1" y2="99.4"></line><line class="cls-4" x1="11.06" y1="108.23" x2="72.92" y2="108.23"></line><line class="cls-4" x1="134.77" y1="108.23" x2="170.11" y2="108.23"></line><line class="cls-4" x1="231.91" y1="108.23" x2="249.64" y2="108.23"></line><line class="cls-4" x1="338" y1="108.23" x2="364.51" y2="108.23"></line><line class="cls-4" x1="46.41" y1="117.09" x2="99.42" y2="117.09"></line><line class="cls-4" x1="152.44" y1="117.07" x2="170.11" y2="117.07"></line><line class="cls-4" x1="11.06" y1="125.93" x2="64.08" y2="125.93"></line><line class="cls-4" x1="125.93" y1="125.9" x2="161.28" y2="125.9"></line><line class="cls-4" x1="46.41" y1="134.77" x2="72.92" y2="134.77"></line><line class="cls-4" x1="117.1" y1="134.73" x2="134.77" y2="134.73"></line><line class="cls-4" x1="214.29" y1="134.73" x2="170.11" y2="134.73"></line><line class="cls-4" x1="125.93" y1="143.6" x2="178.95" y2="143.6"></line><line class="cls-4" x1="99.42" y1="152.47" x2="134.77" y2="152.47"></line><line class="cls-4" x1="196.62" y1="152.47" x2="214.3" y2="152.47"></line><line class="cls-4" x1="117.1" y1="161.28" x2="161.28" y2="161.28"></line><line class="cls-4" x1="205.46" y1="161.28" x2="231.97" y2="161.28"></line><line class="cls-4" x1="134.77" y1="170.21" x2="178.95" y2="170.21"></line><line class="cls-4" x1="214.3" y1="170.11" x2="223.13" y2="170.11"></line><line class="cls-4" x1="117.1" y1="178.95" x2="143.61" y2="178.95"></line><line class="cls-4" x1="196.62" y1="178.95" x2="240.71" y2="178.95"></line><line class="cls-4" x1="294.05" y1="161.34" x2="311.49" y2="161.34"></line><line class="cls-4" x1="276.62" y1="178.95" x2="294.05" y2="178.95"></line><line class="cls-4" x1="143.61" y1="187.78" x2="170.11" y2="187.78"></line><line class="cls-4" x1="214.29" y1="187.69" x2="231.82" y2="187.69"></line><line class="cls-4" x1="258.48" y1="187.69" x2="285.33" y2="187.69"></line><line class="cls-4" x1="134.77" y1="196.62" x2="161.28" y2="196.62"></line><line class="cls-4" x1="187.79" y1="196.62" x2="223.06" y2="196.62"></line><line class="cls-4" x1="249.64" y1="196.62" x2="267.31" y2="196.62"></line><line class="cls-4" x1="311.49" y1="196.62" x2="285.33" y2="196.62"></line><line class="cls-4" x1="152.44" y1="205.45" x2="187.79" y2="205.45"></line><line class="cls-4" x1="214.3" y1="205.45" x2="240.71" y2="205.45"></line><line class="cls-4" x1="134.77" y1="214.28" x2="161.28" y2="214.28"></line><line class="cls-4" x1="205.46" y1="214.29" x2="231.97" y2="214.29"></line><line class="cls-4" x1="276.15" y1="214.28" x2="267.3" y2="214.28"></line><line class="cls-4" x1="146.1" y1="223.12" x2="170.12" y2="223.12"></line><line class="cls-4" x1="196.68" y1="223.13" x2="258.48" y2="223.13"></line><line class="cls-4" x1="143.61" y1="231.95" x2="178.95" y2="231.95"></line><line class="cls-4" x1="214.3" y1="231.95" x2="249.64" y2="231.95"></line><line class="cls-4" x1="170.11" y1="240.78" x2="187.79" y2="240.78"></line><line class="cls-4" x1="214.29" y1="249.61" x2="240.71" y2="249.61"></line><line class="cls-4" x1="187.79" y1="267.31" x2="205.46" y2="267.31"></line><line class="cls-4" x1="214.3" y1="284.91" x2="231.97" y2="284.91"></line><line class="cls-4" x1="276.15" y1="284.98" x2="267.31" y2="284.98"></line><line class="cls-4" x1="276.62" y1="311.41" x2="240.81" y2="311.41"></line><line class="cls-4" x1="294.05" y1="329.08" x2="329.16" y2="329.08"></line><line class="cls-4" x1="276.15" y1="337.92" x2="311.49" y2="337.92"></line><line class="cls-4" x1="302.66" y1="346.84" x2="346.84" y2="346.84"></line><line class="cls-4" x1="373.35" y1="355.67" x2="338" y2="355.67"></line><line class="cls-4" x1="284.98" y1="355.67" x2="258.48" y2="355.67"></line><line class="cls-4" x1="276.62" y1="364.44" x2="311.49" y2="364.44"></line><line class="cls-4" x1="391.02" y1="364.44" x2="364.51" y2="364.44"></line><line class="cls-4" x1="293.82" y1="373.28" x2="338" y2="373.28"></line><line class="cls-4" x1="276.15" y1="382.12" x2="311.61" y2="382.12"></line><line class="cls-4" x1="355.67" y1="382.18" x2="373.35" y2="382.18"></line><line class="cls-4" x1="329.05" y1="391.02" x2="381.95" y2="391.02"></line><line class="cls-4" x1="311.49" y1="399.85" x2="346.84" y2="399.85"></line><line class="cls-4" x1="302.66" y1="408.64" x2="329.16" y2="408.64"></line><line class="cls-4" x1="355.68" y1="417.48" x2="320.33" y2="417.48"></line><line class="cls-4" x1="284.98" y1="426.32" x2="311.49" y2="426.32"></line><line class="cls-4" x1="311.49" y1="444" x2="338" y2="444"></line><line class="cls-4" x1="806.34" y1="55.24" x2="832.83" y2="55.24"></line><line class="cls-4" x1="753.31" y1="64.06" x2="770.98" y2="64.06"></line><line class="cls-4" x1="726.76" y1="72.91" x2="762.14" y2="72.91"></line><line class="cls-4" x1="823.99" y1="72.91" x2="850.51" y2="72.91"></line><line class="cls-4" x1="709.13" y1="81.75" x2="744.47" y2="81.75"></line><line class="cls-4" x1="788.64" y1="81.73" x2="806.32" y2="81.73"></line><line class="cls-4" x1="877.01" y1="81.73" x2="921.19" y2="81.73"></line><line class="cls-4" x1="691.45" y1="90.59" x2="753.31" y2="90.59"></line><line class="cls-4" x1="815.15" y1="90.56" x2="850.5" y2="90.56"></line><line class="cls-4" x1="947.7" y1="90.59" x2="983.05" y2="90.59"></line><line class="cls-4" x1="1000.72" y1="99.4" x2="965.38" y2="99.4"></line><line class="cls-4" x1="541.24" y1="99.4" x2="620.76" y2="99.4"></line><line class="cls-4" x1="788.66" y1="99.4" x2="877.01" y2="99.4"></line><line class="cls-4" x1="567.74" y1="108.23" x2="629.6" y2="108.23"></line><line class="cls-4" x1="691.45" y1="108.26" x2="709.13" y2="108.26"></line><line class="cls-4" x1="806.34" y1="108.26" x2="815.16" y2="108.26"></line><line class="cls-4" x1="903.52" y1="108.23" x2="921.19" y2="108.23"></line><line class="cls-4" x1="859.35" y1="117.09" x2="912.36" y2="117.09"></line><line class="cls-4" x1="753.31" y1="117.09" x2="788.64" y2="117.09"></line><line class="cls-4" x1="611.92" y1="117.09" x2="700.29" y2="117.09"></line><line class="cls-4" x1="523.56" y1="117.07" x2="550.07" y2="117.07"></line><line class="cls-4" x1="1027.23" y1="117.07" x2="965.38" y2="117.07"></line><line class="cls-4" x1="585.42" y1="125.93" x2="629.6" y2="125.93"></line><line class="cls-4" x1="726.8" y1="125.9" x2="815.16" y2="125.9"></line><line class="cls-4" x1="885.85" y1="125.9" x2="921.19" y2="125.9"></line><line class="cls-4" x1="983.05" y1="125.9" x2="1000.72" y2="125.9"></line><line class="cls-4" x1="567.74" y1="134.73" x2="656.11" y2="134.73"></line><line class="cls-4" x1="717.89" y1="134.77" x2="726.76" y2="134.77"></line><line class="cls-4" x1="744.45" y1="134.77" x2="744.45" y2="134.77"></line><line class="cls-4" x1="673.78" y1="231.97" x2="673.78" y2="231.97"></line><line class="cls-4" x1="550.07" y1="276.15" x2="550.07" y2="276.15"></line><line class="cls-4" x1="505.89" y1="284.98" x2="505.89" y2="284.98"></line><line class="cls-4" x1="647.27" y1="240.8" x2="647.27" y2="240.8"></line><line class="cls-4" x1="735.64" y1="214.29" x2="735.64" y2="214.29"></line><line class="cls-4" x1="700.29" y1="170.07" x2="700.29" y2="170.07"></line><line class="cls-4" x1="859.34" y1="205.46" x2="859.34" y2="205.46"></line><line class="cls-4" x1="806.32" y1="258.47" x2="806.32" y2="258.47"></line><line class="cls-4" x1="735.64" y1="249.64" x2="735.64" y2="249.64"></line><line class="cls-4" x1="770.98" y1="90.56" x2="770.98" y2="90.56"></line><line class="cls-4" x1="717.89" y1="108.26" x2="717.89" y2="108.26"></line><line class="cls-4" x1="815.16" y1="72.91" x2="815.16" y2="72.91"></line><line class="cls-4" x1="143.61" y1="152.44" x2="143.61" y2="152.44"></line><line class="cls-4" x1="223.06" y1="108.23" x2="223.06" y2="108.23"></line><line class="cls-4" x1="187.79" y1="81.75" x2="187.79" y2="81.75"></line><line class="cls-4" x1="240.71" y1="187.78" x2="240.71" y2="187.78"></line><line class="cls-4" x1="205.42" y1="249.64" x2="205.42" y2="249.64"></line><line class="cls-4" x1="187.79" y1="231.97" x2="187.79" y2="231.97"></line><line class="cls-4" x1="205.57" y1="284.98" x2="205.57" y2="284.98"></line><line class="cls-4" x1="285.33" y1="311.41" x2="285.33" y2="311.41"></line><line class="cls-4" x1="293.81" y1="311.49" x2="293.81" y2="311.49"></line><line class="cls-4" x1="178.95" y1="117.07" x2="178.95" y2="117.07"></line><line class="cls-4" x1="37.57" y1="117.09" x2="37.57" y2="117.09"></line><line class="cls-4" x1="258.48" y1="37.56" x2="258.48" y2="37.56"></line><line class="cls-4" x1="373.35" y1="72.91" x2="373.35" y2="72.91"></line><line class="cls-4" x1="417.53" y1="55.24" x2="417.53" y2="55.24"></line><line class="cls-4" x1="373.35" y1="108.26" x2="373.35" y2="108.26"></line><line class="cls-4" x1="797.48" y1="117.09" x2="797.48" y2="117.09"></line><line class="cls-4" x1="638.43" y1="125.93" x2="638.43" y2="125.93"></line><line class="cls-4" x1="797.49" y1="134.73" x2="850.51" y2="134.73"></line><line class="cls-4" x1="912.36" y1="143.57" x2="885.85" y2="143.57"></line><line class="cls-4" x1="815.15" y1="143.57" x2="762.14" y2="143.57"></line><line class="cls-4" x1="682.61" y1="143.57" x2="717.89" y2="143.57"></line><line class="cls-4" x1="567.75" y1="143.57" x2="594.25" y2="143.57"></line><line class="cls-4" x1="585.42" y1="152.4" x2="647.27" y2="152.4"></line><line class="cls-4" x1="709.13" y1="152.4" x2="744.45" y2="152.4"></line><line class="cls-4" x1="797.49" y1="152.44" x2="850.5" y2="152.44"></line><line class="cls-4" x1="523.43" y1="161.24" x2="567.74" y2="161.24"></line><line class="cls-4" x1="638.43" y1="161.24" x2="673.78" y2="161.24"></line><line class="cls-4" x1="735.63" y1="161.28" x2="779.81" y2="161.28"></line><line class="cls-4" x1="788.64" y1="161.24" x2="815.16" y2="161.24"></line><line class="cls-4" x1="585.42" y1="170.07" x2="656.11" y2="170.07"></line><line class="cls-4" x1="709.13" y1="170.07" x2="770.98" y2="170.07"></line><line class="cls-4" x1="832.84" y1="170.07" x2="894.68" y2="170.07"></line><line class="cls-4" x1="497.06" y1="178.9" x2="558.91" y2="178.9"></line><line class="cls-4" x1="673.78" y1="178.95" x2="726.8" y2="178.95"></line><line class="cls-4" x1="779.81" y1="178.9" x2="850.5" y2="178.9"></line><line class="cls-4" x1="576.58" y1="187.78" x2="611.92" y2="187.78"></line><line class="cls-4" x1="656.11" y1="187.74" x2="753.31" y2="187.74"></line><line class="cls-4" x1="762.14" y1="187.74" x2="770.98" y2="187.74"></line><line class="cls-4" x1="868.19" y1="187.74" x2="921.19" y2="187.74"></line><line class="cls-4" x1="885.85" y1="196.57" x2="841.67" y2="196.57"></line><line class="cls-4" x1="797.49" y1="196.62" x2="735.63" y2="196.62"></line><line class="cls-4" x1="558.91" y1="196.57" x2="594.25" y2="196.57"></line><line class="cls-4" x1="497.06" y1="205.41" x2="470.55" y2="205.41"></line><line class="cls-4" x1="558.91" y1="214.24" x2="611.92" y2="214.24"></line><line class="cls-4" x1="673.78" y1="214.24" x2="682.61" y2="214.24"></line><line class="cls-4" x1="700.25" y1="214.29" x2="726.8" y2="214.29"></line><line class="cls-4" x1="824" y1="214.29" x2="877.01" y2="214.29"></line><line class="cls-4" x1="850.5" y1="205.41" x2="815.16" y2="205.41"></line><line class="cls-4" x1="770.98" y1="205.41" x2="744.45" y2="205.41"></line><line class="cls-4" x1="673.78" y1="205.41" x2="647.27" y2="205.41"></line><line class="cls-4" x1="594.25" y1="223.07" x2="638.43" y2="223.07"></line><line class="cls-4" x1="691.45" y1="223.13" x2="753.31" y2="223.13"></line><line class="cls-4" x1="806.32" y1="223.13" x2="824" y2="223.13"></line><line class="cls-4" x1="620.76" y1="231.91" x2="664.94" y2="231.91"></line><line class="cls-4" x1="744.47" y1="231.91" x2="779.82" y2="231.91"></line><line class="cls-4" x1="850.5" y1="231.91" x2="832.83" y2="231.91"></line><line class="cls-4" x1="603.09" y1="240.74" x2="638.44" y2="240.74"></line><line class="cls-4" x1="700.29" y1="240.74" x2="717.96" y2="240.74"></line><line class="cls-4" x1="762.14" y1="240.74" x2="815.16" y2="240.74"></line><line class="cls-4" x1="514.73" y1="249.64" x2="567.74" y2="249.64"></line><line class="cls-4" x1="629.6" y1="249.64" x2="682.61" y2="249.64"></line><line class="cls-4" x1="744.47" y1="249.64" x2="779.81" y2="249.64"></line><line class="cls-4" x1="717.89" y1="258.41" x2="762.14" y2="258.41"></line><line class="cls-4" x1="850.5" y1="258.41" x2="815.15" y2="258.41"></line><line class="cls-4" x1="824" y1="267.24" x2="777.33" y2="267.24"></line><line class="cls-4" x1="700.29" y1="267.24" x2="735.64" y2="267.24"></line><line class="cls-4" x1="479.38" y1="276.15" x2="541.24" y2="276.15"></line><line class="cls-4" x1="514.73" y1="284.98" x2="558.91" y2="284.98"></line><line class="cls-4" x1="452.87" y1="284.98" x2="479.38" y2="284.98"></line><line class="cls-4" x1="558.91" y1="302.58" x2="629.6" y2="302.58"></line><line class="cls-4" x1="585.42" y1="311.49" x2="532.4" y2="311.49"></line><line class="cls-4" x1="461.71" y1="311.41" x2="488.22" y2="311.41"></line><line class="cls-4" x1="479.38" y1="320.33" x2="514.73" y2="320.33"></line><line class="cls-4" x1="567.74" y1="320.25" x2="620.76" y2="320.25"></line><line class="cls-4" x1="550.07" y1="329.08" x2="594.25" y2="329.08"></line><line class="cls-4" x1="576.58" y1="338" x2="611.92" y2="338"></line><line class="cls-4" x1="523.56" y1="346.75" x2="550.07" y2="346.75"></line><line class="cls-4" x1="567.75" y1="355.67" x2="594.25" y2="355.67"></line><line class="cls-4" x1="585.42" y1="364.51" x2="611.92" y2="364.51"></line><line class="cls-4" x1="558.91" y1="373.25" x2="541.24" y2="373.25"></line><line class="cls-4" x1="576.58" y1="390.92" x2="611.92" y2="390.92"></line><line class="cls-4" x1="558.91" y1="408.69" x2="594.26" y2="408.69"></line></g><line class="community-svg-orange" x1="90.59" y1="143.6" x2="99.42" y2="143.6"></line><line class="community-svg-orange" x1="134.77" y1="205.45" x2="152.44" y2="205.45"></line><line class="community-svg-orange" x1="342.42" y1="364.44" x2="360.09" y2="364.44"></line><line class="community-svg-orange" x1="205.42" y1="231.97" x2="223.06" y2="231.97"></line><line class="community-svg-orange" x1="134.81" y1="196.62" x2="143.57" y2="196.62"></line><line class="community-svg-orange" x1="523.59" y1="161.34" x2="541.24" y2="161.34"></line><line class="community-svg-orange" x1="258.48" y1="214.29" x2="267.24" y2="214.29"></line><line class="community-svg-orange" x1="470.59" y1="152.47" x2="479.35" y2="152.47"></line><line class="community-svg-purple" x1="134.81" y1="214.29" x2="143.57" y2="214.29"></line><line class="community-svg-blue" x1="143.64" y1="214.29" x2="152.4" y2="214.29"></line><line class="community-svg-blue" x1="461.71" y1="161.34" x2="488.22" y2="161.34"></line><line class="community-svg-blue" x1="162.49" y1="205.45" x2="162.49" y2="205.45"></line><line class="community-svg-purple" x1="231.82" y1="231.95" x2="231.82" y2="231.95"></line><line class="community-svg-purple" x1="360.2" y1="364.44" x2="360.2" y2="364.44"></line><line class="community-svg-purple" x1="258.71" y1="205.45" x2="284.91" y2="205.45"></line><line class="community-svg-purple" x1="267.34" y1="214.29" x2="276.11" y2="214.29"></line><line class="community-svg-purple" x1="488.26" y1="161.34" x2="497.02" y2="161.34"></line><line class="community-svg-purple" x1="479.42" y1="152.47" x2="488.18" y2="152.47"></line><line class="community-svg-purple" x1="342.46" y1="355.67" x2="351.22" y2="355.67"></line><line class="community-svg-orange" x1="223.21" y1="240.78" x2="231.97" y2="240.78"></line><line class="community-svg-orange" x1="479.42" y1="143.6" x2="488.18" y2="143.6"></line><line class="community-svg-blue" x1="223.06" y1="240.78" x2="223.06" y2="240.78"></line><line class="community-svg-orange" x1="912.36" y1="231.91" x2="903.52" y2="231.91"></line><line class="community-svg-orange" x1="877.01" y1="231.91" x2="894.68" y2="231.91"></line><line class="community-svg-orange" x1="850.5" y1="249.58" x2="841.67" y2="249.58"></line><line class="community-svg-orange" x1="850.5" y1="258.41" x2="832.83" y2="258.41"></line><line class="community-svg-orange" x1="850.5" y1="240.74" x2="823.99" y2="240.74"></line><line class="community-svg-orange" x1="832.83" y1="408.59" x2="841.68" y2="408.59"></line><line class="community-svg-orange" x1="841.68" y1="435.09" x2="857.86" y2="435.09"></line><line class="community-svg-orange" x1="947.7" y1="417.42" x2="930.03" y2="417.42"></line><line class="community-svg-orange" x1="576.58" y1="443.93" x2="558.91" y2="443.93"></line><line class="community-svg-orange" x1="550.07" y1="134.73" x2="532.42" y2="134.73"></line><line class="community-svg-orange" x1="505.89" y1="170.07" x2="532.42" y2="170.07"></line><line class="community-svg-orange" x1="470.55" y1="205.41" x2="479.42" y2="205.41"></line><line class="community-svg-orange" x1="550.07" y1="187.78" x2="523.59" y2="187.78"></line><line class="community-svg-blue" x1="479.38" y1="187.74" x2="510.31" y2="187.74"></line><line class="community-svg-blue" x1="550.07" y1="170.21" x2="532.42" y2="170.21"></line><line class="community-svg-blue" x1="514.73" y1="143.57" x2="523.56" y2="143.57"></line><line class="community-svg-blue" x1="550.07" y1="443.93" x2="558.91" y2="443.93"></line><line class="community-svg-blue" x1="585.42" y1="435.09" x2="567.74" y2="435.09"></line><line class="community-svg-blue" x1="196.68" y1="223.13" x2="223.21" y2="223.13"></line><line class="community-svg-blue" x1="267.31" y1="196.62" x2="249.64" y2="196.62"></line><line class="community-svg-blue" x1="240.71" y1="205.45" x2="249.64" y2="205.45"></line><line class="community-svg-blue" x1="267.31" y1="223.12" x2="249.61" y2="223.12"></line><line class="community-svg-blue" x1="196.68" y1="240.78" x2="214.3" y2="240.78"></line><line class="community-svg-blue" x1="125.93" y1="143.6" x2="99.42" y2="143.6"></line><line class="community-svg-blue" x1="894.68" y1="231.91" x2="903.52" y2="231.91"></line><line class="community-svg-blue" x1="868.18" y1="223.07" x2="877.01" y2="223.07"></line><line class="community-svg-blue" x1="912.36" y1="223.07" x2="903.52" y2="223.07"></line><line class="community-svg-blue" x1="841.67" y1="249.58" x2="806.32" y2="249.58"></line><line class="community-svg-blue" x1="793.07" y1="284.98" x2="806.32" y2="284.98"></line><line class="community-svg-blue" x1="841.68" y1="408.59" x2="863.76" y2="408.59"></line><line class="community-svg-blue" x1="857.86" y1="435.09" x2="872.59" y2="435.09"></line><line class="community-svg-blue" x1="832.83" y1="426.26" x2="849.77" y2="426.26"></line><line class="community-svg-blue" x1="930.03" y1="417.42" x2="912.36" y2="417.42"></line><line class="community-svg-purple" x1="187.79" y1="231.97" x2="205.42" y2="231.97"></line><line class="community-svg-purple" x1="99.42" y1="152.47" x2="112.68" y2="152.47"></line><line class="community-svg-purple" x1="152.44" y1="187.69" x2="134.77" y2="187.69"></line><line class="community-svg-purple" x1="214.29" y1="249.61" x2="240.71" y2="249.61"></line><line class="community-svg-purple" x1="240.81" y1="214.24" x2="258.48" y2="214.24"></line><line class="community-svg-purple" x1="541.24" y1="161.34" x2="567.74" y2="161.34"></line><line class="community-svg-purple" x1="523.56" y1="143.57" x2="541.24" y2="143.57"></line><line class="community-svg-purple" x1="488.22" y1="134.73" x2="497.06" y2="134.73"></line><line class="community-svg-purple" x1="479.38" y1="170.21" x2="488.22" y2="170.21"></line><line class="community-svg-purple" x1="510.31" y1="187.74" x2="523.59" y2="187.74"></line><line class="community-svg-purple" x1="497.06" y1="178.9" x2="523.59" y2="178.9"></line><line class="community-svg-purple" x1="479.42" y1="205.41" x2="497.06" y2="205.41"></line><line class="community-svg-purple" x1="558.91" y1="435.16" x2="567.74" y2="435.16"></line><line class="community-svg-purple" x1="832.83" y1="258.41" x2="815.15" y2="258.41"></line><line class="community-svg-purple" x1="859.35" y1="214.24" x2="877.01" y2="214.24"></line><line class="community-svg-purple" x1="849.77" y1="417.42" x2="872.59" y2="417.42"></line><line class="community-svg-purple" x1="925.61" y1="426.32" x2="947.7" y2="426.32"></line><line class="community-svg-blue" x1="351.26" y1="408.55" x2="333.58" y2="408.55"></line><line class="community-svg-purple" x1="324.75" y1="408.62" x2="333.58" y2="408.62"></line><line class="community-svg-orange" x1="655.42" y1="116.97" x2="673.06" y2="116.97"></line><line class="community-svg-purple" x1="637.79" y1="116.97" x2="655.42" y2="116.97"></line><line class="community-svg-orange" x1="647.59" y1="125.6" x2="656.42" y2="125.6"></line><line class="community-svg-blue" x1="682.93" y1="125.6" x2="656.42" y2="125.6"></line><line class="community-svg-purple" x1="634.61" y1="134.32" x2="656.7" y2="134.32"></line><line class="community-svg-orange" x1="382.5" y1="373.58" x2="373.67" y2="373.58"></line><line class="community-svg-blue" x1="373.67" y1="373.58" x2="338.32" y2="373.58"></line><line class="community-svg-orange" x1="894.48" y1="178.29" x2="903.24" y2="178.29"></line><line class="community-svg-purple" x1="894.71" y1="169.45" x2="920.91" y2="169.45"></line><line class="community-svg-purple" x1="903.34" y1="178.29" x2="912.11" y2="178.29"></line><line class="community-svg-blue" x1="903.31" y1="160.62" x2="885.64" y2="160.62"></line><line class="community-svg-orange" x1="466.81" y1="320.62" x2="475.57" y2="320.62"></line></g></g></svg>

      </div>
    </div>

    <div class="text-center">
      <h3 class="alt-h3 mt-3 mb-4 lh-condensed">
        More than a million teams use GitHub
      </h3>
      <ul class="d-flex flex-justify-center flex-items-center flex-wrap list-style-none my-2 my-md-3 grayscale">
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/airbnb-logo.png" alt="Airbnb" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/sap-logo.png" alt="SAP" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/ibm-logo.png" alt="IBM" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/google-logo.png" alt="Google" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/paypal-logo.png" alt="PayPal" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/bloomberg-logo.png" alt="Bloomberg" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/spotify-logo.png" alt="Spotify" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/swift-logo.png" alt="Swift" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/facebook-logo.png" alt="Rails" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/node-logo.png" alt="Node" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/nasa-logo.png" alt="Nasa" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
        <li class="mb-3"><img src="https://assets-cdn.github.com/images/modules/site/logos/walmart-logo.png" alt="Walmart" class="logo-img px-2 px-sm-4 px-md-5 px-lg-0"></li>
      </ul>
    </div>

  </div>
</div>

  <div class="featurette bg-gray-light">
    <div class="container-lg p-responsive text-center">
      <h2 class="alt-h2 mt-0 mb-1">
        Get started for free
      </h2>
      <p class="lead mb-3 col-md-8 mx-auto">
        Join the millions of developers already using GitHub to share their code, work together, and build amazing things.
      </p>
      <p class="f3">
        <a href="/join" class="btn btn-large btn-primary">Sign up for GitHub</a>
      </p>
    </div>
  </div>

  <div class="modal-backdrop js-touch-events"></div>

  </div>

        <div class="site-footer-container mt-6" role="contentinfo">
  <div class="d-flex flex-wrap py-5 mb-5">
    <div class="site-footer-col mb-3">
      <svg aria-hidden="true" class="octicon octicon-logo-github" height="24" version="1.1" viewBox="0 0 45 16" width="67"><path fill-rule="evenodd" d="M18.53 12.03h-.02c.009 0 .015.01.024.011h.006l-.01-.01zm.004.011c-.093.001-.327.05-.574.05-.78 0-1.05-.36-1.05-.83V8.13h1.59c.09 0 .16-.08.16-.19v-1.7c0-.09-.08-.17-.16-.17h-1.59V3.96c0-.08-.05-.13-.14-.13h-2.16c-.09 0-.14.05-.14.13v2.17s-1.09.27-1.16.28c-.08.02-.13.09-.13.17v1.36c0 .11.08.19.17.19h1.11v3.28c0 2.44 1.7 2.69 2.86 2.69.53 0 1.17-.17 1.27-.22.06-.02.09-.09.09-.16v-1.5a.177.177 0 0 0-.146-.18zm23.696-2.2c0-1.81-.73-2.05-1.5-1.97-.6.04-1.08.34-1.08.34v3.52s.49.34 1.22.36c1.03.03 1.36-.34 1.36-2.25zm2.43-.16c0 3.43-1.11 4.41-3.05 4.41-1.64 0-2.52-.83-2.52-.83s-.04.46-.09.52c-.03.06-.08.08-.14.08h-1.48c-.1 0-.19-.08-.19-.17l.02-11.11c0-.09.08-.17.17-.17h2.13c.09 0 .17.08.17.17v3.77s.82-.53 2.02-.53l-.01-.02c1.2 0 2.97.45 2.97 3.88zm-8.72-3.61H33.84c-.11 0-.17.08-.17.19v5.44s-.55.39-1.3.39-.97-.34-.97-1.09V6.25c0-.09-.08-.17-.17-.17h-2.14c-.09 0-.17.08-.17.17v5.11c0 2.2 1.23 2.75 2.92 2.75 1.39 0 2.52-.77 2.52-.77s.05.39.08.45c.02.05.09.09.16.09h1.34c.11 0 .17-.08.17-.17l.02-7.47c0-.09-.08-.17-.19-.17zm-23.7-.01h-2.13c-.09 0-.17.09-.17.2v7.34c0 .2.13.27.3.27h1.92c.2 0 .25-.09.25-.27V6.23c0-.09-.08-.17-.17-.17zm-1.05-3.38c-.77 0-1.38.61-1.38 1.38 0 .77.61 1.38 1.38 1.38.75 0 1.36-.61 1.36-1.38 0-.77-.61-1.38-1.36-1.38zm16.49-.25h-2.11c-.09 0-.17.08-.17.17v4.09h-3.31V2.6c0-.09-.08-.17-.17-.17h-2.13c-.09 0-.17.08-.17.17v11.11c0 .09.09.17.17.17h2.13c.09 0 .17-.08.17-.17V8.96h3.31l-.02 4.75c0 .09.08.17.17.17h2.13c.09 0 .17-.08.17-.17V2.6c0-.09-.08-.17-.17-.17zM8.81 7.35v5.74c0 .04-.01.11-.06.13 0 0-1.25.89-3.31.89-2.49 0-5.44-.78-5.44-5.92S2.58 1.99 5.1 2c2.18 0 3.06.49 3.2.58.04.05.06.09.06.14L7.94 4.5c0 .09-.09.2-.2.17-.36-.11-.9-.33-2.17-.33-1.47 0-3.05.42-3.05 3.73s1.5 3.7 2.58 3.7c.92 0 1.25-.11 1.25-.11v-2.3H4.88c-.11 0-.19-.08-.19-.17V7.35c0-.09.08-.17.19-.17h3.74c.11 0 .19.08.19.17z"/></svg>
      <p class="text-gray alt-text-small">
        &copy; 2017
      </p>
    </div>
    <div class="site-footer-col mb-3 pr-3">
      <h4 class="mb-2">Features</h4>
      <ul class="list-style-none text-gray">
        <li class="lh-condensed mb-2"><a href="/features#code-review" class="muted-link alt-text-small">Code review</a></li>
        <li class="lh-condensed mb-2"><a href="/features#project-management" class="muted-link alt-text-small">Project management</a></li>
        <li class="lh-condensed mb-2"><a href="/features#community-management" class="muted-link alt-text-small">Community</a></li>
        <li class="lh-condensed mb-2"><a href="/features#documentation" class="muted-link alt-text-small">Documentation</a></li>
        <li class="lh-condensed mb-2"><a href="/features#code-hosting" class="muted-link alt-text-small">Code hosting</a></li>
      </ul>
    </div>
    <div class="site-footer-col mb-3 pr-3">
      <h4 class="mb-2">Platform</h4>
      <ul class="list-style-none">
        <li class="lh-condensed mb-2"><a href="https://atom.io" class="muted-link alt-text-small">Atom</a></li>
        <li class="lh-condensed mb-2"><a href="http://electron.atom.io/" class="muted-link alt-text-small">Electron</a></li>
        <li class="lh-condensed mb-2"><a href="https://desktop.github.com/" class="muted-link alt-text-small">GitHub Desktop</a></li>
        <li class="lh-condensed mb-2"><a href="https://developer.github.com" data-ga-click="Footer, go to api, text:api" class="muted-link alt-text-small">Developers</a></li>
      </ul>
    </div>
    <div class="site-footer-col mb-3 pr-3">
      <h4 class="mb-2">Community</h4>
      <ul class="list-style-none">
        <li class="lh-condensed mb-2"><a href="/personal" class="muted-link alt-text-small">Personal</a></li>
        <li class="lh-condensed mb-2"><a href="/open-source" class="muted-link alt-text-small">Open source</a></li>
        <li class="lh-condensed mb-2"><a href="/business" class="muted-link alt-text-small">For Business</a></li>
        <li class="lh-condensed mb-2"><a href="https://education.github.com/" class="muted-link alt-text-small">For Education</a></li>
        <li class="lh-condensed mb-2"><a href="https://community.github.com/" class="muted-link alt-text-small">Sponsorships</a></li>
      </ul>
    </div>
    <div class="site-footer-col mb-3 pr-3">
      <h4 class="mb-2">Company</h4>
      <ul class="list-style-none">
        <li class="lh-condensed mb-2"><a href="https://github.com/about" class="muted-link alt-text-small" data-ga-click="Footer, go to about, text:about">About</a></li>
        <li class="lh-condensed mb-2"><a href="https://github.com/blog" class="muted-link alt-text-small" data-ga-click="Footer, go to blog, text:blog">Blog</a></li>
        <li class="lh-condensed mb-2"><a href="/business/customers" class="muted-link alt-text-small">Customers</a></li>
        <li class="lh-condensed mb-2"><a href="/about/careers" class="muted-link alt-text-small">Careers</a></li>
        <li class="lh-condensed mb-2"><a href="/about/press" class="muted-link alt-text-small">Press</a></li>
        <li class="lh-condensed mb-2"><a href="https://shop.github.com" class="muted-link alt-text-small">Shop</a></li>
      </ul>
    </div>
    <div class="site-footer-col mb-3 pr-3">
      <h4 class="mb-2">Resources</h4>
      <ul class="list-style-none">
        <li class="lh-condensed mb-2"><a href="https://github.com/contact" class="muted-link alt-text-small" data-ga-click="Footer, go to contact, text:contact">Contact GitHub</a></li>
        <li class="lh-condensed mb-2"><a href="https://help.github.com" class="muted-link alt-text-small" data-ga-click="Footer, go to help, text:help">Help</a></li>
        <li class="lh-condensed mb-2"><a href="https://status.github.com/" data-ga-click="Footer, go to status, text:status" class="muted-link alt-text-small">Status</a></li>
        <li class="lh-condensed mb-2"><a href="https://github.com/site/terms" class="muted-link alt-text-small" data-ga-click="Footer, go to terms, text:terms">Terms</a></li>
        <li class="lh-condensed mb-2"><a href="https://github.com/site/privacy" class="muted-link alt-text-small" data-ga-click="Footer, go to privacy, text:privacy">Privacy</a></li>
        <li class="lh-condensed mb-2"><a href="https://github.com/security" class="muted-link alt-text-small" data-ga-click="Footer, go to security, text:security">Security</a></li>
        <li class="lh-condensed mb-2"><a href="https://services.github.com/" class="muted-link alt-text-small">Training</a></li>
      </ul>
    </div>
  </div>
</div>




  <div id="ajax-error-message" class="ajax-error-message flash flash-error">
    <svg aria-hidden="true" class="octicon octicon-alert" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M8.865 1.52c-.18-.31-.51-.5-.87-.5s-.69.19-.87.5L.275 13.5c-.18.31-.18.69 0 1 .19.31.52.5.87.5h13.7c.36 0 .69-.19.86-.5.17-.31.18-.69.01-1L8.865 1.52zM8.995 13h-2v-2h2v2zm0-3h-2V6h2v4z"/></svg>
    <button type="button" class="flash-close js-flash-close js-ajax-error-dismiss" aria-label="Dismiss error">
      <svg aria-hidden="true" class="octicon octicon-x" height="16" version="1.1" viewBox="0 0 12 16" width="12"><path fill-rule="evenodd" d="M7.48 8l3.75 3.75-1.48 1.48L6 9.48l-3.75 3.75-1.48-1.48L4.52 8 .77 4.25l1.48-1.48L6 6.52l3.75-3.75 1.48 1.48z"/></svg>
    </button>
    You can't perform that action at this time.
  </div>



    <script crossorigin="anonymous" integrity="sha256-WPmzrdPnixt4E6nHmALNI0t7Dq7CEh4VbTaZ1YoacGY=" src="https://assets-cdn.github.com/assets/frameworks-58f9b3add3e78b1b7813a9c79802cd234b7b0eaec2121e156d3699d58a1a7066.js"></script>

    <script async="async" crossorigin="anonymous" integrity="sha256-fhhiPL2hTmofanLoOe0nvWXfYdFeVsiwZUD3pfLFcUk=" src="https://assets-cdn.github.com/assets/github-7e18623cbda14e6a1f6a72e839ed27bd65df61d15e56c8b06540f7a5f2c57149.js"></script>




  <div class="js-stale-session-flash stale-session-flash flash flash-warn flash-banner d-none">
    <svg aria-hidden="true" class="octicon octicon-alert" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M8.865 1.52c-.18-.31-.51-.5-.87-.5s-.69.19-.87.5L.275 13.5c-.18.31-.18.69 0 1 .19.31.52.5.87.5h13.7c.36 0 .69-.19.86-.5.17-.31.18-.69.01-1L8.865 1.52zM8.995 13h-2v-2h2v2zm0-3h-2V6h2v4z"/></svg>
    <span class="signed-in-tab-flash">You signed in with another tab or window. <a href="">Reload</a> to refresh your session.</span>
    <span class="signed-out-tab-flash">You signed out in another tab or window. <a href="">Reload</a> to refresh your session.</span>
  </div>
  <div class="facebox" id="facebox" style="display:none;">
  <div class="facebox-popup">
    <div class="facebox-content" role="dialog" aria-labelledby="facebox-header" aria-describedby="facebox-description">
    </div>
    <button type="button" class="facebox-close js-facebox-close" aria-label="Close modal">
      <svg aria-hidden="true" class="octicon octicon-x" height="16" version="1.1" viewBox="0 0 12 16" width="12"><path fill-rule="evenodd" d="M7.48 8l3.75 3.75-1.48 1.48L6 9.48l-3.75 3.75-1.48-1.48L4.52 8 .77 4.25l1.48-1.48L6 6.52l3.75-3.75 1.48 1.48z"/></svg>
    </button>
  </div>
</div>


  </body>
</html>"
  ["status"]=>
  string(3) "200"
  ["filename"]=>
  string(50) "/CURL-edea68cb9b64a35b80e914c7c49a9936f33c7b56.180"
}
*/
```

### Cache Purging:

Although the cache is being purged automatically, you may purge cache yourself (e.g. as crontab job).

```php
use peterkahl\curlMaster\curlMaster;

$curlm = new curlMaster;

$curlm->PurgeCache();
```
