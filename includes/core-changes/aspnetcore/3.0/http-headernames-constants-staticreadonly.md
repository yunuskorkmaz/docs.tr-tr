---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901700"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="c5184-101">HTTP: HeaderNames sabitleri statik ReadOnly olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="c5184-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="c5184-102">ASP.NET Core 3,0 Preview 5 ' ten başlayarak, <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> alan `const` `static readonly`olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="c5184-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="c5184-103">Tartışma için bkz. [DotNet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="c5184-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c5184-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c5184-104">Version introduced</span></span>

<span data-ttu-id="c5184-105">3.0</span><span class="sxs-lookup"><span data-stu-id="c5184-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c5184-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c5184-106">Old behavior</span></span>

<span data-ttu-id="c5184-107">Bu alanlar `const`için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5184-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c5184-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c5184-108">New behavior</span></span>

<span data-ttu-id="c5184-109">Bu alanlar artık `static readonly`.</span><span class="sxs-lookup"><span data-stu-id="c5184-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c5184-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c5184-110">Reason for change</span></span>

<span data-ttu-id="c5184-111">Değişiklik:</span><span class="sxs-lookup"><span data-stu-id="c5184-111">The change:</span></span>

* <span data-ttu-id="c5184-112">Değerlerin, gerektiğinde değer düzeltmeleri için derleme sınırları arasında gömülmesini önler.</span><span class="sxs-lookup"><span data-stu-id="c5184-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="c5184-113">Daha hızlı başvuru eşitlik denetimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5184-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c5184-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c5184-114">Recommended action</span></span>

<span data-ttu-id="c5184-115">3,0 ile yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="c5184-115">Recompile against 3.0.</span></span> <span data-ttu-id="c5184-116">Aşağıdaki yollarla bu alanları kullanan kaynak kodu bundan böyle devam edebilir:</span><span class="sxs-lookup"><span data-stu-id="c5184-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="c5184-117">Öznitelik bağımsız değişkeni olarak</span><span class="sxs-lookup"><span data-stu-id="c5184-117">As an attribute argument</span></span>
* <span data-ttu-id="c5184-118">`switch` bildiriminde `case` olarak</span><span class="sxs-lookup"><span data-stu-id="c5184-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="c5184-119">Başka bir `const` tanımlarken</span><span class="sxs-lookup"><span data-stu-id="c5184-119">When defining another `const`</span></span>

<span data-ttu-id="c5184-120">Son değişikliği geçici olarak çözmek için, kendi kendine tanımlanmış üst bilgi adı sabitleri veya dize sabit değerlerini kullanmaya geçin.</span><span class="sxs-lookup"><span data-stu-id="c5184-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="c5184-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="c5184-121">Category</span></span>

<span data-ttu-id="c5184-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c5184-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c5184-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c5184-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
