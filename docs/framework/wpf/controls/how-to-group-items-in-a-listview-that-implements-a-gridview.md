---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 1570eab70dae690f508975162b7553de92be6f12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664362"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="50408-102">Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="50408-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="50408-103">Bu örnek gruplarını öğeleri göstermek nasıl gösterir <xref:System.Windows.Controls.GridView> görünüm modu bir <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="50408-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50408-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="50408-104">Example</span></span>  
 <span data-ttu-id="50408-105">İçindeki öğe gruplarını görüntülemek için bir <xref:System.Windows.Controls.ListView>, tanımlayan bir <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="50408-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="50408-106">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.CollectionViewSource> veri öğelerinin değerini göre gruplar `Catalog` veri alanı.</span><span class="sxs-lookup"><span data-stu-id="50408-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="50408-107">Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.ListView> için <xref:System.Windows.Data.CollectionViewSource> , önceki örnekte tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50408-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="50408-108">Örnek ayrıca tanımlar bir <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> uygulayan bir <xref:System.Windows.Controls.Expander> denetimi.</span><span class="sxs-lookup"><span data-stu-id="50408-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="50408-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50408-109">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="50408-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="50408-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [<span data-ttu-id="50408-111">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50408-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
- [<span data-ttu-id="50408-112">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50408-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
