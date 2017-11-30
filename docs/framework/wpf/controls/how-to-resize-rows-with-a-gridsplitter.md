---
title: "Nasıl yapılır: GridSplitter ile Satırları Yeniden Boyutlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6621cc0048270b97c42ff4c4e646b0ddd9ca3477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Nasıl yapılır: GridSplitter ile Satırları Yeniden Boyutlandırma
Bu örnek yatay kullanmayı gösterir <xref:System.Windows.Controls.GridSplitter> iki satır arasındaki boşluğu yeniden dağıtmak için bir <xref:System.Windows.Controls.Grid> boyutlarını değiştirmeden <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Örnek  
 **Bu yer GridSplitter nasıl kenarın satır**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bitişik satırları yeniden boyutlandırır bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Row%2A> özelliği yeniden boyutlandırmak istediğiniz satırları birine eklenmiş. Varsa, <xref:System.Windows.Controls.Grid> birden fazla sütun var. ayarlamak <xref:System.Windows.Controls.Grid.ColumnSpan%2A> iliştirilmiş özelliği sütun sayısını belirtin. Ardından <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> için <xref:System.Windows.VerticalAlignment.Top> veya <xref:System.Windows.VerticalAlignment.Bottom> (hangi hizalamayı ayarlayacağınız yeniden boyutlandırmak istediğiniz iki satıra bağlıdır). Son olarak, ayarlamak <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğine <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 Aşağıdaki örnek, yatay tanımlamak gösterilmiştir <xref:System.Windows.Controls.GridSplitter> bitişik satırlara göre yeniden boyutlandırır.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> kendi satırında kaplar değil diğer denetimler tarafından görünmeyebilir <xref:System.Windows.Controls.Grid>. Bu sorunu önlemek nasıl hakkında daha fazla bilgi için bkz: [GridSplitter görünür olduğundan emin olun](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Bir satır kaplayan GridSplitter nasıl oluşturulur**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bir satır kaplayan bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Row%2A> özelliği yeniden boyutlandırmak istediğiniz satırları birine eklenmiş. Varsa, <xref:System.Windows.Controls.Grid> birden fazla sütun var. ayarlamak <xref:System.Windows.Controls.Grid.ColumnSpan%2A> sütun sayısı özelliği eklenmiş. Ardından <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> için <xref:System.Windows.VerticalAlignment.Center>ayarlayın <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğine <xref:System.Windows.HorizontalAlignment.Stretch>ve <xref:System.Windows.Controls.RowDefinition.Height%2A> içeren satırın <xref:System.Windows.Controls.GridSplitter> için <xref:System.Windows.GridLength.Auto%2A>.  
  
 Aşağıdaki örnek, yatay tanımlamak gösterilmiştir <xref:System.Windows.Controls.GridSplitter> , bir satır kaplayan ve her iki tarafında satırları yeniden boyutlandırır.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.GridSplitter>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
