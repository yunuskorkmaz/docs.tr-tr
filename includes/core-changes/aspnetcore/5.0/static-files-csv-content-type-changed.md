---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391188"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Statik dosyalar: CSV içerik türü standartlara uygun olarak değiştirildi

Core 5.0ASP.NETde, `Content-Type` Statik Dosya Ara `text/csv` *ware'inin .csv* dosyaları için kullandığı varsayılan yanıt üstbilgi değeri standartlara uygun değere değiştirildi. [Static File Middleware](/aspnet/core/fundamentals/static-files)

Bu konuda tartışma için [dotnet/aspnetcore#17385'e](https://github.com/dotnet/AspNetCore/issues/17385)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

5.0 Önizleme 1

#### <a name="old-behavior"></a>Eski davranış

Üstbilgi `Content-Type` değeri `application/octet-stream` kullanıldı.

#### <a name="new-behavior"></a>Yeni davranış

Üstbilgi `Content-Type` değeri `text/csv` kullanılır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standardına uygunluk.

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik uygulamanızı etkilerse, dosya uzantısından MIME türüne eşlemesini özelleştirebilirsiniz. MIME türüne `application/octet-stream` dönmek için, 'deki yöntem çağrısını <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> değiştirin. `Startup.Configure` Örnek:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Eşlemenin özelleştirilmesi hakkında daha fazla bilgi için [FileExtensionContentTypeProvider'a](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)bakın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
