---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643965"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog modernizasyonu

Denetim,.NET <xref:System.Windows.Forms.FolderBrowserDialog> Core için Windows Forms uygulamalarında değişti.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework'de, Windows formları <xref:System.Windows.Forms.FolderBrowserDialog> denetim için aşağıdaki iletişim kutusunu kullanır:

![.NET Çerçevesinde FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

.NET Core 3.0'da, Windows Formlar kullanıcıları Windows Vista'da tanıtılan daha yeni bir COM tabanlı denetim:

![.NET Çekirdeğinde FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

İletişim otomatik olarak yükseltilir.

Özgün iletişim kutusunu korumak istiyorsanız, aşağıdaki <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> kod `false` parçasında gösterildiği gibi, iletişim kutusunu göstermeden önce özelliği ayarlayın:

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
