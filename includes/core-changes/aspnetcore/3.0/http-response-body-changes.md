---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198589"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: yanıt gövdesi altyapı değişiklikleri

Bir HTTP yanıt gövdesini yedekleyen altyapı değişti. `HttpResponse` doğrudan kullanıyorsanız, herhangi bir kod değişikliği yapmanız gerekmez. `HttpResponse.Body` sardıysanız veya değiştiriyorsanız ya da `HttpContext.Features`erişimi varsa daha fazla bilgi edinin.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

HTTP yanıt gövdesi ile ilişkili üç API vardı:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Yeni davranış

`HttpResponse.Body`değiştirirseniz, tüm `IHttpResponseBodyFeature`, tüm beklenen API 'Ler için varsayılan uygulamalar sağlamak üzere `StreamResponseBodyFeature` kullanarak verilen akışlarınızın etrafında bir sarmalayıcı ile değiştirir. Özgün akışın geri ayarlanması bu değişikliği geri alır.

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
