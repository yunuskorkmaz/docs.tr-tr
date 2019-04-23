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
ms.openlocfilehash: 3d7da5daf09e06938b8366e0f5f98a599cae4571
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186231"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="58aa9-102">Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="58aa9-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="58aa9-103">Bu örnek başına veya sonuna metin içeriğini imleci konumlandırma nasıl gösterir bir <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="58aa9-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58aa9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="58aa9-104">Example</span></span>  
 <span data-ttu-id="58aa9-105">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu tanımlayan bir <xref:System.Windows.Controls.TextBox> denetlemek ve bir ad atar.</span><span class="sxs-lookup"><span data-stu-id="58aa9-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="58aa9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="58aa9-106">Example</span></span>  
 <span data-ttu-id="58aa9-107">İçeriğini başında İmleç konumuna bir <xref:System.Windows.Controls.TextBox> denetiminde, arama <xref:System.Windows.Controls.TextBox.Select%2A> yöntemi ve seçimi başlangıç konumu 0 ve 0 seçim uzunluğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="58aa9-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="58aa9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="58aa9-108">Example</span></span>  
 <span data-ttu-id="58aa9-109">Sonunda içeriğini, İmleç konumuna bir <xref:System.Windows.Controls.TextBox> denetiminde, arama <xref:System.Windows.Controls.TextBox.Select%2A> yöntemi ve içerik metnin uzunluğunu ve seçim uzunluğu 0 eşit seçimi başlangıç konumu belirtin.</span><span class="sxs-lookup"><span data-stu-id="58aa9-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="58aa9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58aa9-110">See also</span></span>

- [<span data-ttu-id="58aa9-111">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="58aa9-111">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="58aa9-112">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="58aa9-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
