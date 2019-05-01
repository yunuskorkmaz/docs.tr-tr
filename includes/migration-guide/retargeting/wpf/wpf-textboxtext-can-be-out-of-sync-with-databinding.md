---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093643"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text veri bağlama ile zaman uyumsuz olabilir

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, veri bağlama yazma işlemi sırasında <xref:System.Windows.Controls.TextBox.Text> özelliği değiştirilirse, özellik, veriye bağlı özellik değerinin önceki değerini yansıtır.|
|Öneri|Bunun negatif bir etkisi olmamalıdır. Ancak, <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> özelliğini <code>false</code> olarak ayarlayarak önceki davranışı geri yükleyebilirsiniz.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
