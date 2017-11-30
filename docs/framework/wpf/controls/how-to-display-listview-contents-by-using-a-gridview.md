---
title: "Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24560a1e9b663a3145b589b5a03af8a8b72236ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [GridView genel bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
