---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617280"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a><span data-ttu-id="f0285-101">System. Uri. ıwellformeduristring yöntemi, ilk kesimde iki nokta üst üste karakteri olan göreli URI 'Ler için false döndürür</span><span class="sxs-lookup"><span data-stu-id="f0285-101">System.Uri.IsWellFormedUriString method returns false for relative URIs with a colon char in first segment</span></span>

#### <a name="details"></a><span data-ttu-id="f0285-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f0285-102">Details</span></span>

<span data-ttu-id="f0285-103">.NET Framework 4,5 ' den başlayarak, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> göreli URI 'leri `:` ilk segmentlerinde ile, doğru biçimlendirilmemiş olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f0285-103">Beginning with the .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> will treat relative URIs with a `:` in their first segment as not well formed.</span></span> <span data-ttu-id="f0285-104">Bu, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> RFC3986 ile uyumlu hale getirilme .NET Framework 4,0 ' deki davranış değişikdir.</span><span class="sxs-lookup"><span data-stu-id="f0285-104">This is a change from <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> behavior in the .NET Framework 4.0 that was made to conform to RFC3986.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f0285-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="f0285-105">Suggestion</span></span>

<span data-ttu-id="f0285-106">Bu değişiklik (diğer birçok URI değişikliği gibi) yalnızca .NET Framework 4,5 (veya üzeri) hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f0285-106">This change (like many other URI changes) will only affect applications targeting the .NET Framework 4.5 (or later).</span></span> <span data-ttu-id="f0285-107">Eski davranışı kullanmaya devam etmek için uygulamayı 4,0 .NET Framework karşı hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="f0285-107">To keep using the old behavior, target the app against the .NET Framework 4.0.</span></span> <span data-ttu-id="f0285-108">Alternatif olarak, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> `:` eski davranışı tercih ediyorsanız, doğrulama amacıyla kaldırmak isteyebileceğiniz karakterleri arayarak, URI 'yi tarayın.</span><span class="sxs-lookup"><span data-stu-id="f0285-108">Alternatively, scan URI's prior to calling <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> looking for `:` characters that you may want to remove for validation purposes, if the old behavior is desirable.</span></span>

| <span data-ttu-id="f0285-109">Name</span><span class="sxs-lookup"><span data-stu-id="f0285-109">Name</span></span>    | <span data-ttu-id="f0285-110">Değer</span><span class="sxs-lookup"><span data-stu-id="f0285-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0285-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f0285-111">Scope</span></span>   | <span data-ttu-id="f0285-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="f0285-112">Minor</span></span>       |
| <span data-ttu-id="f0285-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f0285-113">Version</span></span> | <span data-ttu-id="f0285-114">4,5</span><span class="sxs-lookup"><span data-stu-id="f0285-114">4.5</span></span>         |
| <span data-ttu-id="f0285-115">Tür</span><span class="sxs-lookup"><span data-stu-id="f0285-115">Type</span></span>    | <span data-ttu-id="f0285-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="f0285-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f0285-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f0285-117">Affected APIs</span></span>

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
