---
title: "Video Games: A Predictive Description"
layout: default
date: 2019-11-10
tags:
  - NLP
  - Python
  - Dimension Reduction
  - Sklearn
  - Supervised Learning
---

<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />

<title>joshua_roberge_quiz_2</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>



<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.7.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.7.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.fa-pull-left {
  float: left;
}
.fa-pull-right {
  float: right;
}
.fa.fa-pull-left {
  margin-right: .3em;
}
.fa.fa-pull-right {
  margin-left: .3em;
}
/* Deprecated as of 4.4.0 */
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
.fa-pulse {
  -webkit-animation: fa-spin 1s infinite steps(8);
  animation: fa-spin 1s infinite steps(8);
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=1)";
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2)";
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=3)";
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1)";
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook-f:before,
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-feed:before,
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before,
.fa-gratipay:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper-pp:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-resistance:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-y-combinator-square:before,
.fa-yc-square:before,
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
.fa-buysellads:before {
  content: "\f20d";
}
.fa-connectdevelop:before {
  content: "\f20e";
}
.fa-dashcube:before {
  content: "\f210";
}
.fa-forumbee:before {
  content: "\f211";
}
.fa-leanpub:before {
  content: "\f212";
}
.fa-sellsy:before {
  content: "\f213";
}
.fa-shirtsinbulk:before {
  content: "\f214";
}
.fa-simplybuilt:before {
  content: "\f215";
}
.fa-skyatlas:before {
  content: "\f216";
}
.fa-cart-plus:before {
  content: "\f217";
}
.fa-cart-arrow-down:before {
  content: "\f218";
}
.fa-diamond:before {
  content: "\f219";
}
.fa-ship:before {
  content: "\f21a";
}
.fa-user-secret:before {
  content: "\f21b";
}
.fa-motorcycle:before {
  content: "\f21c";
}
.fa-street-view:before {
  content: "\f21d";
}
.fa-heartbeat:before {
  content: "\f21e";
}
.fa-venus:before {
  content: "\f221";
}
.fa-mars:before {
  content: "\f222";
}
.fa-mercury:before {
  content: "\f223";
}
.fa-intersex:before,
.fa-transgender:before {
  content: "\f224";
}
.fa-transgender-alt:before {
  content: "\f225";
}
.fa-venus-double:before {
  content: "\f226";
}
.fa-mars-double:before {
  content: "\f227";
}
.fa-venus-mars:before {
  content: "\f228";
}
.fa-mars-stroke:before {
  content: "\f229";
}
.fa-mars-stroke-v:before {
  content: "\f22a";
}
.fa-mars-stroke-h:before {
  content: "\f22b";
}
.fa-neuter:before {
  content: "\f22c";
}
.fa-genderless:before {
  content: "\f22d";
}
.fa-facebook-official:before {
  content: "\f230";
}
.fa-pinterest-p:before {
  content: "\f231";
}
.fa-whatsapp:before {
  content: "\f232";
}
.fa-server:before {
  content: "\f233";
}
.fa-user-plus:before {
  content: "\f234";
}
.fa-user-times:before {
  content: "\f235";
}
.fa-hotel:before,
.fa-bed:before {
  content: "\f236";
}
.fa-viacoin:before {
  content: "\f237";
}
.fa-train:before {
  content: "\f238";
}
.fa-subway:before {
  content: "\f239";
}
.fa-medium:before {
  content: "\f23a";
}
.fa-yc:before,
.fa-y-combinator:before {
  content: "\f23b";
}
.fa-optin-monster:before {
  content: "\f23c";
}
.fa-opencart:before {
  content: "\f23d";
}
.fa-expeditedssl:before {
  content: "\f23e";
}
.fa-battery-4:before,
.fa-battery:before,
.fa-battery-full:before {
  content: "\f240";
}
.fa-battery-3:before,
.fa-battery-three-quarters:before {
  content: "\f241";
}
.fa-battery-2:before,
.fa-battery-half:before {
  content: "\f242";
}
.fa-battery-1:before,
.fa-battery-quarter:before {
  content: "\f243";
}
.fa-battery-0:before,
.fa-battery-empty:before {
  content: "\f244";
}
.fa-mouse-pointer:before {
  content: "\f245";
}
.fa-i-cursor:before {
  content: "\f246";
}
.fa-object-group:before {
  content: "\f247";
}
.fa-object-ungroup:before {
  content: "\f248";
}
.fa-sticky-note:before {
  content: "\f249";
}
.fa-sticky-note-o:before {
  content: "\f24a";
}
.fa-cc-jcb:before {
  content: "\f24b";
}
.fa-cc-diners-club:before {
  content: "\f24c";
}
.fa-clone:before {
  content: "\f24d";
}
.fa-balance-scale:before {
  content: "\f24e";
}
.fa-hourglass-o:before {
  content: "\f250";
}
.fa-hourglass-1:before,
.fa-hourglass-start:before {
  content: "\f251";
}
.fa-hourglass-2:before,
.fa-hourglass-half:before {
  content: "\f252";
}
.fa-hourglass-3:before,
.fa-hourglass-end:before {
  content: "\f253";
}
.fa-hourglass:before {
  content: "\f254";
}
.fa-hand-grab-o:before,
.fa-hand-rock-o:before {
  content: "\f255";
}
.fa-hand-stop-o:before,
.fa-hand-paper-o:before {
  content: "\f256";
}
.fa-hand-scissors-o:before {
  content: "\f257";
}
.fa-hand-lizard-o:before {
  content: "\f258";
}
.fa-hand-spock-o:before {
  content: "\f259";
}
.fa-hand-pointer-o:before {
  content: "\f25a";
}
.fa-hand-peace-o:before {
  content: "\f25b";
}
.fa-trademark:before {
  content: "\f25c";
}
.fa-registered:before {
  content: "\f25d";
}
.fa-creative-commons:before {
  content: "\f25e";
}
.fa-gg:before {
  content: "\f260";
}
.fa-gg-circle:before {
  content: "\f261";
}
.fa-tripadvisor:before {
  content: "\f262";
}
.fa-odnoklassniki:before {
  content: "\f263";
}
.fa-odnoklassniki-square:before {
  content: "\f264";
}
.fa-get-pocket:before {
  content: "\f265";
}
.fa-wikipedia-w:before {
  content: "\f266";
}
.fa-safari:before {
  content: "\f267";
}
.fa-chrome:before {
  content: "\f268";
}
.fa-firefox:before {
  content: "\f269";
}
.fa-opera:before {
  content: "\f26a";
}
.fa-internet-explorer:before {
  content: "\f26b";
}
.fa-tv:before,
.fa-television:before {
  content: "\f26c";
}
.fa-contao:before {
  content: "\f26d";
}
.fa-500px:before {
  content: "\f26e";
}
.fa-amazon:before {
  content: "\f270";
}
.fa-calendar-plus-o:before {
  content: "\f271";
}
.fa-calendar-minus-o:before {
  content: "\f272";
}
.fa-calendar-times-o:before {
  content: "\f273";
}
.fa-calendar-check-o:before {
  content: "\f274";
}
.fa-industry:before {
  content: "\f275";
}
.fa-map-pin:before {
  content: "\f276";
}
.fa-map-signs:before {
  content: "\f277";
}
.fa-map-o:before {
  content: "\f278";
}
.fa-map:before {
  content: "\f279";
}
.fa-commenting:before {
  content: "\f27a";
}
.fa-commenting-o:before {
  content: "\f27b";
}
.fa-houzz:before {
  content: "\f27c";
}
.fa-vimeo:before {
  content: "\f27d";
}
.fa-black-tie:before {
  content: "\f27e";
}
.fa-fonticons:before {
  content: "\f280";
}
.fa-reddit-alien:before {
  content: "\f281";
}
.fa-edge:before {
  content: "\f282";
}
.fa-credit-card-alt:before {
  content: "\f283";
}
.fa-codiepie:before {
  content: "\f284";
}
.fa-modx:before {
  content: "\f285";
}
.fa-fort-awesome:before {
  content: "\f286";
}
.fa-usb:before {
  content: "\f287";
}
.fa-product-hunt:before {
  content: "\f288";
}
.fa-mixcloud:before {
  content: "\f289";
}
.fa-scribd:before {
  content: "\f28a";
}
.fa-pause-circle:before {
  content: "\f28b";
}
.fa-pause-circle-o:before {
  content: "\f28c";
}
.fa-stop-circle:before {
  content: "\f28d";
}
.fa-stop-circle-o:before {
  content: "\f28e";
}
.fa-shopping-bag:before {
  content: "\f290";
}
.fa-shopping-basket:before {
  content: "\f291";
}
.fa-hashtag:before {
  content: "\f292";
}
.fa-bluetooth:before {
  content: "\f293";
}
.fa-bluetooth-b:before {
  content: "\f294";
}
.fa-percent:before {
  content: "\f295";
}
.fa-gitlab:before {
  content: "\f296";
}
.fa-wpbeginner:before {
  content: "\f297";
}
.fa-wpforms:before {
  content: "\f298";
}
.fa-envira:before {
  content: "\f299";
}
.fa-universal-access:before {
  content: "\f29a";
}
.fa-wheelchair-alt:before {
  content: "\f29b";
}
.fa-question-circle-o:before {
  content: "\f29c";
}
.fa-blind:before {
  content: "\f29d";
}
.fa-audio-description:before {
  content: "\f29e";
}
.fa-volume-control-phone:before {
  content: "\f2a0";
}
.fa-braille:before {
  content: "\f2a1";
}
.fa-assistive-listening-systems:before {
  content: "\f2a2";
}
.fa-asl-interpreting:before,
.fa-american-sign-language-interpreting:before {
  content: "\f2a3";
}
.fa-deafness:before,
.fa-hard-of-hearing:before,
.fa-deaf:before {
  content: "\f2a4";
}
.fa-glide:before {
  content: "\f2a5";
}
.fa-glide-g:before {
  content: "\f2a6";
}
.fa-signing:before,
.fa-sign-language:before {
  content: "\f2a7";
}
.fa-low-vision:before {
  content: "\f2a8";
}
.fa-viadeo:before {
  content: "\f2a9";
}
.fa-viadeo-square:before {
  content: "\f2aa";
}
.fa-snapchat:before {
  content: "\f2ab";
}
.fa-snapchat-ghost:before {
  content: "\f2ac";
}
.fa-snapchat-square:before {
  content: "\f2ad";
}
.fa-pied-piper:before {
  content: "\f2ae";
}
.fa-first-order:before {
  content: "\f2b0";
}
.fa-yoast:before {
  content: "\f2b1";
}
.fa-themeisle:before {
  content: "\f2b2";
}
.fa-google-plus-circle:before,
.fa-google-plus-official:before {
  content: "\f2b3";
}
.fa-fa:before,
.fa-font-awesome:before {
  content: "\f2b4";
}
.fa-handshake-o:before {
  content: "\f2b5";
}
.fa-envelope-open:before {
  content: "\f2b6";
}
.fa-envelope-open-o:before {
  content: "\f2b7";
}
.fa-linode:before {
  content: "\f2b8";
}
.fa-address-book:before {
  content: "\f2b9";
}
.fa-address-book-o:before {
  content: "\f2ba";
}
.fa-vcard:before,
.fa-address-card:before {
  content: "\f2bb";
}
.fa-vcard-o:before,
.fa-address-card-o:before {
  content: "\f2bc";
}
.fa-user-circle:before {
  content: "\f2bd";
}
.fa-user-circle-o:before {
  content: "\f2be";
}
.fa-user-o:before {
  content: "\f2c0";
}
.fa-id-badge:before {
  content: "\f2c1";
}
.fa-drivers-license:before,
.fa-id-card:before {
  content: "\f2c2";
}
.fa-drivers-license-o:before,
.fa-id-card-o:before {
  content: "\f2c3";
}
.fa-quora:before {
  content: "\f2c4";
}
.fa-free-code-camp:before {
  content: "\f2c5";
}
.fa-telegram:before {
  content: "\f2c6";
}
.fa-thermometer-4:before,
.fa-thermometer:before,
.fa-thermometer-full:before {
  content: "\f2c7";
}
.fa-thermometer-3:before,
.fa-thermometer-three-quarters:before {
  content: "\f2c8";
}
.fa-thermometer-2:before,
.fa-thermometer-half:before {
  content: "\f2c9";
}
.fa-thermometer-1:before,
.fa-thermometer-quarter:before {
  content: "\f2ca";
}
.fa-thermometer-0:before,
.fa-thermometer-empty:before {
  content: "\f2cb";
}
.fa-shower:before {
  content: "\f2cc";
}
.fa-bathtub:before,
.fa-s15:before,
.fa-bath:before {
  content: "\f2cd";
}
.fa-podcast:before {
  content: "\f2ce";
}
.fa-window-maximize:before {
  content: "\f2d0";
}
.fa-window-minimize:before {
  content: "\f2d1";
}
.fa-window-restore:before {
  content: "\f2d2";
}
.fa-times-rectangle:before,
.fa-window-close:before {
  content: "\f2d3";
}
.fa-times-rectangle-o:before,
.fa-window-close-o:before {
  content: "\f2d4";
}
.fa-bandcamp:before {
  content: "\f2d5";
}
.fa-grav:before {
  content: "\f2d6";
}
.fa-etsy:before {
  content: "\f2d7";
}
.fa-imdb:before {
  content: "\f2d8";
}
.fa-ravelry:before {
  content: "\f2d9";
}
.fa-eercast:before {
  content: "\f2da";
}
.fa-microchip:before {
  content: "\f2db";
}
.fa-snowflake-o:before {
  content: "\f2dc";
}
.fa-superpowers:before {
  content: "\f2dd";
}
.fa-wpexplorer:before {
  content: "\f2de";
}
.fa-meetup:before {
  content: "\f2e0";
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box 
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this 
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+ 
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
div.traceback-wrapper pre.traceback {
  max-height: 600px;
  overflow: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 5px;
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
[dir="rtl"] #ipython_notebook {
  margin-right: 10px;
  margin-left: 0;
}
[dir="rtl"] #ipython_notebook.pull-left {
  float: right !important;
  float: right;
}
.flex-spacer {
  flex: 1;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#kernel_logo_widget {
  margin: 0 10px;
}
span#login_widget {
  float: right;
}
[dir="rtl"] span#login_widget {
  float: left;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
.modal-header {
  cursor: move;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
[dir="rtl"] .center-nav form.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] .center-nav .navbar-text {
  float: right;
}
[dir="rtl"] .navbar-inner {
  text-align: right;
}
[dir="rtl"] div.text-left {
  text-align: right;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: pointer;
  opacity: 0;
  z-index: 2;
}
.alternate_upload .btn-xs > input.fileinput {
  margin: -1px -5px;
}
.alternate_upload .btn-upload {
  position: relative;
  height: 22px;
}
::-webkit-file-upload-button {
  cursor: pointer;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
[dir="rtl"] ul#tabs.nav-tabs > li {
  float: right;
}
[dir="rtl"] ul#tabs.nav.nav-tabs {
  padding-right: 0;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons .pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .list_toolbar .col-sm-4,
[dir="rtl"] .list_toolbar .col-sm-8 {
  float: right;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: text-bottom;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
[dir="rtl"] .list_item > div input {
  margin-right: 0;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_modified {
  margin-right: 7px;
  margin-left: 7px;
}
[dir="rtl"] .item_modified.pull-right {
  float: left !important;
  float: left;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
[dir="rtl"] .item_buttons.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .item_buttons .kernel-name {
  margin-left: 7px;
  float: right;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
.sort_button {
  display: inline-block;
  padding-left: 7px;
}
[dir="rtl"] .sort_button.pull-right {
  float: left !important;
  float: left;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
[dir="rtl"] #button-select-all.btn {
  float: right ;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
  margin-top: 2px;
  height: 16px;
}
[dir="rtl"] #select-all.pull-left {
  float: right !important;
  float: right;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.fa-pull-left {
  margin-right: .3em;
}
.folder_icon:before.fa-pull-right {
  margin-left: .3em;
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.fa-pull-left {
  margin-right: .3em;
}
.file_icon:before.fa-pull-right {
  margin-left: .3em;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
#new-menu .dropdown-header {
  font-size: 10px;
  border-bottom: 1px solid #e5e5e5;
  padding: 0 0 3px;
  margin: -3px 20px 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.move-button {
  display: none;
}
.download-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
.CodeMirror-dialog {
  background-color: #fff;
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI escape sequences */
/* The color values are a mix of
   http://www.xcolors.net/dl/baskerville-ivorylight and
   http://www.xcolors.net/dl/euphrasia */
.ansi-black-fg {
  color: #3E424D;
}
.ansi-black-bg {
  background-color: #3E424D;
}
.ansi-black-intense-fg {
  color: #282C36;
}
.ansi-black-intense-bg {
  background-color: #282C36;
}
.ansi-red-fg {
  color: #E75C58;
}
.ansi-red-bg {
  background-color: #E75C58;
}
.ansi-red-intense-fg {
  color: #B22B31;
}
.ansi-red-intense-bg {
  background-color: #B22B31;
}
.ansi-green-fg {
  color: #00A250;
}
.ansi-green-bg {
  background-color: #00A250;
}
.ansi-green-intense-fg {
  color: #007427;
}
.ansi-green-intense-bg {
  background-color: #007427;
}
.ansi-yellow-fg {
  color: #DDB62B;
}
.ansi-yellow-bg {
  background-color: #DDB62B;
}
.ansi-yellow-intense-fg {
  color: #B27D12;
}
.ansi-yellow-intense-bg {
  background-color: #B27D12;
}
.ansi-blue-fg {
  color: #208FFB;
}
.ansi-blue-bg {
  background-color: #208FFB;
}
.ansi-blue-intense-fg {
  color: #0065CA;
}
.ansi-blue-intense-bg {
  background-color: #0065CA;
}
.ansi-magenta-fg {
  color: #D160C4;
}
.ansi-magenta-bg {
  background-color: #D160C4;
}
.ansi-magenta-intense-fg {
  color: #A03196;
}
.ansi-magenta-intense-bg {
  background-color: #A03196;
}
.ansi-cyan-fg {
  color: #60C6C8;
}
.ansi-cyan-bg {
  background-color: #60C6C8;
}
.ansi-cyan-intense-fg {
  color: #258F8F;
}
.ansi-cyan-intense-bg {
  background-color: #258F8F;
}
.ansi-white-fg {
  color: #C5C1B4;
}
.ansi-white-bg {
  background-color: #C5C1B4;
}
.ansi-white-intense-fg {
  color: #A1A6B2;
}
.ansi-white-intense-bg {
  background-color: #A1A6B2;
}
.ansi-default-inverse-fg {
  color: #FFFFFF;
}
.ansi-default-inverse-bg {
  background-color: #000000;
}
.ansi-bold {
  font-weight: bold;
}
.ansi-underline {
  text-decoration: underline;
}
/* The following styles are deprecated an will be removed in a future version */
.ansibold {
  font-weight: bold;
}
.ansi-inverse {
  outline: 0.5px dotted;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  position: relative;
  overflow: visible;
}
div.cell:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: transparent;
}
div.cell.jupyter-soft-selected {
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected,
div.cell.selected.jupyter-soft-selected {
  border-color: #ababab;
}
div.cell.selected:before,
div.cell.selected.jupyter-soft-selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #42A5F5;
}
@media print {
  div.cell.selected,
  div.cell.selected.jupyter-soft-selected {
    border-color: transparent;
  }
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
}
.edit_mode div.cell.selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #66BB6A;
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  /* Note that this should set vertical padding only, since CodeMirror assumes
       that horizontal padding will be set on CodeMirror pre */
  padding: 0.4em 0;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. This sets horizontal padding only,
    use .CodeMirror-lines for vertical */
  padding: 0 0.4em;
  border: 0;
  border-radius: 0;
}
.CodeMirror-cursor {
  border-left: 1.4px solid black;
}
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .CodeMirror-cursor {
    border-left: 2px solid black;
  }
}
@media screen and (min-width: 4320px) {
  .CodeMirror-cursor {
    border-left: 4px solid black;
  }
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
div.output_area .mglyph > img {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 1px 0 1px 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul:not(.list-inline),
.rendered_html ol:not(.list-inline) {
  padding-left: 2em;
}
.rendered_html ul {
  list-style: disc;
}
.rendered_html ul ul {
  list-style: square;
  margin-top: 0;
}
.rendered_html ul ul ul {
  list-style: circle;
}
.rendered_html ol {
  list-style: decimal;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin-top: 0;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
  padding: 0px;
  background-color: #fff;
}
.rendered_html code {
  background-color: #eff0f1;
}
.rendered_html p code {
  padding: 1px 5px;
}
.rendered_html pre code {
  background-color: #fff;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  color: #000;
  font-size: 100%;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-collapse: collapse;
  border-spacing: 0;
  color: black;
  font-size: 12px;
  table-layout: fixed;
}
.rendered_html thead {
  border-bottom: 1px solid black;
  vertical-align: bottom;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  text-align: right;
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html tbody tr:nth-child(odd) {
  background: #f5f5f5;
}
.rendered_html tbody tr:hover {
  background: rgba(66, 165, 245, 0.2);
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
.rendered_html .alert {
  margin-bottom: initial;
}
.rendered_html * + .alert {
  margin-top: 1em;
}
[dir="rtl"] .rendered_html p {
  text-align: right;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.rendered .rendered_html tr,
.text_cell.rendered .rendered_html th,
.text_cell.rendered .rendered_html td {
  max-width: none;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.text_cell .dropzone .input_area {
  border: 2px dashed #bababa;
  margin: -1px;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
.jupyter-keybindings {
  padding: 1px;
  line-height: 24px;
  border-bottom: 1px solid gray;
}
.jupyter-keybindings input {
  margin: 0;
  padding: 0;
  border: none;
}
.jupyter-keybindings i {
  padding: 6px;
}
.well code {
  background-color: #ffffff;
  border-color: #ababab;
  border-width: 1px;
  border-style: solid;
  padding: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.tags_button_container {
  width: 100%;
  display: flex;
}
.tag-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  overflow: hidden;
  position: relative;
}
.tag-container > * {
  margin: 0 4px;
}
.remove-tag-btn {
  margin-left: 4px;
}
.tags-input {
  display: flex;
}
.cell-tag:last-child:after {
  content: "";
  position: absolute;
  right: 0;
  width: 40px;
  height: 100%;
  /* Fade to background color of cell toolbar */
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #EEE);
}
.tags-input > * {
  margin-left: 4px;
}
.cell-tag,
.tags-input input,
.tags-input button {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  box-shadow: none;
  width: inherit;
  font-size: inherit;
  height: 22px;
  line-height: 22px;
  padding: 0px 4px;
  display: inline-block;
}
.cell-tag:focus,
.tags-input input:focus,
.tags-input button:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.cell-tag::-moz-placeholder,
.tags-input input::-moz-placeholder,
.tags-input button::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.cell-tag:-ms-input-placeholder,
.tags-input input:-ms-input-placeholder,
.tags-input button:-ms-input-placeholder {
  color: #999;
}
.cell-tag::-webkit-input-placeholder,
.tags-input input::-webkit-input-placeholder,
.tags-input button::-webkit-input-placeholder {
  color: #999;
}
.cell-tag::-ms-expand,
.tags-input input::-ms-expand,
.tags-input button::-ms-expand {
  border: 0;
  background-color: transparent;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
.cell-tag[readonly],
.tags-input input[readonly],
.tags-input button[readonly],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  background-color: #eeeeee;
  opacity: 1;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  cursor: not-allowed;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button {
  height: auto;
}
select.cell-tag,
select.tags-input input,
select.tags-input button {
  height: 30px;
  line-height: 30px;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button,
select[multiple].cell-tag,
select[multiple].tags-input input,
select[multiple].tags-input button {
  height: auto;
}
.cell-tag,
.tags-input button {
  padding: 0px 4px;
}
.cell-tag {
  background-color: #fff;
  white-space: nowrap;
}
.tags-input input[type=text]:focus {
  outline: none;
  box-shadow: none;
  border-color: #ccc;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
[dir="rtl"] #kernel_logo_widget {
  float: left !important;
  float: left;
}
.modal .modal-body .move-path {
  display: flex;
  flex-direction: row;
  justify-content: space;
  align-items: center;
}
.modal .modal-body .move-path .server-root {
  padding-right: 20px;
}
.modal .modal-body .move-path .path-input {
  flex: 1;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
[dir="rtl"] #menubar .navbar-toggle {
  float: right;
}
[dir="rtl"] #menubar .navbar-collapse {
  clear: right;
}
[dir="rtl"] #menubar .navbar-nav {
  float: right;
}
[dir="rtl"] #menubar .nav {
  padding-right: 0px;
}
[dir="rtl"] #menubar .navbar-nav > li {
  float: right;
}
[dir="rtl"] #menubar .navbar-right {
  float: left !important;
}
[dir="rtl"] ul.dropdown-menu {
  text-align: right;
  left: auto;
}
[dir="rtl"] ul#new-menu.dropdown-menu {
  right: auto;
  left: 0;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
[dir="rtl"] i.menu-icon.pull-right {
  float: left !important;
  float: left;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
[dir="rtl"] ul#help_menu li a {
  padding-left: 2.2em;
}
[dir="rtl"] ul#help_menu li a i {
  margin-right: 0;
  margin-left: -1.2em;
}
[dir="rtl"] ul#help_menu li a i.pull-right {
  float: left !important;
  float: left;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
[dir="rtl"] .dropdown-submenu > .dropdown-menu {
  right: 100%;
  margin-right: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.fa-pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.fa-pull-right {
  margin-left: .3em;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
[dir="rtl"] .dropdown-submenu > a:after {
  float: left;
  content: "\f0d9";
  margin-right: 0;
  margin-left: -10px;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
[dir="rtl"] #notification_area {
  float: left !important;
  float: left;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] .indicator_area {
  float: left !important;
  float: left;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
[dir="rtl"] #kernel_indicator {
  float: left !important;
  float: left;
  border-left: 0;
  border-right: 1px solid;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] #modal_indicator {
  float: left !important;
  float: left;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for 
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  height: 30px;
  margin-top: 4px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  width: 50%;
  flex: 1;
}
span.save_widget span.filename {
  height: 100%;
  line-height: 1em;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
[dir="rtl"] span.save_widget.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] span.save_widget span.filename {
  margin-left: 0;
  margin-right: 16px;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
  white-space: nowrap;
  padding: 0 5px;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
    padding: 0 0 0 5px;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
.toolbar-btn-label {
  margin-left: 6px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
[dir="rtl"] .btn-group > .btn,
.btn-group-vertical > .btn {
  float: right;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
[dir="rtl"] ul.typeahead-list i {
  margin-left: 0;
  margin-right: -10px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
ul.typeahead-list  > li > a.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .typeahead-list {
  text-align: right;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  min-width: 20px;
  color: transparent;
}
[dir="rtl"] .no-shortcut.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .command-shortcut.pull-right {
  float: left !important;
  float: left;
}
.command-shortcut:before {
  content: "(command mode)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
[dir="rtl"] .edit-shortcut.pull-right {
  float: left !important;
  float: left;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
[dir="ltr"] #find-and-replace .input-group-btn + .form-control {
  border-left: none;
}
[dir="rtl"] #find-and-replace .input-group-btn + .form-control {
  border-right: none;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  } 
  div.output_wrapper { 
    display: block;
    page-break-inside: avoid; 
  }
  div.output { 
    display: block;
    page-break-inside: avoid; 
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Do-Video-Game-Descriptions-Help-Determine-a-Game's-Overall-Rating?">Do Video Game Descriptions Help Determine a Game's Overall Rating?<a class="anchor-link" href="#Do-Video-Game-Descriptions-Help-Determine-a-Game's-Overall-Rating?">&#182;</a></h1><p><strong>by: J.Roberge</strong></p>
<p>How do descriptions effect a video game's performance. Do high ranking video games have a more detailed description and most importantly, can this description be used to predict a video games performance? This analysis will utilize a previously curated dataset that has tokenized the description of 10,000 video games which were found on itunes. The issues going forward will be how to most effectively deal with an extremely sparse matrix and which type of model performs best on this type of dataset. This analysis will be broken down into three sections: section One, will deal with outlier detection; section two, will reduce the dimensions; and section 3 will fit the models. <br><br>
<em>Please note, that the way I fit these models is not 'correct' (you shouldn't touch your y_test until the very end), but method used was only employed do to the constraints of the assignment (which can be found <a href="https://jwr1015.github.io/links/Quiz_2.htm">here</a>)</em></p>
<p><strong>Table of Contents</strong></p>
<p><ul>
    <li><a href="#sec_1">Outlier Detection</a></li>
    <li><a href="#sec_2">Dimension Reduction</a></li>
    <li><a href="#sec_3">Model Training</a></li>
        <ul>
            <li><a href="#part_3_1">Model Dictionary</a></li>
            <li><a href="#part_3_2">Model Function</a></li>
            <li><a href="#part_3_3">All Possible models</a></li>
            <li><a href="#part_3_4">All Possible models with Feature Selection</a></li>
        </ul></p>
<ul>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### importing dependencies ####</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="c1">### dimension reduction teckniques</span>
<span class="kn">from</span> <span class="nn">sklearn.decomposition</span> <span class="k">import</span> <span class="n">PCA</span>
<span class="kn">from</span> <span class="nn">sklearn.decomposition</span> <span class="k">import</span> <span class="n">SparsePCA</span>
<span class="kn">from</span> <span class="nn">sklearn.manifold</span> <span class="k">import</span> <span class="n">TSNE</span>


<span class="c1">### Validation techniques/ search techniques</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">f1_score</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">accuracy_score</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">GridSearchCV</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">train_test_split</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">ParameterGrid</span>


<span class="c1">## models </span>
<span class="kn">from</span> <span class="nn">sklearn.neighbors</span> <span class="k">import</span> <span class="n">KNeighborsClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="k">import</span> <span class="n">RandomForestClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="k">import</span> <span class="n">GradientBoostingClassifier</span>
<span class="kn">from</span> <span class="nn">xgboost</span> <span class="k">import</span> <span class="n">XGBClassifier</span>

<span class="c1">### outlier</span>
<span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="k">import</span> <span class="n">StandardScaler</span>
<span class="kn">from</span> <span class="nn">sklearn.covariance</span> <span class="k">import</span> <span class="n">EllipticEnvelope</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="k">import</span> <span class="n">IsolationForest</span>
<span class="kn">from</span> <span class="nn">sklearn.neighbors</span> <span class="k">import</span> <span class="n">LocalOutlierFactor</span>

<span class="c1">### plotting</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">from</span> <span class="nn">mpl_toolkits.mplot3d</span> <span class="k">import</span> <span class="n">Axes3D</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>

<span class="c1">### feature selection</span>
<span class="kn">from</span> <span class="nn">xgboost</span> <span class="k">import</span> <span class="n">plot_importance</span>
<span class="kn">from</span> <span class="nn">sklearn.feature_selection</span> <span class="k">import</span> <span class="n">SelectKBest</span><span class="p">,</span> <span class="n">chi2</span><span class="p">,</span> <span class="n">f_regression</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### reading in Data Frame</span>
<span class="o">%</span><span class="k">cd</span> &quot;C:\Users\jwr17\OneDrive - University of New Hampshire\machine learning\quiz_2\Quiz 2 ML&quot;
<span class="c1">### importing data sets ###</span>
<span class="n">df_token</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;Apple1000games.csv&quot;</span><span class="p">,</span> <span class="n">index_col</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>

<span class="n">df_des</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;apple1000new.csv&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>C:\Users\jwr17\OneDrive - University of New Hampshire\machine learning\quiz_2\Quiz 2 ML
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### mapping to categorical </span>

<span class="c1"># df_des</span>
<span class="n">cuts</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">cut</span><span class="p">(</span><span class="n">df_des</span><span class="p">[</span><span class="s1">&#39;Average User Rating&#39;</span><span class="p">],</span> <span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">,</span> <span class="mf">2.99</span><span class="p">,</span> <span class="mf">3.99</span><span class="p">,</span> <span class="mf">5.5</span><span class="p">],</span> <span class="n">labels</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Poor&#39;</span><span class="p">,</span> <span class="s1">&#39;Good&#39;</span><span class="p">,</span> <span class="s2">&quot;Great&quot;</span><span class="p">])</span>

<span class="c1"># adding cuts to the description csv</span>
<span class="n">df_des</span><span class="p">[</span><span class="s1">&#39;User_cat&#39;</span><span class="p">]</span><span class="o">=</span><span class="n">cuts</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### checking for missing values</span>
<span class="n">df_des</span><span class="o">.</span><span class="n">User_cat</span><span class="o">.</span><span class="n">isna</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>

<span class="c1">### im going to impute missing values to Poor do to the size of the</span>
<span class="c1">### data set (loosing 100 rows is significant and i believe it is safe to assume that games without a ratting are more than lickley poor)</span>
<span class="n">df_des</span><span class="p">[</span><span class="s1">&#39;User_cat&#39;</span><span class="p">]</span><span class="o">=</span><span class="n">df_des</span><span class="o">.</span><span class="n">User_cat</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="s1">&#39;Poor&#39;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Shape fo description file&quot;</span><span class="p">,</span> <span class="n">df_des</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df_des</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">))</span>

<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="se">\n</span><span class="s2">Shape fo token file&quot;</span><span class="p">,</span> <span class="n">df_token</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df_token</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Shape fo description file (1000, 29)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Icon URL</th>
      <th>Average User Rating</th>
      <th>User Rating Count</th>
      <th>Price</th>
      <th>In-app Purchases</th>
      <th>Description</th>
      <th>Developer</th>
      <th>Age Rating</th>
      <th>Languages</th>
      <th>...</th>
      <th>Unnamed: 19</th>
      <th>Unnamed: 20</th>
      <th>Unnamed: 21</th>
      <th>Unnamed: 22</th>
      <th>Unnamed: 23</th>
      <th>Unnamed: 24</th>
      <th>Unnamed: 25</th>
      <th>Unnamed: 26</th>
      <th>Unnamed: 27</th>
      <th>User_cat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sudoku</td>
      <td>https://is2-ssl.mzstatic.com/image/thumb/Purpl...</td>
      <td>4.0</td>
      <td>3553.0</td>
      <td>2.99</td>
      <td>NaN</td>
      <td>Join over 21,000,000 of our fans and download ...</td>
      <td>Mighty Mighty Good Games</td>
      <td>4+</td>
      <td>DA, NL, EN, FI, FR, DE, IT, JA, KO, NB, PL, PT...</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Great</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Reversi</td>
      <td>https://is4-ssl.mzstatic.com/image/thumb/Purpl...</td>
      <td>3.5</td>
      <td>284.0</td>
      <td>1.99</td>
      <td>NaN</td>
      <td>The classic game of Reversi, also known as Oth...</td>
      <td>Kiss The Machine</td>
      <td>4+</td>
      <td>EN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Good</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Morocco</td>
      <td>https://is5-ssl.mzstatic.com/image/thumb/Purpl...</td>
      <td>3.0</td>
      <td>8376.0</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>Play the classic strategy game Othello (also k...</td>
      <td>Bayou Games</td>
      <td>4+</td>
      <td>EN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Good</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 29 columns</p>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>
Shape fo token file (1000, 2000)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>abil</th>
      <th>abl</th>
      <th>abov</th>
      <th>absolut</th>
      <th>access</th>
      <th>accomplish</th>
      <th>accord</th>
      <th>account</th>
      <th>accur</th>
      <th>ace</th>
      <th>...</th>
      <th>you\u2019r</th>
      <th>you\u2019v</th>
      <th>young</th>
      <th>youtub</th>
      <th>z</th>
      <th>zero</th>
      <th>zingoplaylit</th>
      <th>zombi</th>
      <th>zone</th>
      <th>zoom</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 2000 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div id="sec_1"></div><h1 id="Section-One:-Outliers-Detection">Section One: Outliers Detection<a class="anchor-link" href="#Section-One:-Outliers-Detection">&#182;</a></h1><p>I'm currently at a crossroads with outlier detection. This is a sparse matrixs and I worry that a cell
with any sort of value in it may be considered an outlier. In order to ensure I'm not just getting rid of values good data I will
sort thorough what is considered an outlier.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#### outlier Detection ####</span>

<span class="c1"># I am currently at a corssroads with outlier detection. Im a little worried about the data being sparse and trying to run outlier</span>
<span class="c1"># analysis on it. </span>

<span class="c1">### standardization ####</span>
<span class="n">standard</span><span class="o">=</span><span class="n">StandardScaler</span><span class="p">()</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">df_token</span><span class="p">)</span>
<span class="n">df_token</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">standard</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="n">df_token</span><span class="o">.</span><span class="n">columns</span><span class="p">)</span>

<span class="c1">### mahalanobis ###</span>
<span class="n">clf</span> <span class="o">=</span> <span class="n">EllipticEnvelope</span><span class="p">(</span><span class="n">contamination</span><span class="o">=.</span><span class="mi">05</span><span class="p">,</span><span class="n">random_state</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
<span class="n">clf</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">df_token</span><span class="p">)</span>
<span class="n">Envelope_prediction</span><span class="o">=</span> <span class="n">clf</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">df_token</span><span class="p">)</span>
<span class="n">envelope_scroes</span><span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">clf</span><span class="o">.</span><span class="n">decision_function</span><span class="p">(</span><span class="n">df_token</span><span class="p">))</span> 

<span class="c1">### isolation forest ###</span>
<span class="n">clf</span> <span class="o">=</span> <span class="n">IsolationForest</span><span class="p">(</span> <span class="n">n_estimators</span><span class="o">=</span><span class="mi">400</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span> <span class="n">n_jobs</span><span class="o">=-</span><span class="mi">1</span><span class="p">,</span> <span class="n">contamination</span><span class="o">=.</span><span class="mi">05</span><span class="p">)</span>
<span class="n">clf</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">df_token</span><span class="p">)</span>
<span class="n">outliers</span><span class="o">=</span><span class="n">clf</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">df_token</span><span class="p">)</span>
<span class="n">TagRemovePreprocessor</span><span class="o">.</span><span class="n">remove_all_outputs_tags</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>After reviewing the outliers it seems that the mahalanobis and isolation forest performed well. From here I will drop everything that it considered to be an outlier.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#### dropping outliers ###</span>
<span class="n">outliers_master</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">Envelope_prediction</span><span class="p">),</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">outliers</span><span class="p">)],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">outliers_master</span><span class="o">.</span><span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;mahalanobis&#39;</span><span class="p">,</span> <span class="s1">&#39;isolation&#39;</span><span class="p">]</span>
<span class="n">outliers_master</span><span class="p">[</span><span class="n">outliers_master</span><span class="o">.</span><span class="n">isolation</span><span class="o">&lt;</span><span class="mi">1</span><span class="p">]</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The shape of the outlier dataframe: &quot;</span><span class="p">,</span><span class="n">outliers_master</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">outliers_master</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">))</span>

<span class="c1">### Droping outliers</span>
<span class="n">df_token</span><span class="o">=</span><span class="n">df_token</span><span class="p">[(</span><span class="n">outliers_master</span><span class="o">.</span><span class="n">isolation</span><span class="o">==</span><span class="mi">1</span><span class="p">)</span> <span class="o">|</span> <span class="p">(</span><span class="n">outliers_master</span><span class="o">.</span><span class="n">mahalanobis</span> <span class="o">==</span><span class="mi">1</span><span class="p">)]</span>
<span class="n">df_des</span><span class="o">=</span><span class="n">df_des</span><span class="p">[(</span><span class="n">outliers_master</span><span class="o">.</span><span class="n">isolation</span><span class="o">==</span><span class="mi">1</span><span class="p">)</span> <span class="o">|</span> <span class="p">(</span><span class="n">outliers_master</span><span class="o">.</span><span class="n">mahalanobis</span> <span class="o">==</span><span class="mi">1</span><span class="p">)]</span>

<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The shape of the token dataframe after outlier drop:&quot;</span><span class="p">,</span> <span class="n">df_token</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df_token</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">))</span>

<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;The shape of the description dataframe  after outlier drop:&quot;</span><span class="p">,</span> <span class="n">df_des</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df_des</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>The shape of the outlier dataframe:  (1000, 2)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mahalanobis</th>
      <th>isolation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>The shape of the token dataframe after outlier drop: (991, 2000)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>abil</th>
      <th>abl</th>
      <th>abov</th>
      <th>absolut</th>
      <th>access</th>
      <th>accomplish</th>
      <th>accord</th>
      <th>account</th>
      <th>accur</th>
      <th>ace</th>
      <th>...</th>
      <th>you\u2019r</th>
      <th>you\u2019v</th>
      <th>young</th>
      <th>youtub</th>
      <th>z</th>
      <th>zero</th>
      <th>zingoplaylit</th>
      <th>zombi</th>
      <th>zone</th>
      <th>zoom</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.233203</td>
      <td>-0.251087</td>
      <td>-0.152507</td>
      <td>-0.162088</td>
      <td>-0.220433</td>
      <td>-0.110208</td>
      <td>-0.112333</td>
      <td>-0.171306</td>
      <td>-0.105463</td>
      <td>-0.085064</td>
      <td>...</td>
      <td>-0.20989</td>
      <td>-0.143463</td>
      <td>-0.095298</td>
      <td>-0.153432</td>
      <td>-0.054313</td>
      <td>-0.096659</td>
      <td>-0.031639</td>
      <td>-0.118664</td>
      <td>-0.067919</td>
      <td>-0.168645</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.233203</td>
      <td>-0.251087</td>
      <td>-0.152507</td>
      <td>-0.162088</td>
      <td>-0.220433</td>
      <td>-0.110208</td>
      <td>-0.112333</td>
      <td>-0.171306</td>
      <td>-0.105463</td>
      <td>-0.085064</td>
      <td>...</td>
      <td>-0.20989</td>
      <td>-0.143463</td>
      <td>-0.095298</td>
      <td>-0.153432</td>
      <td>-0.054313</td>
      <td>-0.096659</td>
      <td>-0.031639</td>
      <td>-0.118664</td>
      <td>-0.067919</td>
      <td>-0.168645</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.233203</td>
      <td>-0.251087</td>
      <td>-0.152507</td>
      <td>-0.162088</td>
      <td>-0.220433</td>
      <td>-0.110208</td>
      <td>-0.112333</td>
      <td>-0.171306</td>
      <td>-0.105463</td>
      <td>-0.085064</td>
      <td>...</td>
      <td>-0.20989</td>
      <td>-0.143463</td>
      <td>-0.095298</td>
      <td>-0.153432</td>
      <td>-0.054313</td>
      <td>-0.096659</td>
      <td>-0.031639</td>
      <td>-0.118664</td>
      <td>-0.067919</td>
      <td>-0.168645</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 2000 columns</p>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>The shape of the description dataframe  after outlier drop: (991, 29)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Icon URL</th>
      <th>Average User Rating</th>
      <th>User Rating Count</th>
      <th>Price</th>
      <th>In-app Purchases</th>
      <th>Description</th>
      <th>Developer</th>
      <th>Age Rating</th>
      <th>Languages</th>
      <th>...</th>
      <th>Unnamed: 19</th>
      <th>Unnamed: 20</th>
      <th>Unnamed: 21</th>
      <th>Unnamed: 22</th>
      <th>Unnamed: 23</th>
      <th>Unnamed: 24</th>
      <th>Unnamed: 25</th>
      <th>Unnamed: 26</th>
      <th>Unnamed: 27</th>
      <th>User_cat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sudoku</td>
      <td>https://is2-ssl.mzstatic.com/image/thumb/Purpl...</td>
      <td>4.0</td>
      <td>3553.0</td>
      <td>2.99</td>
      <td>NaN</td>
      <td>Join over 21,000,000 of our fans and download ...</td>
      <td>Mighty Mighty Good Games</td>
      <td>4+</td>
      <td>DA, NL, EN, FI, FR, DE, IT, JA, KO, NB, PL, PT...</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Great</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Reversi</td>
      <td>https://is4-ssl.mzstatic.com/image/thumb/Purpl...</td>
      <td>3.5</td>
      <td>284.0</td>
      <td>1.99</td>
      <td>NaN</td>
      <td>The classic game of Reversi, also known as Oth...</td>
      <td>Kiss The Machine</td>
      <td>4+</td>
      <td>EN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Good</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Morocco</td>
      <td>https://is5-ssl.mzstatic.com/image/thumb/Purpl...</td>
      <td>3.0</td>
      <td>8376.0</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>Play the classic strategy game Othello (also k...</td>
      <td>Bayou Games</td>
      <td>4+</td>
      <td>EN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Good</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 29 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div id="sec_2"></div><h1 id="Section-Two:-Dimension-Reduction">Section Two: Dimension Reduction<a class="anchor-link" href="#Section-Two:-Dimension-Reduction">&#182;</a></h1><p>Currently there is around 10,00 features in this dataset, and these features are extremely sparse. In order to get a working model, dimension reduction must take place. I will employ three dimension reduction techniques: first, I will use Principle Component Analysis and I will keep 90% of the variation; Second, I will employ Sparse PCA and keep the top 20 Components; and third I will use T_SNE and keep three components.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## pca&#39;s</span>
<span class="n">pca</span><span class="o">=</span><span class="n">PCA</span><span class="p">(</span><span class="mf">0.9</span><span class="p">)</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">df_token</span><span class="p">)</span>

<span class="n">master</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">pca</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;PC_&#39;</span><span class="o">+</span><span class="nb">str</span><span class="p">(</span><span class="n">i</span><span class="p">)</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="n">pca</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">1</span><span class="p">]</span><span class="o">+</span><span class="mi">1</span><span class="p">)])</span>

<span class="c1">## sparse pca</span>
<span class="n">sparse</span><span class="o">=</span><span class="n">SparsePCA</span><span class="p">(</span><span class="n">n_components</span><span class="o">=</span><span class="mi">20</span><span class="p">,</span> <span class="n">n_jobs</span><span class="o">=-</span><span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">df_token</span><span class="p">)</span>
<span class="n">sparse</span><span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">sparse</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Sparse_&#39;</span><span class="o">+</span><span class="nb">str</span><span class="p">(</span><span class="n">i</span><span class="p">)</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">21</span><span class="p">)])</span>
<span class="n">master</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">sparse</span><span class="p">,</span><span class="n">master</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="k">del</span><span class="p">(</span><span class="n">sparse</span><span class="p">)</span>
<span class="k">del</span><span class="p">(</span><span class="n">pca</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Shape of the reduced dimension df with sparse and pca&quot;</span><span class="p">,</span> <span class="n">master</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">master</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre>C:\Users\jwr17\Anaconda3\envs\PyhtonAndR\lib\site-packages\sklearn\decomposition\sparse_pca.py:170: DeprecationWarning: normalize_components=False is a backward-compatible setting that implements a non-standard definition of sparse PCA. This compatibility mode will be removed in 0.22.
  DeprecationWarning)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Shape of the reduced dimension df with sparse and pca (991, 458)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Sparse_1</th>
      <th>Sparse_2</th>
      <th>Sparse_3</th>
      <th>Sparse_4</th>
      <th>Sparse_5</th>
      <th>Sparse_6</th>
      <th>Sparse_7</th>
      <th>Sparse_8</th>
      <th>Sparse_9</th>
      <th>Sparse_10</th>
      <th>...</th>
      <th>PC_429</th>
      <th>PC_430</th>
      <th>PC_431</th>
      <th>PC_432</th>
      <th>PC_433</th>
      <th>PC_434</th>
      <th>PC_435</th>
      <th>PC_436</th>
      <th>PC_437</th>
      <th>PC_438</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.003111</td>
      <td>-0.007090</td>
      <td>-0.001605</td>
      <td>0.004124</td>
      <td>-0.003503</td>
      <td>0.001851</td>
      <td>-0.003369</td>
      <td>0.001227</td>
      <td>-0.000279</td>
      <td>0.031796</td>
      <td>...</td>
      <td>-0.020590</td>
      <td>0.021111</td>
      <td>0.321117</td>
      <td>1.142703</td>
      <td>-0.307474</td>
      <td>0.153247</td>
      <td>0.007989</td>
      <td>-0.026510</td>
      <td>-0.548945</td>
      <td>-0.393779</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.003174</td>
      <td>-0.001326</td>
      <td>0.000506</td>
      <td>0.008860</td>
      <td>-0.005468</td>
      <td>-0.008240</td>
      <td>-0.007486</td>
      <td>0.005104</td>
      <td>-0.004304</td>
      <td>0.015580</td>
      <td>...</td>
      <td>0.432841</td>
      <td>-1.572423</td>
      <td>-0.050012</td>
      <td>-3.641469</td>
      <td>-2.554754</td>
      <td>-0.282550</td>
      <td>-1.758610</td>
      <td>-1.931872</td>
      <td>1.902900</td>
      <td>-0.087452</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.002818</td>
      <td>-0.005823</td>
      <td>0.001213</td>
      <td>0.002864</td>
      <td>-0.001885</td>
      <td>-0.007623</td>
      <td>0.001609</td>
      <td>0.006572</td>
      <td>-0.000774</td>
      <td>0.018426</td>
      <td>...</td>
      <td>-1.541419</td>
      <td>-1.448775</td>
      <td>0.905741</td>
      <td>-0.183866</td>
      <td>1.045458</td>
      <td>0.302338</td>
      <td>-1.017309</td>
      <td>-0.331573</td>
      <td>1.140685</td>
      <td>-0.280409</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 458 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="T_SNE">T_SNE<a class="anchor-link" href="#T_SNE">&#182;</a></h4><p>After running through several interactions, and after doing some research I have decided to change the measuring metric on T_SNE from euclidean to cosine distance. According to some research, changing the distance measurement to cosine empirically performs better on a sparse matrices. Additionally, the plot does seems to be slightly better. (the plot will print outside of the notebook)</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[31]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### t_sne</span>
<span class="n">TSNE</span><span class="p">()</span>
<span class="n">X_embedding</span> <span class="o">=</span> <span class="n">TSNE</span><span class="p">(</span><span class="n">metric</span><span class="o">=</span><span class="s1">&#39;cosine&#39;</span><span class="p">,</span><span class="n">n_components</span><span class="o">=</span><span class="mi">3</span><span class="p">,</span> <span class="n">perplexity</span><span class="o">=</span><span class="mi">1000</span><span class="p">,</span> <span class="n">n_iter</span> <span class="o">=</span> <span class="mi">500</span><span class="p">,</span> <span class="n">learning_rate</span><span class="o">=</span><span class="mi">500</span><span class="p">)</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">df_token</span><span class="p">,)</span>

<span class="c1">### 3d Graph Prints outside notebook ###</span>
<span class="n">get_ipython</span><span class="p">()</span><span class="o">.</span><span class="n">run_line_magic</span><span class="p">(</span><span class="s1">&#39;matplotlib&#39;</span><span class="p">,</span> <span class="s1">&#39;inline&#39;</span><span class="p">)</span>
<span class="n">df_sne_3d</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">X_embedding</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;tsne_1&#39;</span><span class="p">,</span><span class="s2">&quot;tsne_2&quot;</span><span class="p">,</span><span class="s2">&quot;tsne_3&quot;</span><span class="p">])</span>
<span class="n">fig</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">()</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">fig</span><span class="o">.</span><span class="n">add_subplot</span><span class="p">(</span><span class="mi">111</span><span class="p">,</span> <span class="n">projection</span><span class="o">=</span><span class="s1">&#39;3d&#39;</span><span class="p">)</span>
<span class="n">color</span><span class="o">=</span><span class="p">[]</span>
<span class="k">for</span> <span class="n">a</span> <span class="ow">in</span> <span class="n">df_des</span><span class="p">[</span><span class="s1">&#39;User_cat&#39;</span><span class="p">]:</span>
    <span class="k">if</span> <span class="n">a</span><span class="o">==</span><span class="s1">&#39;Great&#39;</span><span class="p">:</span>
        <span class="n">color</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s1">&#39;green&#39;</span><span class="p">)</span>
    <span class="k">elif</span> <span class="n">a</span><span class="o">==</span><span class="s1">&#39;Good&#39;</span><span class="p">:</span>
        <span class="n">color</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s1">&#39;yellow&#39;</span><span class="p">)</span>
    <span class="k">elif</span> <span class="n">a</span><span class="o">==</span><span class="s1">&#39;Poor&#39;</span><span class="p">:</span>
        <span class="n">color</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s1">&#39;red&#39;</span><span class="p">)</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">color</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s1">&#39;NaN&#39;</span><span class="p">)</span>
<span class="n">ax</span><span class="o">.</span><span class="n">scatter3D</span><span class="p">(</span><span class="n">xs</span><span class="o">=</span><span class="n">df_sne_3d</span><span class="o">.</span><span class="n">tsne_1</span><span class="p">,</span> <span class="n">ys</span><span class="o">=</span><span class="n">df_sne_3d</span><span class="o">.</span><span class="n">tsne_2</span><span class="p">,</span> <span class="n">zs</span><span class="o">=</span><span class="n">df_sne_3d</span><span class="o">.</span><span class="n">tsne_3</span><span class="p">,</span><span class="n">c</span><span class="o">=</span><span class="n">color</span><span class="p">,</span> <span class="n">marker</span><span class="o">=</span><span class="s1">&#39;o&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[31]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;mpl_toolkits.mplot3d.art3d.Path3DCollection at 0x21507d88908&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### appending t-sne to master</span>
<span class="n">master</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">master</span><span class="p">,</span> <span class="n">df_sne_3d</span><span class="p">],</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Shape of the reduced dimension df with tsne, sparse and pca&quot;</span><span class="p">,</span> <span class="n">master</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">master</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">))</span>

<span class="c1">### Cleaning up my memory</span>
<span class="k">del</span><span class="p">(</span><span class="n">df_sne_3d</span><span class="p">,</span> <span class="n">cuts</span><span class="p">,</span> <span class="n">color</span><span class="p">,</span><span class="n">ax</span><span class="p">,</span><span class="n">fig</span><span class="p">,</span><span class="n">standard</span><span class="p">,</span><span class="n">outliers</span><span class="p">,</span><span class="n">outliers_master</span><span class="p">,</span><span class="n">Envelope_prediction</span><span class="p">,</span><span class="n">X_embedding</span><span class="p">,</span><span class="n">a</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Shape of the reduced dimension df with tsne, sparse and pca (991, 464)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Sparse_1</th>
      <th>Sparse_2</th>
      <th>Sparse_3</th>
      <th>Sparse_4</th>
      <th>Sparse_5</th>
      <th>Sparse_6</th>
      <th>Sparse_7</th>
      <th>Sparse_8</th>
      <th>Sparse_9</th>
      <th>Sparse_10</th>
      <th>...</th>
      <th>PC_435</th>
      <th>PC_436</th>
      <th>PC_437</th>
      <th>PC_438</th>
      <th>tsne_1</th>
      <th>tsne_2</th>
      <th>tsne_3</th>
      <th>tsne_1</th>
      <th>tsne_2</th>
      <th>tsne_3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.003111</td>
      <td>-0.007090</td>
      <td>-0.001605</td>
      <td>0.004124</td>
      <td>-0.003503</td>
      <td>0.001851</td>
      <td>-0.003369</td>
      <td>0.001227</td>
      <td>-0.000279</td>
      <td>0.031796</td>
      <td>...</td>
      <td>0.007989</td>
      <td>-0.026510</td>
      <td>-0.548945</td>
      <td>-0.393779</td>
      <td>-54.483097</td>
      <td>-7.862460</td>
      <td>-46.616386</td>
      <td>79.922234</td>
      <td>75.020866</td>
      <td>-11.045379</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.003174</td>
      <td>-0.001326</td>
      <td>0.000506</td>
      <td>0.008860</td>
      <td>-0.005468</td>
      <td>-0.008240</td>
      <td>-0.007486</td>
      <td>0.005104</td>
      <td>-0.004304</td>
      <td>0.015580</td>
      <td>...</td>
      <td>-1.758610</td>
      <td>-1.931872</td>
      <td>1.902900</td>
      <td>-0.087452</td>
      <td>40.230015</td>
      <td>29.511326</td>
      <td>42.572079</td>
      <td>-71.080284</td>
      <td>-10.586238</td>
      <td>-64.524429</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.002818</td>
      <td>-0.005823</td>
      <td>0.001213</td>
      <td>0.002864</td>
      <td>-0.001885</td>
      <td>-0.007623</td>
      <td>0.001609</td>
      <td>0.006572</td>
      <td>-0.000774</td>
      <td>0.018426</td>
      <td>...</td>
      <td>-1.017309</td>
      <td>-0.331573</td>
      <td>1.140685</td>
      <td>-0.280409</td>
      <td>13.820995</td>
      <td>-53.411522</td>
      <td>-69.516098</td>
      <td>1.341141</td>
      <td>0.462629</td>
      <td>34.949226</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 464 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The following graph shows the total count of all target values. I made this graph to see the balance of the classes. In all, I would say that the class balance is pretty good, and therefor I will not pursue any type of re-sampling techniques.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[458]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### seeing how the classes balance out</span>

<span class="n">get_ipython</span><span class="p">()</span><span class="o">.</span><span class="n">run_line_magic</span><span class="p">(</span><span class="s1">&#39;matplotlib&#39;</span><span class="p">,</span> <span class="s1">&#39;inline&#39;</span><span class="p">)</span>
<span class="n">sns</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">df_des</span><span class="p">[</span><span class="s1">&#39;User_cat&#39;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[458]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a8f66f6788&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAYUAAAEHCAYAAABBW1qbAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjEsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy8QZhcZAAAQp0lEQVR4nO3de6xlZXnH8e9PQAFvgBysZaBDdaxSoagTQWlNC8aAtjIqGA0oIi3VgpfYitTetNpUY1qqhGqpyE1btKAyGqNQLqJWLsNVLhqnpMIUCoPgFcVin/6x3/NyHM7MbGHW3oc5309ycvZ61rv3PDsr8DvvWmu/O1WFJEkAj5h2A5KkhcNQkCR1hoIkqTMUJEmdoSBJ6racdgMPxY477lhLly6ddhuS9LByxRVX3FlVM/Pte1iHwtKlS1m1atW025Ckh5Uk317fPk8fSZI6Q0GS1BkKkqTOUJAkdYaCJKkzFCRJnaEgSeoMBUlSZyhIkrqH9SeaJS18+56w77RbWBS++savbpLXcaYgSeoMBUlSZyhIkjpDQZLUGQqSpM5QkCR1hoIkqTMUJEmdoSBJ6gwFSVJnKEiSOkNBktQNHgpJtkhyVZLPte3dklya5FtJPpHkka3+qLa9uu1fOnRvkqSfN4mZwpuBG+dsvw84vqqWAXcDR7b6kcDdVfUU4Pg2TpI0QYOGQpIlwIuBj7TtAPsBZ7UhpwEr2uOD2jZt//5tvCRpQoaeKfwDcCzwf237CcB3q+q+tr0G2Lk93hm4BaDt/14b/3OSHJVkVZJVa9euHbJ3SVp0BguFJL8L3FFVV8wtzzO0xth3f6HqpKpaXlXLZ2ZmNkGnkqRZQ37z2r7AS5K8CNgaeByjmcN2SbZss4ElwK1t/BpgF2BNki2BxwN3DdifJGkdg80UqupPq2pJVS0FXglcUFWHAhcCB7dhhwPntMcr2zZt/wVV9YCZgiRpONP4nMLbgbcmWc3omsHJrX4y8IRWfytw3BR6k6RFbcjTR11VXQRc1B7fBDxnnjE/AQ6ZRD+SpPn5iWZJUmcoSJI6Q0GS1BkKkqTOUJAkdYaCJKkzFCRJnaEgSeoMBUlSZyhIkjpDQZLUGQqSpM5QkCR1hoIkqTMUJEmdoSBJ6gwFSVJnKEiSOkNBktQZCpKkzlCQJHWGgiSpMxQkSZ2hIEnqDAVJUmcoSJI6Q0GS1BkKkqRuy2k3II3j5r/eY9otbPZ2/cuvT7sFLQDOFCRJnaEgSeoMBUlSZyhIkjpDQZLUGQqSpM5QkCR1hoIkqTMUJEmdoSBJ6gYLhSRbJ7ksyTVJrk/yrlbfLcmlSb6V5BNJHtnqj2rbq9v+pUP1Jkma35AzhXuB/arqN4C9gAOS7AO8Dzi+qpYBdwNHtvFHAndX1VOA49s4SdIEDRYKNfLDtrlV+ylgP+CsVj8NWNEeH9S2afv3T5Kh+pMkPdCg1xSSbJHkauAO4DzgP4HvVtV9bcgaYOf2eGfgFoC2/3vAE+Z5zaOSrEqyau3atUO2L0mLzqChUFU/q6q9gCXAc4Cnzzes/Z5vVlAPKFSdVFXLq2r5zMzMpmtWkjSZu4+q6rvARcA+wHZJZr/HYQlwa3u8BtgFoO1/PHDXJPqTJI0MeffRTJLt2uNtgBcANwIXAge3YYcD57THK9s2bf8FVfWAmYIkaThDfvPak4DTkmzBKHw+WVWfS3IDcGaS9wBXASe38ScDZyRZzWiG8MoBe5MkzWOwUKiqa4FnzlO/idH1hXXrPwEOGaofSdLG+YlmSVJnKEiSOkNBktQZCpKkzlCQJHWGgiSpMxQkSZ2hIEnqDAVJUmcoSJI6Q0GS1BkKkqTOUJAkdYaCJKkzFCRJnaEgSeoMBUlSN1YoJDl/nJok6eFtg1/HmWRrYFtgxyTbA2m7Hgf88sC9SZImbGPf0fyHwFsYBcAV3B8K3wdOHLAvSdIUbDAUquoDwAeSvLGqTphQT5KkKdnYTAGAqjohyfOApXOfU1WnD9SXJGkKxgqFJGcATwauBn7WygUYCpK0GRkrFIDlwO5VVUM2I0marnE/p3Ad8EtDNiJJmr5xZwo7AjckuQy4d7ZYVS8ZpCtJ0lSMGwrvHLIJSdLCMO7dR18auhFJ0vSNe/fRDxjdbQTwSGAr4EdV9bihGpMkTd64M4XHzt1OsgJ4ziAdDeTZb/Pu2Um44v2vmXYLkh6CB7VKalV9BthvE/ciSZqycU8fvWzO5iMYfW7BzyxI0mZm3LuPfm/O4/uA/wIO2uTdSJKmatxrCkcM3YgkafrG/ZKdJUk+neSOJLcnOTvJkqGbkyRN1rgXmk8BVjL6XoWdgc+2miRpMzJuKMxU1SlVdV/7ORWYGbAvSdIUjBsKdyY5LMkW7ecw4DtDNiZJmrxxQ+F1wCuA/wFuAw4GNnjxOckuSS5McmOS65O8udV3SHJekm+139u3epJ8MMnqJNcmedaDf1uSpAdj3FB4N3B4Vc1U1U6MQuKdG3nOfcAfV9XTgX2Ao5PsDhwHnF9Vy4Dz2zbAgcCy9nMU8KFf5I1Ikh66cUNhz6q6e3ajqu4CnrmhJ1TVbVV1ZXv8A+BGRhepDwJOa8NOA1a0xwcBp9fIJcB2SZ409juRJD1k44bCI2ZP88DoFBDjf/CNJEsZhcilwBOr6jYYBQewUxu2M3DLnKetaTVJ0oSM+z/2vwP+I8lZjJa3eAXwN+M8McljgLOBt1TV95Osd+g8tQcspZHkKEanl9h1113HaUGSNKaxZgpVdTrwcuB2YC3wsqo6Y2PPS7IVo0D4eFV9qpVvnz0t1H7f0eprgF3mPH0JcOs8vZxUVcuravnMjHfFStKmNPYpoKq6Abhh3PEZTQlOBm6sqr+fs2slcDjw3vb7nDn1Y5KcCewNfG/2NJMkaTLGDoUHYV/g1cDXk1zdau9gFAafTHIkcDNwSNv3eeBFwGrgHjZyy6skadMbLBSq6ivMf50AYP95xhdw9FD9SJI27kF9yY4kafNkKEiSOkNBktQZCpKkzlCQJHWGgiSpMxQkSZ2hIEnqDAVJUmcoSJI6Q0GS1BkKkqTOUJAkdYaCJKkzFCRJnaEgSeoMBUlSZyhIkjpDQZLUGQqSpM5QkCR1hoIkqTMUJEmdoSBJ6gwFSVJnKEiSOkNBktQZCpKkzlCQJHWGgiSpMxQkSZ2hIEnqDAVJUmcoSJI6Q0GS1BkKkqTOUJAkdYaCJKkzFCRJ3WChkOSjSe5Ict2c2g5JzkvyrfZ7+1ZPkg8mWZ3k2iTPGqovSdL6DTlTOBU4YJ3accD5VbUMOL9tAxwILGs/RwEfGrAvSdJ6DBYKVXUxcNc65YOA09rj04AVc+qn18glwHZJnjRUb5Kk+U36msITq+o2gPZ7p1bfGbhlzrg1rfYASY5KsirJqrVr1w7arCQtNgvlQnPmqdV8A6vqpKpaXlXLZ2ZmBm5LkhaXSYfC7bOnhdrvO1p9DbDLnHFLgFsn3JskLXqTDoWVwOHt8eHAOXPqr2l3Ie0DfG/2NJMkaXK2HOqFk/wr8NvAjknWAH8FvBf4ZJIjgZuBQ9rwzwMvAlYD9wBHDNWXJGn9BguFqnrVenbtP8/YAo4eqhdJ0ngWyoVmSdICYChIkjpDQZLUGQqSpM5QkCR1hoIkqTMUJEmdoSBJ6gwFSVJnKEiSOkNBktQZCpKkzlCQJHWGgiSpMxQkSZ2hIEnqDAVJUmcoSJI6Q0GS1BkKkqTOUJAkdYaCJKkzFCRJnaEgSeoMBUlSZyhIkjpDQZLUGQqSpM5QkCR1hoIkqTMUJEmdoSBJ6gwFSVJnKEiSOkNBktQZCpKkzlCQJHWGgiSpMxQkSd2CCoUkByT5ZpLVSY6bdj+StNgsmFBIsgVwInAgsDvwqiS7T7crSVpcFkwoAM8BVlfVTVX1U+BM4KAp9yRJi0qqato9AJDkYOCAqvr9tv1qYO+qOmadcUcBR7XNXwO+OdFGJ2tH4M5pN6EHxWP38La5H79fqaqZ+XZsOelONiDz1B6QWFV1EnDS8O1MX5JVVbV82n3oF+exe3hbzMdvIZ0+WgPsMmd7CXDrlHqRpEVpIYXC5cCyJLsleSTwSmDllHuSpEVlwZw+qqr7khwDfBHYAvhoVV0/5bambVGcJttMeewe3hbt8VswF5olSdO3kE4fSZKmzFCQJHWGwhQk+VmSq5Ncl+Tfkmw77Z60cUmemORfktyU5IokX0vy0k3wuhclWZS3P07KUMeuvfY7NsXrLBSGwnT8uKr2qqpnAD8FXv9QXiwjHssBJQnwGeDiqvrVqno2ozvklky3M23MuMcuyYO98cZQ0Cb1ZeApAEne2mYP1yV5y+yA+epJlia5Mck/Alfy85/x0Ka3H/DTqvrwbKGqvl1VJyTZOskpSb6e5KokvwOwgfo2Sc5Mcm2STwDbTOctLRobOnavbbP1zwLnAiR5W5LL2/F51+xzknymzTKubysrkOS9wDZt5v/xCb+vQSyYW1IXo/aXyYHAF5I8GzgC2JvRp7svTfIlRsE9X/1uRst8HFFVfzSN/heZX2cUvvM5GqCq9kjyNODcJE/dQP0NwD1VtWeSPTfwuto0NnTsAJ4L7FlVdyV5IbCM0VpsAVYmeX5VXQy8ro3ZBrg8ydlVdVySY6pqr8HfxYQ4U5iObZJcDawCbgZOBn4T+HRV/aiqfgh8CvitDdQBvl1Vl0y+fSU5Mck1SS5ndIzOAKiqbwDfBp66gfrzgY+1+rXAtRN/A4vYOscO4Lyquqs9fmH7uYpRkDyNUUgAvCnJNcAljGbmy9gMOVOYjh+v+5dFO+85n/XVAX606VrSRlwPvHx2o6qOTrIjo2D/7/U8Z0PHzg8ITc6Gjh38/H9HAf62qv5p7gsk+W3gBcBzq+qeJBcBWw/Z9LQ4U1g4LgZWJNk2yaOBlzK63rC+uibrAmDrJG+YU5u9a+xi4FCAdnpoV0ar945Tfwaw5wT6X8w2dOzW9UXgdUkeA5Bk5yQ7AY8H7m6B8DRgnznP+d8kWw3R+DQ4U1ggqurKJKcCl7XSR6rqKoD56kmWTrrHxayqKskK4PgkxwJrGf2F+XbgHODDSb4O3Ae8tqrubTcBzFf/EHBKkmuBq7n/2GoAGzl226wz9twkTwe+1ibvPwQOA74AvL4ds28yOoU06yTg2iRXVtWhg7+hgbnMhSSp8/SRJKkzFCRJnaEgSeoMBUlSZyhIkjpDQZLUGQoSfYHB69apvTPJn0yrpzl9rEiy+7T70OJgKEgDeQhLMa9rBWAoaCIMBWkjkrwpyQ1tKeUzW+3RST7alli+KslBrf6ApZjX85rHtiW1r2nLL5PkD9rrXZPk7La0yfOAlwDvb8szP3kCb1mLmMtcSBt3HLBbW6Jiu1b7M+CCqnpdq12W5N/bvr4U83wvluRARn/9793W0tmh7fpUVf1zG/Me4Mi25v9K4HNVddZA70/qnClII+tb76UYLW398SSHMVrDCEbLKx/XlkC/iNGKmbu2feetLxCaFwCnVNU9AHPGPiPJl9taSYcy+h4AaaIMBWnkO8D269R2AO4EXgycCDwbuKJdKwjw8va1qntV1a5VdWN73saWNA/zh9CpwDFVtQfwLjbTpZm1sBkKEtC+wOi2JPsDtFM6BwBfAXapqguBY4HtgMcwWmL5jbPfg5Hkmb/AP3cuo+WZt53zbwE8tvWwFW1p7eYHbZ80OENBut9rgD9vp4QuYPTX+s3Ax9opnauA46vqu8C7ga0YLZl8XdseS1V9AVgJrGr/1uxtr38BXAqcB3xjzlPOBN7WLmh7oVmDculsSVLnTEGS1HlLqjSQJHsAZ6xTvreq9p5GP9I4PH0kSeo8fSRJ6gwFSVJnKEiSOkNBktT9P4voVG51eLbYAAAAAElFTkSuQmCC
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div id="sec_3"></div><h1 id="Section-Three:-Training-the-models">Section Three: Training the models<a class="anchor-link" href="#Section-Three:-Training-the-models">&#182;</a></h1><p>Do to the constraint of the assignment I will be limited in my use in using gridsearchcv(), and this is because I can't fit my y_testing data on individual models when I run grid search. In order to alleviate this issue I will use Paramgrid(), which is a function that returns the grid of gridsearchcv(). This param grid will be used to fit indivdual models throughout the analysis. The fitting process will be broken down into four parts. Part one, will be the dictionary layout for paramgrid. Part two will be the functions that I plan to use for the modeling fitting. Part three will be fitting all possible models using four types of features which are all possible features, TSNE features, Sparse PCA features and PCA features. The Last Part will fit models all possible models based on feature importance.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div id="part_3_1"></div><h2 id="Part-One:-Param-Dictionaries">Part One: Param Dictionaries<a class="anchor-link" href="#Part-One:-Param-Dictionaries">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[20]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#### dictionaries for paramgrid ###</span>

<span class="n">knn_params</span><span class="o">=</span><span class="p">{</span>
    <span class="s1">&#39;p&#39;</span><span class="p">:[</span><span class="mi">2</span><span class="p">],</span>
    <span class="s1">&#39;n_neighbors&#39;</span><span class="p">:[</span><span class="mi">5</span><span class="p">,</span><span class="mi">10</span><span class="p">,</span><span class="mi">20</span><span class="p">,</span><span class="mi">50</span><span class="p">],</span>
    <span class="s1">&#39;n_jobs&#39;</span><span class="p">:[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>
<span class="p">}</span>

<span class="n">random_params</span><span class="o">=</span><span class="p">{</span>
    <span class="s1">&#39;n_estimators&#39;</span><span class="p">:[</span><span class="mi">100</span><span class="p">,</span><span class="mi">500</span><span class="p">],</span>
    <span class="s1">&#39;min_samples_split&#39;</span><span class="p">:[</span><span class="mi">5</span><span class="p">],</span>
    <span class="s1">&#39;min_samples_leaf&#39;</span><span class="p">:[</span><span class="mi">5</span><span class="p">],</span>
    <span class="s1">&#39;n_jobs&#39;</span><span class="p">:[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>
<span class="p">}</span>
<span class="n">gradient_params</span><span class="o">=</span><span class="p">{</span>
    <span class="s1">&#39;learning_rate&#39;</span><span class="p">:[</span><span class="o">.</span><span class="mi">1</span><span class="p">,</span><span class="o">.</span><span class="mi">01</span><span class="p">,</span><span class="o">.</span><span class="mi">001</span><span class="p">],</span>
    <span class="s1">&#39;n_estimators&#39;</span><span class="p">:[</span><span class="mi">100</span><span class="p">,</span><span class="mi">500</span><span class="p">],</span>
    <span class="s1">&#39;subsample&#39;</span><span class="p">:[</span><span class="o">.</span><span class="mi">6</span><span class="p">,</span><span class="o">.</span><span class="mi">8</span><span class="p">,</span><span class="mi">1</span><span class="p">],</span>
    <span class="s1">&#39;min_samples_split&#39;</span><span class="p">:[</span><span class="mi">5</span><span class="p">],</span>
    <span class="s1">&#39;min_samples_leaf&#39;</span><span class="p">:[</span><span class="mi">5</span><span class="p">],</span>
    <span class="s1">&#39;random_state&#39;</span><span class="p">:[</span><span class="mi">4</span><span class="p">],</span>
<span class="p">}</span>
<span class="n">xg_params</span><span class="o">=</span><span class="p">{</span>
    <span class="s1">&#39;learning_rate&#39;</span><span class="p">:[</span><span class="o">.</span><span class="mi">1</span><span class="p">,</span><span class="o">.</span><span class="mi">01</span><span class="p">,</span><span class="o">.</span><span class="mi">001</span><span class="p">],</span>
    <span class="s1">&#39;n_estimators&#39;</span><span class="p">:[</span><span class="mi">100</span><span class="p">,</span><span class="mi">500</span><span class="p">],</span>
    <span class="s1">&#39;subsample&#39;</span><span class="p">:[</span><span class="o">.</span><span class="mi">6</span><span class="p">,</span><span class="o">.</span><span class="mi">8</span><span class="p">,</span><span class="mi">1</span><span class="p">],</span>
    <span class="s1">&#39;max_depth&#39;</span><span class="p">:[</span><span class="mi">5</span><span class="p">,</span><span class="mi">7</span><span class="p">,</span><span class="mi">9</span><span class="p">],</span>
    <span class="s1">&#39;n_jobs&#39;</span><span class="p">:[</span><span class="o">-</span><span class="mi">1</span><span class="p">]</span>
<span class="p">}</span>

<span class="n">master_params</span><span class="o">=</span><span class="p">[</span><span class="n">knn_params</span><span class="p">,</span> <span class="n">random_params</span><span class="p">,</span> <span class="n">gradient_params</span><span class="p">,</span> <span class="n">xg_params</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div id="part_3_2"></div><h2 id="Part-Two:-Function-for-the-models">Part Two: Function for the models<a class="anchor-link" href="#Part-Two:-Function-for-the-models">&#182;</a></h2><p>The following function takes in a model and a parameter grid and fits all possible models on a training set and then predicts the testing set</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[470]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">ParameterGrid</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">fit_grid_point</span>

<span class="k">def</span> <span class="nf">get_model</span><span class="p">(</span><span class="n">model</span><span class="p">,</span><span class="n">x_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span><span class="n">y_test</span><span class="p">,</span> <span class="n">param</span><span class="p">,</span> <span class="n">scorring1</span><span class="p">,</span> <span class="n">scorring2</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;</span>
<span class="sd">    This function fits and returns a serries for a dataframe</span>
<span class="sd">    What it returns: all models given the paramter grid fit to the test data.</span>
<span class="sd">    &quot;&quot;&quot;</span>
    <span class="c1">### creates the paramter grid</span>
    <span class="n">param_grid</span><span class="o">=</span><span class="n">ParameterGrid</span><span class="p">(</span><span class="n">param</span><span class="p">)</span>
    <span class="c1">### puts the param grid into a dataframe</span>
    <span class="n">df_param_grid</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">param_grid</span><span class="p">)</span>
    <span class="n">master_score1</span><span class="o">=</span><span class="p">[]</span>
    <span class="n">master_score2</span><span class="o">=</span><span class="p">[]</span>
    <span class="c1">### assigning clasifier name to the data frame</span>
    <span class="n">df_param_grid</span><span class="p">[</span><span class="s1">&#39;Clasifier&#39;</span><span class="p">]</span><span class="o">=</span><span class="n">model</span><span class="o">.</span><span class="vm">__name__</span>
    
    <span class="k">for</span> <span class="n">params</span> <span class="ow">in</span> <span class="n">param_grid</span><span class="p">:</span>
        <span class="n">clf</span><span class="o">=</span><span class="n">model</span><span class="p">()</span>
        <span class="c1">## setting the individual parameter grid to the function</span>
        <span class="n">clf</span><span class="o">.</span><span class="n">set_params</span><span class="p">(</span><span class="o">**</span><span class="n">params</span><span class="p">)</span>
        <span class="c1">### fitting the model</span>
        <span class="n">clf</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train</span><span class="o">.</span><span class="n">values</span><span class="p">,</span><span class="n">y_train</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
        <span class="n">pred</span><span class="o">=</span><span class="n">clf</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">x_test</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
        <span class="c1">### calculating the score of y_test vs y_pred</span>
        <span class="n">score</span><span class="o">=</span><span class="n">scorring1</span><span class="p">(</span><span class="n">y_test</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">pred</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="n">score</span><span class="p">)</span>
        <span class="n">master_score1</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">score</span><span class="p">)</span>
        <span class="n">score</span><span class="o">=</span><span class="n">scorring2</span><span class="p">(</span><span class="n">y_test</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">pred</span><span class="p">,</span> <span class="n">average</span><span class="o">=</span><span class="s1">&#39;macro&#39;</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="n">score</span><span class="p">)</span>
        <span class="n">master_score2</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">score</span><span class="p">)</span>
    <span class="c1">### assining the scores to the param grid df   </span>
    <span class="n">df_param_grid</span><span class="p">[</span><span class="n">scorring1</span><span class="o">.</span><span class="vm">__name__</span><span class="p">]</span><span class="o">=</span><span class="n">master_score1</span>
    <span class="n">df_param_grid</span><span class="p">[</span><span class="n">scorring2</span><span class="o">.</span><span class="vm">__name__</span><span class="p">]</span><span class="o">=</span><span class="n">master_score2</span>

    <span class="k">return</span> <span class="n">df_param_grid</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[28]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span><span class="o">=</span><span class="n">ParameterGrid</span><span class="p">(</span><span class="n">xg_params</span><span class="p">)</span>
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="n">x</span><span class="p">:</span>
    <span class="n">x</span><span class="o">=</span><span class="n">XGBClassifier</span><span class="p">(</span><span class="o">**</span><span class="n">i</span><span class="p">)</span>
    <span class="n">x</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">y_train</span><span class="p">)</span>
    <span class="n">x</span><span class="o">.</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[28]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>{&#39;subsample&#39;: 1,
 &#39;n_jobs&#39;: -1,
 &#39;n_estimators&#39;: 100,
 &#39;max_depth&#39;: 5,
 &#39;learning_rate&#39;: 0.1}</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div id="part_3_3"></div><h2 id="Part-Three:-Master-Model-Run">Part Three: Master Model Run<a class="anchor-link" href="#Part-Three:-Master-Model-Run">&#182;</a></h2><p>The following for loop fits all possible models (see master model list) across all possible parameters (see parameter dictionary), and then fits all models across the different dimension reduction techniques.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">master_params</span><span class="o">=</span><span class="p">[</span><span class="n">knn_params</span><span class="p">,</span> <span class="n">random_params</span><span class="p">,</span> <span class="n">gradient_params</span><span class="p">,</span> <span class="n">xg_params</span><span class="p">]</span>
<span class="n">master_models</span><span class="o">=</span><span class="p">[</span><span class="n">KNeighborsClassifier</span><span class="p">,</span> <span class="n">RandomForestClassifier</span><span class="p">,</span> <span class="n">GradientBoostingClassifier</span><span class="p">,</span> <span class="n">XGBClassifier</span><span class="p">]</span>
<span class="n">target</span><span class="o">=</span><span class="n">df_des</span><span class="p">[</span><span class="s1">&#39;User_cat&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span>

<span class="c1">### column list for fitting th different models</span>
<span class="n">master_cols</span><span class="o">=</span><span class="n">master</span><span class="o">.</span><span class="n">columns</span>
<span class="n">sparse_cols</span><span class="o">=</span><span class="p">[</span><span class="n">col</span> <span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="n">master</span><span class="o">.</span><span class="n">columns</span> <span class="k">if</span> <span class="s1">&#39;Sparse&#39;</span> <span class="ow">in</span> <span class="n">col</span><span class="p">]</span>
<span class="n">PC_cols</span><span class="o">=</span><span class="p">[</span><span class="n">col</span> <span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="n">master</span><span class="o">.</span><span class="n">columns</span> <span class="k">if</span> <span class="s1">&#39;PC&#39;</span> <span class="ow">in</span> <span class="n">col</span><span class="p">]</span>
<span class="n">TSNE</span><span class="o">=</span><span class="p">[</span><span class="n">col</span> <span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="n">master</span><span class="o">.</span><span class="n">columns</span> <span class="k">if</span> <span class="s1">&#39;tsne&#39;</span> <span class="ow">in</span> <span class="n">col</span><span class="p">]</span>
<span class="n">col_list</span><span class="o">=</span><span class="p">[</span><span class="n">master_cols</span><span class="p">,</span> <span class="n">sparse_cols</span><span class="p">,</span> <span class="n">PC_cols</span><span class="p">,</span> <span class="n">sparse_cols</span><span class="p">]</span>
<span class="n">col_names</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;all&#39;</span><span class="p">,</span> <span class="s1">&#39;sparse&#39;</span><span class="p">,</span> <span class="s1">&#39;PCA&#39;</span><span class="p">,</span> <span class="s1">&#39;TSNE&#39;</span><span class="p">]</span>


<span class="n">master_df</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">()</span>

<span class="k">for</span> <span class="n">i</span> <span class="p">,</span><span class="n">col</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">col_list</span><span class="p">):</span>
    <span class="c1">## splits train and Test </span>
    <span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span><span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">master</span><span class="p">[</span><span class="n">col</span><span class="p">],</span> <span class="n">target</span><span class="p">,</span><span class="n">test_size</span><span class="o">=.</span><span class="mi">2</span><span class="p">)</span> 
    
    <span class="c1">### fits model on dimensions col</span>
    <span class="k">for</span> <span class="n">j</span> <span class="p">,</span><span class="n">model</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">master_models</span><span class="p">):</span>
        <span class="n">df</span><span class="o">=</span><span class="n">get_model</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">x_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span><span class="n">x_test</span><span class="p">,</span><span class="n">y_test</span><span class="p">,</span> <span class="n">master_params</span><span class="p">[</span><span class="n">j</span><span class="p">],</span> <span class="n">accuracy_score</span><span class="p">,</span> <span class="n">f1_score</span><span class="p">)</span>
        <span class="n">df</span><span class="p">[</span><span class="s1">&#39;features&#39;</span><span class="p">]</span><span class="o">=</span><span class="n">col_names</span><span class="p">[</span><span class="n">i</span><span class="p">]</span>
        <span class="n">master_df</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">master_df</span><span class="p">,</span> <span class="n">df</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>

<span class="n">master_df</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s2">&quot;master_quiz_3.csv&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[18]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### Observing The output ###</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Shape of Paramgrid: &quot;</span><span class="p">,</span> <span class="n">master_df</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">master_df</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Shape of Paramgrid:  (312, 15)
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Clasifier</th>
      <th>accuracy_score</th>
      <th>f1_score</th>
      <th>features</th>
      <th>learning_rate</th>
      <th>max_depth</th>
      <th>min_samples_leaf</th>
      <th>min_samples_split</th>
      <th>n_estimators</th>
      <th>n_jobs</th>
      <th>n_neighbors</th>
      <th>p</th>
      <th>random_state</th>
      <th>subsample</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>KNeighborsClassifier</td>
      <td>0.336683</td>
      <td>0.313983</td>
      <td>all</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>KNeighborsClassifier</td>
      <td>0.346734</td>
      <td>0.339408</td>
      <td>all</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>10.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>KNeighborsClassifier</td>
      <td>0.366834</td>
      <td>0.352205</td>
      <td>all</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>20.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<div id="part_3_4"></div><h2 id="Part-Four:-Models-from-Feature-Importance">Part Four: Models from Feature Importance<a class="anchor-link" href="#Part-Four:-Models-from-Feature-Importance">&#182;</a></h2><p>The following are models based on feature importance. The features importance was determined through XGBoost's feature importance moduel. The model fit from XGBoost feature importance was determined using the best fit model from the previous model fitting. The features for this model run was determined using three criteria: information gain, weight, and total information gain. These features will be broken down into four categories and these categoreis will be run through all possible models.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[547]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### looking through the results i beleive a combination of features may produce the best results, for this excercise i will</span>
<span class="c1">### pick what seem to be the best features. </span>

<span class="c1">## step one using the best model thuse far (using f1-score) and extracting the best features</span>
<span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span><span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">master</span><span class="p">,</span> <span class="n">target</span><span class="p">,</span><span class="n">test_size</span><span class="o">=.</span><span class="mi">2</span><span class="p">)</span> 

<span class="c1">### fitting the top model from previous model fittings</span>
<span class="n">clf</span><span class="o">=</span><span class="n">XGBClassifier</span><span class="p">(</span><span class="n">learning_rate</span><span class="o">=.</span><span class="mi">1</span><span class="p">,</span> <span class="n">max_depth</span><span class="o">=</span><span class="mi">7</span><span class="p">,</span> <span class="n">n_estimators</span><span class="o">=</span><span class="mi">100</span><span class="p">,</span> <span class="n">n_jobs</span><span class="o">=-</span><span class="mi">1</span><span class="p">,</span> <span class="n">subsample</span><span class="o">=</span><span class="mf">1.</span><span class="p">)</span>
<span class="n">clf</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">x_train</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>

<span class="c1">### plotting best features</span>
<span class="c1">### To get gain and weight chnage importance_type=&#39;total_gain&#39;</span>
<span class="n">plot_importance</span><span class="p">(</span><span class="n">clf</span><span class="p">,</span><span class="n">max_num_features</span><span class="o">=</span><span class="mi">20</span><span class="p">,</span> <span class="n">importance_type</span><span class="o">=</span><span class="s1">&#39;total_gain&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[547]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a8ff343048&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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+mqOHTvmZHLPmDGDm2++mTp16pTyceutt5KYmAjAqlWraNPG12aScPXVV9OiRQtc2hYrVqygbdu2gKXeNnOmtWHZzJkz6devn1c/LlyP7vfv38/HH3/srK0DfPHFFwQHB9O8+ZktLq655hoSExNRVbKzs1m3bh3BwcE0aNDAa7/c73H37t3k5eXRsGFDr2pzHTp04IcffiAlJYW8vDzmzZtHfHw8IkK3bt346KOPSt2ju6Ld4sWLCQkJKfPeDReYi/3t4nwd2DP3ErYeWDKyv9bnu8AAX3XMzN03ZlZaNiZGvnHFZ+DAgXr11Vern5+fNmvWTGfMmFGsnvve5GvWrNHAwEANCgrS2267TY8ePerUu+WWW/TQoUOqqpqZmam9e/fWsLAw7dy5s27dulVVrRl6s2bNtHbt2lq3bl1t1qyZM/PfsmWLtm/fXsPDw7Vfv36O7/T0dO3evbsGBgZq9+7dNSMjo0xfN954o4aEhGhERIR+8cUXxe4nISFBp0+fXsyWlZWlAwYM0LZt22pISIi+8sorToy89Ss3N1fvueceDQ0N1euuu05XrFjh+BszZowGBARomzZtnD3mVa295Vu3bq0BAQE6ZswYx753717t0KGDtmrVSgcMGOBk4I8aNUrbtm2rERER2rVrV925c2eZnytm5n5Bj3KlUOeL86FeJyLNgQxVzRGR+sB64HZV3ebtukahzjflUTnr98bEyDcmPmVTHmNkFOouLBXpsXwp7G+H56JeFwKsF5FkYBUwwdfAbjAYDAbDpUiFyZYvOWt3s6cBd56lj8+xsuwNBoPBYCi3VOiZu8FguPQpS1a2W7dujqzsnDlziIiIICIiguuvv57k5GSfvh977DFq1TrzvX/fvn306NGDiIgIunbtysGDB52y/fv3ExcXR0hICG3btiU1NRWwtmVt164dYWFhJCQkONunLlq0iIiICKKiooiOjuarr75yfFWuXNmRYo2Pj3fsN910k2Nv2rQpt956K+BbotZbfLZu3Urnzp2Jiopi2LBhbNiwocx+GS4jLvai/8U4gHBga4lj/a/xZRLqfGOSxcrmco9RWbKyjRs3dhLlvv76aydRbOnSpdqxY0evfr/55hu99957tWbNmo5twIAB+t5776mq6ooVK/Tee+91ymJiYnT58uWqaiWuZWdna2FhoTZv3lx37dqlqqqjR492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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#### fitting model after slecting features based on gain, weight and total gain</span>

<span class="n">total_gain</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;PC_1&#39;</span><span class="p">,</span><span class="s1">&#39;PC_12&#39;</span><span class="p">,</span><span class="s1">&#39;PC_3&#39;</span><span class="p">,</span><span class="s1">&#39;PC_10&#39;</span><span class="p">,</span><span class="s1">&#39;PC_220&#39;</span><span class="p">,</span> <span class="s1">&#39;PC_16&#39;</span><span class="p">,</span><span class="s1">&#39;PC_45&#39;</span><span class="p">,</span><span class="s1">&#39;PC_54&#39;</span><span class="p">,</span><span class="s1">&#39;PC_57&#39;</span><span class="p">,</span> <span class="s1">&#39;tsne_3&#39;</span><span class="p">]</span>
<span class="n">weight</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;tsne_1&#39;</span><span class="p">,</span><span class="s1">&#39;tsne_2&#39;</span><span class="p">,</span><span class="s1">&#39;tsne_3&#39;</span><span class="p">,</span><span class="s1">&#39;Pc_12&#39;</span><span class="p">,</span> <span class="s1">&#39;PC_3&#39;</span><span class="p">,</span> <span class="s1">&#39;PC_16&#39;</span><span class="p">,</span> <span class="s1">&#39;Sparse_1&#39;</span><span class="p">,</span> <span class="s1">&#39;Sparse_11&#39;</span><span class="p">,</span><span class="s1">&#39;PC_9&#39;</span><span class="p">,</span> <span class="s1">&#39;PC_4&#39;</span><span class="p">]</span>
<span class="n">gain</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;PC_1&#39;</span><span class="p">,</span><span class="s1">&#39;PC_57&#39;</span><span class="p">,</span><span class="s1">&#39;PC_177&#39;</span><span class="p">,</span><span class="s1">&#39;PC_408&#39;</span><span class="p">,</span> <span class="s1">&#39;PC_10&#39;</span><span class="p">,</span> <span class="s1">&#39;PC_328&#39;</span><span class="p">,</span><span class="s1">&#39;PC_126&#39;</span><span class="p">,</span><span class="s1">&#39;PC_195&#39;</span><span class="p">,</span><span class="s1">&#39;PC_278&#39;</span><span class="p">,</span><span class="s1">&#39;PC_307&#39;</span><span class="p">]</span>
<span class="n">all_select</span><span class="o">=</span><span class="nb">set</span><span class="p">(</span><span class="n">total_gain</span><span class="o">+</span><span class="n">weight</span><span class="o">+</span><span class="n">gain</span><span class="p">)</span>

<span class="n">col</span><span class="o">=</span><span class="p">[</span><span class="n">total_gain</span><span class="p">,</span> <span class="n">weight</span><span class="p">,</span> <span class="n">gain</span><span class="p">,</span> <span class="n">all_select</span><span class="p">]</span>
<span class="n">col_names</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;Total_Gain&#39;</span><span class="p">,</span> <span class="s1">&#39;Weight&#39;</span><span class="p">,</span> <span class="s1">&#39;Gain&#39;</span><span class="p">,</span> <span class="s1">&#39;All_select&#39;</span><span class="p">]</span>

<span class="n">select_master</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">()</span>

<span class="k">for</span> <span class="n">i</span> <span class="p">,</span><span class="n">col</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">col_list</span><span class="p">):</span>
    <span class="c1">## splits train and Test </span>
    <span class="n">x_train</span><span class="p">,</span> <span class="n">x_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span><span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">master</span><span class="p">[</span><span class="n">col</span><span class="p">],</span> <span class="n">target</span><span class="p">,</span><span class="n">test_size</span><span class="o">=.</span><span class="mi">2</span><span class="p">)</span> 
    
    <span class="c1">### fits model on dimensions col</span>
    <span class="k">for</span> <span class="n">j</span> <span class="p">,</span><span class="n">model</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">master_models</span><span class="p">):</span>
        <span class="n">df</span><span class="o">=</span><span class="n">get_model</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">x_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span><span class="n">x_test</span><span class="p">,</span><span class="n">y_test</span><span class="p">,</span> <span class="n">master_params</span><span class="p">[</span><span class="n">j</span><span class="p">],</span> <span class="n">accuracy_score</span><span class="p">,</span> <span class="n">f1_score</span><span class="p">)</span>
        <span class="n">df</span><span class="p">[</span><span class="s1">&#39;features&#39;</span><span class="p">]</span><span class="o">=</span><span class="n">col_names</span><span class="p">[</span><span class="n">i</span><span class="p">]</span>
        <span class="n">select_master</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">select_master</span><span class="p">,</span> <span class="n">df</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[554]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">select_master</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="s1">&#39;accuracy_score&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[554]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Clasifier</th>
      <th>accuracy_score</th>
      <th>f1_score</th>
      <th>features</th>
      <th>learning_rate</th>
      <th>max_depth</th>
      <th>min_samples_leaf</th>
      <th>min_samples_split</th>
      <th>n_estimators</th>
      <th>n_jobs</th>
      <th>n_neighbors</th>
      <th>p</th>
      <th>random_state</th>
      <th>subsample</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>KNeighborsClassifier</td>
      <td>0.261307</td>
      <td>0.206945</td>
      <td>Gain</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>KNeighborsClassifier</td>
      <td>0.336683</td>
      <td>0.305608</td>
      <td>Total_Gain</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>20.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>KNeighborsClassifier</td>
      <td>0.336683</td>
      <td>0.289420</td>
      <td>Total_Gain</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>50.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>KNeighborsClassifier</td>
      <td>0.341709</td>
      <td>0.333114</td>
      <td>Total_Gain</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>10.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>KNeighborsClassifier</td>
      <td>0.341709</td>
      <td>0.330366</td>
      <td>Gain</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-1.0</td>
      <td>20.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>49</th>
      <td>XGBClassifier</td>
      <td>0.582915</td>
      <td>0.545212</td>
      <td>Gain</td>
      <td>0.001</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>100.0</td>
      <td>-1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.8</td>
    </tr>
    <tr>
      <th>6</th>
      <td>XGBClassifier</td>
      <td>0.582915</td>
      <td>0.535810</td>
      <td>Gain</td>
      <td>0.100</td>
      <td>7.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>100.0</td>
      <td>-1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.6</td>
    </tr>
    <tr>
      <th>51</th>
      <td>XGBClassifier</td>
      <td>0.582915</td>
      <td>0.528345</td>
      <td>Gain</td>
      <td>0.001</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>500.0</td>
      <td>-1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.6</td>
    </tr>
    <tr>
      <th>10</th>
      <td>GradientBoostingClassifier</td>
      <td>0.582915</td>
      <td>0.524818</td>
      <td>Gain</td>
      <td>0.010</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>500.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>0.8</td>
    </tr>
    <tr>
      <th>7</th>
      <td>GradientBoostingClassifier</td>
      <td>0.592965</td>
      <td>0.507791</td>
      <td>Gain</td>
      <td>0.010</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>100.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>0.8</td>
    </tr>
  </tbody>
</table>
<p>312 rows × 14 columns</p>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[566]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">master_model</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">select_master</span><span class="p">,</span><span class="n">master_df</span><span class="p">])</span>


<span class="n">master_model</span><span class="p">[</span><span class="s1">&#39;Your Name&#39;</span><span class="p">]</span><span class="o">=</span><span class="s1">&#39;Joshua Roberge&#39;</span>
<span class="n">master_model</span><span class="p">[</span><span class="s1">&#39;Random State&#39;</span><span class="p">]</span><span class="o">=</span><span class="mi">4</span>
<span class="n">master_model_1</span><span class="o">=</span><span class="n">master_model</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;p&#39;</span><span class="p">,</span><span class="s1">&#39;random_state&#39;</span><span class="p">,</span> <span class="s1">&#39;min_samples_split&#39;</span><span class="p">,</span> <span class="s1">&#39;n_jobs&#39;</span><span class="p">,</span><span class="s1">&#39;min_samples_leaf&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">master_model_1</span><span class="o">=</span><span class="n">master_model_1</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;Clasifier&#39;</span><span class="p">:</span> <span class="s1">&#39;Algorithm&#39;</span><span class="p">})</span>
<span class="n">master_model_1</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;Master_model_1.csv&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Conclusion">Conclusion<a class="anchor-link" href="#Conclusion">&#182;</a></h1><p>At This point in time I can not conclusively say that a video game's performance effects its outcome, nor can I say that a video games description has any sort of predictive capabilities for predicting a video games performance.</p>
<h3 id="Going-Forward:">Going Forward:<a class="anchor-link" href="#Going-Forward:">&#182;</a></h3><p>Not all is lost! Perhaps a deeper dive into NLP could solve the issue. Going forward the use of a lexicon could prove beneficial and produce better predictive features. Additionally, I believe playing around with transformations on the matrix could improve the model's overall performance.</p>

</div>
</div>
</div>
    </div>
  </div>
</body>

 


</html>







