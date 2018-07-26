### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService artık uyulduğundan

|   |   |
|---|---|
|Ayrıntılar|Bu ayar, bir WCF hizmet aktif edilmeden önce sunucuda bellek alt sınırı belirler. Önlemek üzere tasarlanmış <xref:System.OutOfMemoryException?displayProperty=name> özel durumlar. .NET Framework 4.5, bu ayarın hiçbir etkisi vardı. .NET Framework 4.5.1, ayar dikkate alınır.|
|Öneri|Web sunucusunda kullanılabilir boş bellek yapılandırma ayarları tarafından tanımlandığı yüzdenin ise bir özel durum oluşur. Başarıyla başlatıldı ve kısıtlı bellek ortamında çalışan bazı WCF hizmetlerinde başarısız olabilir.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|

