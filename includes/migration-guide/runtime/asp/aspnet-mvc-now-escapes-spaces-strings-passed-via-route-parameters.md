---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620536"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC şimdi yol parametreleri aracılığıyla geçirilen dizelerin içindeki boşlukları çıkar

#### <a name="details"></a>Ayrıntılar

RFC 2396 ' e uymak için rota yollarındaki boşluklar artık bir rotadaki eylem parametreleri doldurulurken kaçışla sonuçlanır. Bu nedenle, <code>/controller/action/some data</code> daha önce rotayla eşleşmekte <code>/controller/action/{data}</code> ve <code>some data</code> veri parametresi olarak sağlayacağından, artık <code>some%20data</code> bunun yerine sağlama yapılır.

#### <a name="suggestion"></a>Öneri

Kod, bir rotadaki kaçış dize parametrelerine karşı güncellenmelidir. Özgün URI gerekliyse, ile erişilebilir <xref:System.Net.HttpWebRequest.RequestUri> . OriginalString API 'SI.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
