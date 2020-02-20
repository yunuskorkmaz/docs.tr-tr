---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453110"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)
Bu örnek, bir nesnenin yol üzerinde animasyonunu yapmak için <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sınıfının nasıl kullanılacağını gösterir ve animasyonun, yineleme değerlerini tekrarlandığı şekilde birikmesini sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir düğmeye uygulanan bir <xref:System.Windows.Media.MatrixTransform> <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliğine animasyon eklemek için <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesnesini kullanır. Sonuç olarak, bir düğme eğri yol üzerinde taşınıyor.  
  
 Buna ek olarak, örnek <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliğini `true`olarak ayarlar, bu da animasyon yinelendikçe animasyonlu matrisin sapmasını birikmesine neden olur. Fark biriktiğinden, düğme, animasyon yinelendiğinde, başlangıç konumuna sıfırlamak yerine, ekran üzerinde daha fazla gider.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliği, fark değerlerinin tekrarları üzerinden birikmesine neden olmasına rağmen, döndürme değerlerinin birikmesine neden olmaz. Döndürme değerlerinin birikmesini sağlamak için, animasyonun <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> ve <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> özelliklerini `true`olarak ayarlayın.  
  
 Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Bir <xref:System.Windows.Media.Matrix> değerinin, fark birikmesi olmadan yol boyunca nasıl hareketlendirileceğini gösteren bir örnek için, bkz. bir [nesneye animasyon ekleme (matris animasyonu)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
