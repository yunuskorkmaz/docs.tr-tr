### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>Farklı bir .NET sürüm ile seri hale getirilmiş bir ConcurrentDictionary seri durumdan çıkarılacak NetDataContractSerializer başarısız

|   |   |
|---|---|
|Ayrıntılar|Tasarıma göre <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> yalnızca hem seri hale getirme ve uçları seri durumdan aynı CLR Türleri paylaşıyorsa kullanılabilir. Bu nedenle, bir .NET Framework sürümü ile seri hale getirilmiş bir nesneyi farklı bir sürüm tarafından seri durumdan çıkarılabiliyorsa garanti edilmez.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> bilinen doğru .NET Framework 4.5 veya önceki serileştirilmiş ve .NET Framework 4.5.1 serisi seri durumdan değil ya da daha yeni bir türüdür.|
|Öneri|Bu sorunun olası iş geçici çözüm vardır:<ul><li>.NET Framework 4.5.1, de kullanmak için biçimlendiricisi bilgisayar yükseltin.</li><li>Kullanım <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> yerine <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> tam aynı CLR türlerini hem seri hale getirme ve uçları seri durumdan beklemiyor gibi.</li><li>Kullanım <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> yerine <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> , bu belirli 4.5 - gerçekleştirilmez beri&gt;4.5.1 bölün.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|

