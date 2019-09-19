---
ms.openlocfilehash: a7cf6210e288d3521f1df248927f0e7cfaf45cab
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119326"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="da881-101">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="da881-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="da881-102">Denetim <xref:System.Windows.Forms.FolderBrowserDialog> , .NET Core için Windows Forms uygulamalarda değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="da881-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="da881-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="da881-103">Change description</span></span>

<span data-ttu-id="da881-104">.NET Framework, Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> denetim için aşağıdaki iletişim kutusunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="da881-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![.NET Framework FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="da881-106">.NET Core 3,0 ' de, kullanıcılara Windows Vista 'da tanıtılan daha yeni bir COM tabanlı denetim Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="da881-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![.NET Core 'da FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="da881-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="da881-108">Version introduced</span></span>

<span data-ttu-id="da881-109">3.0</span><span class="sxs-lookup"><span data-stu-id="da881-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da881-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="da881-110">Recommended action</span></span>

<span data-ttu-id="da881-111">İletişim kutusu otomatik olarak yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="da881-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="da881-112">Özgün iletişim kutusunu saklamayı istiyorsanız, aşağıdaki kod parçası tarafından gösterildiği <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> gibi, `false` iletişim kutusunu göstermeden önce özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="da881-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="da881-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="da881-113">Category</span></span>

<span data-ttu-id="da881-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da881-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da881-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="da881-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!-- 

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->