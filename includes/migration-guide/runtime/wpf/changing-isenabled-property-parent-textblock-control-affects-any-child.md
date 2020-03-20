---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857543"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>TextBlock denetiminin üst öğesinin Etkinleştirilmiş özelliğinin değiştirilmesi tüm alt denetimleri etkiler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, bir <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetimin üst özelliğini <xref:System.Windows.Controls.TextBlock?displayProperty=name> değiştirmek, denetimin alt denetimlerini (köprüler ve düğmeler gibi) etkiler. .NET Framework 4.6.1 ve önceki sürümlerinde, a <xref:System.Windows.Controls.TextBlock?displayProperty=name> içindeki denetimler <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> her <xref:System.Windows.Controls.TextBlock?displayProperty=name> zaman ebeveynin özelliğinin durumunu yansıtmadı.|
|Öneri|Yok. Bu değişiklik, denetim içindeki denetimler <xref:System.Windows.Controls.TextBlock?displayProperty=name> için beklenen davranışa uygundur.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
