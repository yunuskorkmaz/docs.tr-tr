---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621399"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Bir TextBlock denetiminin üst öğesinin IsEnabled özelliğini değiştirmek, tüm alt denetimleri etkiler

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 başlayarak, <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> bir denetimin üst öğesinin özelliğini değiştirmek, <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> denetimin tüm alt denetimlerini (köprüler ve düğmeler gibi) etkiler <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> . .NET Framework 4.6.1 ve önceki sürümlerde, içindeki denetimler <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> her zaman üst öğenin özelliğinin durumunu yansıtmamaktadır <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Yok. Bu değişiklik, denetim içindeki denetimler için beklenen davranışa uyar <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
