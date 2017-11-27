---
title: "Nasıl yapılır: Görüntü ile bir Alanı Boyama"
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
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3edbe30347580bb4f9677d7fb98d3b4fd8b92cff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-an-image"></a>Nasıl yapılır: Görüntü ile bir Alanı Boyama
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.ImageBrush> alanı bir görüntü ile boyamak için sınıf. Bir <xref:System.Windows.Media.ImageBrush> tarafından belirtilen tek bir resmi görüntüler kendi <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek paints <xref:System.Windows.Controls.Control.Background%2A> kullanarak düğmesinin bir <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.ImageBrush> boyama alanını tamamen doldurmak için kendi resmini uzatır. Önceki örnekte, görüntü, büyük olasılıkla resim bozulur düğmesi, dolduracak şekilde genişletilir. Bu davranış ayarlayarak denetleyebilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği <xref:System.Windows.Media.TileBrush> için <xref:System.Windows.Media.Stretch.Uniform> veya <xref:System.Windows.Media.Stretch.UniformToFill>, resmin oranını korumak fırça neden olur.  
  
 Ayarlarsanız <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliklerini bir <xref:System.Windows.Media.ImageBrush>, yinelenen bir desen oluşturabilirsiniz. Aşağıdaki örnek, bir görüntüden oluşturulan bir desen kullanılarak bir düğme boyar.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> sınıfı için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.ImageBrush> sınıfı. Tam bir örnek için bkz: [ImageBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
