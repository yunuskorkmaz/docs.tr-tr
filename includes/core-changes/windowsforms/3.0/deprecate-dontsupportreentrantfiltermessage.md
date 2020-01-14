---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937011"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="de790-101">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="de790-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="de790-102">.NET Framework 4.6.1 içinde tanıtılan `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="de790-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="de790-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="de790-103">Change description</span></span>

<span data-ttu-id="de790-104">.NET Framework 4.6.1 ile başlayarak, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` uyumluluk anahtarı, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulamasıyla çağrıldığında olası <xref:System.IndexOutOfRangeException> özel durumları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de790-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="de790-105">Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="de790-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="de790-106">.NET Core 'da `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="de790-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="de790-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="de790-107">Version introduced</span></span>

<span data-ttu-id="de790-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="de790-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="de790-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="de790-109">Recommended action</span></span>

<span data-ttu-id="de790-110">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="de790-110">Remove the switch.</span></span> <span data-ttu-id="de790-111">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="de790-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="de790-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="de790-112">Category</span></span>

<span data-ttu-id="de790-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de790-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="de790-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="de790-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
