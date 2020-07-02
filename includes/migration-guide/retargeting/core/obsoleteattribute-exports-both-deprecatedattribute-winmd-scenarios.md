---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616115"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>Kullanımdan kaldırıldı Teattribute, WinMD senaryolarında hem kullanımdan kaldırıldı hem de kullanımdan kaldırıldı olarak dışarı aktarmalar

#### <a name="details"></a>Ayrıntılar

Bir Windows meta veri kitaplığı (. winmd dosyası) oluşturduğunuzda, <xref:System.ObsoleteAttribute?displayProperty=fullName> öznitelik hem <xref:System.ObsoleteAttribute?displayProperty=fullName> ve [Windows. Foundation. kullanımdan](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)kaldırıldı ' olarak verilir.

#### <a name="suggestion"></a>Öneri

Özniteliği kullanan mevcut kaynak kodun yeniden derlenmesi, <xref:System.ObsoleteAttribute?displayProperty=fullName> Bu kodu C++/CX veya JavaScript 'ten kullanırken uyarılar oluşturabilir. <xref:System.ObsoleteAttribute?displayProperty=fullName> yönetilen derlemelerdeki koda hem hem de [Windows. Foundation. kullanımdan kaldırıldı.](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.5.1       |
| Tür    | Yeniden Hedefleme |
