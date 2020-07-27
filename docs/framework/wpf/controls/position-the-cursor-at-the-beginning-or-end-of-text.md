---
title: 'Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma'
description: Windows Presentation Foundation TextBox denetiminin metin içeriğinin başlangıcında veya sonunda imlecin nasıl konumlandıralınacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167515"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma
Bu örnek, bir denetimin metin içeriğinin başlangıcında veya sonunda imlecin nasıl konumlandıralınacağını gösterir <xref:System.Windows.Controls.TextBox> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod bir denetimi açıklar <xref:System.Windows.Controls.TextBox> ve bir adı atar.  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>Örnek  
 İmleci bir denetimin içeriğinin başlangıcına yerleştirmek için <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.TextBox.Select%2A> yöntemini çağırın ve 0 ' ın seçim başlangıç konumunu ve 0 seçim uzunluğunu belirtin.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>Örnek  
 İmleci bir denetimin içeriğinin sonuna yerleştirmek için <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.TextBox.Select%2A> yöntemini çağırın ve seçim başlangıç konumunu metin içeriğinin uzunluğuna eşit ve seçim uzunluğu 0 olarak belirtin.  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakışı](textbox-overview.md)
- [RichTextBox Genel Bakışı](richtextbox-overview.md)
