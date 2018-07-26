### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>.NET Framework 4. 5'altında serileştirilen MailMessage nesneleri seri durumdan çıkarma işlemi başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 ile başlayarak <xref:System.Web.Mail.MailMessage> nesneleri, ASCII olmayan karakterler içerebilir. .NET Framework 4'te yalnızca ASCII karakterleri desteklenir. <xref:System.Web.Mail.MailMessage> ASCII olmayan karakterler içeren ve .NET Framework 4.5 ya da daha sonra serileştirilmiş nesneler, .NET Framework 4 altında seri durumdan çıkarılamıyor.|
|Öneri|Kodunuzu işlenirken özel durum işleme sağladığı, bir <xref:System.Web.Mail.MailMessage> nesne.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|

