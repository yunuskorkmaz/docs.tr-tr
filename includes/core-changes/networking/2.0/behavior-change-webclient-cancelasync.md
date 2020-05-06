---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859628"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a>WebClient. Iptallasync her zaman hemen iptal etmez

.NET Core 2,0 ' den başlayarak, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> çağrı yanıt getirilmeye başladıysa isteği hemen iptal etmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> çağıran isteği hemen iptal etti. .NET Core 2,0 ' den başlayarak, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> çağrı yalnızca yanıt getirmeyi başlatmamışsa isteği hemen iptal eder. Yanıt getirilmeye başladıysa, istek yalnızca bir yanıt okunduktan sonra iptal edilir.

Bu değişiklik, API 'nin <xref:System.Net.WebClient> <xref:System.Net.Http.HttpClient>kullanım dışı bırakıldığı için uygulandı.

#### <a name="version-introduced"></a>Sunulan sürüm

2,0

#### <a name="recommended-action"></a>Önerilen eylem

Kullanım dışı <xref:System.Net.Http.HttpClient?displayProperty=fullName> olan yerine <xref:System.Net.WebClient?displayProperty=fullName>sınıfı kullanın.

#### <a name="category"></a>Kategori

Ağ

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
