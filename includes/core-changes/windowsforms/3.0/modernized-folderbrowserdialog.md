---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888153"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="aa69e-101">FolderBrowserDialog modernizasyonu</span><span class="sxs-lookup"><span data-stu-id="aa69e-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="aa69e-102">Denetim,.NET <xref:System.Windows.Forms.FolderBrowserDialog> Core için Windows Forms uygulamalarında değişti.</span><span class="sxs-lookup"><span data-stu-id="aa69e-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="aa69e-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="aa69e-103">Change description</span></span>

<span data-ttu-id="aa69e-104">.NET Framework'de, Windows formları <xref:System.Windows.Forms.FolderBrowserDialog> denetim için aşağıdaki iletişim kutusunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="aa69e-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![.NET Çerçevesinde FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="aa69e-106">.NET Core 3.0'da, Windows Formlar kullanıcıları Windows Vista'da tanıtılan daha yeni bir COM tabanlı denetim:</span><span class="sxs-lookup"><span data-stu-id="aa69e-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![.NET Çekirdeğinde FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="aa69e-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="aa69e-108">Version introduced</span></span>

<span data-ttu-id="aa69e-109">3,0</span><span class="sxs-lookup"><span data-stu-id="aa69e-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aa69e-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="aa69e-110">Recommended action</span></span>

<span data-ttu-id="aa69e-111">İletişim otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="aa69e-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="aa69e-112">Özgün iletişim kutusunu korumak istiyorsanız, aşağıdaki <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> kod `false` parçasında gösterildiği gibi, iletişim kutusunu göstermeden önce özelliği ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="aa69e-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="aa69e-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="aa69e-113">Category</span></span>

<span data-ttu-id="aa69e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa69e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aa69e-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="aa69e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
