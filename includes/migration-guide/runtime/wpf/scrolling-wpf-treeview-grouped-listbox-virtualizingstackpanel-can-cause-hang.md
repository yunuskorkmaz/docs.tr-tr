---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622152"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="abd2b-101">Bir VirtualizingStackPanel içindeki WPF TreeView veya gruplanmış ListBox 'ın kaydırılacağı bir askıda kalmasına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="abd2b-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="abd2b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="abd2b-102">Details</span></span>

<span data-ttu-id="abd2b-103">.NET Framework v 4.5 ' te, bir sanallaştırılmış yığın panelinde bir WPF kaydırmak, <xref:System.Windows.Controls.TreeView?displayProperty=fullName> Görünüm penceresinde ( <xref:System.Windows.Controls.TreeView?displayProperty=fullName> Örneğin, veya bir ItemsPresenter öğesinde bulunan öğeler arasında) kenar boşlukları varsa askıda kalmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="abd2b-104">Ayrıca, bazı durumlarda görünümdeki farklı boyutlardaki öğeler, kenar boşluğu olmasa bile kararsızlığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="abd2b-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="abd2b-105">Suggestion</span></span>

<span data-ttu-id="abd2b-106">.NET Framework 4.5.1 ' e yükselterek bu hataya kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="abd2b-107">Alternatif olarak, <xref:System.Windows.Controls.TreeView?displayProperty=fullName> içerilen tüm öğelerin aynı boyutta olması halinde, sanallaştırılmış yığın panellerinde (gibi), kenar boşlukları kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="abd2b-108">Name</span><span class="sxs-lookup"><span data-stu-id="abd2b-108">Name</span></span>    | <span data-ttu-id="abd2b-109">Değer</span><span class="sxs-lookup"><span data-stu-id="abd2b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="abd2b-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="abd2b-110">Scope</span></span>   |<span data-ttu-id="abd2b-111">Ana</span><span class="sxs-lookup"><span data-stu-id="abd2b-111">Major</span></span>|
|<span data-ttu-id="abd2b-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="abd2b-112">Version</span></span>|<span data-ttu-id="abd2b-113">4,5</span><span class="sxs-lookup"><span data-stu-id="abd2b-113">4.5</span></span>|
|<span data-ttu-id="abd2b-114">Tür</span><span class="sxs-lookup"><span data-stu-id="abd2b-114">Type</span></span>|<span data-ttu-id="abd2b-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="abd2b-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abd2b-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="abd2b-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
