---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394434"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Paylaşılan çerçeve: Kaldırıldı Microsoft.AspNetCore.All

Core 3.0ASP.NETdan `Microsoft.AspNetCore.All` başlayarak, metapaket `Microsoft.AspNetCore.All` ve eşleşen paylaşılan çerçeve artık üretilmemaktadır. Bu paket Core 2.2ASP.NETde mevcuttur ve ASP.NET Core 2.1'de servis güncellemeleri almaya devam edecektir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.All` Uygulamalar,.NET Core'daki `Microsoft.AspNetCore.All` paylaşılan çerçeveyi hedeflemek için meta paketi kullanabilir.

#### <a name="new-behavior"></a>Yeni davranış

.NET Core 3.0 paylaşılan `Microsoft.AspNetCore.All` bir çerçeve içermez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Meta `Microsoft.AspNetCore.All` paket çok sayıda dış bağımlılık içeriyordu.

#### <a name="recommended-action"></a>Önerilen eylem

Çerçeveyi kullanmak için `Microsoft.AspNetCore.App` projenizi geçirin. Daha önce mevcut olan `Microsoft.AspNetCore.All` bileşenler NuGet'de hala kullanılabilir. Bu bileşenler artık paylaşılan çerçeveye dahil olmak yerine uygulamanızla birlikte dağıtılır.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
