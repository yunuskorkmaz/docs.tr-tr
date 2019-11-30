---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643965"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 'u modernleştirme

<xref:System.Windows.Forms.FolderBrowserDialog> denetimi .NET Core için Windows Forms uygulamalarda değişmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> denetimi için aşağıdaki iletişim kutusunu kullanır:

![.NET Framework FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

.NET Core 3,0 ' de, kullanıcılara Windows Vista 'da tanıtılan daha yeni bir COM tabanlı denetim Windows Forms:

![.NET Core 'da FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

İletişim kutusu otomatik olarak yükseltilir.

Özgün iletişim kutusunu saklamayı istiyorsanız, aşağıdaki kod parçasında gösterildiği gibi, iletişim kutusunu göstermeden önce <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> özelliğini `false` olarak ayarlayın:

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
