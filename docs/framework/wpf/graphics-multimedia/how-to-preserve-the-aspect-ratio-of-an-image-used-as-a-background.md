---
title: 'Nasıl yapılır: Arka Plan Olarak Kullanılan bir Görüntünün En Boy Oranını Koruma'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186027"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Nasıl yapılır: Arka Plan Olarak Kullanılan bir Görüntünün En Boy Oranını Koruma
Bu örnek, görüntünün <xref:System.Windows.Media.TileBrush.Stretch%2A> en <xref:System.Windows.Media.ImageBrush> boy oranını korumak için bir özelliğin nasıl kullanılacağını gösterir.  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.ImageBrush> alanı boyamak için bir alanı kullandığınızda, içeriği çıktı alanını tamamen doldurmak için uzanır. Çıkış alanı ve görüntü farklı en boy oranlarına sahip olduğunda, görüntü bu esneme ile deforme olur.  
  
 Görüntünün <xref:System.Windows.Media.ImageBrush> en boy oranını korumak için <xref:System.Windows.Media.TileBrush.Stretch%2A> <xref:System.Windows.Media.Stretch.Uniform> özelliği veya <xref:System.Windows.Media.Stretch.UniformToFill>özelliği ni ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.ImageBrush> iki dikdörtgen boyamak için iki nesne kullanır. Her dikdörtgen 300'e 150 pikseldir ve her biri 300'e 300 piksel lik bir görüntü içerir. İlk <xref:System.Windows.Media.TileBrush.Stretch%2A> fırçanın özelliği <xref:System.Windows.Media.Stretch.Uniform>,' olarak <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarlanır ve ikinci fırçanın <xref:System.Windows.Media.Stretch.UniformToFill>özelliği .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Aşağıdaki resimde ilk fırçanın çıktısı gösterilmektedir, <xref:System.Windows.Media.TileBrush.Stretch%2A> <xref:System.Windows.Media.Stretch.Uniform>bu da .  
  
 ![Uniform stretching ile ImageBrush](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Sonraki resimde ikinci fırçanın çıktısı gösterilmektedir, bu da <xref:System.Windows.Media.TileBrush.Stretch%2A> <xref:System.Windows.Media.Stretch.UniformToFill>.'  
  
 ![UniformToFill germe ile ImageBrush](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Özelliğin <xref:System.Windows.Media.TileBrush.Stretch%2A> diğer <xref:System.Windows.Media.TileBrush> nesneler için aynı şekilde şekilde olduğunu unutmayın, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>yani, için ve . Ve diğer <xref:System.Windows.Media.TileBrush> <xref:System.Windows.Media.ImageBrush> nesneler hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)konusuna bakın.  
  
 Ayrıca, <xref:System.Windows.Media.TileBrush.Stretch%2A> özellik içeriğin <xref:System.Windows.Media.TileBrush> çıktı alanına uyacak şekilde nasıl uzadığını belirtse de, <xref:System.Windows.Media.TileBrush> içeriğin temel döşemesini doldurmak için nasıl uzadığını belirtir. Daha fazla bilgi için bkz. <xref:System.Windows.Media.TileBrush>.  
  
 Bu kod örneği, <xref:System.Windows.Media.ImageBrush> sınıf için sağlanan daha büyük bir örneğin bir parçasıdır. Tam örnek için [ImageBrush Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.TileBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
