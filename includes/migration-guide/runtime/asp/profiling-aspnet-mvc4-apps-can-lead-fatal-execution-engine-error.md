---
ms.openlocfilehash: 8b70df0fb2072fd5243d9e46a4a20c22cc7fd677
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607804"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profil oluşturma ASP.NET MVC4 Apps önemli yürütme altyapısı hatasına neden olabilir

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
