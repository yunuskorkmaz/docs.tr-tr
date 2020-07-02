---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620627"
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
