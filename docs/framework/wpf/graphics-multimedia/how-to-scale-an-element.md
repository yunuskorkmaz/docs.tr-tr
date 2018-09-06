---
title: 'Nasıl yapılır: Öğe Ölçeklendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 44c638b58d828e5beb0b9de5c7bb0b67c8e82d87
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884953"
---
# <a name="how-to-scale-an-element"></a>Nasıl yapılır: Öğe Ölçeklendirme
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.ScaleTransform> öğe ölçeklendirme için.  
  
 Kullanım <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> Belirttiğiniz faktörle öğeyi yeniden boyutlandırmak için özellikler. Örneğin, bir <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> özgün genişliğinin yüzde 150 öğesine 1.5 değerini uzatır. A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 değeri öğenin yüksekliğini yüzde 50 küçültür.  
  
 Kullanım <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> ölçeklendirme işleminin merkez noktası belirtmek için özellikleri. Varsayılan olarak, bir <xref:System.Windows.Media.ScaleTransform> dikdörtgenin sol üst köşesinin karşılık gelir (0,0) noktasında ortalanır. Bu öğeyi taşımak ve ayrıca uyguladığınızda olduğundan daha büyük görünmesini sağlama etkisi bir <xref:System.Windows.Media.Transform>, nesnenin bulunduğu koordinat değiştirin.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.ScaleTransform> boyutu 50-tarafından-50 çift <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Media.ScaleTransform> Her ikisi için 0 (varsayılan) değerini içeren <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Genellikle, ayarladığınız <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> ölçeklendirilir nesnenin Merkezi: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 Aşağıdaki örnek başka gösterir <xref:System.Windows.Shapes.Rectangle> ; boyutundaki işledi ancak bu <xref:System.Windows.Media.ScaleTransform> her ikisi için 25 değerini içeren <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, dikdörtgen merkezine karşılık gelir.  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 İkisi arasındaki fark aşağıdaki çizimde <xref:System.Windows.Media.ScaleTransform> operations. Noktalı çizgi ölçeklendirmeden önce boyutunu ve konumunu dikdörtgenin gösterir.  
  
 ![Farklı orta noktaları 2 x ölçekler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Aynı ScaleX ve ScaleY değerleri ancak farklı olan iki ScaleTransform işlem  
  
 Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
