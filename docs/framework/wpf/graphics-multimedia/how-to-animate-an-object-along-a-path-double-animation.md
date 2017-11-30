---
title: "Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)"
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
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a461b741675a18ac1e3544b17a9bbe9a8d18547
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> sınıfı tarafından tanımlanan bir yol boyunca bir nesneyi taşımak için bir <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki kullanan <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> dikdörtgeni geometrik yol boyunca taşımak için nesneler:  
  
-   İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır <xref:System.Windows.Media.TranslateTransform.X%2A> , <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanan. Bu dikdörtgeni yol boyunca yatay olarak taşır.  
  
-   İkinci <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır <xref:System.Windows.Media.TranslateTransform.Y%2A> , <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanan. Bu dikdörtgeni yol boyunca dikey olarak taşır.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Geometrik yol kullanarak bir nesne taşımak için başka bir yolu bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesnesi. Bir örnek için bkz: [bir nesne boyunca bir yolu (Matris Animasyonu) animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Yol animasyon nasıl yapılır konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
