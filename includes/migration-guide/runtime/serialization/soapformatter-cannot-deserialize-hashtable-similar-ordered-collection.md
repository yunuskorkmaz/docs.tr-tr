### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter Hashtable seri durumdan olamaz ve benzer sıralanmış koleksiyon nesnesi

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> Nesneleri'nin altında bir .NET Framework sürüm seri hale getirilmiş garantisi başarıyla altında farklı bir sürüm serisini yapar. Özellikle, bazı koleksiyonları sıralı (gibi <xref:System.Collections.Hashtable?displayProperty=name>) .NET Framework 4. 5'ile sıralanmış varsa bu tür nesneler ile .NET Framework 4.0 seri durumdan çıkarılamıyor, üyeleri 4.0 ve 4.5 arasında eklendi. Serileştirilmiş verilerini seri hale getirilmiş hem aynı .NET Framework sürümü ile seri halinde sorun ortaya çıkar unutmayın.|
|Öneri|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> seri hale getirme yerine <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> seri hale getirme veya <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> .NET Framework değişiklikler dayanıklı olması.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

