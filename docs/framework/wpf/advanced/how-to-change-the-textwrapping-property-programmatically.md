---
title: "Nasıl yapılır: TextWrapping Özelliğini Program Aracılığıyla Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 74ddcf55c8918602ecac866913f2007da143f443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Nasıl yapılır: TextWrapping Özelliğini Program Aracılığıyla Değiştirme
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde değerini değiştirmek gösterilmiştir <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> özelliği programlı olarak.  
  
 Üç <xref:System.Windows.Controls.Button> öğesi içinde yerleştirilir bir <xref:System.Windows.Controls.StackPanel> öğesinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Her <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir <xref:System.Windows.Controls.Button> kodundaki olay işleyici ile karşılık gelir. Olay işleyicileri aynı adı kullanmak <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> bunlar geçerli değer `txt2` düğmesine tıklandığında. Ayrıca, metinde `txt1` (bir <xref:System.Windows.Controls.TextBlock> içinde gösterilmez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) özellik değişikliği yansıtacak şekilde güncelleştirilir.  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
