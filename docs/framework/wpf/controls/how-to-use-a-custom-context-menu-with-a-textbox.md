---
title: 'Nasıl yapılır: TextBox ile Özel Bağlam Menüsü Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: b0507c6fa37f0f51f9e12ebe5f908c39c25b50d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129422"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>Nasıl yapılır: TextBox ile Özel Bağlam Menüsü Kullanma
Bu örnek için basit bir özel bağlam menüsü tanımlaması ve nasıl gösterir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek tanımlayan bir <xref:System.Windows.Controls.TextBox> özel bağlam menüsü içeren denetim.  
  
 Bağlam menüsünü kullanarak tanımlanan bir <xref:System.Windows.Controls.ContextMenu> öğesi.  Bağlam menüsü oluşan bir dizi <xref:System.Windows.Controls.MenuItem> öğeleri ve <xref:System.Windows.Controls.Separator> öğeleri.  Her <xref:System.Windows.Controls.MenuItem> öğe tanımlar komut bağlam menüsü; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özniteliği menü komutu için görüntü metni tanımlar ve <xref:System.Windows.Controls.MenuItem.Click> özniteliği, her bir menü öğesi için bir işleyici yöntemi belirtir.  <xref:System.Windows.Controls.Separator> Öğenin yalnızca önceki ve sonraki menü öğeleri arasında işlenecek ayıran bir çizginin neden olur.  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki bağlam menüsü tanımı uygulama kodunu yanı sıra, sağlar ve içerik menüsünden devre dışı bırakan kod gösterir.  <xref:System.Windows.Controls.ContextMenu.Opened> Dinamik olarak etkinleştirme veya geçerli durumuna bağlı olarak belirli komutları devre dışı bırakmak için kullanılan olay <xref:System.Windows.Controls.TextBox>.  
  
 Varsayılan bağlam menüsünü kullanarak geri yükleme, <xref:System.Windows.DependencyObject.ClearValue%2A> değerini temizlemek için yöntemi <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği.  Bağlam menüsü tamamen devre dışı bırakmak için ayarlanmış <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği bir null başvuruya (`Nothing` Visual Basic'te).  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Açılır Menü ile Yazım Denetimi Kullanma](how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
