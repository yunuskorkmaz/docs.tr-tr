---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236670"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Öğesinden farklı 4.5 SQL oluşturma için daha basit 4.0 SQL oluşturma dönmek için kabul etme sonu

|   |   |
|---|---|
|Ayrıntılar|JOIN deyimleri oluşturmak ve bir çağrı içeren sorgular sınırlayan bir işleme ilk olmadan OrderBy artık ürettiğiniz daha basit SQL. Bu sorgular, .NET Framework 4.5 sürümüne yükselttikten sonra önceki sürümlerinden daha karmaşık SQL oluşturdu.|
|Öneri|Bu özellik varsayılan olarak devre dışıdır. Entity Framework performans düşüşüne neden fazladan JOIN deyimleri oluşturursa aşağıdaki girişe ekleyerek bu özelliği etkinleştirebilirsiniz <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasından bölümünü:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|
