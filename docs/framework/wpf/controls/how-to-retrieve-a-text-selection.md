---
title: 'Nasıl yapılır: Metin Seçimi Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: 3e2a4d9938f73cb306e8fd8b0e6b25b5abfa3b4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517779"
---
# <a name="how-to-retrieve-a-text-selection"></a>Nasıl yapılır: Metin Seçimi Alma
Bu örnekte kullanılacak yollarından biri gösterilmektedir <xref:System.Windows.Controls.TextBox.SelectedText%2A> kullanıcının seçtiği metni almak için özellik bir <xref:System.Windows.Controls.TextBox> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek gösterir tanımının bir <xref:System.Windows.Controls.TextBox> seçmek için bazı metni içeren denetim ve <xref:System.Windows.Controls.Button> denetimi belirtilen <xref:System.Windows.Controls.Button.OnClick%2A> yöntemi.  
  
 Bu örnekte, bir düğme ile ilişkili <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi, metin seçimi alma için kullanılır. Kullanıcı düğmeye tıkladığında <xref:System.Windows.Controls.Button.OnClick%2A> yöntemi metin kutusunda seçili metin herhangi bir dizeye kopyalar. Belirli koşullara tarafından metin seçimi (bir düğmeye tıklanması) yanı sıra (metin seçimi dizeye kopyalama) bu seçimle gerçekleştirilecek eylemi kolayca değiştirilebilir bir çeşitli senaryolar uyum sağlayacak şekilde alınır.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örnekte gösterildiği bir <xref:System.Windows.Controls.Button.OnClick%2A> tanımlanan düğmesi için olay işleyicisi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu örneğin.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
