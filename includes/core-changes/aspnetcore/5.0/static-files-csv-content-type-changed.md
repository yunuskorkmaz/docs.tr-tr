---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391188"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="b719a-101">Statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="b719a-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="b719a-102">ASP.NET Core 5,0 ' de, `Content-Type` [statik dosya ara yazılım](/aspnet/core/fundamentals/static-files) 'nin *. csv* dosyaları için kullandığı varsayılan yanıt üst bilgisi değeri, standartlara uyumlu değere değiştirilmiştir `text/csv` .</span><span class="sxs-lookup"><span data-stu-id="b719a-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="b719a-103">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="b719a-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b719a-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b719a-104">Version introduced</span></span>

<span data-ttu-id="b719a-105">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="b719a-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b719a-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b719a-106">Old behavior</span></span>

<span data-ttu-id="b719a-107">`Content-Type`Üst bilgi değeri `application/octet-stream` kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="b719a-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b719a-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b719a-108">New behavior</span></span>

<span data-ttu-id="b719a-109">`Content-Type`Üst bilgi değeri `text/csv` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b719a-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b719a-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b719a-110">Reason for change</span></span>

<span data-ttu-id="b719a-111">[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standardına uyum.</span><span class="sxs-lookup"><span data-stu-id="b719a-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b719a-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b719a-112">Recommended action</span></span>

<span data-ttu-id="b719a-113">Bu değişiklik uygulamanızı etkile etkileirse, dosya uzantısı-MIME tür eşlemesini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b719a-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="b719a-114">MIME türüne dönmek için `application/octet-stream` <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> içindeki yöntem çağrısını değiştirin `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="b719a-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="b719a-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b719a-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="b719a-116">Eşlemeyi özelleştirme hakkında daha fazla bilgi için bkz. [Fileextensioncontenttypeprovider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="b719a-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="b719a-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="b719a-117">Category</span></span>

<span data-ttu-id="b719a-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b719a-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b719a-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b719a-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
