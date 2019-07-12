---
ms.openlocfilehash: 64d540278544e74c46d46b77c97bccd26d4116dd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803219"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Öğesinden farklı 4.5 SQL oluşturma için daha basit 4.0 SQL oluşturma dönmek için kabul etme sonu

|   |   |
|---|---|
|Ayrıntılar|JOIN deyimleri oluşturmak ve bir çağrı içeren sorgular sınırlayan bir işleme ilk olmadan OrderBy artık ürettiğiniz daha basit SQL. Bu sorgular, .NET Framework 4.5 sürümüne yükselttikten sonra önceki sürümlerinden daha karmaşık SQL oluşturdu.|
|Öneri|Bu özellik varsayılan olarak devre dışıdır. Entity Framework performans düşüşüne neden fazladan JOIN deyimleri oluşturursa aşağıdaki girişe ekleyerek bu özelliği etkinleştirebilirsiniz <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasından bölümünü:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|

