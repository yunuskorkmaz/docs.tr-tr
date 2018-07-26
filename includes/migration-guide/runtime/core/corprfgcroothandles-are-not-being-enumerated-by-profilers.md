### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs profil oluşturucular tarafından numaralandırılan değil

|   |   |
|---|---|
|Ayrıntılar|.NET Framework v4.5.1, profil oluşturma API içinde <code>RootReferences2()</code> yanlış hiçbir zaman döndüren <code>COR_PRF_GC_ROOT_HANDLE</code> (olarak döndürülen <code>COR_PRF_GC_ROOT_OTHER</code> bunun yerine). .NET Framework 4. 6 ' ' den itibaren bu sorun düzeltilmiştir.|
|Öneri|Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|

