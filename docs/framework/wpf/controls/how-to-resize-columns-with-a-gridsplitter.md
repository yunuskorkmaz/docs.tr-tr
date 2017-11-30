---
title: "Nasıl yapılır: GridSplitter ile Sütunları Yeniden Boyutlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c8299a3f4885618601c8087a61c21dc5d989813
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Nasıl yapılır: GridSplitter ile Sütunları Yeniden Boyutlandırma
Bu örnek dikey oluşturulacağını gösterir <xref:System.Windows.Controls.GridSplitter> iki sütun arasındaki boşluğu yeniden dağıtmak için bir <xref:System.Windows.Controls.Grid> boyutlarını değiştirmeden <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Örnek  
 **Bu yer GridSplitter nasıl sütunun kenarına**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bitişik sütunları yeniden boyutlandırır bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Column%2A> özelliği yeniden boyutlandırmak istediğiniz sütunlardan biri için eklenmiş. Varsa, <xref:System.Windows.Controls.Grid> birden fazla satır içeriyorsa ayarlamak <xref:System.Windows.Controls.Grid.RowSpan%2A> satır sayısı özelliği eklenmiş. Ardından <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğine <xref:System.Windows.HorizontalAlignment.Left> veya <xref:System.Windows.HorizontalAlignment.Right> (hangi hizalamayı ayarlayacağınız yeniden boyutlandırmak istediğiniz iki sütuna bağlıdır). Son olarak, ayarlamak <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğine <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> kendi sütun yok'deki diğer denetimler tarafından görünmeyebilir <xref:System.Windows.Controls.Grid>. Bu sorunu önlemek nasıl hakkında daha fazla bilgi için bkz: [GridSplitter görünür olduğundan emin olun](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Bir sütun kaplayan GridSplitter nasıl oluşturulur**  
  
 Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bir sütun kaplayan bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Column%2A> özelliği yeniden boyutlandırmak istediğiniz sütunlardan biri için eklenmiş. Kılavuzunuzun birden fazla satır varsa ayarlamak <xref:System.Windows.Controls.Grid.RowSpan%2A> satır sayısı özelliği eklenmiş. Ardından <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> için <xref:System.Windows.HorizontalAlignment.Center>ayarlayın <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğine <xref:System.Windows.VerticalAlignment.Stretch>ve <xref:System.Windows.Controls.ColumnDefinition.Width%2A> içeren sütunun <xref:System.Windows.Controls.GridSplitter> için <xref:System.Windows.GridLength.Auto%2A>.  
  
 Aşağıdaki örnek, dikey tanımlamak gösterilmiştir <xref:System.Windows.Controls.GridSplitter> , bir sütun kaplayan ve her iki tarafında sütunları yeniden boyutlandırır.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.GridSplitter>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
