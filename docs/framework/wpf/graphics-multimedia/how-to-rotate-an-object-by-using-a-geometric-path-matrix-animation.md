---
title: 'Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme (Matris Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187408"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme (Matris Animasyonu)
Bu örnek, bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> <xref:System.Windows.Media.PathGeometry> nesne <xref:System.Windows.Media.MatrixTransform> tarafından tanımlanan geometrik bir yol boyunca bir nesneyi döndürmek (döndürmek) için a ve a'nın nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> bir <xref:System.Windows.Media.MatrixTransform>. özelliğini <xref:System.Windows.Media.MatrixTransform.Matrix%2A> canlandırmak için nesneyi kullanır. Bir <xref:System.Windows.Media.MatrixTransform> düğmeye uygulanır ve eğri bir yol boyunca hareket etmesini neden olur. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> Özellik ayarlandığı için, `true`dikdörtgen yolun teğet boyunca döner.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Tam örnek için [Yol Animasyon Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)bakın.  
  
 Yalnızca bir animasyon uygulanmış olsa <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.EllipseGeometry>bile, önceki örneğin kod sürümü , animasyon için a kullanılır. Koddaki bir özelliğe tek bir animasyon uygulamanın <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> daha kolay bir yolu yöntemi kullanmaktır. Örneğin, Bir [Storyboard kullanmadan bir Özellik Animasyon](how-to-animate-a-property-without-using-a-storyboard.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
- [Yol Animasyon Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
