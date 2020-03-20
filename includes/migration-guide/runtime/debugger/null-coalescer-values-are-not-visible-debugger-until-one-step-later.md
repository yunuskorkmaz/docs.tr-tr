---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858600"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Null coalescer değerleri bir adım sonraya kadar hata ayıklama görünmez

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5'teki bir hata, null coalescing işlemi aracılığıyla ayarlanan değerlerin, Çerçeve'nin 64 bit sürümünde çalışırken atama işlemi yürütüldükten hemen sonra hata ayıklayıcıda görünmemelerine neden olur.|
|Öneri|Hata ayıklamada bir kez daha zaman ayırMak, yerel/alanın değerinin doğru şekilde güncelleştirilmesine neden olur. Ayrıca, bu sorun .NET Framework 4.6'da giderilmiştir; Çerçeve'nin bu sürümüne yükseltme sorunu çözmek gerekir.|
|Kapsam|Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
