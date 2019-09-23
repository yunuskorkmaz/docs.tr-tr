---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181829"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="81fac-101">Switch. System. Windows. Forms. Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="81fac-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="81fac-102">.NET Framework 4.6.1 ' de tanıtılan Uyumlulukanahtarı.NETCore3,0'deWindowsFormsdesteklenmez.`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`</span><span class="sxs-lookup"><span data-stu-id="81fac-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81fac-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="81fac-103">Change description</span></span>

<span data-ttu-id="81fac-104">.NET Framework 4.6.1 ' den başlayarak <xref:System.Windows.Forms.TextBox> , bir denetimde <kbd>CTRL</kbd> + <kbd>kısayol tuşunu</kbd> seçerek tüm metinler seçilir.</span><span class="sxs-lookup"><span data-stu-id="81fac-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="81fac-105">.NET Framework 4,6 ve önceki sürümlerde, [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> ve Properties öğelerinin her ikisi de olarak `true`ayarlandığında, <kbd>CTRL</kbd> + tuşuna<kbd>bir</kbd> kısayol tuşu seçmek başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="81fac-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="81fac-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` Uyumluluk anahtarı .NET Framework 4.6.1 ' de özgün davranışı koruyacak şekilde sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="81fac-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="81fac-107">Daha fazla bilgi için <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>bkz.</span><span class="sxs-lookup"><span data-stu-id="81fac-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="81fac-108">.NET Core 'da, `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="81fac-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81fac-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="81fac-109">Version introduced</span></span>

<span data-ttu-id="81fac-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="81fac-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81fac-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="81fac-111">Recommended action</span></span>

<span data-ttu-id="81fac-112">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="81fac-112">Remove the switch.</span></span> <span data-ttu-id="81fac-113">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="81fac-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="81fac-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="81fac-114">Category</span></span>

<span data-ttu-id="81fac-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81fac-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81fac-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="81fac-116">Affected APIs</span></span>

- <span data-ttu-id="81fac-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fac-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
