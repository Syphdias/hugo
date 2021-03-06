---
title: "cCSVParse"
date: 2014-11-07T09:49:22+01:00
aliases:
  - /cCSVParse
---

<div id="content">
<p style="border: 2px solid red; padding: 1em">
cCSVParse is maintained by Jan Weiß on <a
href="https://github.com/JanX2/cCSVParse">github.com/JanX2/cCSVParse</a> now
since I don’t do Apple stuff since many years.
</p>

<p>
cCSVParse ist eine Cocoa-Klasse (Apples Objective-C Framework), welche
CSV-Dateien schnell und effizient einliest. Es wurde darauf geachtet, dass die
Klasse mit allen typischen Eigenheiten des standardlosen CSV-Formats umgehen
kann. Dazu gehören:
</p>

<ul>
  <li>Das korrekte Erkennen von Trennzeichen innerhalb von Werten in Anführungszeichen</li>
  <li>Anführungszeichen innerhalb Anführungszeichen</li>
  <li>Zeilenumbrüche innerhalb von Feldern</li>
  <li>Die Wahl eines beliebigen Trennzeichens inklusive automatischer Erkennung desselbigen</li>
</ul>

<p>
Diese Eigenheiten sind der Grund, warum das simple Aufteilen eines NSStrings
nicht genügt, um CSV-Dateien einzulesen ;-).
</p>

<p>
Die eigentliche Funktion, welche die Daten prüft, ist in C geschrieben und
benutzt C-Strings, damit die größtmögliche Geschwindigkeit erreicht wird.
Zurückgegeben werden die eingelesenen Werte als NSStrings innerhalb eines
NSMutableArray pro Zeile.
</p>

<p>
Die gesamte Klasse (inklusive Headerdatei) ist nur 218 Quelltextzeilen lang
(laut SLOCCount) und lässt sich somit bedenkenlos in jedes Projekt integrieren
oder zumindest als Basis verwenden.
</p>

<p>
Mit der Methode -(void)setEncoding:(NSStringEncoding)newEncoding kann man das
Encoding der zu verarbeitenden Datei angeben, sodass man nicht hinterher die
eingelesenen Daten konvertieren muss.
</p>

<h2>Beispielaufruf</h2>

<pre>
CSVParser *parser = [CSVParser new];
[parser openFile: @"./sample.csv"];
NSMutableArray *csvContent = [parser parseFile];
int c;
for (c = 0; c < [csvContent count]; c++) {
	NSLog(@"content of line %d: %@", c, [csvContent objectAtIndex: c]);
}
[parser closeFile];
</pre>

<h2>Geschwindigkeit</h2>

<p>
In meinem Test wurde eine 115 KB große, ca 1500 Zeilen beinhaltende Datei in
0,2 Sekunden komplett eingelesen und (auf Konsole) ausgegeben.
</p>
</div>
	<h3>Herunterladen</h3>
	<ul id="downloads"><li><a class="download_filename" href="/cCSVParse-1.2.tar.gz"><span class="download_name">cCSVParse 1.2</span></a> (<span class="download_size">3.5K</span>, <a class="download_gpg" href="/cCSVParse-1.2.tar.gz.asc">GPG-Signatur</a>)</li></ul>
	<h3>Lizenz</h3>
	<p><span class="name">cCSVParse</span> ist freie Open-Source-Software unter der <span class="license">BSD-Lizenz</span>.</p>
	<div id="development">
		<h3>Entwicklung</h3>
		<p>Der aktuelle Entwicklungsstand kann <a class="dev_url" href="https://github.com/JanX2/cCSVParse">in gitweb</a> verfolgt werden.</p>
	</div>
	<h3>Feedback</h3>
	<p>Solltest du mir eine Nachricht zukommen lassen wollen, <a href="/Impressum">schreib mir doch bitte eine E-Mail</a>.</p>
</div>
