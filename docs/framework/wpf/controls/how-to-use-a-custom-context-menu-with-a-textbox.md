---
title: "Nasıl yapılır: TextBox ile Özel Bağlam Menüsü Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4552031a08680af2f4d41702d2f76ed0c44af21b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>Nasıl yapılır: TextBox ile Özel Bağlam Menüsü Kullanma
Bu örnek tanımlamak ve uygulamak için basit özel bağlam menüsü gösterilmektedir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek tanımlayan bir <xref:System.Windows.Controls.TextBox> özel bağlam menüsünü içeren denetim.  
  
 Bağlam menüsü kullanılarak tanımlanan bir <xref:System.Windows.Controls.ContextMenu> öğesi.  Bağlam menüsüne bir dizi oluşur <xref:System.Windows.Controls.MenuItem> öğeleri ve <xref:System.Windows.Controls.Separator> öğeleri.  Her <xref:System.Windows.Controls.MenuItem> öğesi bağlam menüsünde; bir komut tanımlar <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özniteliği menü komutu için görüntü metni tanımlar ve <xref:System.Windows.Controls.MenuItem.Click> özniteliği, her bir menü öğesi için bir işleyici yöntemi belirtir.  <xref:System.Windows.Controls.Separator> Öğenin yalnızca önceki ve sonraki menü öğeleri arasında işlenmek üzere ayıran bir çizginin neden olur.  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki bağlam menü tanımının uygulama kodunu yanı sıra, sağlar ve bağlam menüsünden devre dışı bırakan kodu gösterir.  <xref:System.Windows.Controls.ContextMenu.Opened> Dinamik olarak etkinleştirmek veya geçerli durumuna bağlı olarak bazı komutlar devre dışı bırakmak için kullanılan olay <xref:System.Windows.Controls.TextBox>.  
  
 Varsayılan bağlam menüsünü geri yüklemek için kullanmak <xref:System.Windows.DependencyObject.ClearValue%2A> değerini temizlemek için yöntemi <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği.  Bağlam menüsü tamamen devre dışı bırakmak için ayarlanmış <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği bir null başvuru için (`Nothing` Visual Basic'te).  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Açılır Menü ile Yazım Denetimi Kullanma](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
