### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>MachineKey.Encode ve MachineKey.Decode yöntemleri geçersiz

|   |   |
|---|---|
|Ayrıntılar|Bu yöntemler artık kullanım dışıdır. Bu yöntemleri çağıran kodun derlemesi bir derleyici uyarısı meydana getirir.|
|Öneri|Önerilen Alternatiflerle olan <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> ve <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Alternatif olarak, derleme uyarıları gizlenebilir veya eski bir derleyici kullanılarak önlenebilir. API'ler hala desteklenmektedir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|

