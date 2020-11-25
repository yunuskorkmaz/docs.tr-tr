---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032764"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="c6bf8-101">HTTP: HeaderNames sabitleri statik ReadOnly olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="c6bf8-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="c6bf8-102">ASP.NET Core 3,0 Preview 5 ' ten başlayarak, içindeki alanlar <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> olarak değişir `const` `static readonly` .</span><span class="sxs-lookup"><span data-stu-id="c6bf8-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="c6bf8-103">Tartışma için bkz. [DotNet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="c6bf8-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c6bf8-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c6bf8-104">Version introduced</span></span>

<span data-ttu-id="c6bf8-105">3,0</span><span class="sxs-lookup"><span data-stu-id="c6bf8-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c6bf8-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c6bf8-106">Old behavior</span></span>

<span data-ttu-id="c6bf8-107">Bu alanlar için kullanılır `const` .</span><span class="sxs-lookup"><span data-stu-id="c6bf8-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c6bf8-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c6bf8-108">New behavior</span></span>

<span data-ttu-id="c6bf8-109">Bu alanlar artık `static readonly` .</span><span class="sxs-lookup"><span data-stu-id="c6bf8-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c6bf8-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c6bf8-110">Reason for change</span></span>

<span data-ttu-id="c6bf8-111">Değişiklik:</span><span class="sxs-lookup"><span data-stu-id="c6bf8-111">The change:</span></span>

* <span data-ttu-id="c6bf8-112">Değerlerin, gerektiğinde değer düzeltmeleri için derleme sınırları arasında gömülmesini önler.</span><span class="sxs-lookup"><span data-stu-id="c6bf8-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="c6bf8-113">Daha hızlı başvuru eşitlik denetimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6bf8-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c6bf8-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c6bf8-114">Recommended action</span></span>

<span data-ttu-id="c6bf8-115">3,0 ile yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="c6bf8-115">Recompile against 3.0.</span></span> <span data-ttu-id="c6bf8-116">Aşağıdaki yollarla bu alanları kullanan kaynak kodu bundan böyle devam edebilir:</span><span class="sxs-lookup"><span data-stu-id="c6bf8-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="c6bf8-117">Öznitelik bağımsız değişkeni olarak</span><span class="sxs-lookup"><span data-stu-id="c6bf8-117">As an attribute argument</span></span>
* <span data-ttu-id="c6bf8-118">Bir `case` `switch` bildirimde olarak</span><span class="sxs-lookup"><span data-stu-id="c6bf8-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="c6bf8-119">Başka bir tanımlama `const`</span><span class="sxs-lookup"><span data-stu-id="c6bf8-119">When defining another `const`</span></span>

<span data-ttu-id="c6bf8-120">Son değişikliği geçici olarak çözmek için, kendi kendine tanımlanmış üst bilgi adı sabitleri veya dize sabit değerlerini kullanmaya geçin.</span><span class="sxs-lookup"><span data-stu-id="c6bf8-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="c6bf8-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="c6bf8-121">Category</span></span>

<span data-ttu-id="c6bf8-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6bf8-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c6bf8-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c6bf8-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
