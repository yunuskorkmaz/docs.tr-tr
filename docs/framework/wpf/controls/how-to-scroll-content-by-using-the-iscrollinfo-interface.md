---
title: 'Nasıl yapılır: IScrollInfo Arabirimini Kullanarak İçerik Kaydırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 49b3483750582aa51d1de418f745d931604d2786
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637865"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Nasıl yapılır: IScrollInfo Arabirimini Kullanarak İçerik Kaydırma
Bu örnekte kullanarak içerik kaydırma gösterilmektedir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek özelliklerini gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi. Örnek bir <xref:System.Windows.Controls.StackPanel> öğesinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir üst içe <xref:System.Windows.Controls.ScrollViewer>. Alt öğeleri <xref:System.Windows.Controls.StackPanel> tarafından tanımlanan yöntemler kullanılarak mantıksal olarak kaydırılabileceğini <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi ve atama örneğine <xref:System.Windows.Controls.StackPanel> (`sp1`) kod.  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Her <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya içinde kaydırma davranışını denetleyen bir ilişkili özel yöntemi tetikler <xref:System.Windows.Controls.StackPanel>. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> yöntemleri; ayrıca genel konumlandırma tüm yöntemlerin nasıl kullanılacağını gösterir, <xref:System.Windows.Controls.Primitives.IScrollInfo> sınıfı tanımlar.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [ScrollViewer Genel Bakış](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)
- [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
