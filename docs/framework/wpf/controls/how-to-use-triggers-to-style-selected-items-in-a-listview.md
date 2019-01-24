---
title: 'Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 5229c8db70d7d1200c75c7cbefd497e62cf72bdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682075"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a>Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma
Bu örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Style.Triggers%2A> için bir <xref:System.Windows.Controls.ListViewItem> denetim böylece bir özellik değeri, bir <xref:System.Windows.Controls.ListViewItem> değişiklikleri <xref:System.Windows.Style> , <xref:System.Windows.Controls.ListViewItem> değişiklikleri yanıt.  
  
## <a name="example"></a>Örnek  
 İsterseniz <xref:System.Windows.Style> , bir <xref:System.Windows.Controls.ListViewItem> özelliği değişikliklere yanıt olarak değiştirmek için tanımladığınız <xref:System.Windows.Style.Triggers%2A> için <xref:System.Windows.Style> değiştirin.  
  
 Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Trigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliğini <xref:System.Windows.Media.Brushes.Blue%2A> ve değişiklikleri <xref:System.Windows.FrameworkElement.Cursor%2A> görüntülemek için bir <xref:System.Windows.Input.CursorType.Hand> olduğunda <xref:System.Windows.UIElement.IsMouseOver%2A> özellik değişiklikleri `true`.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.MultiTrigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.ListViewItem> için <xref:System.Windows.Media.Brushes.Yellow%2A> olduğunda <xref:System.Windows.Controls.ListViewItem> seçili öğe ve klavye girintisine sahip.  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
