---
title: "Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5259e930060a8ac6118d232f08d02193a6a1b300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sapması birikmesini animasyonun bir yol boyunca bir nesneyi hale getirmeyi ve sınıf değerleri yinelenecek şekilde.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> hale getirmeyi nesnesine <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> bir düğmeye uygulanan. Sonuç olarak, bir düğme eğri bir yol boyunca taşır.  
  
 Ayrıca, örnek ayarlar <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliğine `true`, animasyon yinelendikçe animasyonlu matris uzaklığını neden olur. Uzaklık öğelerden çünkü düğme uzağa başlangıç konumunu sıfırlamak yerine animasyonu yineler ekrana arasında taşır.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Ancak Not <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliği sapma değerlerinin tekrarları birikmesine neden olur, döndürme değerlerinin birikmesine neden olmaz. Animasyonun birikmesini döndürme değerlerini ayarlayın <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> ve <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> özelliklerine `true`.  
  
 Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028). Nasıl yapıldığını gösteren bir örnek bir <xref:System.Windows.Media.Matrix> değer uzaklık Birikme olmadan bir yol için bkz: [bir nesne boyunca bir yolu (Matris Animasyonu) animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
