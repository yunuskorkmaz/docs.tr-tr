---
title: 'Son değişiklik: NegotiateStream ve SslStream art arda başlama işlemlerine izin ver'
description: Güvenlik akış5,0 larındaki hata durumlarının farklı işlendiği ve BeginAuthenticateAsServer veya BeginAuthenticateAsClient 'a yönelik art arda çağrılar artık başarısız olmayabilir.
ms.date: 10/18/2020
ms.openlocfilehash: e0226d0f5586efca050ca3497ca1490fa21fd943
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761437"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="fa2d4-103">NegotiateStream ve SslStream ardışık başlama işlemlerine izin ver</span><span class="sxs-lookup"><span data-stu-id="fa2d4-103">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="fa2d4-104">Güvenlik akışlarındaki hata durumları farklı şekilde işlenir ve bir `BeginAuthenticateAsServer` veya daha fazla çağrı `BeginAuthenticateAsClient` başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-104">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fa2d4-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="fa2d4-105">Version introduced</span></span>

<span data-ttu-id="fa2d4-106">5.0</span><span class="sxs-lookup"><span data-stu-id="fa2d4-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="fa2d4-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="fa2d4-107">Change description</span></span>

<span data-ttu-id="fa2d4-108">Önceki .NET sürümlerinde, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` ilk olarak çağrılmadan veya bir ile `EndAuthenticateAsServer` `EndAuthenticateAsClient` sonuçlamadan çok <xref:System.NotSupportedException> daha fazla.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-108">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="fa2d4-109">.NET 5,0 ' den başlayarak, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` <xref:System.NotSupportedException> Bu API 'ler tabanlı bir uygulamayla korunduğundan, art arda yapılan çağrılar veya artık sonuç vermez <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="fa2d4-109">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="fa2d4-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="fa2d4-110">Reason for change</span></span>

<span data-ttu-id="fa2d4-111">İç uygulamanın zaman uyumsuz programlama modeli (APM) ile tabanlı olarak değiştirilmesi <xref:System.Threading.Tasks.Task> performansı artırır ve kod karmaşıklığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-111">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fa2d4-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="fa2d4-112">Recommended action</span></span>

<span data-ttu-id="fa2d4-113">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-113">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fa2d4-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fa2d4-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

### Category

Networking

-->
