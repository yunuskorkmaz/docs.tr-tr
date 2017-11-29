---
title: "Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)"
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
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70426e3341f78a22c8367daefc07d071c7add3ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sınıfı tarafından tanımlanan bir yol boyunca bir nesneyi animasyon bir <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, aşağıdakileri yaparak bir yol boyunca bir nesneyi canlandırır:  
  
-   Geçerli bir <xref:System.Windows.Media.MatrixTransform> taşımak için nesne.  
  
-   Yol kullanarak tanımlayan bir <xref:System.Windows.Media.PathGeometry>.  
  
-   Oluşturur bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> ve animasyon için kullandığı <xref:System.Windows.Media.Matrix> özelliği <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Geçen <xref:System.Windows.Media.PathGeometry> ve oluşturmak için kullandığı <xref:System.Windows.Media.Matrix> değerleri.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028). Geometrik yolları hakkında daha fazla bilgi için bkz: [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Yol animasyon nasıl yapılır konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
