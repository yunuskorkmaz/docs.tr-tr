---
title: "Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: e440cf49b8b16051361650f9659dc6006c2e7b56
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072165"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme
Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, animasyon uygulamak için üç animasyonlarını kullanıp <xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush>.  
  
-   İlk animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, fırça rengi değişir <xref:System.Windows.Media.Colors.Gray%2A> fare dikdörtgen girdiğinde.  
  
-   Sonraki animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, fırça rengi değişir <xref:System.Windows.Media.Colors.Orange%2A> fare dikdörtgen ayrıldığında.  
  
-   Son animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, farenin sol düğmesine basıldığında fırça opaklığını 0.0 değiştirir.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Farklı türde Fırçalar animasyonunu gösteren daha eksiksiz bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973). Animasyon hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md).  
  
 Diğer animasyon örnekleriyle tutarlılık sağlamak için bu örnek kod sürümleri kullanan bir <xref:System.Windows.Media.Animation.Storyboard> kendi animasyon uygulamak için nesne. Ancak, tek bir animasyonu kod uygularken kullanmak daha basit olduğu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmak yerine bir <xref:System.Windows.Media.Animation.Storyboard>. Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Fırça örneği](https://go.microsoft.com/fwlink/?LinkID=159973)
