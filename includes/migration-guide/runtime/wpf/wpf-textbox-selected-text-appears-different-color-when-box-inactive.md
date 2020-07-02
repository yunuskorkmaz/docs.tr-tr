---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620706"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
