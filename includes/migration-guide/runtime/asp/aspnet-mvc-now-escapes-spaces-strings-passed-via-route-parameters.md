---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774279"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC artık alanları dizelerinde de rota parametreleri aracılığıyla düğümlere geçirilir çıkışları

|   |   |
|---|---|
|Ayrıntılar|RFC 2396 uymak için rota yollarda alanları artık bir rota eylemi parametrelerinden doldurulurken atlanır. Bu nedenle, oysa <code>/controller/action/some data</code> rota daha önce eşleşir <code>/controller/action/{data}</code> ve sağlayın <code>some data</code> veri parametre olarak, artık sağlayacak <code>some%20data</code> bunun yerine.|
|Öneri|Kod bir rotadaki dizesi parametreleri unescape güncelleştirilmesi gerekir. Özgün bir URI gerekirse ile erişilebileceğini <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.|
|Kapsam|İkincil|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
