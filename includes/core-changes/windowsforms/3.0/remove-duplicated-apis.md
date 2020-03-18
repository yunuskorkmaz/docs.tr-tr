---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937090"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="87f7d-101">Windows Formlarından Kaldırılan Yinelenen API'ler</span><span class="sxs-lookup"><span data-stu-id="87f7d-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="87f7d-102">.NET Core 3.0 Preview <xref:System.Windows.Forms?displayProperty=fullName> 4'ten başlayarak ad alanında yanlışlıkla yinelenen bir dizi API ,NET Core 3.0 RC1'de kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="87f7d-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="87f7d-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="87f7d-103">Change description</span></span>

<span data-ttu-id="87f7d-104">.NET Core 3.0 Preview 4, <xref:System.Windows.Forms?displayProperty=fullName> <xref:System.ComponentModel.Design?displayProperty=fullName> ad alanında zaten var olan ad alanında yanlışlıkla bir dizi türü yineledi.</span><span class="sxs-lookup"><span data-stu-id="87f7d-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="87f7d-105">.NET Core 3.0 RC1 ile başlayarak, bu yinelenen türleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="87f7d-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="87f7d-106">Aşağıdaki tabloda özgün türü ve yinelenen türü listelenir:</span><span class="sxs-lookup"><span data-stu-id="87f7d-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="87f7d-107">Orijinal tür</span><span class="sxs-lookup"><span data-stu-id="87f7d-107">Original type</span></span>|<span data-ttu-id="87f7d-108">Yinelenen tür</span><span class="sxs-lookup"><span data-stu-id="87f7d-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="87f7d-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="87f7d-109">Version introduced</span></span>

<span data-ttu-id="87f7d-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="87f7d-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87f7d-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="87f7d-111">Recommended action</span></span>

<span data-ttu-id="87f7d-112">Tablonun **Özgün türü** sütununda gösterildiği gibi, özgün türe başvurmak için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="87f7d-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="87f7d-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="87f7d-113">Category</span></span>

<span data-ttu-id="87f7d-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87f7d-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87f7d-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="87f7d-115">Affected APIs</span></span>

- <span data-ttu-id="87f7d-116">API analizi ile tespit edilemez.</span><span class="sxs-lookup"><span data-stu-id="87f7d-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
