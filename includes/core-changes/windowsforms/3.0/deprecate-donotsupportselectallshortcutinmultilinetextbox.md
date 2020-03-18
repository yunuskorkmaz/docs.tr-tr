---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936984"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="837da-101">DoNotSupportSelectAllShortcutInMultilineTextBox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="837da-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="837da-102">.NET Framework 4.6.1'de tanıtılan `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="837da-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="837da-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="837da-103">Change description</span></span>

<span data-ttu-id="837da-104">.NET Framework 4.6.1 ile başlayarak, tüm metni seçen <xref:System.Windows.Forms.TextBox> bir denetimde <kbd>Ctrl</kbd> + <kbd>A</kbd> kısayol anahtarını seçin.</span><span class="sxs-lookup"><span data-stu-id="837da-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="837da-105">.NET Framework 4.6 ve önceki sürümlerde, <kbd>Ctrl</kbd> + <kbd>A</kbd> kısayol tuşu seçilerek [Textbox.ShortcutsEtkin](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> özellikleri her ikisi de ayarlanmışsa tüm metni seçmek için `true`başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="837da-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="837da-106">Uyumluluk `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtarı,.NET Framework 4.6.1'de özgün davranışı korumak için tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="837da-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="837da-107">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="837da-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="837da-108">.NET Core'da `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="837da-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="837da-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="837da-109">Version introduced</span></span>

<span data-ttu-id="837da-110">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="837da-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="837da-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="837da-111">Recommended action</span></span>

<span data-ttu-id="837da-112">Anahtarı çıkarın.</span><span class="sxs-lookup"><span data-stu-id="837da-112">Remove the switch.</span></span> <span data-ttu-id="837da-113">Anahtar desteklenmez ve alternatif bir işlevsellik yok.</span><span class="sxs-lookup"><span data-stu-id="837da-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="837da-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="837da-114">Category</span></span>

<span data-ttu-id="837da-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="837da-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="837da-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="837da-116">Affected APIs</span></span>

- <span data-ttu-id="837da-117">None</span><span class="sxs-lookup"><span data-stu-id="837da-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
