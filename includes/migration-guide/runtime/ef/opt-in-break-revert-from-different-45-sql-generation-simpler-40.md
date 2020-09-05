---
ms.openlocfilehash: 346fb6ecd43f7f93529e45f169c79b7acacc9c1f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497934"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Farklı 4,5 SQL neslini daha basit 4,0 SQL oluşturmaya geri dönmek için kabul etme kesmesi

#### <a name="details"></a>Ayrıntılar

JOIN deyimleri üreten ve önce OrderBy kullanılmadan sınırlayan bir işleme çağrı içeren sorgular artık daha basit bir SQL üretin. .NET Framework 4,5 ' e yükselttikten sonra, bu sorgular önceki sürümlerden daha karmaşık bir SQL üretti.

#### <a name="suggestion"></a>Öneri

Bu özellik varsayılan olarak devre dışıdır. Entity Framework, performans düşüşüne neden olan ek JOIN deyimleri oluşturursa, <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasının bölümüne aşağıdaki girişi ekleyerek bu özelliği etkinleştirebilirsiniz:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Geçirgen|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
