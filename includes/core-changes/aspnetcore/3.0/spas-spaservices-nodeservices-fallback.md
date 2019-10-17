---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394216"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Maça 'Lar: Spaservice ve NodeServices artık konsol günlükçüsü 'e geri düşmüyor

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> ve <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType>, günlüğe kaydetme yapılandırılmadığı takdirde konsol günlüklerini görüntülemez.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.SpaServices` ve `Microsoft.AspNetCore.NodeServices` günlük yapılandırılmadığı zaman otomatik olarak bir konsol günlükçüsü oluşturmak için kullanılır. 

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.AspNetCore.SpaServices` ve `Microsoft.AspNetCore.NodeServices`, günlüğe kaydetme yapılandırılmadığı takdirde konsol günlüklerini görüntülemez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Diğer ASP.NET Core paketlerinin günlüğe kaydetme işleminin nasıl uygulanacağını hizalamanız gerekir.

#### <a name="recommended-action"></a>Önerilen eylem

Eski davranış gerekliyse konsol günlüğünü yapılandırmak için `services.AddLogging(builder => builder.AddConsole())` ' ı `Setup.ConfigureServices` yöntemine ekleyin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
