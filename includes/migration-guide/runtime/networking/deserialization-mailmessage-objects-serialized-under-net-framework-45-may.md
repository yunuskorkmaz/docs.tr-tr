### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>.NET Framework 4. 5'altında seri posta iletisi nesneleri seri durumdan çıkarma başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 ile başlayan <xref:System.Web.Mail.MailMessage> nesneleri ASCII olmayan karakterler içerebilir. .NET Framework 4'te yalnızca ASCII karakterleri desteklenir. <xref:System.Web.Mail.MailMessage> .NET Framework 4 altında ASCII olmayan karakterler içeren ve .NET Framework 4.5 veya sonraki sürümlerinde seri nesneleri serisi kaldırılamıyor.|
|Öneri|Kodunuzu işlenirken özel durum işleme sağladığından emin olun bir <xref:System.Web.Mail.MailMessage> nesnesi.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|

