---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394326"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="40a19-101">HTTP: HeaderNames sabitleri statik ReadOnly olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="40a19-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="40a19-102">ASP.NET Core 3,0 Preview 5 ' ten başlayarak, <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> ' daki alanlar `const` ' den `static readonly` ' ye değişti.</span><span class="sxs-lookup"><span data-stu-id="40a19-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="40a19-103">Tartışma için bkz. [ASPNET/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="40a19-103">For discussion, see [aspnet/AspNetCore#9514](https://github.com/aspnet/AspNetCore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40a19-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="40a19-104">Version introduced</span></span>

<span data-ttu-id="40a19-105">3.0</span><span class="sxs-lookup"><span data-stu-id="40a19-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="40a19-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="40a19-106">Old behavior</span></span>

<span data-ttu-id="40a19-107">Bu alanlar `const` olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40a19-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="40a19-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="40a19-108">New behavior</span></span>

<span data-ttu-id="40a19-109">Bu alanlar artık `static readonly` ' dır.</span><span class="sxs-lookup"><span data-stu-id="40a19-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="40a19-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="40a19-110">Reason for change</span></span>

<span data-ttu-id="40a19-111">Değişiklik:</span><span class="sxs-lookup"><span data-stu-id="40a19-111">The change:</span></span>

* <span data-ttu-id="40a19-112">Değerlerin, gerektiğinde değer düzeltmeleri için derleme sınırları arasında gömülmesini önler.</span><span class="sxs-lookup"><span data-stu-id="40a19-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="40a19-113">Daha hızlı başvuru eşitlik denetimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="40a19-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40a19-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="40a19-114">Recommended action</span></span>

<span data-ttu-id="40a19-115">3,0 ile yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="40a19-115">Recompile against 3.0.</span></span> <span data-ttu-id="40a19-116">Aşağıdaki yollarla bu alanları kullanan kaynak kodu bundan böyle devam edebilir:</span><span class="sxs-lookup"><span data-stu-id="40a19-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="40a19-117">Öznitelik bağımsız değişkeni olarak</span><span class="sxs-lookup"><span data-stu-id="40a19-117">As an attribute argument</span></span>
* <span data-ttu-id="40a19-118">Bir `switch` ifadesinde `case`</span><span class="sxs-lookup"><span data-stu-id="40a19-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="40a19-119">Başka bir @no__t tanımlarken-0</span><span class="sxs-lookup"><span data-stu-id="40a19-119">When defining another `const`</span></span>

<span data-ttu-id="40a19-120">Son değişikliği geçici olarak çözmek için, kendi kendine tanımlanmış üst bilgi adı sabitleri veya dize sabit değerlerini kullanmaya geçin.</span><span class="sxs-lookup"><span data-stu-id="40a19-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="40a19-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="40a19-121">Category</span></span>

<span data-ttu-id="40a19-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40a19-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40a19-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="40a19-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
