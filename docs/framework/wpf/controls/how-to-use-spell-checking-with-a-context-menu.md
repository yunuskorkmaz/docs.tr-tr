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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699155"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="c6fee-102">Nasıl yapılır: Açılır Menü ile Yazım Denetimi Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6fee-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="c6fee-103">Varsayılan olarak, bir düzenleme denetiminde yazım etkinleştirdiğinizde, ister <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>, yazım denetimi seçenekleri bağlam menüsü alın.</span><span class="sxs-lookup"><span data-stu-id="c6fee-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="c6fee-104">Kullanıcı yanlış yazılmış bir sözcük tıkladığında, örneğin, bir dizi yazım önerileri veya seçeneği aldıkları **Tümünü Yoksay**.</span><span class="sxs-lookup"><span data-stu-id="c6fee-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="c6fee-105">Ancak, kendi özel bağlam menüsü ile varsayılan bağlam menüsü geçersiz kıldığınızda, bu işlevselliğinin kaybolduğu ve bağlam menüsünde yazım denetimi özelliği yeniden etkinleştirmek için kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6fee-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="c6fee-106">Aşağıdaki örnek bu üzerinde nasıl etkinleştirileceğini gösterir bir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c6fee-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6fee-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6fee-107">Example</span></span>  
 <span data-ttu-id="c6fee-108">Aşağıdaki örnekte gösterildiği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturan bir <xref:System.Windows.Controls.TextBox> bağlam menüsünü uygulamak için kullanılan bazı olaylar ile.</span><span class="sxs-lookup"><span data-stu-id="c6fee-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="c6fee-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6fee-109">Example</span></span>  
 <span data-ttu-id="c6fee-110">Aşağıdaki örnek, bağlam menüsünü uygulayan kod gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6fee-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="c6fee-111">Bunu yapmak için kullanılan kod bir <xref:System.Windows.Controls.RichTextBox> benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c6fee-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="c6fee-112">Geçirilen parametre ana fark `GetSpellingError` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c6fee-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="c6fee-113">İçin bir <xref:System.Windows.Controls.TextBox>, şapka tamsayı dizini geçirin:</span><span class="sxs-lookup"><span data-stu-id="c6fee-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="c6fee-114">İçin bir <xref:System.Windows.Controls.RichTextBox>, geçmesi <xref:System.Windows.Documents.TextPointer> şapka belirtir:</span><span class="sxs-lookup"><span data-stu-id="c6fee-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="c6fee-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6fee-115">See also</span></span>

- [<span data-ttu-id="c6fee-116">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6fee-116">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="c6fee-117">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6fee-117">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="c6fee-118">Metin Düzenleme Denetiminde Yazım Denetimini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c6fee-118">Enable Spell Checking in a Text Editing Control</span></span>](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [<span data-ttu-id="c6fee-119">TextBox ile Özel Bağlam Menüsü Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6fee-119">Use a Custom Context Menu with a TextBox</span></span>](how-to-use-a-custom-context-menu-with-a-textbox.md)
