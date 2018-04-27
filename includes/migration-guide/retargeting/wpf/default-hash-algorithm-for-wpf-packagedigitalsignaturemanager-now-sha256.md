### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>WPF PackageDigitalSignatureManager için varsayılan karma algoritma SHA256 sunulmuştur

|   |   |
|---|---|
|Ayrıntılar|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> WPF paketleri ile ilgili olarak dijital imzalar için işlevsellik sağlar.  .NET Framework 4.7 ve önceki sürümlerinde, varsayılan algoritma (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) bir paket bölümlerini imzalama için kullanılan SHA1 oluştu.  SHA1 ile en son güvenlik sorunları nedeniyle bu varsayılan değer SHA256 için değiştirildi .NET Framework ile 4.7.1 başlatılıyor.  Bu değişiklik, tüm paket imzalama, XPS belgeleri de dahil olmak üzere etkiler.|
|Öneri|Aşağıda 4.7.1 .NET framework sürümünü hedefleme sırasında bu değişikliği kullanmak isteyen bir geliştirici veya .NET 4.7.1 ya da büyük can hedefleme sırasında önceki işlevselliği gerektiren bir geliştirici aşağıdaki AppContext bayrağını uygun şekilde ayarlayın.  Doğru değeri SHA1 neden olur varsayılan algoritması olarak; kullanılan SHA256 false sonuçlanır.<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|

