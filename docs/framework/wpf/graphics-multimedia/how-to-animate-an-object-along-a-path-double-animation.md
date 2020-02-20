---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452863"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)
Bu örnek, bir nesneyi bir <xref:System.Windows.Media.PathGeometry>tarafından tanımlanan yol üzerinde taşımak için <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> sınıfını nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dikdörtgeni geometrik yol üzerinde taşımak için iki <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> nesnesi kullanır:  
  
- İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>, dikdörtgene uygulanan <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.X%2A> hareketlendirir. Dikdörtgeni yol üzerinde yatay olarak hareket ettirin.  
  
- İkinci <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>, dikdörtgene uygulanan <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.Y%2A> hareketlendirir. Dikdörtgeni yol üzerinde dikey olarak hareket ettirin.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Bir geometrik yol kullanarak nesneyi taşımanın bir başka yolu da <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesnesi kullanmaktır. Bir örnek için bkz. bir [nesnenin yol üzerinde animasyonunu oluşturma (matris animasyonu)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
