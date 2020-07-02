---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620547"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad artık bir tarayıcı özelliği olduğundan, IPad özel özellikler dosyasında kullanılmamalıdır

#### <a name="details"></a>Ayrıntılar

İPad .NET Framework 4,5 ' den başlayarak, varsayılan ASP.NET Browser özellikleri dosyasındaki bir tanıtıcıdır, bu nedenle özel bir yetenekler dosyasında kullanılmamalıdır

#### <a name="suggestion"></a>Öneri

İPad 'e özgü yetenekler gerekliyse, &quot; &quot; &quot; &quot; Kullanıcı Aracısı eşleştirmesi tarafından yeni bir iPad kimliği oluşturmak yerine önceden tanımlanmış ağ geçidi yeniden oluşturma iPad üzerinde özellikleri ayarlayarak iPad davranışını değiştirmek gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
