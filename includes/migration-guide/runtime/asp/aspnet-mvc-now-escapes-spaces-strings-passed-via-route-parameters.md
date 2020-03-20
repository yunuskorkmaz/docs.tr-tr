---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803195"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC artık rota parametreleri üzerinden geçirilen dizeleri alanlarda kaçar

|   |   |
|---|---|
|Ayrıntılar|RFC 2396'ya uymak için, bir rotadan eylem parametreleri doldurulurken rota yollarında boşluklar artık kaçmaktadır. Bu nedenle, <code>/controller/action/some data</code> daha önce rota <code>/controller/action/{data}</code> eşleşen <code>some data</code> ve veri parametresi olarak <code>some%20data</code> sağlamak, şimdi yerine sağlayacaktır.|
|Öneri|Kod, bir rotadan kaçış dize parametreleri için güncelleştirilmelidir. Orijinal URI gerekirse, bu <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.|
|Kapsam|İkincil|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
