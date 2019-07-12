---
ms.openlocfilehash: 107b34c7bd26e1396e8a6638d6929c15de92b8e4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803267"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>ASP.Net MVC4 uygulamaları profil oluşturma için önemli yürütme altyapısı hata neden olabilir

|   |   |
|---|---|
|Ayrıntılar|NGEN/profile bütünleştirilmiş kodları kullanarak profil oluşturucular başlangıçta 'Önemli yürütme altyapısı bir özel durum' ile profili oluşturulmuş ASP.NET MVC4 uygulamalarının çökebilir|
|Öneri|.NET Framework 4.5.2 Bu sorun düzeltilmiştir. Alternatif olarak, profil oluşturucu bu sorunu belirterek önlemek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> kendi olay maske.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

