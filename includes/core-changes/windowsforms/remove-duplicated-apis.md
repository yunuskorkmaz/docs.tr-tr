---
ms.openlocfilehash: 3d0a90a57c2b1c2759b8420e74c284668d54e9cb
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72526781"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="30418-101">Yinelenen API 'Ler Windows Forms kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="30418-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="30418-102">.NET Core 3,0 Preview 4 ' te başlayan <xref:System.Windows.Forms?displayProperty=fullName> ad alanında yanlışlıkla çoğaltılan bir dizi API 'Ler .NET Core 3,0 RC1 sürümünde kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="30418-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="30418-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="30418-103">Change description</span></span>

<span data-ttu-id="30418-104">.NET Core 3,0 Preview 4 istenmeden yinelenen <xref:System.ComponentModel.Design?displayProperty=fullName> ad alanında zaten bulunan <xref:System.Windows.Forms?displayProperty=fullName> ad alanında bir dizi tür.</span><span class="sxs-lookup"><span data-stu-id="30418-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="30418-105">.NET Core 3,0 RC1 ile başlayarak, bu yinelenen türler artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30418-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="30418-106">Aşağıdaki tabloda, özgün tür ve onun yinelenen türü listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="30418-106">The following table shows lists the original type and its duplicated type:</span></span>

|<span data-ttu-id="30418-107">Özgün tür</span><span class="sxs-lookup"><span data-stu-id="30418-107">Original type</span></span>|<span data-ttu-id="30418-108">Yinelenen tür</span><span class="sxs-lookup"><span data-stu-id="30418-108">Duplicated type</span></span>|
|---|---|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
|<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
|<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="30418-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="30418-109">Version introduced</span></span>

<span data-ttu-id="30418-110">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="30418-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30418-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="30418-111">Recommended action</span></span>

<span data-ttu-id="30418-112">Kodu, tablonun **özgün tür** sütununda gösterildiği gibi özgün türe başvuracak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="30418-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="30418-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="30418-113">Category</span></span>

<span data-ttu-id="30418-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30418-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30418-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="30418-115">Affected APIs</span></span>

- <span data-ttu-id="30418-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="30418-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
