### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService artık dikkate

|   |   |
|---|---|
|Ayrıntılar|Bu ayar bir WCF Hizmeti etkinleştirilebilmesi için önce sunucuda kullanılabilir olması gereken en az bellek belirler. Önlemek üzere tasarlanmış <xref:System.OutOfMemoryException?displayProperty=name> özel durumları. .NET Framework 4.5 bu ayarı herhangi bir etkisi vardı. .NET Framework 4.5.1'da, ayar dikkate alınır.|
|Öneri|Web sunucusunda kullanılabilir boş bellek yapılandırma ayarı tarafından tanımlanan yüzdeden küçük olduğunda bir özel durum oluşur. Başarıyla başlatıldı ve kısıtlı bellek ortamında çalışan bazı WCF hizmetleri artık başarısız olabilir.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|çalışma zamanı|

