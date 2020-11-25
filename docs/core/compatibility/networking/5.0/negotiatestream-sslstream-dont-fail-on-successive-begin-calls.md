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
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream ve SslStream ardışık başlama işlemlerine izin ver

Güvenlik akışlarındaki hata durumları farklı şekilde işlenir ve bir `BeginAuthenticateAsServer` veya daha fazla çağrı `BeginAuthenticateAsClient` başarısız olabilir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` ilk olarak çağrılmadan veya bir ile `EndAuthenticateAsServer` `EndAuthenticateAsClient` sonuçlamadan çok <xref:System.NotSupportedException> daha fazla. .NET 5,0 ' den başlayarak, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` <xref:System.NotSupportedException> Bu API 'ler tabanlı bir uygulamayla korunduğundan, art arda yapılan çağrılar veya artık sonuç vermez <xref:System.Threading.Tasks.Task> .

## <a name="reason-for-change"></a>Değişiklik nedeni

İç uygulamanın zaman uyumsuz programlama modeli (APM) ile tabanlı olarak değiştirilmesi <xref:System.Threading.Tasks.Task> performansı artırır ve kod karmaşıklığını azaltır.

## <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez.

## <a name="affected-apis"></a>Etkilenen API’ler

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
