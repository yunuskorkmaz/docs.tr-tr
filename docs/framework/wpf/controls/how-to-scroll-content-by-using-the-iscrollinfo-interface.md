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
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098552"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Nasıl yapılır: IScrollInfo Arabirimini Kullanarak İçerik Kaydırma
Bu örnekte kullanarak içerik kaydırma gösterilmektedir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek özelliklerini gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi. Örnek bir <xref:System.Windows.Controls.StackPanel> öğesinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir üst içe <xref:System.Windows.Controls.ScrollViewer>. Alt öğeleri <xref:System.Windows.Controls.StackPanel> tarafından tanımlanan yöntemler kullanılarak mantıksal olarak kaydırılabileceğini <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi ve atama örneğine <xref:System.Windows.Controls.StackPanel> (`sp1`) kod.  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Her <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya içinde kaydırma davranışını denetleyen bir ilişkili özel yöntemi tetikler <xref:System.Windows.Controls.StackPanel>. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> yöntemleri; ayrıca genel konumlandırma tüm yöntemlerin nasıl kullanılacağını gösterir, <xref:System.Windows.Controls.Primitives.IScrollInfo> sınıfı tanımlar.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [ScrollViewer Genel Bakışı](scrollviewer-overview.md)
- [Nasıl Yapılır Konuları](scrollviewer-how-to-topics.md)
- [Panellere Genel Bakış](panels-overview.md)
