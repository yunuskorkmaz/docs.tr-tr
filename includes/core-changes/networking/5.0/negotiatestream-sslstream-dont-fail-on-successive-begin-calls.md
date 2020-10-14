---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050538"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream ve SslStream ardışık başlama işlemlerine izin ver

Güvenlik akışlarındaki hata durumları farklı şekilde işlenir ve bir `BeginAuthenticateAsServer` veya daha fazla çağrı `BeginAuthenticateAsClient` başarısız olabilir.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 RC1

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` ilk olarak çağrılmadan veya bir ile `EndAuthenticateAsServer` `EndAuthenticateAsClient` sonuçlamadan çok <xref:System.NotSupportedException> daha fazla. .NET 5,0 ' den başlayarak, `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` <xref:System.NotSupportedException> Bu API 'ler tabanlı bir uygulamayla korunduğundan, art arda yapılan çağrılar veya artık sonuç vermez <xref:System.Threading.Tasks.Task> .

#### <a name="reason-for-change"></a>Değişiklik nedeni

İç uygulamanın zaman uyumsuz programlama modeli (APM) ile tabanlı olarak değiştirilmesi <xref:System.Threading.Tasks.Task> performansı artırır ve kod karmaşıklığını azaltır.

#### <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez.

#### <a name="category"></a>Kategori

Ağ

#### <a name="affected-apis"></a>Etkilenen API’ler

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
