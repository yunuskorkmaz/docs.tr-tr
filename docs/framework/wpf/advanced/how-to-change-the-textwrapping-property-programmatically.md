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
ms.openlocfilehash: 6cf0993d0433e03a3c19bb59bf3621672e164b43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640231"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Nasıl yapılır: TextWrapping Özelliğini Program Aracılığıyla Değiştirme
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, değerini değiştirmek gösterilmektedir <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> özelliğini program aracılığıyla.  
  
 Üç <xref:System.Windows.Controls.Button> öğesi içinde yerleştirilir bir <xref:System.Windows.Controls.StackPanel> öğesinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Her <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay için bir <xref:System.Windows.Controls.Button> olay işleyicisinde kodu karşılık gelir. Olay işleyicileri olarak aynı adı kullanın <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> bunlar geçerli değer `txt2` düğmeye tıklandığında. Ayrıca, metnin `txt1` (bir <xref:System.Windows.Controls.TextBlock> içinde gösterilmez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) özellik değişikliği yansıtacak şekilde güncelleştirilir.  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
