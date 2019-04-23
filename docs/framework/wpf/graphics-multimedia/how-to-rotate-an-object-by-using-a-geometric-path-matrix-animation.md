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
ms.openlocfilehash: 8f1b0ac42ea7509f8bc22b0bd2f50e2f96b5bee5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087892"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme (Matris Animasyonu)
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> ve <xref:System.Windows.Media.MatrixTransform> (Özet) tarafından tanımlanan bir geometrik yol boyunca bir nesneyi döndürmek için bir <xref:System.Windows.Media.PathGeometry> nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> animasyon uygulamak için nesne <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Düğmeye uygulanır ve eğik bir yolu boyunca taşımak neden olur. Çünkü <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliği `true`, dikdörtgen yol tanjantını döndürür.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Önceki örnekte kullanılan kod sürümünü bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry>, yalnızca bir animasyon uygulanmış olmasına rağmen. Kod bir özelliği tek bir animasyon uygulamak için daha kolay bir yolu kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi. Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
- [Yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028)
