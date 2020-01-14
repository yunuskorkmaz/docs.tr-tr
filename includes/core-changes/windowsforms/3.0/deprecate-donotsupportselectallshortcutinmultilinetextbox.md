---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936984"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="c7556-101">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="c7556-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="c7556-102">.NET Framework 4.6.1 içinde tanıtılan `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c7556-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c7556-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c7556-103">Change description</span></span>

<span data-ttu-id="c7556-104">.NET Framework 4.6.1 ' den başlayarak <kbd>, bir <xref:System.Windows.Forms.TextBox></kbd> denetimindeki kısayol tuşu + <kbd>CTRL</kbd> ' i seçerek tüm metni seçin.</span><span class="sxs-lookup"><span data-stu-id="c7556-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="c7556-105">.NET Framework 4,6 ve önceki sürümlerde, [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> özelliklerinin ikisi de `true`olarak ayarlanana kadar, <kbd>CTRL</kbd> <kbd> + kısayol</kbd> tuşu seçimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c7556-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="c7556-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` uyumluluk anahtarı, özgün davranışı sürdürmek için .NET Framework 4.6.1 eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7556-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="c7556-107">Daha fazla bilgi için <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>bkz.</span><span class="sxs-lookup"><span data-stu-id="c7556-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c7556-108">.NET Core 'da `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c7556-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c7556-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c7556-109">Version introduced</span></span>

<span data-ttu-id="c7556-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="c7556-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c7556-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c7556-111">Recommended action</span></span>

<span data-ttu-id="c7556-112">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c7556-112">Remove the switch.</span></span> <span data-ttu-id="c7556-113">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7556-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="c7556-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="c7556-114">Category</span></span>

<span data-ttu-id="c7556-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7556-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c7556-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c7556-116">Affected APIs</span></span>

- <span data-ttu-id="c7556-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="c7556-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
