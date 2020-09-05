---
ms.openlocfilehash: c679cb2603d39f580203d9373d76481e904e6c1d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497366"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profil oluşturma ASP.Net MVC4 Apps önemli yürütme altyapısı hatasına neden olabilir

#### <a name="details"></a>Ayrıntılar

NGEN/profile derlemeleri kullanılarak profil oluşturucular, bir ' önemli yürütme altyapısı özel durumu ile başlangıçtaki profili oluşturulmuş ASP.NET MVC4 uygulamalarını çökebilir

#### <a name="suggestion"></a>Öneri

Bu sorun .NET Framework 4.5.2 düzeltilmiştir. Alternatif olarak, profil oluşturucu kendi olay maskesini belirterek bu sorundan kaçınabilir <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
