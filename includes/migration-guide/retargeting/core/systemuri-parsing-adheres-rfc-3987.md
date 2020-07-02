---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617279"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="c309b-101">System. Uri ayrıştırma, RFC 3987 ' e uyar</span><span class="sxs-lookup"><span data-stu-id="c309b-101">System.Uri parsing adheres to RFC 3987</span></span>

#### <a name="details"></a><span data-ttu-id="c309b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c309b-102">Details</span></span>

<span data-ttu-id="c309b-103">URI ayrıştırma .NET Framework 4,5 ' de çeşitli yollarla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c309b-103">URI parsing has changed in several ways in .NET Framework 4.5.</span></span> <span data-ttu-id="c309b-104">Ancak, bu değişikliklerin yalnızca 4,5 .NET Framework kod hedeflemesi etkilediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c309b-104">Note, however, that these changes only affect code targeting .NET Framework 4.5.</span></span> <span data-ttu-id="c309b-105">Bir ikili .NET Framework 4,0 hedefliyorsa, eski davranış gözlenecek.</span><span class="sxs-lookup"><span data-stu-id="c309b-105">If a binary targets .NET Framework 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="c309b-106">.NET Framework 4,5 ' de URI ayrıştırmasında yapılan değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="c309b-106">Changes to URI parsing in .NET Framework 4.5 include:</span></span>

- <span data-ttu-id="c309b-107">URI ayrıştırma, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c309b-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span>
- <span data-ttu-id="c309b-108">Unicode normalleştirme biçimi C yalnızca URI 'nin ana bilgisayar bölümünde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c309b-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span>
- <span data-ttu-id="c309b-109">Geçersiz mailto: URI 'Ler şimdi bir özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="c309b-109">Invalid mailto: URIs will now cause an exception.</span></span>
- <span data-ttu-id="c309b-110">Bir yol kesiminin sonundaki sondaki noktalar artık korunur.</span><span class="sxs-lookup"><span data-stu-id="c309b-110">Trailing dots at the end of a path segment are now preserved.</span></span>
- <span data-ttu-id="c309b-111">`file://`URI 'Ler karakterden kaçmaz `?` .</span><span class="sxs-lookup"><span data-stu-id="c309b-111">`file://` URIs do not escape the `?` character.</span></span>
- <span data-ttu-id="c309b-112">İle Unicode denetim `U+0080` karakterleri `U+009F` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c309b-112">Unicode control characters `U+0080` through `U+009F` are not supported.</span></span>
- <span data-ttu-id="c309b-113">Virgül karakterleri `,` veya `%2c` otomatik olarak geri atlanmaz.</span><span class="sxs-lookup"><span data-stu-id="c309b-113">Comma characters `,` or `%2c` are not automatically unescaped.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c309b-114">Öneri</span><span class="sxs-lookup"><span data-stu-id="c309b-114">Suggestion</span></span>

<span data-ttu-id="c309b-115">Eski .NET Framework 4,0 URI ayrıştırma semantiği gerekliyse (genellikle bunlar), .NET Framework 4,0 ' i hedefleyerek kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="c309b-115">If the old .NET Framework 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET Framework 4.0.</span></span> <span data-ttu-id="c309b-116">Bu, <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> derlemede bir veya ' Proje Özellikleri ' sayfasında Visual Studio 'nun proje sistem kullanıcı arabirimi aracılığıyla gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c309b-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>

| <span data-ttu-id="c309b-117">Name</span><span class="sxs-lookup"><span data-stu-id="c309b-117">Name</span></span>    | <span data-ttu-id="c309b-118">Değer</span><span class="sxs-lookup"><span data-stu-id="c309b-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c309b-119">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c309b-119">Scope</span></span>   | <span data-ttu-id="c309b-120">Ana</span><span class="sxs-lookup"><span data-stu-id="c309b-120">Major</span></span>       |
| <span data-ttu-id="c309b-121">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c309b-121">Version</span></span> | <span data-ttu-id="c309b-122">4,5</span><span class="sxs-lookup"><span data-stu-id="c309b-122">4.5</span></span>         |
| <span data-ttu-id="c309b-123">Tür</span><span class="sxs-lookup"><span data-stu-id="c309b-123">Type</span></span>    | <span data-ttu-id="c309b-124">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="c309b-124">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c309b-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c309b-125">Affected APIs</span></span>

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
