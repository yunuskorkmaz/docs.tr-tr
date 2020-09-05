---
ms.openlocfilehash: c01705002ad87a12389078d75ffd0f91f934d36e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496917"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Metin kutusu etkin olmadığında WPF metin kutusu seçili metni farklı bir renk görünüyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, bir WPF metin kutusu denetimi etkin olmadığında (odağa sahip değilse), kutudaki seçili metin, denetimin etkin olduğu değerden farklı bir renkle gösterilir.

#### <a name="suggestion"></a>Öneri

Önceki (.NET Framework 4,0) davranışı özelliği olarak ayarlanarak geri yüklenebilir <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> <code>false</code> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
