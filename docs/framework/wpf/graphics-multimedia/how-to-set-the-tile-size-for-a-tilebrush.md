---
title: 'Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 16f0a4b3a5c9b9075126ba6d8f19d65169f70921
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561754"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama
Bu örnek için döşeme boyutunu nasıl ayarlayacağınızı gösterir bir <xref:System.Windows.Media.TileBrush>. Varsayılan olarak, bir <xref:System.Windows.Media.TileBrush> tamamen boyama alanını dolduracak tek bir döşeme üretir. Ayarlayarak bu davranışı geçersiz kılabilirsiniz <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri.  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Özelliği için döşeme boyutunu belirtir bir <xref:System.Windows.Media.TileBrush>. Varsayılan olarak, değeri <xref:System.Windows.Media.TileBrush.Viewport%2A> boyandığında alanının boyutunu göreli bir özelliktir. Yapmak için <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliğini belirtin, mutlak bir döşeme boyutunu ayarlamak <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliğine <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.ImageBrush>, bir tür <xref:System.Windows.Media.TileBrush>, bir dikdörtgeni döşeme ile boyamak için. Örnek çıktı alanının (dikdörtgen) yüzde 50 yüzde 50 her bölme ayarlar. Sonuç olarak, dikdörtgen dört tane yansıması ile boyanır.  
  
 Aşağıdaki çizimde örnek üretir çıkış gösterir.
  
 ![Resim fırçası ile döşeme örneği](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 Sonraki örnekte bir <xref:System.Windows.Media.ImageBrush>, ayarlar, <xref:System.Windows.Media.TileBrush.Viewport%2A> için `0,0,25,25` ve kendi <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> için <xref:System.Windows.Media.BrushMappingMode.Absolute>ve başka bir dikdörtgen boyamak için kullanır. Sonuç olarak, fırça 25 piksel genişliği ve yüksekliği 25 piksel sahip döşeme üretir.  
  
 Aşağıdaki çizimde örnek üretir çıkış gösterir.  
  
 ![A döşeli bir 0,0,0,25,0,25 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 Önceki örneklerde daha büyük bir örneğin parçasıdır. Tam bir örnek için bkz: [ImageBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
 Bu örnek kullansa <xref:System.Windows.Media.ImageBrush> sınıfı, <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri aynı şekilde davranır diğer <xref:System.Windows.Media.TileBrush> , yani, nesne için <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush>. Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> ve diğer <xref:System.Windows.Media.TileBrush> nesneleri bkz [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.TileBrush>  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [TileBrush ile Farklı Döşeme Desenleri Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
