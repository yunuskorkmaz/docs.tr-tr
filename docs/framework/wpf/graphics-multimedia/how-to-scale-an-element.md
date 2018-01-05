---
title: "Nasıl yapılır: Öğe Ölçeklendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2bff810dc9b44b25db93c8565da27acc4f0ccc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scale-an-element"></a>Nasıl yapılır: Öğe Ölçeklendirme
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.ScaleTransform> bir öğeyi ölçeklendirmek için.  
  
 Kullanım <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> Belirttiğiniz faktörle öğeyi yeniden boyutlandırmak için özellikler. Örneğin, bir <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1.5 değeri öğenin özgün genişliğinin yüzde 150'si uzatır. A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 değeri öğenin yüksekliğini yüzde 50 küçültür.  
  
 Kullanım <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> ölçeklendirme işlemi merkezi noktası belirtmek için özellikleri. Varsayılan olarak, bir <xref:System.Windows.Media.ScaleTransform> dikdörtgen sol üst köşesindeki karşılık gelir (0,0) noktasında ortalanır. Bu öğe taşıma ve ayrıca uyguladığınızda olduğundan daha büyük görünmesini yapma etkisi bir <xref:System.Windows.Media.Transform>, nesnenin bulunduğu koordinat değiştirin.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.ScaleTransform> 50-tarafından-50 boyutunu çift <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Media.ScaleTransform> Her ikisi için 0 (varsayılan) değerine sahip <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Genellikle, ayarladığınız <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> ölçeklendirilir nesne merkezine: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 Aşağıdaki örnek başka gösterir <xref:System.Windows.Shapes.Rectangle> boyutunda; çift ancak, bu <xref:System.Windows.Media.ScaleTransform> her ikisi için 25 değerine sahip <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, dikdörtgenin merkezine karşılık gelir.  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 İkisi arasındaki farkı aşağıda gösterilmiştir <xref:System.Windows.Media.ScaleTransform> işlemleri. Noktalı çizgi ölçeklendirmeden önce boyutunu ve konumunu dikdörtgenin gösterir.  
  
 ![farklı merkez nokta 2 x ölçekler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Aynı ScaleX ve ScaleY değerleri ancak farklı merkezleri ile iki ScaleTransform işlemleri  
  
 Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
