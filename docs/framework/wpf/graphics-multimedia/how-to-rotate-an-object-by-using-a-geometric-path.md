---
title: 'Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186869"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme
Bu örnek, bir <xref:System.Windows.Media.PathGeometry> nesne tarafından tanımlanan geometrik bir yol boyunca bir nesneyi nasıl döndürecek (döndürmeyi) gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> geometrik bir yol boyunca bir dikdörtgeni taşımak için üç nesne kullanır.  
  
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> İlk animasyon dikdörtgen <xref:System.Windows.Media.RotateTransform> uygulanır. Animasyon açı değerleri oluşturur. Dikdörtgenin yolun hatları boyunca dönmesini (pivot) sağlar.  
  
- Diğer iki nesne, dikdörtgeniçin <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform.Y%2A> uygulanan bir <xref:System.Windows.Media.TranslateTransform> nesnenin değerlerini ve değerlerini animasyona salar. Dikdörtgenin yol boyunca yatay ve dikey olarak hareket ettirin.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Geometrik bir yol kullanarak bir nesneyi döndürmenin <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> başka bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> yolu `true`da nesneyi kullanmak ve özelliğini .'e ayarlamaktır. Daha fazla bilgi ve örnek için [bkz.](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)  
  
 Tam örnek için [Yol Animasyon Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol Animasyon Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
