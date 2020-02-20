---
title: 'Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452798"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama
Bu örnek, bir <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>kullanarak nasıl bir öğe dönmesi yapılacağını gösterir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.RotateTransform> öğesinin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygular. Örnek, <xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.Angle%2A> hareketlendirmek için bir <xref:System.Windows.Media.Animation.DoubleAnimation> kullanır. Öğe dönmesini yerine getirmek için, örnek, öğesinin <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliğini nokta (0,5, 0,5) olarak ayarlar.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Daha fazla dönüştürme örneği içeren tam örnek için bkz. [2-b dönüşümler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
