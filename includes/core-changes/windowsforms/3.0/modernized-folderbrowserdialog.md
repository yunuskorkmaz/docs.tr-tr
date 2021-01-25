---
ms.openlocfilehash: 27c6353f8f71254a505b434921f4b1e61e64cdda
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758170"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="8ba24-101">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="8ba24-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="8ba24-102"><xref:System.Windows.Forms.FolderBrowserDialog>Denetim, .NET Core için Windows Forms uygulamalarda değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ba24-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8ba24-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="8ba24-103">Change description</span></span>

<span data-ttu-id="8ba24-104">.NET Framework, Windows Forms denetim için aşağıdaki iletişim kutusunu kullanır <xref:System.Windows.Forms.FolderBrowserDialog> :</span><span class="sxs-lookup"><span data-stu-id="8ba24-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![.NET Framework FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="8ba24-106">.NET Core 3,0 ' de Windows Forms, Windows Vista 'da tanıtılan daha yeni bir COM tabanlı denetim kullanır:</span><span class="sxs-lookup"><span data-stu-id="8ba24-106">In .NET Core 3.0, Windows Forms uses a newer COM-based control that was introduced in Windows Vista:</span></span>

![.NET Core 'da FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="8ba24-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="8ba24-108">Version introduced</span></span>

<span data-ttu-id="8ba24-109">3.0</span><span class="sxs-lookup"><span data-stu-id="8ba24-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8ba24-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="8ba24-110">Recommended action</span></span>

<span data-ttu-id="8ba24-111">İletişim kutusu otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="8ba24-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="8ba24-112">Özgün iletişim kutusunu saklamayı istiyorsanız, <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> `false` Aşağıdaki kod parçası tarafından gösterildiği gibi, iletişim kutusunu göstermeden önce özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8ba24-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="8ba24-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="8ba24-113">Category</span></span>

<span data-ttu-id="8ba24-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ba24-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8ba24-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8ba24-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
