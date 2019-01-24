---
title: "Nasıl yapılır: ScrollViewer'ın İçerik Kaydırma Yöntemlerini Kullanma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: 0f2ed1c0ac0d29a47ab98e0329ff161fd54daba6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547046"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>Nasıl yapılır: ScrollViewer'ın İçerik Kaydırma Yöntemlerini Kullanma
Bu örnek, kaydırma yöntemlerini kullanma işlemini gösterir. <xref:System.Windows.Controls.ScrollViewer> öğesi. Artımlı içeriğini, çizgi veya sayfası, kaydırma bu yöntemler sağlayan bir <xref:System.Windows.Controls.ScrollViewer>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.ScrollViewer> adlı `sv1`, bir alt barındıran <xref:System.Windows.Controls.TextBlock> öğesi. Çünkü <xref:System.Windows.Controls.TextBlock> üst büyük <xref:System.Windows.Controls.ScrollViewer>, kaydırma etkinleştirmek için kaydırma çubukları görünür. <xref:System.Windows.Controls.Button> çeşitli kaydırma yöntemleri temsil eden öğeler, ayrı bir soldaki tutturulmuştur <xref:System.Windows.Controls.StackPanel>. Her <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya içinde kaydırma davranışını denetleyen ilgili özel bir yöntem çağırır <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> ve <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> yöntemleri.  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
