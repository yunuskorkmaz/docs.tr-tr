---
title: 'Son değişiklik: NegotiateStream ve SslStream art arda başlama işlemlerine izin ver'
description: .NET 5 ' teki önemli değişiklik hakkında bilgi edinmek için güvenlik akışlarındaki hata durumlarının farklı işlendiği ve BeginAuthenticateAsServer veya BeginAuthenticateAsClient için art arda yapılan çağrılar artık başarısız olmayabilir.
ms.date: 10/18/2020
ms.openlocfilehash: 5c042be01873849cc154111a31fc007521508c7b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256445"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream ve SslStream ardışık başlama işlemlerine izin ver

Güvenlik akışlarındaki hata durumları farklı şekilde işlenir ve bir `BeginAuthenticateAsServer` veya daha fazla çağrı `BeginAuthenticateAsClient` başarısız olabilir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` ilk olarak çağrılmadan veya bir ile `EndAuthenticateAsServer` `EndAuthenticateAsClient` sonuçlamadan çok <xref:System.NotSupportedException> daha fazla. .NET 5 ' den başlayarak, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` <xref:System.NotSupportedException> Bu API 'ler tabanlı bir uygulamayla korunduğundan, art arda yapılan çağrılar veya artık sonuç vermez <xref:System.Threading.Tasks.Task> .

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
