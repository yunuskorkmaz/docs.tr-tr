### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>.NET Framework 4. 5'NetDataContractSerializer ile seri ConcurrentDictionary .NET Framework 4.5.1 veya 4.5.2 tarafından kaldırılamaz

|   |   |
|---|---|
|Ayrıntılar|Türü iç değişiklikler nedeniyle <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ile .NET Framework 4.5 serileştirilmiş nesneler kullanarak <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> .NET Framework 4.5.1 veya .NET Framework 4.5.2.Note kaldırılamaz bir yön (Bu taşıma .NET Framework ile seri hale getirme 4.5.x ve .NET Framework 4. 5'ile seri) çalışır. Benzer şekilde, tüm 4.x sürümler arası seri hale getirme ile .NET Framework 4.6.Serializing çalışır ve tek bir .NET Framework sürümü ile seri durumdan etkilenmez.|
|Öneri|Seri hale getirmek ve seri durumdan gerekliyse bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> .NET Framework 4.5 ve .NET Framework 4.5.1/4.5.2 arasında alternatif bir seri hale getirici gibi <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> seri hale getirici, yerine kullanılmalıdır <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Bu sorun .NET Framework 4.6 ele olduğundan, alternatif olarak, bu .NET Framework'ün bu sürümüne yükselterek çözülmesi.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|

