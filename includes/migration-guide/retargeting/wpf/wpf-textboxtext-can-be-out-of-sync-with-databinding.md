---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617295"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text veri bağlama ile zaman uyumsuz olabilir

#### <a name="details"></a>Ayrıntılar

Bazı durumlarda, veri bağlama yazma işlemi sırasında <xref:System.Windows.Controls.TextBox.Text> özelliği değiştirilirse, özellik, veriye bağlı özellik değerinin önceki değerini yansıtır.

#### <a name="suggestion"></a>Öneri

Bunun negatif bir etkisi olmamalıdır. Ancak, <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> özelliğini `false` olarak ayarlayarak önceki davranışı geri yükleyebilirsiniz.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,5         |
|Tür|Yeniden Hedefleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
