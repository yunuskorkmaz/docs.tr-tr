### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute ObsoleteAttribute ve DeprecatedAttribute WinMD senaryolarda verir

|   |   |
|---|---|
|Ayrıntılar|Bir Windows meta verileri kitaplığı (.winmd dosyası) oluşturduğunuzda <xref:System.ObsoleteAttribute?displayProperty=name> özniteliği her ikisi de aktarılır <xref:System.ObsoleteAttribute?displayProperty=name> ve [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Öneri|Kullanan mevcut kaynak kodu derleme <xref:System.ObsoleteAttribute?displayProperty=name> özniteliği, uyarılar oluşturabilir, bu koddan C + kullanırken +/ CX veya JavaScript.We önerilmez hem de uygulama <xref:System.ObsoleteAttribute?displayProperty=name> ve [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) Yönetilen derlemeler; kodunda yapı uyarısına neden.|
|Kapsam|Kenar|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|

