### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>Farklı bir .NET sürümü ile seri hale getirilmiş bir ConcurrentDictionary seri durumdan çıkarılacak NetDataContractSerializer başarısız

|   |   |
|---|---|
|Ayrıntılar|Tasarıma göre <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> yalnızca, aynı CLR Türleri serileştirmek hem de sona erer seri durumdan çıkarılırken paylaşıyorsa kullanılır. Bu nedenle, bir .NET Framework sürümü ile seri hale getirilmiş bir nesneyi farklı bir sürümü ile seri durumdan çıkarılabiliyorsa olduğunu garanti edilmez.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> bilinen doğru .NET Framework 4.5 veya önceki serileştirilmiş ve seri durumdan .NET Framework 4.5.1 ile seri durumdan değil veya sonraki bir türdür.|
|Öneri|Bu sorunun olası iş geçici çözüm vardır:<ul><li>.NET Framework 4.5.1 de kullanmak için serileştirmek bilgisayar yükseltin.</li><li>Kullanım <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> yerine <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> gibi tam aynı CLR türleri, hem seri hale getirme hem de sona erer seri durumdan çıkarılırken beklemiyor.</li><li>Kullanım <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> yerine <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> olduğundan, bu belirli 4.5 - gerçekleştirilmez&gt;4.5.1 bölün.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|

