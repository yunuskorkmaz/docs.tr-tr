---
title: 'Nasıl yapılır: TextWrapping Özelliğini Program Aracılığıyla Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 21ca31d24121492fe6927cd533d5b3c0785b5a28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776668"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="6d536-102">Nasıl yapılır: TextWrapping Özelliğini Program Aracılığıyla Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6d536-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="6d536-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d536-103">Example</span></span>  
 <span data-ttu-id="6d536-104">Aşağıdaki kod örneği, değerini değiştirmek gösterilmektedir <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> özelliğini program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="6d536-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="6d536-105">Üç <xref:System.Windows.Controls.Button> öğesi içinde yerleştirilir bir <xref:System.Windows.Controls.StackPanel> öğesinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d536-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="6d536-106">Her <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay için bir <xref:System.Windows.Controls.Button> olay işleyicisinde kodu karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6d536-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="6d536-107">Olay işleyicileri olarak aynı adı kullanın <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> bunlar geçerli değer `txt2` düğmeye tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="6d536-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="6d536-108">Ayrıca, metnin `txt1` (bir <xref:System.Windows.Controls.TextBlock> içinde gösterilmez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) özellik değişikliği yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6d536-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6d536-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d536-109">See also</span></span>

- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
