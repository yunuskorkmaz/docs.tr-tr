---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937011"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="9a667-101">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9a667-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="9a667-102">.NET Framework 4.6.1'de tanıtılan `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9a667-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9a667-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="9a667-103">Change description</span></span>

<span data-ttu-id="9a667-104">.NET Framework 4.6.1'den `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` başlayarak, <xref:System.IndexOutOfRangeException> <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> bir uygulamayla çağrıldığında uyumluluk anahtarı olası özel durumları giderer.</span><span class="sxs-lookup"><span data-stu-id="9a667-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="9a667-105">Daha fazla bilgi için [bkz: Azaltma: Özel IMessageFilter.PreFilterMessage Uygulamaları.](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)</span><span class="sxs-lookup"><span data-stu-id="9a667-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="9a667-106">.NET Core'da `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9a667-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9a667-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="9a667-107">Version introduced</span></span>

<span data-ttu-id="9a667-108">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="9a667-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9a667-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9a667-109">Recommended action</span></span>

<span data-ttu-id="9a667-110">Anahtarı çıkarın.</span><span class="sxs-lookup"><span data-stu-id="9a667-110">Remove the switch.</span></span> <span data-ttu-id="9a667-111">Anahtar desteklenmez ve alternatif bir işlevsellik yok.</span><span class="sxs-lookup"><span data-stu-id="9a667-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="9a667-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="9a667-112">Category</span></span>

<span data-ttu-id="9a667-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a667-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a667-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9a667-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
