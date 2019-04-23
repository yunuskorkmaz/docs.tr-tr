---
title: 'Nasıl yapılır: PointAnimation Kullanarak bir Nesnenin Konumuna Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 1ef3f77e551affaa7e61d2aabf95f10c29275417
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111312"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Nasıl yapılır: PointAnimation Kullanarak bir Nesnenin Konumuna Animasyon Ekleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.PointAnimation> bir nesnenin animasyon uygulamak için sınıfı bir <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir elips taşır bir <xref:System.Windows.Shapes.Path> başka bir ekrandaki bir noktadan. Örnek konumunu canlandırır bir <xref:System.Windows.Media.EllipseGeometry> kullanarak <xref:System.Windows.Media.Animation.PointAnimation> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [Animasyona Genel bakış](animation-overview.md)
- [Grafikler ve Multimedya](index.md)
- [Grafikler ile ilgili nasıl yapılır konuları](graphics-how-to-topics.md)
- [Animasyon ve zamanlama ile ilgili nasıl yapılır konuları](animation-and-timing-how-to-topics.md)
