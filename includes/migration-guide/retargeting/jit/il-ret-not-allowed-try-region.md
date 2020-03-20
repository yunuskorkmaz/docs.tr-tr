---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804480"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret bir deneme bölgesinde izin verilmez

|   |   |
|---|---|
|Ayrıntılar|JIT64 tam zamanında derleyicinin aksine, RyuJIT (.NET Framework 4.6'da kullanılır) deneme bölgesinde IL ret yönergesi kullanmaz. Bir deneme bölgesinden dönüş, ECMA-335 belirtimi tarafından izin verilmez ve bilinen hiçbir yönetilen derleyici böyle bir IL üretmez. Ancak, JIT64 derleyicisi yansıma yayan kullanılarak oluşturulursa bu TÜR IL yürütür.|
|Öneri|Bir uygulama deneme bölgesinde ret opcode içeren IL oluşturuyorsa, uygulama eski JIT'yi kullanmak ve bu kopuşu önlemek için .NET Framework 4.5'i hedefleyebilir. Alternatif olarak, oluşturulan IL deneme bölgesinden sonra dönmek için güncelleştirilmiş olabilir.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
