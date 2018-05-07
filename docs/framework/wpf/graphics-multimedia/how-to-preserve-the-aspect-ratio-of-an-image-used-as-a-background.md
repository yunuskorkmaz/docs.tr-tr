---
title: 'Nasıl yapılır: Arka Plan Olarak Kullanılan bir Görüntünün En Boy Oranını Koruma'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 906033b43ba657acc873f12a00000189db6796ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Nasıl yapılır: Arka Plan Olarak Kullanılan bir Görüntünün En Boy Oranını Koruma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği bir <xref:System.Windows.Media.ImageBrush> resmin oranını korumak için.  
  
 Varsayılan olarak kullandığınızda, bir <xref:System.Windows.Media.ImageBrush> bir alanı boyamak için tamamen çıktı alanını doldurmak için içeriği uzatılır. Çıkış alanı ve görüntünün farklı en boy oranlarına sahip olduğunda bu yayarak resmin bozuk.  
  
 Yapmak için bir <xref:System.Windows.Media.ImageBrush> görüntüsünü en boy oranını korumak, Ayarla <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliğine <xref:System.Windows.Media.Stretch.Uniform> veya <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki kullanan <xref:System.Windows.Media.ImageBrush> iki dikdörtgen boyamak için nesneleri. Her dikdörtgen 300 150 piksel ve her 300 tarafından 300 piksel resim içerir. <xref:System.Windows.Media.TileBrush.Stretch%2A> İlk fırça özelliği ayarlanmış <xref:System.Windows.Media.Stretch.Uniform>ve <xref:System.Windows.Media.TileBrush.Stretch%2A> ikinci fırça özelliği ayarlanmış <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Aşağıdaki çizimde sahip ilk fırça çıktısını gösterir bir <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarıyla <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![Uniform uzatma içeren ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Sonraki şekilde sahip ikinci fırça çıktısı gösterilmektedir bir <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarıyla <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![UniformToFill uzatma ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Unutmayın <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği aynı şekilde davrandığını diğer <xref:System.Windows.Media.TileBrush> , yani, nesne için <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush>. Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> ve diğer <xref:System.Windows.Media.TileBrush> nesneleri bkz [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Ancak ayrıca <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği görünür belirtmek için nasıl <xref:System.Windows.Media.TileBrush> içeriğini uzatır çıkış alanına uyacak şekilde gerçekte belirtir nasıl <xref:System.Windows.Media.TileBrush> içerik temel döşemesinin doldurmak için uzatır. Daha fazla bilgi için bkz. <xref:System.Windows.Media.TileBrush>.  
  
 Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.ImageBrush> sınıfı. Tam bir örnek için bkz: [ImageBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.TileBrush>  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
