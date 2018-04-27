### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>WCF bağlamayla TransportWithMessageCredential güvenlik modu

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1 başlayarak, TransportWithMessageCredential güvenlik modu kullanan WCF bağlama imzasız ile iletileri alacak şekilde ayarlanabilir &quot;için&quot; asimetrik güvenlik anahtarları için üstbilgiler. Varsayılan olarak, imzasız &quot;için&quot; üstbilgileri .NET 4.6.1 reddedilir devam edecek. Bir uygulama bu işlemi Switch.System.ServiceModel.AllowUnsignedToHeader yapılandırma anahtarı kullanarak yeni moduna çevrilir varsa bunlar yalnızca kabul edilecektir. Bu katılımı özelliği olduğundan, mevcut uygulamalarınızın davranışını etkilemez.|
|Öneri|Bu katılımı özelliği olduğundan, mevcut uygulamalarınızın davranışını etkilemez. Yeni davranış veya kullanılıp kullanılmadığını kontrol etmek için şu yapılandırma ayarı kullanın:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.6.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

