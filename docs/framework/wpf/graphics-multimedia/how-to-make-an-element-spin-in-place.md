---
title: 'Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: aca9bd577f2882e31e8d49abe5eeb5ade86f95f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110670"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama
Bu örnek nasıl döndürme kullanarak bir öğeyi gösterir bir <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Aşağıdaki örnek geçerli <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesinin özelliği. Örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için <xref:System.Windows.Media.RotateTransform.Angle%2A> , <xref:System.Windows.Media.RotateTransform>. Yerinde öğe yapmak için örnekte <xref:System.Windows.UIElement.RenderTransformOrigin%2A> noktasına (0,5, 0,5) öğesinin özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Daha fazla dönüşüm örnekleri içeren, tam örnek için bkz [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
