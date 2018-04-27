### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Yanlış kod oluşturma geçirme ve UInt16 değerleri karşılaştırma

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda .NET Framework 4.7 sunulan değişiklikler nedeniyle, .NET Framework 4.7 üzerinde hatalı çalışan uygulamalardaki JIT Derleyici tarafından üretilen kod iki karşılaştırır <code>T:System.UInt16</code> değerleri. Daha fazla bilgi için bkz: [sorunu #11508: geçirme ve karşılaştırma ushort args sessiz hatalı codegen](https://github.com/dotnet/coreclr/issues/11508) Github.com'u üzerinde.|
|Öneri|.NET Framework 4.7 16 bit işaretsiz değerleri karşılaştırma sorunlarla karşılaşırsanız, .NET Framework 4.7.1 yükseltin.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

