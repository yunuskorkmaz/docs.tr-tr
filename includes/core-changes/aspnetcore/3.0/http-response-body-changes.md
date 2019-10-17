---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394120"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: yanıt gövdesi altyapı değişiklikleri

Bir HTTP yanıt gövdesini yedekleyen altyapı değişti. @No__t-0 ' ı doğrudan kullanıyorsanız, herhangi bir kod değişikliği yapmanız gerekmez. @No__t-0 ' yı sardıysanız veya değiştirirken veya `HttpContext.Features` ' i kullanırken daha fazla bilgi edinin.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

HTTP yanıt gövdesi ile ilişkili üç API vardı:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Yeni davranış

@No__t-0 ' ı değiştirirseniz, tüm `IHttpResponseBodyFeature` ' i, tüm beklenen API 'Ler için varsayılan uygulamalar sağlamak üzere `StreamResponseBodyFeature` kullanarak verilen akışlarınızın etrafındaki bir sarmalayıcı ile değiştirir. Özgün akışın geri ayarlanması bu değişikliği geri alır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Mosyon, yanıt gövdesi API 'Lerini tek bir yeni özellik arabirimi halinde birleştirmenize olanak sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

Daha önce `IHttpResponseFeature.Body`, `IHttpSendFileFeature` veya `IHttpBufferingFeature` ' ü kullandığınız `IHttpResponseBodyFeature` ' ı kullanın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>
 
<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
