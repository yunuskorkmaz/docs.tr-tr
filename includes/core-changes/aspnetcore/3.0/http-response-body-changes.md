---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198589"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: Yanıt gövde altyapı değişiklikleri

BIR HTTP yanıt organını destekleyen altyapı değişti. Doğrudan kullanıyorsanız, `HttpResponse` herhangi bir kod değişikliği yapmanız gerekmez. Sarma lıyor, değiştiriyor `HttpResponse.Body` veya erişiyorsanız `HttpContext.Features`daha fazla bilgi edinin.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

HTTP yanıt gövdesi ile ilişkili üç API vardı:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Yeni davranış

Değiştirirseniz, `HttpResponse.Body`beklenen API'lerin tümü için varsayılan uygulamaları `StreamResponseBodyFeature` sağlamak için verilen akışınızın etrafındaki bir sarmalayıcıyla tümünün `IHttpResponseBodyFeature` yerini alır. Özgün akışı geri ayarlamak bu değişikliği geri döndürer.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Motivasyon tek bir yeni özellik arabirimi içine yanıt gövdesi API'ler birleştirmektir.

#### <a name="recommended-action"></a>Önerilen eylem

Daha `IHttpResponseBodyFeature` önce kullandığınız `IHttpResponseFeature.Body` `IHttpSendFileFeature`yeri , `IHttpBufferingFeature`veya .

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

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
