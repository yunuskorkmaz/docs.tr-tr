---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615776"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Birleşik anahtarlar kullanılıyorsa ve bir anahtar boşsa, XSD şema doğrulaması artık benzersiz kısıtlamaların ihlallerini doğru şekilde algılar

#### <a name="details"></a>Ayrıntılar

4,6 ' dan önceki .NET Framework sürümleri, anahtarlardan biri boş olduğunda, XSD doğrulamasına neden olan bileşik anahtarlar üzerinde benzersiz kısıtlamalar algılamaması nedeniyle oluşan bir hataya sahipti. 4,6 .NET Framework bu sorun düzeltildi. Bu, daha doğru doğrulamaya neden olur, ancak daha önce sahip olacağı bazı XML doğrulamaları da neden olabilir.

#### <a name="suggestion"></a>Öneri

Gevllanıcı .NET Framework 4,0 doğrulaması gerekliyse, doğrulama uygulaması .NET Framework sürüm 4,5 ' i (veya önceki bir sürümü) hedefleyebilir. Ancak 4,6 .NET Framework için yeniden hedeflendiğinde, yinelenen bileşik anahtarların (Bu sorunun açıklamasında açıklandığı gibi) doğrulanması beklenmediğinden emin olmak için kod incelemesi yapılmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |
