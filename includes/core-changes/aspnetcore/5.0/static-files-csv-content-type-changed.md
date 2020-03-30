---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391188"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="ce2e9-101">Statik dosyalar: CSV içerik türü standartlara uygun olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="ce2e9-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="ce2e9-102">Core 5.0ASP.NETde, `Content-Type` Statik Dosya Ara `text/csv` *ware'inin .csv* dosyaları için kullandığı varsayılan yanıt üstbilgi değeri standartlara uygun değere değiştirildi. [Static File Middleware](/aspnet/core/fundamentals/static-files)</span><span class="sxs-lookup"><span data-stu-id="ce2e9-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="ce2e9-103">Bu konuda tartışma için [dotnet/aspnetcore#17385'e](https://github.com/dotnet/AspNetCore/issues/17385)bakın.</span><span class="sxs-lookup"><span data-stu-id="ce2e9-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ce2e9-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="ce2e9-104">Version introduced</span></span>

<span data-ttu-id="ce2e9-105">5.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="ce2e9-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ce2e9-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="ce2e9-106">Old behavior</span></span>

<span data-ttu-id="ce2e9-107">Üstbilgi `Content-Type` değeri `application/octet-stream` kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="ce2e9-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ce2e9-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="ce2e9-108">New behavior</span></span>

<span data-ttu-id="ce2e9-109">Üstbilgi `Content-Type` değeri `text/csv` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce2e9-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ce2e9-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="ce2e9-110">Reason for change</span></span>

<span data-ttu-id="ce2e9-111">[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standardına uygunluk.</span><span class="sxs-lookup"><span data-stu-id="ce2e9-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ce2e9-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ce2e9-112">Recommended action</span></span>

<span data-ttu-id="ce2e9-113">Bu değişiklik uygulamanızı etkilerse, dosya uzantısından MIME türüne eşlemesini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce2e9-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="ce2e9-114">MIME türüne `application/octet-stream` dönmek için, 'deki yöntem çağrısını <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> değiştirin. `Startup.Configure`</span><span class="sxs-lookup"><span data-stu-id="ce2e9-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="ce2e9-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ce2e9-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="ce2e9-116">Eşlemenin özelleştirilmesi hakkında daha fazla bilgi için [FileExtensionContentTypeProvider'a](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)bakın.</span><span class="sxs-lookup"><span data-stu-id="ce2e9-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="ce2e9-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="ce2e9-117">Category</span></span>

<span data-ttu-id="ce2e9-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce2e9-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ce2e9-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ce2e9-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
