---
title: 'Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 1066869c80bf5bd87d656bcb4994c188ee0e8efc
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185616"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme
Bu örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.GridView> görünüm modu için bir <xref:System.Windows.Controls.ListView> denetimi.  
  
## <a name="example"></a>Örnek  
 Görünüm modu, tanımladığınız bir <xref:System.Windows.Controls.GridView> belirterek <xref:System.Windows.Controls.GridViewColumn> nesneleri. Aşağıdaki örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.GridViewColumn> için belirtilen veri içeriği bağlama nesnelerini <xref:System.Windows.Controls.ListView> denetimi. Bu <xref:System.Windows.Controls.GridView> örnek üç belirtir <xref:System.Windows.Controls.GridViewColumn> eşleyen nesneleri `FirstName`, `LastName`, ve `EmployeeNumber` alanlarının `EmployeeInfoDataSource` olarak ayarlanan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListView> denetimi.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Bu örnek nasıl göründüğü aşağıda gösterilmiştir.  
  
 ![Bir ListView GridView çıktıyla gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView Genel Bakış](listview-overview.md)
- [GridView Genel Bakış](gridview-overview.md)
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
