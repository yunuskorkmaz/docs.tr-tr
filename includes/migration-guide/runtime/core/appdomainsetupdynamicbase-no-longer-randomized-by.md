---
ms.openlocfilehash: 3f553f95941eaf36cf335e9765a670a05bd157f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664544"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase UseRandomizedStringHashAlgorithm tarafından artık rastgeledir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 değerini önce <xref:System.AppDomainSetup.DynamicBase> UseRandomizedStringHashAlgorithm uygulamanın yapılandırma dosyasında etkinleştirilirse işlemleri veya uygulama etki alanları arasında rastgele. .NET Framework 4.6, başlangıç <xref:System.AppDomainSetup.DynamicBase> çalıştıran bir uygulama farklı örnekleri arasında ve farklı uygulama etki alanları arasında tutarlı bir sonuç döndürür. Dinamik tabanları farklı uygulamalar için yine de değişir; Bu değişiklik, yalnızca aynı uygulamanın farklı örneklerini için rastgele adlandırma öğeyi kaldırır.|
|Öneri|Unutmayın, etkinleştirme <code>UseRandomizedStringHashAlgorithm</code> açmayacaktır <xref:System.AppDomainSetup.DynamicBase> rastgele. Rastgele temel gerekirse, uygulamanızın kod yerine bu API aracılığıyla oluşturulması gerekir.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
