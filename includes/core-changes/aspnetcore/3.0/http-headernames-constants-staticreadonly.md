---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901700"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="6e956-101">HTTP: BaşlıkAdları sabitleri yalnızca statik okunur olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="6e956-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="6e956-102">Core 3.0 Preview 5ASP.NET'den <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> `const` başlayarak, `static readonly`'deki alanlar .</span><span class="sxs-lookup"><span data-stu-id="6e956-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="6e956-103">Tartışma için [dotnet/aspnetcore#9514'e](https://github.com/dotnet/aspnetcore/issues/9514)bakın.</span><span class="sxs-lookup"><span data-stu-id="6e956-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6e956-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="6e956-104">Version introduced</span></span>

<span data-ttu-id="6e956-105">3,0</span><span class="sxs-lookup"><span data-stu-id="6e956-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6e956-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="6e956-106">Old behavior</span></span>

<span data-ttu-id="6e956-107">Bu alanlar `const`eskiden.</span><span class="sxs-lookup"><span data-stu-id="6e956-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6e956-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="6e956-108">New behavior</span></span>

<span data-ttu-id="6e956-109">Bu alanlar `static readonly`artık.</span><span class="sxs-lookup"><span data-stu-id="6e956-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6e956-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="6e956-110">Reason for change</span></span>

<span data-ttu-id="6e956-111">Değişiklik:</span><span class="sxs-lookup"><span data-stu-id="6e956-111">The change:</span></span>

* <span data-ttu-id="6e956-112">Değerlerin montaj sınırları nın ötesine gömülmesini önler ve gerektiğinde değer düzeltmelerine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e956-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="6e956-113">Daha hızlı başvuru eşitliği denetimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e956-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6e956-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6e956-114">Recommended action</span></span>

<span data-ttu-id="6e956-115">3.0'a karşı yeniden derle.</span><span class="sxs-lookup"><span data-stu-id="6e956-115">Recompile against 3.0.</span></span> <span data-ttu-id="6e956-116">Bu alanları aşağıdaki yollarla kullanan kaynak kodu artık bunu yapamaz:</span><span class="sxs-lookup"><span data-stu-id="6e956-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="6e956-117">Öznitelik bağımsız değişkeni olarak</span><span class="sxs-lookup"><span data-stu-id="6e956-117">As an attribute argument</span></span>
* <span data-ttu-id="6e956-118">`case` Bir `switch` açıklamada olduğu gibi</span><span class="sxs-lookup"><span data-stu-id="6e956-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="6e956-119">Başka bir tanımlama`const`</span><span class="sxs-lookup"><span data-stu-id="6e956-119">When defining another `const`</span></span>

<span data-ttu-id="6e956-120">Kesme değişikliğini aşmak için, kendi tanımladığı üstbilgi adı sabitlerini veya dize gerçeklerini kullanmaya geçin.</span><span class="sxs-lookup"><span data-stu-id="6e956-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="6e956-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="6e956-121">Category</span></span>

<span data-ttu-id="6e956-122">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="6e956-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6e956-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6e956-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
