---
title: 'Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma'
description: Windows Presentation Foundation TextBox denetiminin metin içeriğinin başlangıcında veya sonunda imlecin nasıl konumlandıralınacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167515"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="3adc1-103">Nasıl yapılır: TextBox Denetiminde İmleci Metnin Başlangıcında veya Sonunda Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="3adc1-103">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="3adc1-104">Bu örnek, bir denetimin metin içeriğinin başlangıcında veya sonunda imlecin nasıl konumlandıralınacağını gösterir <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="3adc1-104">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3adc1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3adc1-105">Example</span></span>  
 <span data-ttu-id="3adc1-106">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod bir denetimi açıklar <xref:System.Windows.Controls.TextBox> ve bir adı atar.</span><span class="sxs-lookup"><span data-stu-id="3adc1-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="3adc1-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="3adc1-107">Example</span></span>  
 <span data-ttu-id="3adc1-108">İmleci bir denetimin içeriğinin başlangıcına yerleştirmek için <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.TextBox.Select%2A> yöntemini çağırın ve 0 ' ın seçim başlangıç konumunu ve 0 seçim uzunluğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="3adc1-108">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="3adc1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="3adc1-109">Example</span></span>  
 <span data-ttu-id="3adc1-110">İmleci bir denetimin içeriğinin sonuna yerleştirmek için <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.TextBox.Select%2A> yöntemini çağırın ve seçim başlangıç konumunu metin içeriğinin uzunluğuna eşit ve seçim uzunluğu 0 olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="3adc1-110">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="3adc1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3adc1-111">See also</span></span>

- [<span data-ttu-id="3adc1-112">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="3adc1-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="3adc1-113">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="3adc1-113">RichTextBox Overview</span></span>](richtextbox-overview.md)
