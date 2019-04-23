---
title: 'Nasıl yapılır: Açılır Menü ile Yazım Denetimi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 72b24c386eb99140c9c2729688994b81f92e1a6f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192985"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Nasıl yapılır: Açılır Menü ile Yazım Denetimi Kullanma
Varsayılan olarak, bir düzenleme denetiminde yazım etkinleştirdiğinizde, ister <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>, yazım denetimi seçenekleri bağlam menüsü alın. Kullanıcı yanlış yazılmış bir sözcük tıkladığında, örneğin, bir dizi yazım önerileri veya seçeneği aldıkları **Tümünü Yoksay**. Ancak, kendi özel bağlam menüsü ile varsayılan bağlam menüsü geçersiz kıldığınızda, bu işlevselliğinin kaybolduğu ve bağlam menüsünde yazım denetimi özelliği yeniden etkinleştirmek için kod yazmanız gerekir. Aşağıdaki örnek bu üzerinde nasıl etkinleştirileceğini gösterir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturan bir <xref:System.Windows.Controls.TextBox> bağlam menüsünü uygulamak için kullanılan bazı olaylar ile.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bağlam menüsünü uygulayan kod gösterir.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Bunu yapmak için kullanılan kod bir <xref:System.Windows.Controls.RichTextBox> benzerdir. Geçirilen parametre ana fark `GetSpellingError` yöntemi. İçin bir <xref:System.Windows.Controls.TextBox>, şapka tamsayı dizini geçirin:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 İçin bir <xref:System.Windows.Controls.RichTextBox>, geçmesi <xref:System.Windows.Documents.TextPointer> şapka belirtir:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
- [Metin Düzenleme Denetiminde Yazım Denetimini Etkinleştirme](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [TextBox ile Özel Bağlam Menüsü Kullanma](how-to-use-a-custom-context-menu-with-a-textbox.md)
