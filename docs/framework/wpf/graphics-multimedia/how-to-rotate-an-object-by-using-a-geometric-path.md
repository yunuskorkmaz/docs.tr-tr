---
title: "Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 078d1054f9b6a4c2f6172f00aa8c4ad9077e6db2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme
Bu örnek, bir nesne tarafından tanımlanan geometrik yol boyunca nasıl döndürüleceğini (pivot) gösterir bir <xref:System.Windows.Media.PathGeometry> nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç kullanır <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> dikdörtgeni geometrik yol boyunca taşımak için nesneleri.  
  
-   İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır bir <xref:System.Windows.Media.RotateTransform> dikdörtgene uygulanır. Animasyon açı değerleri oluşturur. Bu dikdörtgeni yolun dağılımlarını (Özet) döndürün.  
  
-   Diğer iki nesnelere animasyon <xref:System.Windows.Media.TranslateTransform.X%2A> ve <xref:System.Windows.Media.TranslateTransform.Y%2A> değerlerini bir <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanır. Yatay ve dikey olarak yol boyunca taşır dikdörtgen yaptıkları.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Geometrik yol kullanarak bir nesne döndürmek için başka bir yolu bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesne ve ayarlayın, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliğine `true`. Daha fazla bilgi ve bir örnek için bkz: [geometrik yol (Matris Animasyonu) kullanarak bir nesne döndürme](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Yol animasyon nasıl yapılır konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
