---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720932"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="6244c-101">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6244c-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="6244c-102">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET Framework 4.6.1 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6244c-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6244c-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="6244c-103">Change description</span></span>

<span data-ttu-id="6244c-104">.NET Framework 4.6.1 ' den başlayarak, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> bir denetimde CTRL kısayol tuşunu seçerek <xref:System.Windows.Forms.TextBox> tüm metinler seçilir.</span><span class="sxs-lookup"><span data-stu-id="6244c-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="6244c-105">.NET Framework 4,6 ve önceki sürümlerde, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties öğelerinin her ikisi de olarak ayarlandığında, CTRL tuşuna bir kısayol tuşu seçmek başarısız oldu `true` .</span><span class="sxs-lookup"><span data-stu-id="6244c-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="6244c-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Uyumluluk anahtarı .NET Framework 4.6.1 ' de özgün davranışı koruyacak şekilde sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="6244c-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="6244c-107">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6244c-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6244c-108">.NET Core 'da, `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6244c-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6244c-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6244c-109">Version introduced</span></span>

<span data-ttu-id="6244c-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="6244c-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6244c-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6244c-111">Recommended action</span></span>

<span data-ttu-id="6244c-112">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6244c-112">Remove the switch.</span></span> <span data-ttu-id="6244c-113">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6244c-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="6244c-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="6244c-114">Category</span></span>

<span data-ttu-id="6244c-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6244c-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6244c-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6244c-116">Affected APIs</span></span>

- <span data-ttu-id="6244c-117">Yok</span><span class="sxs-lookup"><span data-stu-id="6244c-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
