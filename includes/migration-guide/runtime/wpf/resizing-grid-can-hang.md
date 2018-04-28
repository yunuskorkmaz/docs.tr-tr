### <a name="resizing-a-grid-can-hang"></a>Bir kılavuz yeniden boyutlandırma askıda kalabilir

|   |   |
|---|---|
|Ayrıntılar|Sonsuz bir döngüde yerleşimini sırasında ortaya çıkabilir bir <code>T:System.Windows.Controls.Grid</code> aşağıdaki koşullarda:<ul><li>Satır tanımlarını içeren iki *-satırlar, hem bir MinHeight ve bir MaxHeight bildirme.</li><li>İçeriği *-satırları karşılık gelen MaxHeight aşan değil</li><li>İlk MinHeight tarafından kılavuz kullanılabilir yüksekliği aşıldı (ve diğer sabit veya satır otomatik)</li><li>Uygulamayı .net 4.7 hedefler ya da 4.7 ayırma algoritmasını ayarlayarak kabul eder <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Döngü aynı zamanda ikiden fazla satır ile ya da benzer durumda sütunlar için gerçekleşir. .Net 4.7.1 sorun düzeltilmiştir.|
|Öneri|.Net 4.7.1'ye yükseltin.  Alternatif olarak, 4.7 ayırma algoritmasını gerekmiyorsa şu yapılandırma ayarı kullanabilirsiniz:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

