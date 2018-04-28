### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>PrintSystemJobInfo.JobStream için yazılan veriler XPS biçiminde olmalıdır

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Printing.PrintSystemJobInfo.JobStream> Özelliği bir yazdırma işi akışı kullanıma sunar. Kullanıcı bu akışa yazarak temel işletim sistemi yazdırma bileşenleri ham veriler gönderebilir. Bu akışa yazılan veriler, Windows 8 ve Windows işletim sisteminin sonraki sürümlerini .NET Framework 4.5 sürümünden itibaren bir paket akışı XPS biçiminde olmalıdır.|
|Öneri|Yazdırma içerik çıktısını almak için aşağıdakilerden birini yapabilirsiniz:<ul><li>Kullanım <xref:System.Windows.Xps.XpsDocumentWriter> yazdırma içerik çıktısını almak için sınıf. Önerilen seçenek budur.</li><li>Tarafından döndürülen akışa gönderilen verileri emin <xref:System.Printing.PrintSystemJobInfo.JobStream> özelliği olan bir paket akışı olarak XPS biçiminde.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|

