---
title: 'Son değişiklik: statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi'
description: "Statik dosyaları başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: CSV içerik türü, standartlara uyumlu olarak değiştirildi"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c94a0cf213970d20559b7c061d8be220b43961e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761709"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="a0b6a-103">Statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="a0b6a-103">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="a0b6a-104">ASP.NET Core 5,0 ' de, `Content-Type` [statik dosya ara yazılım](/aspnet/core/fundamentals/static-files) 'nin *. csv* dosyaları için kullandığı varsayılan yanıt üst bilgisi değeri, standartlara uyumlu değere değiştirilmiştir `text/csv` .</span><span class="sxs-lookup"><span data-stu-id="a0b6a-104">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="a0b6a-105">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="a0b6a-105">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a0b6a-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a0b6a-106">Version introduced</span></span>

<span data-ttu-id="a0b6a-107">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="a0b6a-107">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a0b6a-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a0b6a-108">Old behavior</span></span>

<span data-ttu-id="a0b6a-109">`Content-Type`Üst bilgi değeri `application/octet-stream` kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="a0b6a-109">The `Content-Type` header value `application/octet-stream` was used.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a0b6a-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a0b6a-110">New behavior</span></span>

<span data-ttu-id="a0b6a-111">`Content-Type`Üst bilgi değeri `text/csv` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0b6a-111">The `Content-Type` header value `text/csv` is used.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a0b6a-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a0b6a-112">Reason for change</span></span>

<span data-ttu-id="a0b6a-113">[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standardına uyum.</span><span class="sxs-lookup"><span data-stu-id="a0b6a-113">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a0b6a-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a0b6a-114">Recommended action</span></span>

<span data-ttu-id="a0b6a-115">Bu değişiklik uygulamanızı etkile etkileirse, dosya uzantısı-MIME tür eşlemesini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0b6a-115">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="a0b6a-116">MIME türüne dönmek için `application/octet-stream` <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> içindeki yöntem çağrısını değiştirin `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="a0b6a-116">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="a0b6a-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a0b6a-117">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="a0b6a-118">Eşlemeyi özelleştirme hakkında daha fazla bilgi için bkz. [Fileextensioncontenttypeprovider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="a0b6a-118">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a0b6a-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a0b6a-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
