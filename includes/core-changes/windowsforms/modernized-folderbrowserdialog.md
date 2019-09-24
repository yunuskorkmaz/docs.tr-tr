---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217026"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 'u modernleştirme

Denetim <xref:System.Windows.Forms.FolderBrowserDialog> , .NET Core için Windows Forms uygulamalarda değişmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> denetim için aşağıdaki iletişim kutusunu kullanır:

![.NET Framework FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

.NET Core 3,0 ' de, kullanıcılara Windows Vista 'da tanıtılan daha yeni bir COM tabanlı denetim Windows Forms:

![.NET Core 'da FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

İletişim kutusu otomatik olarak yükseltilir.

Özgün iletişim kutusunu saklamayı istiyorsanız, aşağıdaki kod parçası tarafından gösterildiği <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> gibi, `false` iletişim kutusunu göstermeden önce özelliğini olarak ayarlayın:

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

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
