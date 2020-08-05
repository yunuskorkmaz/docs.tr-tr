---
ms.openlocfilehash: 95aa243a5790d4201c7871e617dbe4ccafb7c1a1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556244"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="74cee-101">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="74cee-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="74cee-102">`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.NET Framework 4.6.1 ' de tanıtılan uyumluluk anahtarı .NET Core ve .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="74cee-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74cee-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="74cee-103">Change description</span></span>

<span data-ttu-id="74cee-104">.NET Framework 4.6.1 ile başlayarak, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` Uyumluluk anahtarı <xref:System.IndexOutOfRangeException> <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel bir uygulamayla çağrıldığında olası özel durumları ele alınmaktadır <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74cee-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="74cee-105">Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="74cee-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="74cee-106">.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="74cee-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74cee-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="74cee-107">Version introduced</span></span>

<span data-ttu-id="74cee-108">3,0</span><span class="sxs-lookup"><span data-stu-id="74cee-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74cee-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="74cee-109">Recommended action</span></span>

<span data-ttu-id="74cee-110">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="74cee-110">Remove the switch.</span></span> <span data-ttu-id="74cee-111">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="74cee-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="74cee-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="74cee-112">Category</span></span>

<span data-ttu-id="74cee-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74cee-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74cee-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="74cee-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
