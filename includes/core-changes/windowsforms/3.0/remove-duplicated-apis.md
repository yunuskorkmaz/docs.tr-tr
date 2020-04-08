---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888154"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="e89ea-101">Windows Formlarından Kaldırılan Yinelenen API'ler</span><span class="sxs-lookup"><span data-stu-id="e89ea-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="e89ea-102">.NET Core 3.0 Preview <xref:System.Windows.Forms?displayProperty=fullName> 4'ten başlayarak ad alanında yanlışlıkla yinelenen bir dizi API ,NET Core 3.0 RC1'de kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="e89ea-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e89ea-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="e89ea-103">Change description</span></span>

<span data-ttu-id="e89ea-104">.NET Core 3.0 Preview 4, <xref:System.Windows.Forms?displayProperty=fullName> <xref:System.ComponentModel.Design?displayProperty=fullName> ad alanında zaten var olan ad alanında yanlışlıkla bir dizi türü yineledi.</span><span class="sxs-lookup"><span data-stu-id="e89ea-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="e89ea-105">.NET Core 3.0 RC1 ile başlayarak, bu yinelenen türleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e89ea-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="e89ea-106">Aşağıdaki tabloda özgün türü ve yinelenen türü listelenir:</span><span class="sxs-lookup"><span data-stu-id="e89ea-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="e89ea-107">Orijinal tür</span><span class="sxs-lookup"><span data-stu-id="e89ea-107">Original type</span></span>|<span data-ttu-id="e89ea-108">Yinelenen tür</span><span class="sxs-lookup"><span data-stu-id="e89ea-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="e89ea-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="e89ea-109">Version introduced</span></span>

<span data-ttu-id="e89ea-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="e89ea-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e89ea-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e89ea-111">Recommended action</span></span>

<span data-ttu-id="e89ea-112">Tablonun **Özgün türü** sütununda gösterildiği gibi, özgün türe başvurmak için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e89ea-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="e89ea-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="e89ea-113">Category</span></span>

<span data-ttu-id="e89ea-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e89ea-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e89ea-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e89ea-115">Affected APIs</span></span>

- <span data-ttu-id="e89ea-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e89ea-116">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
