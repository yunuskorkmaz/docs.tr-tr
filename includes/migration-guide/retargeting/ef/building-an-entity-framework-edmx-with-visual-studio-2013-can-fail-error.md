---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615758"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Visual Studio 2013 ile bir Entity Framework edmx oluşturma işlemi, EntityDeploySplit veya EntityClean görevleri kullanılıyorsa MSB4062 hatasıyla başarısız olabilir

#### <a name="details"></a>Ayrıntılar

MSBuild 12.0 araçlarındaki (Visual Studio 2013’e dahildir) MSBuild dosya konumları değiştirilmiş ve eski Entity Framework hedef dosyalarının geçersiz olmasına neden olmuştur. Sonuç olarak, `EntityDeploySplit` ve `EntityClean` görevleri `Microsoft.Data.Entity.Build.Tasks.dll` dosyasını bulamadıkları için başarısız olur. Bu kesintinin bir .NET Framework değişikliğinden değil bir araç takımı (MSBuild/VS) değişikliğinden kaynaklandığına dikkat edin. .NET Framework’ü yükseltirken değil, yalnızca geliştirici araçlarını yükseltirken oluşur.

#### <a name="suggestion"></a>Öneri

Entity Framework hedef dosyaları, .NET Framework 4.6 sürümünden başlayarak yeni MSBuild düzeniyle çalışmak için düzeltildi. Bu Framework sürümüne yükseltmek bu sorunu çözecektir. Alternatif olarak, [Bu geçici çözüm](https://stackoverflow.com/a/24249247/131944) hedefler dosyalarını doğrudan düzeltme için de kullanılabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4.5.1       |
| Tür    | Yeniden Hedefleme |
