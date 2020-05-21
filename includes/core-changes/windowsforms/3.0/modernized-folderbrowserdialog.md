---
ms.openlocfilehash: 11c04441dcec260f0bfb90f6ed2b919b1545b382
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721300"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 'u modernleştirme

<xref:System.Windows.Forms.FolderBrowserDialog>Denetim, .NET Core için Windows Forms uygulamalarda değişmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, Windows Forms denetim için aşağıdaki iletişim kutusunu kullanır <xref:System.Windows.Forms.FolderBrowserDialog> :

![.NET Framework FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

.NET Core 3,0 ' de, kullanıcılara Windows Vista 'da tanıtılan daha yeni bir COM tabanlı denetim Windows Forms:

![.NET Core 'da FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

İletişim kutusu otomatik olarak yükseltilir.

Özgün iletişim kutusunu saklamayı istiyorsanız, <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> `false` Aşağıdaki kod parçası tarafından gösterildiği gibi, iletişim kutusunu göstermeden önce özelliğini olarak ayarlayın:

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
