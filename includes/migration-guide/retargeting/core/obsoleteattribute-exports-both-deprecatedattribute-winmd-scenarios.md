---
ms.openlocfilehash: 7d7424b3ca0d295022999e95ed9862b5226b6220
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606203"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>Kullanımdan kaldırıldı Teattribute, WinMD senaryolarında hem kullanımdan kaldırıldı hem de kullanımdan kaldırıldı olarak dışarı aktarmalar

#### <a name="details"></a>Ayrıntılar

Bir Windows meta veri kitaplığı (. winmd dosyası) oluşturduğunuzda, <xref:System.ObsoleteAttribute?displayProperty=fullName> öznitelik hem <xref:System.ObsoleteAttribute?displayProperty=fullName> ve [Windows. Foundation. kullanımdan](/uwp/api/windows.foundation.metadata.deprecatedattribute)kaldırıldı ' olarak verilir.

#### <a name="suggestion"></a>Öneri

Özniteliği kullanan mevcut kaynak kodun yeniden derlenmesi, <xref:System.ObsoleteAttribute?displayProperty=fullName> Bu kodu C++/CX veya JavaScript 'ten kullanırken uyarılar oluşturabilir. <xref:System.ObsoleteAttribute?displayProperty=fullName> yönetilen derlemelerdeki koda hem hem de [Windows. Foundation. kullanımdan kaldırıldı.](/uwp/api/windows.foundation.metadata.deprecatedattribute)

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.5.1       |
| Tür    | Yeniden Hedefleme |
