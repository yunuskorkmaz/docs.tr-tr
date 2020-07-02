---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621372"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="430a1-101">Unicode mevcut olduğunda özel göreli URI gösterimini destekleme</span><span class="sxs-lookup"><span data-stu-id="430a1-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="430a1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="430a1-102">Details</span></span>

<span data-ttu-id="430a1-103"><xref:System.Uri>, artık <xref:System.NullReferenceException> <xref:System.Uri.TryCreate%2A> Unicode içeren belirli göreli URI 'ler üzerinde çağrılırken bir oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="430a1-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="430a1-104">En basit üretilmesi, <xref:System.NullReferenceException> iki deyimle denk olacak şekilde aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="430a1-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="430a1-105"><xref:System.NullReferenceException>Öğesini yeniden oluşturmak için aşağıdaki öğelerin doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="430a1-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="430a1-106">URI, ' http: ' ile bir ön bekleyen olarak belirtilmelidir ve '//' ile takip edilmez.</span><span class="sxs-lookup"><span data-stu-id="430a1-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="430a1-107">URI, yüzde kodlamalı Unicode veya ayrılmamış simgeler içermelidir.</span><span class="sxs-lookup"><span data-stu-id="430a1-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="430a1-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="430a1-108">Suggestion</span></span>

<span data-ttu-id="430a1-109">Göreli URI 'lara izin vermemek için bu davranışa bağlı olarak, <xref:System.UriKind.Absolute?displayProperty=nameWithType> bir URI oluşturma sırasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="430a1-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="430a1-110">Name</span><span class="sxs-lookup"><span data-stu-id="430a1-110">Name</span></span>    | <span data-ttu-id="430a1-111">Değer</span><span class="sxs-lookup"><span data-stu-id="430a1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="430a1-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="430a1-112">Scope</span></span>   |<span data-ttu-id="430a1-113">Edge</span><span class="sxs-lookup"><span data-stu-id="430a1-113">Edge</span></span>|
|<span data-ttu-id="430a1-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="430a1-114">Version</span></span>|<span data-ttu-id="430a1-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="430a1-115">4.7.2</span></span>|
|<span data-ttu-id="430a1-116">Tür</span><span class="sxs-lookup"><span data-stu-id="430a1-116">Type</span></span>|<span data-ttu-id="430a1-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="430a1-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="430a1-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="430a1-118">Affected APIs</span></span>

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
