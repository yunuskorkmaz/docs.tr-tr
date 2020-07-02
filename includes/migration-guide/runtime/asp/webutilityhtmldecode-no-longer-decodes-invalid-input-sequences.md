---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620540"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmLşifre çözme artık geçersiz giriş sıralarının kodunu çözer

#### <a name="details"></a>Ayrıntılar

Varsayılan olarak, kod çözme yöntemleri artık geçersiz bir girdi dizisini geçersiz bir UTF-16 dizisi halinde çözemez. Bunun yerine, özgün girişi geri döndürürler.

#### <a name="suggestion"></a>Öneri

Kod çözücü çıktısındaki değişiklik yalnızca dizelerde UTF-16 verileri yerine ikili veriler saklıyorsanız önemli olmalıdır. Bu davranışı açıkça denetlemek için, <code>aspnet:AllowRelaxedUnicodeDecoding</code> [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) öğesinin özniteliğini, <code>true</code> eski davranışı etkinleştirmek veya <code>false</code> geçerli davranışı etkinleştirmek için olarak ayarlayın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
