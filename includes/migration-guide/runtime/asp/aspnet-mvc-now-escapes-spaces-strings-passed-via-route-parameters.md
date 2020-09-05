---
ms.openlocfilehash: afbf34710c75d0f0586ddfdb2e7937d8d76d5399
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497728"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC şimdi yol parametreleri aracılığıyla geçirilen dizelerin içindeki boşlukları çıkar

#### <a name="details"></a>Ayrıntılar

RFC 2396 ' e uymak için rota yollarındaki boşluklar artık bir rotadaki eylem parametreleri doldurulurken kaçışla sonuçlanır. Bu nedenle,  <code>/controller/action/some data</code> daha önce rotayla eşleşmekte <code>/controller/action/{data}</code> ve <code>some data</code> veri parametresi olarak sağlayacağından, artık <code>some%20data</code> bunun yerine sağlama yapılır.

#### <a name="suggestion"></a>Öneri

Kod, bir rotadaki kaçış dize parametrelerine karşı güncellenmelidir. Özgün URI gerekliyse, ile erişilebilir <xref:System.Net.HttpWebRequest.RequestUri> . OriginalString API 'SI.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)>

<!--

#### Affected APIs

- `M:System.Web.Mvc.RouteAttribute.#ctor(System.String)`

-->
