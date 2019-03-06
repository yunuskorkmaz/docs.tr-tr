---
title: 'Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: e4058518e4eb56e1cd9d5fdafd792d8f8d3b77ab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367849"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma
Bu örnek başına veya sonuna metin içeriğini imleci konumlandırma nasıl gösterir bir <xref:System.Windows.Controls.TextBox> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu tanımlayan bir <xref:System.Windows.Controls.TextBox> denetlemek ve bir ad atar.  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>Örnek  
 İçeriğini başında İmleç konumuna bir <xref:System.Windows.Controls.TextBox> denetiminde, arama <xref:System.Windows.Controls.TextBox.Select%2A> yöntemi ve seçimi başlangıç konumu 0 ve 0 seçim uzunluğunu belirtin.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>Örnek  
 Sonunda içeriğini, İmleç konumuna bir <xref:System.Windows.Controls.TextBox> denetiminde, arama <xref:System.Windows.Controls.TextBox.Select%2A> yöntemi ve içerik metnin uzunluğunu ve seçim uzunluğu 0 eşit seçimi başlangıç konumu belirtin.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
