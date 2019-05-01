---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093622"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Null coalescer değerleri daha sonra bir adım kadar hata ayıklayıcıda görünür değildir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 hatada atama işlemi Framework'ün 64 bit sürümünde çalıştırıldığı sırada yürütüldükten hemen sonra hata ayıklayıcısı'nda görünür olmaması için null bir birleştirme işlemi ayarlanan değerleri neden olur.|
|Öneri|Hata ayıklayıcı ek bir kerelik atlama doğru şekilde güncelleştirilmesi, yerel/alanın değeri neden olur. Ayrıca, .NET Framework 4. 6 ' Bu sorun düzeltilmiştir; Framework'ün bu sürüme yükseltme sorunu çözecektir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
