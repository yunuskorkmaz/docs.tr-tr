---
title: 'Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: da91e27b804d649f5b8010bc9d7c074425be26f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212199"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TextBox.Text%2A> ilk metin içeriğini ayarlama özelliği bir <xref:System.Windows.Controls.TextBox> denetimi.  
  
 **Not** rağmen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örneğinin sürümü kullanması `<TextBox.Text>` etiketleri her düğmenin etrafında <xref:System.Windows.Controls.TextBox> içerik, gerekli değildir çünkü <xref:System.Windows.Controls.TextBox> geçerlidir <xref:System.Windows.Markup.ContentPropertyAttribute> özniteliğini <xref:System.Windows.Controls.TextBox.Text%2A> özelliği. Daha fazla bilgi için [XAML genel bakış (WPF)](../advanced/xaml-overview-wpf.md).  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
