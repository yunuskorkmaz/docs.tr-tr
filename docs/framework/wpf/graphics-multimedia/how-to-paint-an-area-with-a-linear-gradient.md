---
title: 'Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 76c491632911c48db34d932ba3895278591378a5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452772"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama
Bu örnek, doğrusal gradyan ile bir alanı boyamak için <xref:System.Windows.Media.LinearGradientBrush> sınıfını nasıl kullanacağınızı gösterir. Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> sarıdan kırmızıya ve sıfırdan yeşil arasında geçiş yapan köşegen doğrusal gradyan ile boyanmıştır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Aşağıdaki çizimde, önceki örnek tarafından oluşturulan gradyan gösterilmektedir.  
  
 ![Köşegen doğrusal gradyan](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Yatay doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, (0, 0,5) ve (1, 0,5) olarak değiştirin. Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> Yatay doğrusal gradyan ile boyanmıştır.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Aşağıdaki çizimde, önceki örnek tarafından oluşturulan gradyan gösterilmektedir.  
  
 ![Yatay doğrusal gradyan](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Dikey bir doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, (0,5, 0) ve (0,5, 1) olarak değiştirin. Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> Dikey doğrusal gradyan ile boyanmıştır.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Aşağıdaki çizimde, önceki örnek tarafından oluşturulan gradyan gösterilmektedir.  
  
 ![Dikey doğrusal gradyan](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
> Bu konudaki örneklerde, başlangıç noktalarını ve bitiş noktalarını ayarlamak için varsayılan koordinat sistemi kullanılır. Varsayılan koordinat sistemi bir sınırlayıcı kutuya göredir: 0 sınırlayıcı kutunun yüzde 0 ' ı gösterir ve 1 sınırlayıcı kutunun yüzde 100 ' unu gösterir. <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğini <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>değerine ayarlayarak bu koordinat sistemini değiştirebilirsiniz. Mutlak koordinat sistemi bir sınırlayıcı kutuya göreli değildir. Değerler doğrudan yerel alanda yorumlanır.  
  
 Daha fazla örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Degradeler ve diğer fırça türleri hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).
