---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394434"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı

ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.All` metapackage ve eşleşen `Microsoft.AspNetCore.All` paylaşılan Framework artık üretilmez. Bu paket ASP.NET Core 2,2 ' de kullanılabilir ve ASP.NET Core 2,1 ' de hizmet güncelleştirmelerini almaya devam edecektir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Uygulamalar, .NET Core 'da `Microsoft.AspNetCore.All` paylaşılan Framework 'ü hedeflemek için `Microsoft.AspNetCore.All` metapaketini kullanabilir.

#### <a name="new-behavior"></a>Yeni davranış

.NET Core 3,0 `Microsoft.AspNetCore.All` paylaşılan bir çerçeve içermez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`Microsoft.AspNetCore.All` metapackage çok sayıda dış bağımlılığı içeriyordu.

#### <a name="recommended-action"></a>Önerilen eylem

`Microsoft.AspNetCore.App` çerçevesini kullanmak için projenizi geçirin. Daha önce `Microsoft.AspNetCore.All` ' de kullanılabilir olan bileşenler NuGet üzerinde hala kullanılabilir. Bu bileşenler artık, paylaşılan çerçeveye eklenmek yerine uygulamanızla birlikte dağıtılır.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
