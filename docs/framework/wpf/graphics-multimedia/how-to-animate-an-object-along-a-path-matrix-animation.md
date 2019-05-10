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
ms.openlocfilehash: 3c90d20cac60004aa9876d9fe8d213d33c5a6883
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651429"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sınıfının bir nesnenin tarafından tanımlanan bir yol üzerinde animasyonunu bir <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aşağıdakileri yaparak bir nesnenin yol canlandırın:  
  
- Geçerli bir <xref:System.Windows.Media.MatrixTransform> taşımak için nesne.  
  
- Yolu kullanarak tanımlayan bir <xref:System.Windows.Media.PathGeometry>.  
  
- Oluşturur bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> ve animasyon uygulamak için kullandığı <xref:System.Windows.Media.Matrix> özelliği <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Alır <xref:System.Windows.Media.PathGeometry> ve oluşturmak için kullandığı <xref:System.Windows.Media.Matrix> değerleri.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028). Geometrik yollar hakkında daha fazla bilgi için bkz. [geometrisi](geometry-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
