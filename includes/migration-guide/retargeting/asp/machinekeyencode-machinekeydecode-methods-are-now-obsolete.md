### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>MachineKey.Encode ve MachineKey.Decode yöntemleri artık kullanılmamaktadır

|   |   |
|---|---|
|Ayrıntılar|Bu yöntemler artık kullanım dışıdır. Bu yöntemleri çağıran kodun derlemesi bir derleyici uyarısı meydana getirir.|
|Öneri|Önerilen alternatifler, <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> ve <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Alternatif olarak, derleme uyarıları gizlenebilir ya da daha eski bir derleyici kullanılarak önlenebilir. API'leri hala desteklenmektedir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|

