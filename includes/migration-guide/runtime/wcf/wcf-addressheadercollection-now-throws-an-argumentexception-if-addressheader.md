### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>WCF AddressHeaderCollection addressHeader öğesi null ise şimdi ArgumentException oluşturur.

|   |   |
|---|---|
|Ayrıntılar|4.7.1, .NET Framework ile başlayan <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Oluşturucusu oluşturur bir <xref:System.ArgumentException> öğeleri ise <code>null</code>. .NET Framework 4.7 ve önceki sürümleri, hiçbir özel durum oluşur.|
|Öneri|Bu değişiklik .NET Framework 4.7.1 veya sonraki bir sürümünü uyumluluk sorunlarıyla karşılaşırsanız, bunu aşağıdaki satırı ekleyerek çevirin <code>&lt;runtime&gt;</code> app.config dosyasının::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})?displayProperty=nameWithType></li></ul>|

