---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 76074449d4ea1454689c51ecad54d7c495f00872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551914"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="5f7b4-102">Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="5f7b4-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="5f7b4-103">Bu örnek öğelerinin gruplarını görüntülemek nasıl gösterir <xref:System.Windows.Controls.GridView> görüntüleme modu, bir <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f7b4-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f7b4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f7b4-104">Example</span></span>  
 <span data-ttu-id="5f7b4-105">İçindeki öğe gruplarını görüntülemek için bir <xref:System.Windows.Controls.ListView>, tanımlayan bir <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="5f7b4-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="5f7b4-106">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.CollectionViewSource> değerini göre veri öğelerini gruplayan `Catalog` veri alanı.</span><span class="sxs-lookup"><span data-stu-id="5f7b4-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="5f7b4-107">Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.ListView> için <xref:System.Windows.Data.CollectionViewSource> , önceki örnekte tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f7b4-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="5f7b4-108">Örnek ayrıca tanımlar bir <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> uygulayan bir <xref:System.Windows.Controls.Expander> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f7b4-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="5f7b4-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f7b4-109">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="5f7b4-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5f7b4-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="5f7b4-111">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5f7b4-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="5f7b4-112">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5f7b4-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
