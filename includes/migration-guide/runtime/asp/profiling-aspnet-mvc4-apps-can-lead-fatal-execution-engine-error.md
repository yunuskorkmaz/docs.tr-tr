---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649572"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>ASP.Net MVC4 uygulamaları profil oluşturma için önemli yürütme altyapısı hata neden olabilir

|   |   |
|---|---|
|Ayrıntılar|NGEN/profile bütünleştirilmiş kodları kullanarak profil oluşturucular başlangıçta 'Önemli yürütme altyapısı bir özel durum' ile profili oluşturulmuş ASP.NET MVC4 uygulamalarının çökebilir|
|Öneri|.NET Framework 4.5.2 Bu sorun düzeltilmiştir. Alternatif olarak, profil oluşturucu bu sorunu belirterek önlemek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> kendi olay maske.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
