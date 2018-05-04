### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException özel durum ImageSourceConverter.ConvertFrom koddan işleme

|   |   |
|---|---|
|Ayrıntılar|Hata özel durum kodunu işleme <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> yanlış bir neden <xref:System.NullReferenceException?displayProperty=name> yerine hedeflenen özel durum için (örneğin <xref:System.IO.DirectoryNotFoundException?displayProperty=name>, <xref:System.IO.FileNotFoundException?displayProperty=name>). Böylece yöntemi artık doğru özel durum oluşturur bu değişikliği hatayı düzeltir. <p/>İle .NET Framework 4.6.2 hedefleyen tüm uygulamaların varsayılan ve daha önce throw devam <xref:System.NullReferenceException?displayProperty=name> uyumluluk için. .NET Framework 4.7 hedefleyen geliştiriciler ve yukarıdaki sağ özel durumlar görmeniz gerekir.|
|Öneri|Alma için geri isteyen geliştiriciler <xref:System.NullReferenceException?displayProperty=name> zaman .NET Framework 4.7 hedefleme ekleme/merge kendi uygulamanın App.config dosyasını aşağıdaki:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

