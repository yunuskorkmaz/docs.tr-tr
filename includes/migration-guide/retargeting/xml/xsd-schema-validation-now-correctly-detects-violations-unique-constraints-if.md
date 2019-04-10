---
ms.openlocfilehash: 5844dbc2c3c89baeb39b69f16846f92ac10e97f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234551"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>XSD şema doğrulaması artık doğru şekilde bileşik anahtarlar kullanılır ve bir anahtar boş ise benzersiz kısıtlamalar ihlalleri algılar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 önce sürümleri anahtarlarından birini boşsa bileşik anahtarlar benzersiz kısıtlamalar algılamamak üzere XSD doğrulaması nedeniyle bir hata oluştu. .NET Framework 4.6, bu sorun düzeltilmiştir. Bu, daha doğru doğrulama neden olur, ancak bazı XML içinde değil, daha önce sahip doğrulanıyor sonuçlanabilir.|
|Öneri|Bazı .NET Framework 4.0 doğrulama gerekli değilse, doğrulama uygulamanın sürüm 4.5 (veya öncesi) hedefleyebilirsiniz .NET Framework'ün. Ancak, .NET Framework 4. 6'için ' yeniden hedefleme, kod incelemesi yinelenen bileşik anahtarlar (Bu sorunun açıklamasında tanımlandığı gibi) doğrulamak için beklenmiyor emin emin olmak için yapılmalıdır.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
