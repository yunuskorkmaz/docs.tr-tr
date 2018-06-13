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
ms.openlocfilehash: 2457bdb794d81e7c482f735cad4ade34564328e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559330"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme
Bu örnek animasyon gösterilmektedir <xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, animasyon uygulamak için üç animasyon kullanır <xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush>.  
  
-   İlk animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, fırça renge dönüşür <xref:System.Windows.Media.Colors.Gray%2A> fare dikdörtgen girdiğinde.  
  
-   Sonraki animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, fırça renge dönüşür <xref:System.Windows.Media.Colors.Orange%2A> zaman fare dikdörtgenden.  
  
-   Son animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, sol fare düğmesine basıldığında fırça opaklık 0,0 olarak değiştirir.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Fırçalar farklı türlerde animasyon gösterilmektedir, daha tam bir örnek için bkz [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973). Animasyon hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Diğer animasyon örnekleriyle tutarlılık için bu örnek kodu sürümlerini kullanan bir <xref:System.Windows.Media.Animation.Storyboard> kendi animasyonları uygulamak için nesne. Ancak, kodda tek bir animasyonu uygularken, bunu kullanmak daha basittir <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kullanmak yerine yöntemi bir <xref:System.Windows.Media.Animation.Storyboard>. Bir örnek için bkz: [özelliği olmadan kullanarak bir film şeridi animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973)
