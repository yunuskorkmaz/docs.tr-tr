---
ms.openlocfilehash: ab7731d34aad5b6b6481f13ba11b778393e2cac2
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761426"
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

