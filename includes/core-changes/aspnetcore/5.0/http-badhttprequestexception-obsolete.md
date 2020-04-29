---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507110"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="e009f-101">HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="e009f-101">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="e009f-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor olarak işaretlendi ve öğesinden `Microsoft.AspNetCore.Http.BadHttpRequestException`türetilme değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="e009f-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="e009f-103">Kestrel ve IIS sunucuları geriye dönük uyumluluk için eski özel durum türlerini hala oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e009f-103">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="e009f-104">Eski türler gelecek sürümde kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="e009f-104">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="e009f-105">Tartışma için bkz. [DotNet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="e009f-105">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e009f-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e009f-106">Version introduced</span></span>

<span data-ttu-id="e009f-107">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="e009f-107">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e009f-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e009f-108">Old behavior</span></span>

<span data-ttu-id="e009f-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` öğesinden <xref:System.IO.IOException?displayProperty=nameWithType>türetilir.</span><span class="sxs-lookup"><span data-stu-id="e009f-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e009f-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e009f-110">New behavior</span></span>

<span data-ttu-id="e009f-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e009f-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="e009f-112">Türler Ayrıca `Microsoft.AspNetCore.Http.BadHttpRequestException`öğesinden türetilir `System.IO.IOException`.</span><span class="sxs-lookup"><span data-stu-id="e009f-112">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e009f-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e009f-113">Reason for change</span></span>

<span data-ttu-id="e009f-114">Değişikliğin yapıldığı yer:</span><span class="sxs-lookup"><span data-stu-id="e009f-114">The change was made to:</span></span>

* <span data-ttu-id="e009f-115">Yinelenen türleri birleştirin.</span><span class="sxs-lookup"><span data-stu-id="e009f-115">Consolidate duplicate types.</span></span>
* <span data-ttu-id="e009f-116">Sunucu uygulamalarında davranışı bütünleştirme.</span><span class="sxs-lookup"><span data-stu-id="e009f-116">Unify behavior across server implementations.</span></span>

<span data-ttu-id="e009f-117">Uygulama artık Kestrel veya IIS kullanırken temel özel `Microsoft.AspNetCore.Http.BadHttpRequestException` durumu yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="e009f-117">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e009f-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e009f-118">Recommended action</span></span>

<span data-ttu-id="e009f-119">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` Ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` kullanımlarının kullanımlarını ile `Microsoft.AspNetCore.Http.BadHttpRequestException`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e009f-119">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

#### <a name="category"></a><span data-ttu-id="e009f-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="e009f-120">Category</span></span>

<span data-ttu-id="e009f-121">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="e009f-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e009f-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e009f-122">Affected APIs</span></span>

- [<span data-ttu-id="e009f-123">Microsoft. AspNetCore. Server. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="e009f-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="e009f-124">Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="e009f-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
