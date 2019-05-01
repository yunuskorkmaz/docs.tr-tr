---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093616"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF QueryViews için belirli özelliklere sahip artık oluşturur.

|   |   |
|---|---|
|Ayrıntılar|Entity Framework artık oluşturur bir <xref:System.StackOverflowException?displayProperty=name> uygulama ile bir 0..1 bir QueryView içeren bir sorgu yürütüldüğünde bir özel durum sorgunun bir parçası ilişkili varlıkları içermesi dener gezinme özelliği. Örneğin, arama tarafından <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Öneri|Bu değişiklik, yalnızca 1 ile QueryViews kullanan kodu etkiler-0..1 çalışan bu çağrı sorguladığında ilişkileri. İçerir. Güvenilirlik artar ve neredeyse tüm uygulamalar için saydam olmalıdır. Beklenmeyen davranışlara neden olur, ancak bu aşağıdaki girişe ekleyerek devre dışı bırakabilirsiniz <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|
