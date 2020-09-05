---
ms.openlocfilehash: 12a26030a9a336d887ae9d53994a9daf13356618
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497871"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="710e8-101">Bir TextBlock denetiminin üst öğesinin IsEnabled özelliğini değiştirmek, tüm alt denetimleri etkiler</span><span class="sxs-lookup"><span data-stu-id="710e8-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

#### <a name="details"></a><span data-ttu-id="710e8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="710e8-102">Details</span></span>

<span data-ttu-id="710e8-103">.NET Framework 4.6.2 başlayarak, <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> bir denetimin üst öğesinin özelliğini değiştirmek, <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> denetimin tüm alt denetimlerini (köprüler ve düğmeler gibi) etkiler <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> . .NET Framework 4.6.1 ve önceki sürümlerde, içindeki denetimler <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> her zaman üst öğenin özelliğinin durumunu yansıtmamaktadır <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="710e8-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> parent.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="710e8-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="710e8-104">Suggestion</span></span>

<span data-ttu-id="710e8-105">Yok.</span><span class="sxs-lookup"><span data-stu-id="710e8-105">None.</span></span> <span data-ttu-id="710e8-106">Bu değişiklik, denetim içindeki denetimler için beklenen davranışa uyar <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="710e8-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.</span></span>

| <span data-ttu-id="710e8-107">Name</span><span class="sxs-lookup"><span data-stu-id="710e8-107">Name</span></span>    | <span data-ttu-id="710e8-108">Değer</span><span class="sxs-lookup"><span data-stu-id="710e8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="710e8-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="710e8-109">Scope</span></span>   |<span data-ttu-id="710e8-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="710e8-110">Minor</span></span>|
|<span data-ttu-id="710e8-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="710e8-111">Version</span></span>|<span data-ttu-id="710e8-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="710e8-112">4.6.2</span></span>|
|<span data-ttu-id="710e8-113">Tür</span><span class="sxs-lookup"><span data-stu-id="710e8-113">Type</span></span>|<span data-ttu-id="710e8-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="710e8-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="710e8-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="710e8-115">Affected APIs</span></span>

- <xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.UIElement.IsEnabled`

-->
