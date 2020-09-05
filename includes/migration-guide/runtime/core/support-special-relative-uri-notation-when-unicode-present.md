---
ms.openlocfilehash: 3c32d2e13447f8fd9aa6b185b5fc7e60f9e1bb61
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497236"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="02bba-101">Unicode mevcut olduğunda özel göreli URI gösterimini destekleme</span><span class="sxs-lookup"><span data-stu-id="02bba-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="02bba-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="02bba-102">Details</span></span>

<span data-ttu-id="02bba-103"><xref:System.Uri> , artık <xref:System.NullReferenceException> <xref:System.Uri.TryCreate%2A> Unicode içeren belirli göreli URI 'ler üzerinde çağrılırken bir oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="02bba-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="02bba-104">En basit üretilmesi, <xref:System.NullReferenceException> iki deyimle denk olacak şekilde aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="02bba-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="02bba-105"><xref:System.NullReferenceException>Öğesini yeniden oluşturmak için aşağıdaki öğelerin doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="02bba-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="02bba-106">URI, ' http: ' ile bir ön bekleyen olarak belirtilmelidir ve '//' ile takip edilmez.</span><span class="sxs-lookup"><span data-stu-id="02bba-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="02bba-107">URI, yüzde kodlamalı Unicode veya ayrılmamış simgeler içermelidir.</span><span class="sxs-lookup"><span data-stu-id="02bba-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="02bba-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="02bba-108">Suggestion</span></span>

<span data-ttu-id="02bba-109">Göreli URI 'lara izin vermemek için bu davranışa bağlı olarak, <xref:System.UriKind.Absolute?displayProperty=nameWithType> bir URI oluşturma sırasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="02bba-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="02bba-110">Name</span><span class="sxs-lookup"><span data-stu-id="02bba-110">Name</span></span>    | <span data-ttu-id="02bba-111">Değer</span><span class="sxs-lookup"><span data-stu-id="02bba-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="02bba-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="02bba-112">Scope</span></span>   |<span data-ttu-id="02bba-113">Edge</span><span class="sxs-lookup"><span data-stu-id="02bba-113">Edge</span></span>|
|<span data-ttu-id="02bba-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="02bba-114">Version</span></span>|<span data-ttu-id="02bba-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="02bba-115">4.7.2</span></span>|
|<span data-ttu-id="02bba-116">Tür</span><span class="sxs-lookup"><span data-stu-id="02bba-116">Type</span></span>|<span data-ttu-id="02bba-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="02bba-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="02bba-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="02bba-118">Affected APIs</span></span>

- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)`
- `M:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)`
- `M:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)`

-->
