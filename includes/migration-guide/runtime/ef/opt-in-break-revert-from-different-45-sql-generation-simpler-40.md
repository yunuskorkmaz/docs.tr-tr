---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803219"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Farklı 4,5 SQL neslinden daha basit 4.0 SQL nesle dönmek için devre dışı bırakma

|   |   |
|---|---|
|Ayrıntılar|JOIN deyimleri üreten ve orderby'yi kullanmadan sınırlayıcı bir işlem çağrısı içeren sorgular artık daha basit BIR SQL üretir. .NET Framework 4.5'e yükselttikten sonra, bu sorgular önceki sürümlerden daha karmaşık SQL üretti.|
|Öneri|Bu özellik varsayılan olarak devre dışı bırakılır. Entity Framework performans düşüşüne neden olan ek JOIN deyimleri oluşturursa, uygulama <code>&lt;appSettings&gt;</code> yapılandırması (app.config) dosyasının bölümüne aşağıdaki girişi ekleyerek bu özelliği etkinleştirebilirsiniz:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|
