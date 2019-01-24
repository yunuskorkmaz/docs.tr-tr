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
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Nasıl yapılır: GridView Uygulayan ListView İçinde Öğeleri Gruplandırma
Bu örnek gruplarını öğeleri göstermek nasıl gösterir <xref:System.Windows.Controls.GridView> görünüm modu bir <xref:System.Windows.Controls.ListView> denetimi.  
  
## <a name="example"></a>Örnek  
 İçindeki öğe gruplarını görüntülemek için bir <xref:System.Windows.Controls.ListView>, tanımlayan bir <xref:System.Windows.Data.CollectionViewSource>. Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.CollectionViewSource> veri öğelerinin değerini göre gruplar `Catalog` veri alanı.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için <xref:System.Windows.Controls.ListView> için <xref:System.Windows.Data.CollectionViewSource> , önceki örnekte tanımlar. Örnek ayrıca tanımlar bir <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> uygulayan bir <xref:System.Windows.Controls.Expander> denetimi.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
