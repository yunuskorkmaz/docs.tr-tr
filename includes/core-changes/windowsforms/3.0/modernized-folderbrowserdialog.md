---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643965"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="92b3f-101">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="92b3f-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="92b3f-102"><xref:System.Windows.Forms.FolderBrowserDialog> denetimi .NET Core için Windows Forms uygulamalarda değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="92b3f-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="92b3f-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="92b3f-103">Change description</span></span>

<span data-ttu-id="92b3f-104">.NET Framework, Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> denetimi için aşağıdaki iletişim kutusunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="92b3f-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![.NET Framework FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="92b3f-106">.NET Core 3,0 ' de, kullanıcılara Windows Vista 'da tanıtılan daha yeni bir COM tabanlı denetim Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="92b3f-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![.NET Core 'da FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="92b3f-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="92b3f-108">Version introduced</span></span>

<span data-ttu-id="92b3f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="92b3f-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="92b3f-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="92b3f-110">Recommended action</span></span>

<span data-ttu-id="92b3f-111">İletişim kutusu otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="92b3f-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="92b3f-112">Özgün iletişim kutusunu saklamayı istiyorsanız, aşağıdaki kod parçasında gösterildiği gibi, iletişim kutusunu göstermeden önce <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> özelliğini `false` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="92b3f-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="92b3f-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="92b3f-113">Category</span></span>

<span data-ttu-id="92b3f-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="92b3f-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="92b3f-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="92b3f-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
