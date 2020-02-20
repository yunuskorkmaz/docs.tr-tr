---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452902"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)
Bu örnek, bir <xref:System.Windows.Point> eğri yol üzerinde hareketlendirmek için bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nesnesinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.PathGeometry>tarafından tanımlanan bir yol üzerinde taşıdır. Elips geometrisinin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği, bir <xref:System.Windows.Point> değeri alır, konumunu belirtir; elips geometrisini taşımak için <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliğine animasyon uygularsınız. Örnek, <xref:System.Windows.Media.EllipseGeometry> nesnesinin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliğine animasyon uygulamak için bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> kullanır.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Önceki örneğin kod sürümü, yalnızca bir animasyon uygulanmış olsa da <xref:System.Windows.Media.EllipseGeometry>hareketlendirmek için bir <xref:System.Windows.Media.Animation.Storyboard> kullandı. <xref:System.Windows.Media.Animation.Storyboard>, bu animasyonlar aynı <xref:System.Windows.Media.Animation.Storyboard>tarafından denetlenebildiğinden, genellikle birden çok animasyon uygulamanın en kolay yoludur. Ancak, kod kullanırken bir özelliğe tek bir animasyon uygulamak için daha kolay bir yol <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmaktır. Bir örnek için bkz. [görsel taslak kullanmadan özelliğe animasyon ekleme](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Animasyona Genel bakış](animation-overview.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
