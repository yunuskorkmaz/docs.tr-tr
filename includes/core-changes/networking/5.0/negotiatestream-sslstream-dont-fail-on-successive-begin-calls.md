---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050538"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="67cca-101">NegotiateStream ve SslStream ardışık başlama işlemlerine izin ver</span><span class="sxs-lookup"><span data-stu-id="67cca-101">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="67cca-102">Güvenlik akışlarındaki hata durumları farklı şekilde işlenir ve bir `BeginAuthenticateAsServer` veya daha fazla çağrı `BeginAuthenticateAsClient` başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="67cca-102">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="67cca-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="67cca-103">Version introduced</span></span>

<span data-ttu-id="67cca-104">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="67cca-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="67cca-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="67cca-105">Change description</span></span>

<span data-ttu-id="67cca-106">Önceki .NET sürümlerinde, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` ilk olarak çağrılmadan veya bir ile `EndAuthenticateAsServer` `EndAuthenticateAsClient` sonuçlamadan çok <xref:System.NotSupportedException> daha fazla.</span><span class="sxs-lookup"><span data-stu-id="67cca-106">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="67cca-107">.NET 5,0 ' den başlayarak, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` <xref:System.NotSupportedException> Bu API 'ler tabanlı bir uygulamayla korunduğundan, art arda yapılan çağrılar veya artık sonuç vermez <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="67cca-107">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="67cca-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="67cca-108">Reason for change</span></span>

<span data-ttu-id="67cca-109">İç uygulamanın zaman uyumsuz programlama modeli (APM) ile tabanlı olarak değiştirilmesi <xref:System.Threading.Tasks.Task> performansı artırır ve kod karmaşıklığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="67cca-109">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="67cca-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="67cca-110">Recommended action</span></span>

<span data-ttu-id="67cca-111">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="67cca-111">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="67cca-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="67cca-112">Category</span></span>

<span data-ttu-id="67cca-113">Ağ</span><span class="sxs-lookup"><span data-stu-id="67cca-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="67cca-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="67cca-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

-->
