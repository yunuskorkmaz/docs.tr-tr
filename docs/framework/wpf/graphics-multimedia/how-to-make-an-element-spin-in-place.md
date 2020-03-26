---
title: 'Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112082"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama
Bu örnek, bir öğenin a <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>a kullanarak nasıl döndürülür hale getirilebildiğini gösterir.  
  
 Aşağıdaki örnek öğenin <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> özelliği ne uygulanır. Örnek, a'yı <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.RotateTransform.Angle%2A> animasyona vermek <xref:System.Windows.Media.RotateTransform>için kullanır. Öğeyi yerinde döndürmek için, örnek <xref:System.Windows.UIElement.RenderTransformOrigin%2A> öğenin özelliğini noktaya ayarlar (0,5, 0,5).  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Daha fazla dönüşüm örneği içeren tam örnek için [bkz.](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
