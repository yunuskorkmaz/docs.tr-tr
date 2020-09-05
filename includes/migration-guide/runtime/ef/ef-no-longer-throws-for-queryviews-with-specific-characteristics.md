---
ms.openlocfilehash: ceae6b85c14862b1b1183d01def0dda723ee0c2b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497315"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF artık belirli özelliklere sahip QueryViews için oluşturmaz

#### <a name="details"></a>Ayrıntılar

Entity Framework, bir uygulama bir <xref:System.StackOverflowException?displayProperty=fullName> QueryView içeren bir sorgu yürüttüğünde, ilişkili varlıkları sorgunun bir parçası olarak içerme girişiminde bulunan 0.. 1 gezinti özelliği içeren bir sorgu çalıştırdığında artık bir özel durum oluşturmaz. Örneğin, çağırarak <code>.Include(e =&gt; e.RelatedNavProp)</code> .

#### <a name="suggestion"></a>Öneri

Bu değişiklik yalnızca, çağıran sorguları çalıştırırken 1-0.. 1 ilişkiyle birlikte QueryViews kullanan kodu etkiler. İçeriyor. Güvenilirliği artırır ve neredeyse tüm uygulamalara şeffaf olmalıdır. Ancak, beklenmeyen davranışlara neden oluyorsa, <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasının bölümüne aşağıdaki girdiyi ekleyerek devre dışı bırakabilirsiniz:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
