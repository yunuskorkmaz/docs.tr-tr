---
ms.openlocfilehash: 38dd0b33202b8e8f1708ebec689333bd5367c93f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857543"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>TextBlock denetimi üst IsEnabled özelliğinin değiştirilmesi tüm alt denetimler etkiler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, değiştirme ile başlayarak <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> üst öğesinin özellik bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetimi etkiler (örneğin, köprüler ve düğmeler) tüm alt denetimler <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetimi. İçinde .NET Framework 4.6.1 ve önceki sürümlerle denetleyen bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> her zaman durumunu yansıtmıyor <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> özelliği <xref:System.Windows.Controls.TextBlock?displayProperty=name> üst.|
|Öneri|Yok. Bu değişiklik içindeki denetimlerin yönelik beklenen davranışın uyan bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetimi.|
|`Scope`|Küçük|
|Version|4.6.2|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

