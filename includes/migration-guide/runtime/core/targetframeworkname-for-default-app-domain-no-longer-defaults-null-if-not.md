---
ms.openlocfilehash: f221f923381d874e1d9e8b420811a770d86f7578
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858479"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Null değilse ayarlamak için varsayılan uygulama etki alanı için TargetFrameworkName artık varsayılan olarak

|   |   |
|---|---|
|Ayrıntılar|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Açıkça ayarlamadığınız sürece varsayılan uygulama etki alanında daha önce null idi. 4\.6 içinde başlayan <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> özelliği varsayılan uygulama etki alanı için (varsa) TargetFrameworkAttribute türetilmiş bir varsayılan değer olacaktır. Varsayılan olmayan uygulama etki alanları devralmak devam edecek, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> (hangi 4.6 null varsayılan değil) varsayılan uygulama etki alanından, açıkça geçersiz kılınmadığı sürece.|
|Öneri|Kodu bağımlı değil için güncelleştirilmesi gerektiğini <xref:System.AppDomainSetup.TargetFrameworkName> null varsayılan olarak ayarlanıyor. Gerekirse bu özellik null olarak değerlendirilecek devam, onu açıkça bu değere ayarlanabilir.|
|`Scope`|Kenar|
|Version|4.6|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

