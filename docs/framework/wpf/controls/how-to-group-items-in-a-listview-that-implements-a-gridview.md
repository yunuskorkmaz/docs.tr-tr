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
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma
Bu örnek öğelerinin gruplarını görüntülemek nasıl gösterir <xref:System.Windows.Controls.GridView> görüntüleme modu, bir <xref:System.Windows.Controls.ListView> denetim.  
  
## <a name="example"></a>Örnek  
 İçindeki öğe gruplarını görüntülemek için bir <xref:System.Windows.Controls.ListView>, tanımlayan bir <xref:System.Windows.Data.CollectionViewSource>. Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.CollectionViewSource> değerini göre veri öğelerini gruplayan `Catalog` veri alanı.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.ListView> için <xref:System.Windows.Data.CollectionViewSource> , önceki örnekte tanımlar. Örnek ayrıca tanımlar bir <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> uygulayan bir <xref:System.Windows.Controls.Expander> denetim.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
