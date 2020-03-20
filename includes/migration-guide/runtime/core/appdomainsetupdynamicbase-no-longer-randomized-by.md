---
ms.openlocfilehash: 3f553f95941eaf36cf335e9765a670a05bd157f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858367"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase artık UseRandomizedStringHashAlgorithm tarafından randomize edilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6'dan önce, <xref:System.AppDomainSetup.DynamicBase> uygulamanın config dosyasında RandomizedStringHashAlgorithm etkinleştirilmişse, uygulama etki alanları arasında veya işlemler arasında randomize edilecektir. .NET Framework 4.6'dan <xref:System.AppDomainSetup.DynamicBase> başlayarak, çalışan bir uygulamanın farklı örnekleri ile farklı uygulama etki alanları arasında kararlı bir sonuç döndürecektir. Dinamik tabanlar farklı uygulamalar için farklılık gösterir; bu değişiklik yalnızca aynı uygulamanın farklı örnekleri için rasgele adlandırma öğesini kaldırır.|
|Öneri|Etkinleştirme <code>UseRandomizedStringHashAlgorithm</code> randomize <xref:System.AppDomainSetup.DynamicBase> neden olmaz unutmayın. Rasgele bir taban gerekiyorsa, bu API yerine uygulamanızın kodunda üretilmelidir.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
