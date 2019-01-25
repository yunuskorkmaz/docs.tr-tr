---
title: 'Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 4bfc14693f1714206e89ec50128ad62dd239dbee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713570"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama
Bu örnek için döşeme boyutunu ayarlama işlemi gösterilmektedir bir <xref:System.Windows.Media.TileBrush>. Varsayılan olarak, bir <xref:System.Windows.Media.TileBrush> tamamen boyama yaptığınız alanı dolduran kutucuk üretir. Ayarlayarak bu davranışı geçersiz kılabilirsiniz <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri.  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Özelliği için döşeme boyutunu belirten bir <xref:System.Windows.Media.TileBrush>. Varsayılan olarak, değerini <xref:System.Windows.Media.TileBrush.Viewport%2A> boyanan alanın boyutuna göre bir özelliktir. Yapmak <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliğini belirtin, mutlak bir döşeme boyutunu ayarlama <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliğini <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.ImageBrush>, bir tür <xref:System.Windows.Media.TileBrush>kutucuklar içeren bir dikdörtgen boyamak için. Örnek her kutucuk yüzde 50 ' (dikdörtgen) çıktı alanının yüzde 50 ayarlar. Sonuç olarak, dikdörtgeni görüntünün dört projeksiyonlar ile boyanır.  
  
 Örneğin oluşturduğu çıktı aşağıda gösterilmiştir.
  
 ![Resim fırçası ile döşeme](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 Sonraki örnek, oluşturur bir <xref:System.Windows.Media.ImageBrush>, ayarlar, <xref:System.Windows.Media.TileBrush.Viewport%2A> için `0,0,25,25` ve kendi <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> için <xref:System.Windows.Media.BrushMappingMode.Absolute>ve başka bir dikdörtgen boyamak için kullanır. Sonuç olarak, fırça 25 piksel genişliği ve yüksekliği 25 piksel kutucukları üretir.  
  
 Örneğin oluşturduğu çıktı aşağıda gösterilmiştir.  
  
 ![A döşenmiş bir 0,0,0,25,0,25 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 Önceki örneklerde, daha büyük bir örnek bir parçasıdır. Tam bir örnek için bkz. [ImageBrush örnek](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
 Bu örnek kullansa <xref:System.Windows.Media.ImageBrush> sınıfı <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri aynı şekilde davranır diğeri için <xref:System.Windows.Media.TileBrush> nesnelerini, diğer bir deyişle, için <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush>. Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> ve diğer <xref:System.Windows.Media.TileBrush> nesneleri bkz [görüntüler, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.TileBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [TileBrush ile Farklı Döşeme Desenleri Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
