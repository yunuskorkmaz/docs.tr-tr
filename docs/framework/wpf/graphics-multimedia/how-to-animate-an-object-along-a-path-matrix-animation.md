---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452915"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)
Bu örnek, bir <xref:System.Windows.Media.PathGeometry>tarafından tanımlanan yol üzerinde bir nesneye animasyon uygulamak için <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sınıfını nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aşağıdakileri yaparak bir nesneyi yol üzerinde hareketlendirir:  
  
- Taşımak için nesnesine bir <xref:System.Windows.Media.MatrixTransform> uygular.  
  
- <xref:System.Windows.Media.PathGeometry>kullanarak yolu tanımlar.  
  
- Bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> oluşturur ve <xref:System.Windows.Media.MatrixTransform><xref:System.Windows.Media.Matrix> özelliğine animasyon uygulamak için onu kullanır. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> <xref:System.Windows.Media.PathGeometry> alır ve <xref:System.Windows.Media.Matrix> değerler oluşturmak için onu kullanır.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Geometrik yollar hakkında daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
