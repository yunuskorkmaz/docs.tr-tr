---
ms.openlocfilehash: 12a26030a9a336d887ae9d53994a9daf13356618
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497871"
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
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.UIElement.IsEnabled`

-->
