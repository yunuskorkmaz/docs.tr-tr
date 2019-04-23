---
ms.openlocfilehash: dfc1a0d05142861ff1c1b7391126d86e09fa71c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805329"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>Geçersiz giriş dizilerini WebUtility.HtmlDecode artık kodunu çözer

|   |   |
|---|---|
|Ayrıntılar|Varsayılan olarak, kod çözme yöntemleri artık geçersiz bir girdi dizisini geçersiz bir UTF-16 dizisi halinde çözemez. Bunun yerine, özgün girişi geri döndürürler.|
|Öneri|Kod çözücü çıktısındaki değişiklik yalnızca dizelerde UTF-16 verileri yerine ikili veriler saklıyorsanız önemli olmalıdır. Bu davranışı açıkça denetlemek için ayarlanmış <code>aspnet:AllowRelaxedUnicodeDecoding</code> özniteliği [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) öğesine <code>true</code> eski davranışı etkinleştirmek için veya <code>false</code> geçerli davranışı etkinleştirmek için.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
