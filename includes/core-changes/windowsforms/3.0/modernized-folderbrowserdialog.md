---
ms.openlocfilehash: 27c6353f8f71254a505b434921f4b1e61e64cdda
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758170"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 'u modernleştirme

<xref:System.Windows.Forms.FolderBrowserDialog>Denetim, .NET Core için Windows Forms uygulamalarda değişmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, Windows Forms denetim için aşağıdaki iletişim kutusunu kullanır <xref:System.Windows.Forms.FolderBrowserDialog> :

![.NET Framework FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

.NET Core 3,0 ' de Windows Forms, Windows Vista 'da tanıtılan daha yeni bir COM tabanlı denetim kullanır:

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
