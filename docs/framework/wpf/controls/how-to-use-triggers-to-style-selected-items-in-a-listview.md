---
title: "Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e86c7f875376a4ab28eec7cd032a165745445441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma
Bu örnek nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Style.Triggers%2A> için bir <xref:System.Windows.Controls.ListViewItem> denetim için bir özellik değeri, bir <xref:System.Windows.Controls.ListViewItem> değişiklikleri, <xref:System.Windows.Style> , <xref:System.Windows.Controls.ListViewItem> yanıt değişiklikler.  
  
## <a name="example"></a>Örnek  
 İsterseniz <xref:System.Windows.Style> , bir <xref:System.Windows.Controls.ListViewItem> özelliği değişikliklere yanıt değiştirmek için tanımlamak <xref:System.Windows.Style.Triggers%2A> için <xref:System.Windows.Style> değiştirin.  
  
 Aşağıdaki örnek tanımlar bir <xref:System.Windows.Trigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliğine <xref:System.Windows.Media.Brushes.Blue%2A> ve değişiklikleri <xref:System.Windows.FrameworkElement.Cursor%2A> görüntülemek için bir <xref:System.Windows.Input.CursorType.Hand> zaman <xref:System.Windows.UIElement.IsMouseOver%2A> özelliği değişiklikler `true`.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 Aşağıdaki örnek tanımlayan bir <xref:System.Windows.MultiTrigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.ListViewItem> için <xref:System.Windows.Media.Brushes.Yellow%2A> zaman <xref:System.Windows.Controls.ListViewItem> seçili öğe ve klavye odağı olan.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView genel bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
