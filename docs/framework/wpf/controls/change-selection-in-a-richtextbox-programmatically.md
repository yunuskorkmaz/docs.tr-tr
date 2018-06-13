---
title: RichTextBox İçinde Program Aracılığıyla Seçimi Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
ms.openlocfilehash: e8ad33956f1a9fdddc728457e6c302635115b709
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551009"
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a><span data-ttu-id="d4018-102">RichTextBox İçinde Program Aracılığıyla Seçimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d4018-102">Change Selection in a RichTextBox Programmatically</span></span>
<span data-ttu-id="d4018-103">Bu örnek, geçerli seçim programlı olarak değiştirmek gösterilmiştir bir <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="d4018-103">This example shows how to programmatically change the current selection in a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="d4018-104">Kullanıcı içeriği kullanıcı arabirimini kullanarak gibi seçtiyseniz bu seçim aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d4018-104">This selection is the same as if the user had selected the content by using the user interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4018-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4018-105">Example</span></span>  
 <span data-ttu-id="d4018-106">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu tanımlayan bir adlandırılmış <xref:System.Windows.Controls.RichTextBox> denetim basit içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="d4018-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="d4018-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4018-107">Example</span></span>  
 <span data-ttu-id="d4018-108">Aşağıdaki kod kullanıcı içine tıkladığında programlı olarak bazı metinleri rasgele seçer. <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="d4018-108">The following code programmatically selects some arbitrary text when the user clicks inside the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d4018-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4018-109">See Also</span></span>  
 [<span data-ttu-id="d4018-110">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4018-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="d4018-111">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4018-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
