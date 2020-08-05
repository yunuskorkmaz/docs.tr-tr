---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556251"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="94f57-101">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="94f57-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="94f57-102">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET Framework 4.6.1 ' de tanıtılan uyumluluk anahtarı .NET Core ve .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="94f57-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="94f57-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="94f57-103">Change description</span></span>

<span data-ttu-id="94f57-104">.NET Framework 4.6.1 ' den başlayarak, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> bir denetimde CTRL kısayol tuşunu seçerek <xref:System.Windows.Forms.TextBox> tüm metinler seçilir.</span><span class="sxs-lookup"><span data-stu-id="94f57-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="94f57-105">.NET Framework 4,6 ve önceki sürümlerde, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties öğelerinin her ikisi de olarak ayarlandığında, CTRL tuşuna bir kısayol tuşu seçmek başarısız oldu `true` .</span><span class="sxs-lookup"><span data-stu-id="94f57-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="94f57-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Uyumluluk anahtarı .NET Framework 4.6.1 ' de özgün davranışı koruyacak şekilde sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="94f57-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="94f57-107">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="94f57-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="94f57-108">.NET Core ve .NET 5,0 ve sonraki sürümlerinde, `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="94f57-108">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="94f57-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="94f57-109">Version introduced</span></span>

<span data-ttu-id="94f57-110">3,0</span><span class="sxs-lookup"><span data-stu-id="94f57-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="94f57-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="94f57-111">Recommended action</span></span>

<span data-ttu-id="94f57-112">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="94f57-112">Remove the switch.</span></span> <span data-ttu-id="94f57-113">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="94f57-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="94f57-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="94f57-114">Category</span></span>

<span data-ttu-id="94f57-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94f57-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="94f57-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="94f57-116">Affected APIs</span></span>

- <span data-ttu-id="94f57-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="94f57-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
