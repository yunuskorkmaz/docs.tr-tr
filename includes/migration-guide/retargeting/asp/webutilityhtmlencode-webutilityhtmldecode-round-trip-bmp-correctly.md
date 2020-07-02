---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617261"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode ve WebUtility.HtmlDecode, BMP üzerinde doğru şekilde gidiş ve dönüş gerçekleştiriyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.5’i hedefleyen uygulamalar için, Temel Çok Dilli Düzlem (BMP) dışındaki karakterler <xref:System.Net.WebUtility.HtmlDecode(System.String)> metotlarına geçirildiğinde, doğru bir şekilde gidiş ve dönüş yapar.

#### <a name="suggestion"></a>Öneri

Bu değişikliğin geçerli uygulamalar üzerinde hiçbir etkisi olmamalıdır, ancak özgün davranışı geri yüklemek için, `targetFramework` `<httpRuntime>` öğesinin özniteliğini "4,5" dışında bir dizeye ayarlayın. Ayrıca bu davranışı, hedeflenen .NET Framework sürümünden bağımsız olarak denetlemek için `<webUtility>` yapılandırma öğesinin `unicodeEncodingConformance` ve `unicodeDecodingConformance` özniteliklerini ayarlayabilirsiniz.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
