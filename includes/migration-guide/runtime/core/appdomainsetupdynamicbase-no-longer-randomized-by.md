---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621412"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup. DynamicBase artık UseRandomizedStringHashAlgorithm tarafından rasgeleleştirilmedi

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' dan önce, değeri <xref:System.AppDomainSetup.DynamicBase> uygulama etki alanları arasında rastgele hale getirilir veya UseRandomizedStringHashAlgorithm, uygulamanın yapılandırma dosyasında etkinleştirildiyse, süreçler arasında rasgeledir. .NET Framework 4,6 ' den başlayarak, <xref:System.AppDomainSetup.DynamicBase> çalıştıran bir uygulamanın farklı örnekleri arasında ve farklı uygulama etki alanları arasında kararlı bir sonuç döndürür. Dinamik tabanlar farklı uygulamalar için hala farklılık gösterir; Bu değişiklik yalnızca aynı uygulamanın farklı örneklerinin rastgele adlandırma öğesini kaldırır.

#### <a name="suggestion"></a>Öneri

Etkinleştirmenin rastgele hale gelemeyeceğini unutmayın <code>UseRandomizedStringHashAlgorithm</code> <xref:System.AppDomainSetup.DynamicBase> . Rastgele bir taban gerekliyse, bu API 'nin yerine uygulamanızın kodunda oluşturulması gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
