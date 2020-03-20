---
ms.openlocfilehash: cbe1b32fa40e509f620845866c7a584e37f49a80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858479"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Varsayılan uygulama etki alanı için TargetFrameworkName ayarlanmadığı takdirde artık null varsayılan

|   |   |
|---|---|
|Ayrıntılar|Açık <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> olarak ayarlanan olmadıkça, varsayılan uygulama etki alanında daha önce null oldu. 4.6'dan başlayarak, varsayılan uygulama etki alanının <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> özelliği TargetFrameworkAttribute'tan türetilen varsayılan bir değere sahip olacaktır (varsa). Varsayılan olmayan uygulama etki alanları, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> açıkça geçersiz kılınmadığı sürece varsayılan uygulama etki alanından (varsayılan olarak 4,6'da geçersiz kılınmayan) devralmaya devam eder.|
|Öneri|Kod, <xref:System.AppDomainSetup.TargetFrameworkName> varsayılan olarak null'a bağlı olmayacak şekilde güncelleştirilmelidir. Bu özelliğin null olarak değerlendirmeye devam etmesi gerekiyorsa, açıkça bu değere ayarlanabilir.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
