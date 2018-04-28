### <a name="aspnet-accessibility-improvement-in-net-471"></a>.NET 4.7.1 ASP.NET erişilebilirlik geliştirme

|   |   |
|---|---|
|Ayrıntılar|ASP.NET, ASP.NET Web denetimleri daha iyi destek ASP.NET müşterilere Erişilebilirlik teknolojisi Visual Studio ile nasıl çalıştığıyla artırma.  Bunlar aşağıdaki değişiklikleri içerir:<ul><li>Ayrıntılar Görünümü Sihirbazı'nda alan Ekle iletişim kutusu gibi denetimlerinde eksik UI erişilebilirlik desenlerini uygulama şekilde değişir.</li><li>Yüksek karşıtlık modunda gibi veri çağrı cihazı alanları Düzenleyicisi görüntü iyileştirmeye yönelik değişiklikler.</li><li>Klavye gezinti iyileştirmeye yönelik değişiklikler karşılaştığında yapılandırma nesnesi bağlam penceresi veya veri kaynağı yapılandırma penceresi gibi denetimleri için.</li></ul>|
|Öneri|**İçinde veya dışında bu değişiklikleri kabul etmek nasıl** sırada bu değişikliklerden yararlanmak Visual Studio tasarımcısı için .NET Framework 4.7.1 çalıştırmanız gerekir ya da daha sonra. Web uygulama aşağıdaki yollardan biriyle bu değişiklikleri yararlı olabilir:<ul><li>Visual Studio 2017 15.3 yükleyin veya daha sonra aşağıdaki AppContext anahtarıyla yeni erişilebilirlik özellikleri varsayılan olarak destekler.</li><li>Eski erişilebilirlik davranışları dışında ekleyerek opt **Switch.UseLegacyAccessibility** AppContext anahtara `<runtime>` bölümünde devenv.exe.config dosyasında ve ayarlamak `false`, aşağıdaki örnek olarak gösterir.</li></ul><pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;<br />&lt;configuration&gt;<br />&lt;runtime&gt;<br />...</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
