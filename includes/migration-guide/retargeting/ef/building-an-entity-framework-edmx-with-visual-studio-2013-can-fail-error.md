---
ms.openlocfilehash: ffafb0c9e3982dd168f907d32a8f59f96e6040d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234848"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Visual Studio 2013 ile bir Entity Framework edmx oluşturma işlemi, EntityDeploySplit veya EntityClean görevleri kullanılıyorsa MSB4062 hatasıyla başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|MSBuild 12.0 araçlarındaki (Visual Studio 2013’e dahildir) MSBuild dosya konumları değiştirilmiş ve eski Entity Framework hedef dosyalarının geçersiz olmasına neden olmuştur. Sonuç olarak, <code>EntityDeploySplit</code> ve <code>EntityClean</code> görevleri <code>Microsoft.Data.Entity.Build.Tasks.dll</code> dosyasını bulamadıkları için başarısız olur. Bu kesintinin bir .NET Framework değişikliğinden değil bir araç takımı (MSBuild/VS) değişikliğinden kaynaklandığına dikkat edin. .NET Framework’ü yükseltirken değil, yalnızca geliştirici araçlarını yükseltirken oluşur.|
|Öneri|Entity Framework hedef dosyaları, .NET Framework 4.6 sürümünden başlayarak yeni MSBuild düzeniyle çalışmak için düzeltildi. Bu Framework sürümüne yükseltmek bu sorunu çözecektir. Alternatif olarak, [bu geçici çözüm](https://stackoverflow.com/a/24249247/131944) MSBuild doğrudan düzeltme eki için kullanılabilir.|
|Kapsam|Ana|
|Sürüm|4.5.1|
|Tür|Yeniden Hedefleme|
