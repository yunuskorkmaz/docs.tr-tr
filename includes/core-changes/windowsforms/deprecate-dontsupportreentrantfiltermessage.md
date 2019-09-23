---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181782"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="1516b-101">Switch. System. Windows. Forms. DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1516b-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="1516b-102">.NET Framework 4.6.1 ' de tanıtılan Uyumlulukanahtarı.NETCore3,0'deWindowsFormsdesteklenmez.`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`</span><span class="sxs-lookup"><span data-stu-id="1516b-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1516b-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1516b-103">Change description</span></span>

<span data-ttu-id="1516b-104">.NET Framework 4.6.1 ile `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` başlayarak, uyumluluk anahtarı <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> ileti özel <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> bir uygulamayla <xref:System.IndexOutOfRangeException> çağrıldığında olası özel durumları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1516b-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="1516b-105">Daha fazla bilgi için bkz [. azaltma: Özel IMessageFilter. PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="1516b-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="1516b-106">.NET Core 'da, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1516b-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1516b-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1516b-107">Version introduced</span></span>

<span data-ttu-id="1516b-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="1516b-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1516b-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1516b-109">Recommended action</span></span>

<span data-ttu-id="1516b-110">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1516b-110">Remove the switch.</span></span> <span data-ttu-id="1516b-111">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1516b-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1516b-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="1516b-112">Category</span></span>

<span data-ttu-id="1516b-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1516b-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1516b-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1516b-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
