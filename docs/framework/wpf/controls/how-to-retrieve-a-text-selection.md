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
ms.openlocfilehash: b7f0b9ee02a7ace717787fc8eeb6e15649829a49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224591"
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="701a8-102">Nasıl yapılır: Metin Seçimi Alma</span><span class="sxs-lookup"><span data-stu-id="701a8-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="701a8-103">Bu örnekte kullanılacak yollarından biri gösterilmektedir <xref:System.Windows.Controls.TextBox.SelectedText%2A> kullanıcının seçtiği metni almak için özellik bir <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="701a8-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="701a8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="701a8-104">Example</span></span>  
 <span data-ttu-id="701a8-105">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek gösterir tanımının bir <xref:System.Windows.Controls.TextBox> seçmek için bazı metni içeren denetim ve <xref:System.Windows.Controls.Button> denetimi belirtilen <xref:System.Windows.Controls.Button.OnClick%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="701a8-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="701a8-106">Bu örnekte, bir düğme ile ilişkili <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi, metin seçimi alma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="701a8-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="701a8-107">Kullanıcı düğmeye tıkladığında <xref:System.Windows.Controls.Button.OnClick%2A> yöntemi metin kutusunda seçili metin herhangi bir dizeye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="701a8-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="701a8-108">Belirli koşullara tarafından metin seçimi (bir düğmeye tıklanması) yanı sıra (metin seçimi dizeye kopyalama) bu seçimle gerçekleştirilecek eylemi kolayca değiştirilebilir bir çeşitli senaryolar uyum sağlayacak şekilde alınır.</span><span class="sxs-lookup"><span data-stu-id="701a8-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="701a8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="701a8-109">Example</span></span>  
 <span data-ttu-id="701a8-110">Aşağıdaki C# örnekte gösterildiği bir <xref:System.Windows.Controls.Button.OnClick%2A> tanımlanan düğmesi için olay işleyicisi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu örneğin.</span><span class="sxs-lookup"><span data-stu-id="701a8-110">The following C# example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="701a8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="701a8-111">See also</span></span>

- [<span data-ttu-id="701a8-112">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="701a8-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="701a8-113">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="701a8-113">RichTextBox Overview</span></span>](richtextbox-overview.md)
