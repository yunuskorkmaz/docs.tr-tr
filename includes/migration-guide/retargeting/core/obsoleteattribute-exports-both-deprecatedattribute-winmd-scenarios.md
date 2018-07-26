### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute WinMD senaryolarda ObsoleteAttribute ve DeprecatedAttribute dışarı aktarır

|   |   |
|---|---|
|Ayrıntılar|Windows meta veri (.winmd dosyası) kitaplık oluşturduğunuzda <xref:System.ObsoleteAttribute?displayProperty=name> özniteliği, her ikisi de olarak aktarılır <xref:System.ObsoleteAttribute?displayProperty=name> ve [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Öneri|Yeniden derleme kullanan mevcut kaynak kodu <xref:System.ObsoleteAttribute?displayProperty=name> özniteliği, uyarılar oluşturabilir, bu kodu nereden C + tüketildiğinde +/ CX veya JavaScript.We önerilmez hem de uygulama <xref:System.ObsoleteAttribute?displayProperty=name> ve [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) Yönetilen derlemeler; kodunda derleme uyarıların sonuçlanabilir.|
|Kapsam|Kenar|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|

