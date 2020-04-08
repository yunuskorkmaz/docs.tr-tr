---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888153"
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

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
