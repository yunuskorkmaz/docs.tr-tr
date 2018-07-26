### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Unicode çift yönlü denetim karakterleri Urılar içinde izin ver

|   |   |
|---|---|
|Ayrıntılar|Metnin yönünü belirtmek için kullanılan çeşitli özel denetim karakterleri Unicode belirtir. Yüzde olarak kodlanmış biçimde yoktu bile '.NET Framework'ün önceki sürümlerinde, bu karakterler yanlış tüm bir URI'leri kesilmiş. Daha iyi izlemek için [RFC 3987](http://tools.ietf.org/html/rfc3987), artık bu karakterleri Urılar içinde izin veriyoruz. Bulunduğunda bir URI kodlanmamış, bunlar yüzde olarak kodlanmış. Yüzde olarak kodlanmış bulunduğunda bunlar olarak bırakılır-olduğu.|
|Öneri|Unicode çift yönlü karakter, varsayılan olarak etkindir 4.7.2 ile başlayan .NET Framework'ün sürümlerini hedefleyen uygulamalar için destek. Bu değişiklik, istenmeyen ise, bunu aşağıdaki ekleyerek devre dışı bırakabilirsiniz [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) geçin <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework'ün önceki sürümlerini hedefleyen ancak sürümler altında çalışan uygulamalar için .NET Framework 4.7.2, Unicode çift yönlü karakter desteği ile başlayarak varsayılan olarak devre dışıdır. Aşağıdakileri ekleyerek etkinleştirebilirsiniz [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) geçin <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyası bölümünü::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

