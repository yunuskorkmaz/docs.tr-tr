---
title: "Nasıl yapılır: Bağlam Menüsü ile Yazım Denetimi Kullanma"
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
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a85426dc526e1e8560f494bcde5247fc394f7bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Nasıl yapılır: Bağlam Menüsü ile Yazım Denetimi Kullanma
Varsayılan olarak, bir düzenleme denetiminde yazım etkinleştirdiğinizde ister <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>, bağlam menüsünde yazım denetimi seçenekleri Al. Kullanıcı yanlış yazılmış bir sözcük tıkladığında, örneğin, yazım önerileri ya da seçeneğini elde **Tümünü Yoksay**. Ancak, kendi özel bağlam menüsü ile varsayılan bağlam menüsünü geçersiz kıldığınızda, bu işlevsellik kaybolur ve bağlam menüsünden Yazım denetimi özelliği yeniden etkinleştirmek için kod yazmanız gerekir. Aşağıdaki örnek, bunu etkinleştirmek gösterilmiştir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturan bir <xref:System.Windows.Controls.TextBox> bağlam menüsünü uygulamak için kullanılan bazı olaylar ile.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bağlam menüsünü uygulayan kodu gösterir.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Bunu yapmak için kullanılan kod bir <xref:System.Windows.Controls.RichTextBox> benzer. Geçirilen parametre ana farktır `GetSpellingError` yöntemi. İçin bir <xref:System.Windows.Controls.TextBox>, düzeltme işareti konumunun tamsayı dizinini geçirin:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 İçin bir <xref:System.Windows.Controls.RichTextBox>, geçirmek <xref:System.Windows.Documents.TextPointer> imleç konumunu belirtir:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Metin Düzenleme Denetiminde Yazım Denetimini Etkinleştirme](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [TextBox ile Özel Bağlam Menüsü Kullanma](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
