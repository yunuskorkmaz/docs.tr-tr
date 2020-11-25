---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032902"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Maça 'Lar: Spaservice ve NodeServices artık konsol günlükçüsü 'e geri düşmüyor

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> ve <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> günlüğe kaydetme yapılandırılmadığı takdirde konsol günlükleri görüntülenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.SpaServices` ve `Microsoft.AspNetCore.NodeServices` günlüğe kaydetme yapılandırılmadığında otomatik olarak bir konsol günlükçüsü oluşturmak için kullanılır.

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.AspNetCore.SpaServices` ve `Microsoft.AspNetCore.NodeServices` günlüğe kaydetme yapılandırılmadığı takdirde konsol günlükleri görüntülenmez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Diğer ASP.NET Core paketlerinin günlüğe kaydetme işleminin nasıl uygulanacağını hizalamanız gerekir.

#### <a name="recommended-action"></a>Önerilen eylem

Eski davranış gerekliyse konsol günlüğünü yapılandırmak için `services.AddLogging(builder => builder.AddConsole())` `Setup.ConfigureServices` yönteminizi ekleyin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

#### Affected APIs

Not detectable via API analysis

-->
