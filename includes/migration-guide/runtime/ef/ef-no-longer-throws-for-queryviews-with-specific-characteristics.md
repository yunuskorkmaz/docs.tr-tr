---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803233"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF artık belirli özelliklere sahip QueryViews için atmadı

|   |   |
|---|---|
|Ayrıntılar|Varlık Çerçevesi, bir <xref:System.StackOverflowException?displayProperty=name> uygulama sorgunun bir parçası olarak ilgili varlıkları dahil etmeye çalışan 0..1 gezinme özelliğine sahip bir QueryView içeren bir sorgu yürüdüğünde artık bir özel durum atmaz. Örneğin, arayarak. <code>.Include(e =&gt; e.RelatedNavProp)</code>|
|Öneri|Bu değişiklik yalnızca 1-0..1 ilişkileri ile QueryViews kullanan kodu etkiler. Içerir. Güvenilirliği artırır ve hemen hemen tüm uygulamalariçin saydam olmalıdır. Ancak, beklenmeyen davranışlara neden oluyorsa, uygulamanın yapılandırma dosyasının <code>&lt;appSettings&gt;</code> bölümüne aşağıdaki girişi ekleyerek devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.5.2|
|Tür|Çalışma Zamanı|
