---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391188"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi

ASP.NET Core 5,0 ' de, `Content-Type` [statik dosya ara yazılım](/aspnet/core/fundamentals/static-files) 'nin *. csv* dosyaları için kullandığı varsayılan yanıt üst bilgisi değeri, standartlara uyumlu değere değiştirilmiştir `text/csv` .

Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

#### <a name="old-behavior"></a>Eski davranış

`Content-Type`Üst bilgi değeri `application/octet-stream` kullanıldı.

#### <a name="new-behavior"></a>Yeni davranış

`Content-Type`Üst bilgi değeri `text/csv` kullanılır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standardına uyum.

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik uygulamanızı etkile etkileirse, dosya uzantısı-MIME tür eşlemesini özelleştirebilirsiniz. MIME türüne dönmek için `application/octet-stream` <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> içindeki yöntem çağrısını değiştirin `Startup.Configure` . Örnek:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Eşlemeyi özelleştirme hakkında daha fazla bilgi için bkz. [Fileextensioncontenttypeprovider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
