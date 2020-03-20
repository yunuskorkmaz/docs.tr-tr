---
title: 'Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186829"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama

Bu örnek, bir <xref:System.Windows.Media.TileBrush>. Varsayılan olarak, <xref:System.Windows.Media.TileBrush> bir resim yaptığınız alanı tamamen dolduran tek bir döşeme üretir. Bu davranışı <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri ayarlayarak geçersiz kılabilirsiniz.

Özellik, <xref:System.Windows.Media.TileBrush.Viewport%2A> bir <xref:System.Windows.Media.TileBrush>. Varsayılan olarak, özelliğin <xref:System.Windows.Media.TileBrush.Viewport%2A> değeri boyanmakta olan alanın boyutuna göredir. <xref:System.Windows.Media.TileBrush.Viewport%2A> Özelliğin mutlak bir döşeme boyutu belirtinsin, <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliği ' ne <xref:System.Windows.Media.BrushMappingMode.Absolute>göre ayarlayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Windows.Media.ImageBrush>bir dikdörtgeni <xref:System.Windows.Media.TileBrush>karolarla boyamak için bir tür , bir tür kullanır. Örnek, her döşemeyi çıkış alanının (dikdörtgenin) yüzde 50'si oranında yüzde 50 olarak ayarlar. Sonuç olarak, dikdörtgen görüntünün dört projeksiyonları ile boyanır.

Aşağıdaki resimde, örneğin ürettiği çıktı gösterilmektedir:

![Bir görüntü fırçası ile fayans gösteren dört kiraz ile bir dikdörtgen.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

Sonraki örnek, bir <xref:System.Windows.Media.ImageBrush>oluşturur <xref:System.Windows.Media.TileBrush.Viewport%2A> , `0,0,25,25` onun <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.BrushMappingMode.Absolute>ve onun ayarlar , ve başka bir dikdörtgen boyamak için kullanır. Sonuç olarak, fırça 25 piksel genişliğinde ve 25 piksel yüksekliğe sahip karolar üretir.

Aşağıdaki resimde, örneğin ürettiği çıktı gösterilmektedir:

![Kırk sekiz kiraz ile bir dikdörtgen bir Viewport ile bir kiremitli TileFırça gösteren.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

Önceki örnekler daha büyük bir örneğin parçasıdır. Tam örnek için [ImageBrush Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)bakın.

Bu örnek sınıfı <xref:System.Windows.Media.ImageBrush> kullansa da, <xref:System.Windows.Media.TileBrush.Viewport%2A> diğer <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.TileBrush> nesneler için özellikler aynı şekilde <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>çalışır, yani, için ve . Ve diğer <xref:System.Windows.Media.TileBrush> <xref:System.Windows.Media.ImageBrush> nesneler hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.TileBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [TileBrush ile Farklı Döşeme Desenleri Oluşturma](how-to-create-different-tile-patterns-with-a-tilebrush.md)
