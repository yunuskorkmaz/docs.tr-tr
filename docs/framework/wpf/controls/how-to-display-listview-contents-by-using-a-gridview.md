---
title: 'Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 0e2b37cb061cc92b34c3a4f94bcd42e8ffc69ab5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606013"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme
Bu örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.GridView> görünüm modu için bir <xref:System.Windows.Controls.ListView> denetimi.  
  
## <a name="example"></a>Örnek  
 Görünüm modu, tanımladığınız bir <xref:System.Windows.Controls.GridView> belirterek <xref:System.Windows.Controls.GridViewColumn> nesneleri. Aşağıdaki örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.GridViewColumn> için belirtilen veri içeriği bağlama nesnelerini <xref:System.Windows.Controls.ListView> denetimi. Bu <xref:System.Windows.Controls.GridView> örnek üç belirtir <xref:System.Windows.Controls.GridViewColumn> eşleyen nesneleri `FirstName`, `LastName`, ve `EmployeeNumber` alanlarının `EmployeeInfoDataSource` olarak ayarlanan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListView> denetimi.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Bu örnek nasıl göründüğü aşağıda gösterilmiştir.  
  
 ![ListView GridView çıktıyla](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
