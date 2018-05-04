### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>URI Unicode çift yönlü denetim karakterlerine izin ver

|   |   |
|---|---|
|Ayrıntılar|Unicode metin yönünü belirtmek için kullanılan birkaç özel denetim karakterleri belirtir. Bunların yüzde olarak kodlanmış form içinde mevcut olsa bile .NET Framework önceki sürümlerinde, bu karakterler yanlış tüm URI'ler atılmış. Daha iyi takip etmek için [RFC 3987](http://tools.ietf.org/html/rfc3987), artık bu karakterleri URI'ler içinde izin veriyoruz. Bulunduğunda bir URI kodlanmamış, bunların yüzde olarak kodlanmış. Yüzde olarak kodlanmış bulunduğunda bunlar olarak kalır-değil.|
|Öneri|Unicode çift yönlü karakter, varsayılan olarak etkindir 4.7.2 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için destek. Bu değişiklik istenmeyen ise, onu aşağıdakileri ekleyerek devre dışı bırakabilirsiniz [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) geçiş <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework'ün önceki sürümlerini hedefleyen ancak sürümler altında çalışan uygulamalar için .NET Framework 4.7.2, Unicode çift yönlü karakterleri desteğini başlayarak varsayılan olarak devre dışıdır. Aşağıdakileri ekleyerek etkinleştirebilirsiniz [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) geçiş <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasının::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

