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
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452889"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme
Bu örnek, bir <xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> nasıl hareketlendirileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> hareketlendirmek için üç animasyon kullanır.  
  
- İlk animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, fare dikdörtgene girdiğinde fırçanın rengini <xref:System.Windows.Media.Colors.Gray%2A> olarak değiştirir.  
  
- Sonraki animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, fare dikdörtgenden çıktığında fırçanın rengini <xref:System.Windows.Media.Colors.Orange%2A> olarak değiştirir.  
  
- Son animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, sol fare düğmesine basıldığında fırçanın saydamlığını 0,0 olarak değiştirir.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Farklı fırça türlerine nasıl animasyon ekleneceğini gösteren daha kapsamlı bir örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Animasyon hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md).  
  
 Diğer animasyon örnekleriyle tutarlılık için, bu örneğin kod sürümleri animasyonlarını uygulamak için bir <xref:System.Windows.Media.Animation.Storyboard> nesnesi kullanır. Ancak, kodda tek bir animasyon uygulanırken, <xref:System.Windows.Media.Animation.Storyboard>kullanmak yerine <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yönteminin kullanılması daha basittir. Bir örnek için bkz. [görsel taslak kullanmadan özelliğe animasyon ekleme](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
