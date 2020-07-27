---
title: 'Nasıl yapılır: TextBox Denetiminde Odak Ayarlama'
description: Odak yönteminin bir Windows Presentation Foundation TextBox denetimine odaklanmak için nasıl kullanılacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: e107c22a3c5b701e02cbc8506d10fa35ee15c79d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168054"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>Nasıl yapılır: TextBox Denetiminde Odak Ayarlama
Bu örnek, <xref:System.Windows.UIElement.Focus%2A> bir denetim üzerinde odağı ayarlamak için yönteminin nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TextBox> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekte, <xref:System.Windows.Controls.TextBox> *tbFocusMe* adlı basit bir denetim açıklanmaktadır  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.UIElement.Focus%2A> <xref:System.Windows.Controls.TextBox> *tbFocusMe*adlı denetimin üzerindeki odağı ayarlamak için yöntemini çağırır.  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox Genel Bakışı](textbox-overview.md)
- [RichTextBox Genel Bakışı](richtextbox-overview.md)
