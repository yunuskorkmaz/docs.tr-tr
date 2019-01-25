---
title: 'Nasıl yapılır: Bağlam Menüsü ile Yazım Denetimi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 2b6790fd4d5d2e322a46bd98ed19e7b88c4923c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713122"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Nasıl yapılır: Bağlam Menüsü ile Yazım Denetimi Kullanma
Varsayılan olarak, bir düzenleme denetiminde yazım etkinleştirdiğinizde, ister <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>, yazım denetimi seçenekleri bağlam menüsü alın. Kullanıcı yanlış yazılmış bir sözcük tıkladığında, örneğin, bir dizi yazım önerileri veya seçeneği aldıkları **Tümünü Yoksay**. Ancak, kendi özel bağlam menüsü ile varsayılan bağlam menüsü geçersiz kıldığınızda, bu işlevselliğinin kaybolduğu ve bağlam menüsünde yazım denetimi özelliği yeniden etkinleştirmek için kod yazmanız gerekir. Aşağıdaki örnek bu üzerinde nasıl etkinleştirileceğini gösterir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturan bir <xref:System.Windows.Controls.TextBox> bağlam menüsünü uygulamak için kullanılan bazı olaylar ile.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bağlam menüsünü uygulayan kod gösterir.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Bunu yapmak için kullanılan kod bir <xref:System.Windows.Controls.RichTextBox> benzerdir. Geçirilen parametre ana fark `GetSpellingError` yöntemi. İçin bir <xref:System.Windows.Controls.TextBox>, şapka tamsayı dizini geçirin:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 İçin bir <xref:System.Windows.Controls.RichTextBox>, geçmesi <xref:System.Windows.Documents.TextPointer> şapka belirtir:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
- [Metin Düzenleme Denetiminde Yazım Denetimini Etkinleştirme](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)
- [TextBox ile Özel Bağlam Menüsü Kullanma](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
