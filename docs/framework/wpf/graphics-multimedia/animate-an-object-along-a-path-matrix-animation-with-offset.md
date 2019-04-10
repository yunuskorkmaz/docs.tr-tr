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
ms.openlocfilehash: 3e7b892e2a2215d26512850477844d71bce7fe09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207376"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> uzaklığı accumulate animasyonun bir nesnenin yol üzerinde animasyonunu oluşturma ve sınıf yinelenecek şekilde değerleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> animasyon uygulamak için nesne <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> düğmeye uygulanır. Sonuç olarak, bir düğme eğri yola taşır.  
  
 Ayrıca, örnek ayarlar <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliğini `true`, animasyonlu matris animasyonu yineler gibi accumulate uzaklığı neden olur. Uzaklık biriktirir olduğundan, düğme daha da esnetmenize için başlangıç konumu sıfırlama yerine, ekranın animasyonu yinelendiğinde arasında taşır.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Ancak Not <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliği repetitions ulaşıncaya kadar uzaklık değerleri neden olur, dönüş değerleri birikmesine neden olmaz. Accumulate dönüş değerleri için animasyonun ayarlayın <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> ve <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> özelliklerine `true`.  
  
 Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028). Nasıl yapıldığını gösteren bir örnek için bir <xref:System.Windows.Media.Matrix> sapma birikmesi olmadan yol değeri için bkz: [bir nesne boyunca bir yolu (Matris Animasyonu) animasyon](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
