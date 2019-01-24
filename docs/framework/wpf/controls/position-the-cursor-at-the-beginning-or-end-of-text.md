---
title: 'Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: 2b280c6ea74a4b7a896f33a3552997a730d24a39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497624"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="d0c0c-102">Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="d0c0c-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="d0c0c-103">Bu örnek başına veya sonuna metin içeriğini imleci konumlandırma nasıl gösterir bir <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d0c0c-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0c0c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0c0c-104">Example</span></span>  
 <span data-ttu-id="d0c0c-105">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu tanımlayan bir <xref:System.Windows.Controls.TextBox> denetlemek ve bir ad atar.</span><span class="sxs-lookup"><span data-stu-id="d0c0c-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="d0c0c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0c0c-106">Example</span></span>  
 <span data-ttu-id="d0c0c-107">İçeriğini başında İmleç konumuna bir <xref:System.Windows.Controls.TextBox> denetiminde, arama <xref:System.Windows.Controls.TextBox.Select%2A> yöntemi ve seçimi başlangıç konumu 0 ve 0 seçim uzunluğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="d0c0c-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="d0c0c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0c0c-108">Example</span></span>  
 <span data-ttu-id="d0c0c-109">Sonunda içeriğini, İmleç konumuna bir <xref:System.Windows.Controls.TextBox> denetiminde, arama <xref:System.Windows.Controls.TextBox.Select%2A> yöntemi ve içerik metnin uzunluğunu ve seçim uzunluğu 0 eşit seçimi başlangıç konumu belirtin.</span><span class="sxs-lookup"><span data-stu-id="d0c0c-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="d0c0c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0c0c-110">See also</span></span>
- [<span data-ttu-id="d0c0c-111">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0c0c-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="d0c0c-112">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0c0c-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
