---
title: 'Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 103a439b9cee959d0077e5a759364eb9b943905d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554057"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme
Bu örnek nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.GridView> görüntüleme modu için bir <xref:System.Windows.Controls.ListView> denetim.  
  
## <a name="example"></a>Örnek  
 Görünüm modunu tanımlayabilirsiniz bir <xref:System.Windows.Controls.GridView> belirterek <xref:System.Windows.Controls.GridViewColumn> nesneleri. Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.GridViewColumn> için belirtilen veri içeriğine bağlanan nesneleri <xref:System.Windows.Controls.ListView> denetim. Bu <xref:System.Windows.Controls.GridView> örnek belirtir üç <xref:System.Windows.Controls.GridViewColumn> Eşle nesneleri `FirstName`, `LastName`, ve `EmployeeNumber` alanlarının `EmployeeInfoDataSource` olarak ayarlanmış <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListView> denetim.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki çizimde, bu örnek nasıl göründüğünü gösterir.  
  
 ![GridView çıkışıyla ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
