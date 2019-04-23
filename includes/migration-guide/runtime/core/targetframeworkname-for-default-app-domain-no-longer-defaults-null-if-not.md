---
ms.openlocfilehash: cbe1b32fa40e509f620845866c7a584e37f49a80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774239"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Null değilse ayarlamak için varsayılan uygulama etki alanı için TargetFrameworkName artık varsayılan olarak

|   |   |
|---|---|
|Ayrıntılar|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Açıkça ayarlamadığınız sürece varsayılan uygulama etki alanında daha önce null idi. 4.6 içinde başlayan <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> özelliği varsayılan uygulama etki alanı için (varsa) TargetFrameworkAttribute türetilmiş bir varsayılan değer olacaktır. Varsayılan olmayan uygulama etki alanları devralmak devam edecek, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> (hangi 4.6 null varsayılan değil) varsayılan uygulama etki alanından, açıkça geçersiz kılınmadığı sürece.|
|Öneri|Kodu bağımlı değil için güncelleştirilmesi gerektiğini <xref:System.AppDomainSetup.TargetFrameworkName> null varsayılan olarak ayarlanıyor. Gerekirse bu özellik null olarak değerlendirilecek devam, onu açıkça bu değere ayarlanabilir.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
