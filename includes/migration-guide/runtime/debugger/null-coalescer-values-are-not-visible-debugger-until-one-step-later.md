---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858600"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Null coalescer değerleri daha sonra bir adım kadar hata ayıklayıcıda görünür değildir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 hatada atama işlemi Framework'ün 64 bit sürümünde çalıştırıldığı sırada yürütüldükten hemen sonra hata ayıklayıcısı'nda görünür olmaması için null bir birleştirme işlemi ayarlanan değerleri neden olur.|
|Öneri|Hata ayıklayıcı ek bir kerelik atlama doğru şekilde güncelleştirilmesi, yerel/alanın değeri neden olur. Ayrıca, .NET Framework 4. 6 ' Bu sorun düzeltilmiştir; Framework'ün bu sürüme yükseltme sorunu çözecektir.|
|`Scope`|Kenar|
|Version|4,5|
|Type|Çalışma zamanı|

