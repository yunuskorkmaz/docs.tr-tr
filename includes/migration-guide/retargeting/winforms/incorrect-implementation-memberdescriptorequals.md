### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor.Equals yanlış uygulaması

|   |   |
|---|---|
|Ayrıntılar|Özgün uygulaması &quot;eşittir&quot; yöntemi karşılaştırma altındaki nesneleri iki farklı dize özelliklerinden karşılaştırma: kategori adı için açıklama dizesi. Karşılaştırılacak durumda düzeltme &quot;kategori&quot; ilk nesne &quot;kategori&quot; ikinci ve &quot;açıklama&quot; için &quot;açıklama&quot;. MemberDescriptorEqualsReturnsFalseIfEquivalent yapılandırma değeri 4.6.2 hedefleme olursa dışında yeni davranış tercih true veya false framework sürümünü hedefleme 4.6.2 altında olduğunda bu düzeltmeyi etkinleştirmek için ayarlayabilirsiniz.|
|Öneri|Uygulamanızın üzerinde bazen false değerinin döndürülmesi MemberDescriptor.Equals bağımlıysa zaman tanımlayıcıları eşdeğerdir ve 4.6.2 hedeflediğiniz sürüm .NET Framework, birkaç seçeneğiniz vardır:<ol><li>Karşılaştırılacak kod değişiklikleri yapabilir &quot;kategori&quot; ve &quot;açıklama&quot; el ile Equals yöntemini çalıştıran ek alanlar.</li><li>Aşağıdaki değeri app.config dosyasına ekleyerek bu değişikliği çıkma:</li></ol><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Uygulama hedefleri 4.6.1 veya .NET Framework ve daha düşük sürümünü etkin bu değişikliği istiyorsanız, aşağıdaki değeri app.config dosyasına ekleyerek uyumluluk anahtarı false olarak ayarlayabilirsiniz:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

