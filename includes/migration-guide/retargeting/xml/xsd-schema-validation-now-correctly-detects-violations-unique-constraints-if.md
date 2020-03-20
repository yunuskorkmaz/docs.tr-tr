---
ms.openlocfilehash: 5844dbc2c3c89baeb39b69f16846f92ac10e97f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804500"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>XSD Şema doğrulaması artık bileşik anahtarlar kullanılıyorsa ve bir anahtar boşsa benzersiz kısıtlamaların ihlallerini doğru bir şekilde algılar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework'ün 4.6'dan önceki sürümlerinde, anahtarlardan biri boşsa, XSD doğrulamanın bileşik anahtarlar üzerinde benzersiz kısıtlamaları algılamamalarına neden olan bir hata vardı. .NET Framework 4.6'da bu sorun düzeltilir. Bu daha doğru doğrulama neden olur, ancak aynı zamanda bazı XML daha önce olurdu doğrulama değil neden olabilir.|
|Öneri|Daha gevşek .NET Framework 4.0 doğrulama gerekiyorsa, doğrulama uygulaması .NET Framework'ün 4.5 (veya önceki) sürümünü hedefleyebilir. Ancak,.NET Framework 4.6'ya yeniden hedefleme yapılırken, yinelenen bileşik anahtarların (bu sorunun açıklamasında açıklandığı gibi) doğrulamanın beklenmediğinden emin olmak için kod incelemesi yapılmalıdır.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
