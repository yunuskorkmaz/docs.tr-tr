---
title: 'Nasıl yapılır: Arka Plan Olarak Kullanılan bir Görüntünün En Boy Oranını Koruma'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 4ae6f1242548038bcd54b7218783e5063fa67872
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921777"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Nasıl yapılır: Arka Plan Olarak Kullanılan bir Görüntünün En Boy Oranını Koruma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği bir <xref:System.Windows.Media.ImageBrush> görüntünün en boy oranını korumak için.  
  
 Varsayılan olarak kullandığınızda, bir <xref:System.Windows.Media.ImageBrush> bir alanı boyama için tamamen çıkış alanı dolduracak şekilde içeriği uzatılır. Çıkış alanı ve görüntüyü farklı en boy oranlarına sahip olduğunuzda bu yayarak resmin bozuk.  
  
 Yapmak için bir <xref:System.Windows.Media.ImageBrush> , görüntünün en boy oranını korumak için ayarlayın <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliğini <xref:System.Windows.Media.Stretch.Uniform> veya <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki örnekte <xref:System.Windows.Media.ImageBrush> iki dikdörtgenler boyamak için nesneleri. Her dikdörtgenin 300 x 150 piksel olan ve her 300 x 300 piksel resim içerir. <xref:System.Windows.Media.TileBrush.Stretch%2A> İlk fırça özelliği <xref:System.Windows.Media.Stretch.Uniform>ve <xref:System.Windows.Media.TileBrush.Stretch%2A> ikinci fırça özelliği <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Sahip olan ilk fırçanın çıktısı aşağıdaki çizimde bir <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarıyla <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![Tekdüzen uzatma ile ImageBrush](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Bir sonraki çizimde sahip ikinci bir fırça çıktısını gösterir bir <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarıyla <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![UniformToFill uzatma ImageBrush](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Unutmayın <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği aynı şekilde davrandığını diğer <xref:System.Windows.Media.TileBrush> nesnelerini, diğer bir deyişle, için <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush>. Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> ve diğer <xref:System.Windows.Media.TileBrush> nesneleri bkz [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
 Ayrıca, ancak unutmayın <xref:System.Windows.Media.TileBrush.Stretch%2A> özellik görünür belirtmek için nasıl <xref:System.Windows.Media.TileBrush> içeriği uzatılır, çıkış alana uyacak şekilde, bu gerçekte belirtir nasıl <xref:System.Windows.Media.TileBrush> içerik kendi taban döşemesi dolduracak şekilde uzatır. Daha fazla bilgi için bkz. <xref:System.Windows.Media.TileBrush>.  
  
 Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.ImageBrush> sınıfı. Tam bir örnek için bkz. [ImageBrush örnek](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.TileBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
