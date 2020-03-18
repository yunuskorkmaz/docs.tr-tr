---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522662"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SP'ler: SpaServices ve NodeServices artık konsol logger geri düşmek

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType><xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> ve günlük yapılandırması yapılmadığı sürece konsol günlüklerini görüntülemez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.SpaServices`ve `Microsoft.AspNetCore.NodeServices` günlük yapılandırma olmadığında otomatik olarak bir konsol kaydedici oluşturmak için kullanılır.

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.AspNetCore.SpaServices``Microsoft.AspNetCore.NodeServices` ve günlük yapılandırması yapılmadığı sürece konsol günlüklerini görüntülemez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Diğer ASP.NET Core paketlerinin günlüğe kaydetmeyi nasıl uyguladığıyla uyumlu hale getirmek gerekir.

#### <a name="recommended-action"></a>Önerilen eylem

Eski davranış gerekiyorsa, konsol günlüğe yapılandırmak `services.AddLogging(builder => builder.AddConsole())` için, yönteminize `Setup.ConfigureServices` ekleyin.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
