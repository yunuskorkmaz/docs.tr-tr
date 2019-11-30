---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644007"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="46b56-101">Switch. System. Windows. Forms. DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="46b56-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="46b56-102">.NET Framework 4.6.1 içinde tanıtılan `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="46b56-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="46b56-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="46b56-103">Change description</span></span>

<span data-ttu-id="46b56-104">.NET Framework 4.6.1 ile başlayarak, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulamasıyla çağrıldığında olası <xref:System.IndexOutOfRangeException> özel durumları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46b56-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="46b56-105">Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="46b56-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="46b56-106">.NET Core 'da `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="46b56-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="46b56-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="46b56-107">Version introduced</span></span>

<span data-ttu-id="46b56-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="46b56-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="46b56-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="46b56-109">Recommended action</span></span>

<span data-ttu-id="46b56-110">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="46b56-110">Remove the switch.</span></span> <span data-ttu-id="46b56-111">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="46b56-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="46b56-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="46b56-112">Category</span></span>

<span data-ttu-id="46b56-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46b56-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="46b56-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="46b56-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
