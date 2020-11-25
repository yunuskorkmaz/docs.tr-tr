---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032772"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: yanıt gövdesi altyapı değişiklikleri

Bir HTTP yanıt gövdesini yedekleyen altyapı değişti. `HttpResponse`Doğrudan kullanıyorsanız, herhangi bir kod değişikliği yapmanız gerekmez. Sarmalandıysanız veya değiştiriyorsanız daha fazla bilgi edinin `HttpResponse.Body` `HttpContext.Features` .

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

HTTP yanıt gövdesi ile ilişkili üç API vardı:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Yeni davranış

`HttpResponse.Body`' Yi değiştirirseniz, `IHttpResponseBodyFeature` `StreamResponseBodyFeature` tüm beklenen API 'ler için varsayılan uygulamalar sağlamak üzere, kullanarak, verilen akışın çevresindeki bir sarmalayıcı ile tamamen değiştirilir. Özgün akışın geri ayarlanması bu değişikliği geri alır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Mosyon, yanıt gövdesi API 'Lerini tek bir yeni özellik arabirimi halinde birleştirmenize olanak sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

`IHttpResponseBodyFeature`Daha önce, veya kullandığınızı kullanın `IHttpResponseFeature.Body` `IHttpSendFileFeature` `IHttpBufferingFeature` .

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
