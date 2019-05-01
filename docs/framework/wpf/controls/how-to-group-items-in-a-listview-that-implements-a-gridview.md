---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: b3dd6891976a942b299c87fca25e430e9ee59a51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910279"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="e9ccb-102">Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="e9ccb-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="e9ccb-103">Bu örnek gruplarını öğeleri göstermek nasıl gösterir <xref:System.Windows.Controls.GridView> görünüm modu bir <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e9ccb-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9ccb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9ccb-104">Example</span></span>  
 <span data-ttu-id="e9ccb-105">İçindeki öğe gruplarını görüntülemek için bir <xref:System.Windows.Controls.ListView>, tanımlayan bir <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="e9ccb-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="e9ccb-106">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.CollectionViewSource> veri öğelerinin değerini göre gruplar `Catalog` veri alanı.</span><span class="sxs-lookup"><span data-stu-id="e9ccb-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="e9ccb-107">Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.ListView> için <xref:System.Windows.Data.CollectionViewSource> , önceki örnekte tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9ccb-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="e9ccb-108">Örnek ayrıca tanımlar bir <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> uygulayan bir <xref:System.Windows.Controls.Expander> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e9ccb-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="e9ccb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9ccb-109">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="e9ccb-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e9ccb-110">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="e9ccb-111">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9ccb-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="e9ccb-112">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9ccb-112">GridView Overview</span></span>](gridview-overview.md)
