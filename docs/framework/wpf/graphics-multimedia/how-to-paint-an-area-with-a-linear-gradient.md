---
title: 'Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: aee9931fc366131ae492891cc4d0fff70b4a4441
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780003"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.LinearGradientBrush> doğrusal gradyan ile bir alanı boyama için sınıf. Aşağıdaki örnekte, <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle> sarı kırmızı, mavi yeşile geçişleri çapraz bir doğrusal gradyan ile boyanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Aşağıdaki resimde önceki örnekte oluşturulan gradyanı gösterir.  
  
 ![Çapraz doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Yatay doğrusal gradyan oluşturmak isterseniz değiştirme <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , <xref:System.Windows.Media.LinearGradientBrush> ' ini (0,0.5) ve (1,0.5)'e. Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> yatay bir doğrusal gradyan ile boyanır.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Aşağıdaki resimde önceki örnekte oluşturulan gradyanı gösterir.  
  
 ![Yatay doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Dikey doğrusal gradyan oluşturmak isterseniz değiştirme <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , <xref:System.Windows.Media.LinearGradientBrush> ' ini (0.5,0) ve (0.5,1)'e. Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> dikey bir doğrusal gradyan ile boyanır.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Aşağıdaki resimde önceki örnekte oluşturulan gradyanı gösterir.  
  
 ![Dikey doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  Bu konudaki örnekler, başlangıç ve bitiş noktalarını ayarlamak için varsayılan koordinat sistemini kullanır. Varsayılan koordinat sistemi olan bir sınırlayıcı kutu göreli: 0 gösterir sınırlayıcı kutusunun yüzde 0 ve 1, sınırlayıcı kutunun yüzde 100 gösterir. Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özellik değerine <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>. Mutlak koordinat sistemi bir sınırlayıcı kutu göreli değil. Değerleri, doğrudan yerel alan yorumlanır.  
  
 Diğer örnekler için [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973). Gradyanlar ve diğer türleri Fırçalar hakkında daha fazla bilgi için bkz: [düz renkler ve gradyanlar genel bakış boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
