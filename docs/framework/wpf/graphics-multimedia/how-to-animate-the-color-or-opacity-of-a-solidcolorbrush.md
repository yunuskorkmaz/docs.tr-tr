---
title: "Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 03052cdf68a5a8564d5a24c91521749c10afa6cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973)
