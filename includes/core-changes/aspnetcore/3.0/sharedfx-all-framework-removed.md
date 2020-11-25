---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032862"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı

ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.All` metapackage ve eşleşen `Microsoft.AspNetCore.All` paylaşılan çerçeve artık üretilmez. Bu paket ASP.NET Core 2,2 ' de kullanılabilir ve ASP.NET Core 2,1 ' de hizmet güncelleştirmelerini almaya devam edecektir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Uygulamalar, `Microsoft.AspNetCore.All` `Microsoft.AspNetCore.All` .NET Core 'da paylaşılan çerçeveyi hedeflemek için metapackage kullanabilir.

#### <a name="new-behavior"></a>Yeni davranış

.NET Core 3,0, paylaşılan bir `Microsoft.AspNetCore.All` çerçeve içermez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`Microsoft.AspNetCore.All`Metapackage çok sayıda dış bağımlılığı içeriyordu.

#### <a name="recommended-action"></a>Önerilen eylem

Çerçevesini kullanmak için projenizi geçirin `Microsoft.AspNetCore.App` . Daha önce ' de kullanılabilir olan bileşenler `Microsoft.AspNetCore.All` NuGet üzerinde hala kullanılabilir. Bu bileşenler artık, paylaşılan çerçeveye eklenmek yerine uygulamanızla birlikte dağıtılır.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
