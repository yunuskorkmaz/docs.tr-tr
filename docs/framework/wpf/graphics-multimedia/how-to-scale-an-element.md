---
title: 'Nasıl yapılır: Öğe Ölçeklendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112056"
---
# <a name="how-to-scale-an-element"></a>Nasıl yapılır: Öğe Ölçeklendirme
Bu örnek, bir <xref:System.Windows.Media.ScaleTransform> öğeyi ölçeklendirmek için a'nın nasıl kullanılacağını gösterir.  
  
 Öğeyi <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> belirttiğiniz faktöre göre yeniden boyutlandırmak için ve özellikleri kullanın. Örneğin, 1,5 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> değeri öğeyi özgün genişliğinin yüzde 150'sine kadar genişletir. 0,5 değeri, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> bir öğenin yüksekliğini yüzde 50 küçültür.  
  
 Ölçek <xref:System.Windows.Media.ScaleTransform.CenterX%2A> işleminin merkezi olan noktayı belirtmek için ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> özellikleri kullanın. Varsayılan olarak, <xref:System.Windows.Media.ScaleTransform> a, dikdörtgenin sol üst köşesine karşılık gelen noktada (0,0) ortalanır. Bu, öğeyi hareket ettirme ve aynı zamanda daha büyük görünmesini <xref:System.Windows.Media.Transform>sağlama etkisine sahiptir, çünkü bir , nesnenin bulunduğu koordinat alanını değiştirirsiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.ScaleTransform> 50'ye 50 boyutunda a <xref:System.Windows.Shapes.Rectangle>kullanır. Her <xref:System.Windows.Media.ScaleTransform> ikisi <xref:System.Windows.Media.ScaleTransform.CenterX%2A> için 0 (varsayılan) değeri <xref:System.Windows.Media.ScaleTransform.CenterY%2A>vardır ve.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Genellikle, ölçeklenmiş <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> nesnenin ortasına ayarlarsınız: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).  
  
 Aşağıdaki örnek, <xref:System.Windows.Shapes.Rectangle> boyutu iki katına başka bir gösterir; ancak, <xref:System.Windows.Media.ScaleTransform> bu her ikisi <xref:System.Windows.Media.ScaleTransform.CenterX%2A> için 25 değerine sahiptir ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, dikdörtgenin merkezine karşılık gelir.  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Aşağıdaki resimde iki <xref:System.Windows.Media.ScaleTransform> işlem arasındaki farkı gösterilmektedir. Noktalı çizgi ölçekleme den önce dikdörtgenin boyutunu ve konumunu gösterir.  
  
 ![Farklı merkez noktaları ile 2x ölçekler](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Aynı ScaleX ve ScaleY değerlerine sahip ancak farklı merkezlere sahip iki ÖlçekDönüştürme işlemi  
  
 Tam örnek için [2B Dönüşümler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Nasıl Dır Konular](transformations-how-to-topics.md)
