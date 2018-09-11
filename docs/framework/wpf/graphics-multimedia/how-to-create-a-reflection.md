---
title: 'Nasıl yapılır: Yansıma Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 716adff5c5c41e6601e384b6669516cb6ba1041d
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339481"
---
# <a name="how-to-create-a-reflection"></a>Nasıl yapılır: Yansıma Oluşturma
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.VisualBrush> yansımasını oluşturmak için. Çünkü bir <xref:System.Windows.Media.VisualBrush> mevcut bir görselin görüntüleyebilir, yansıma ve büyütme gibi ilgi çekici görsel efektler üretmek için bu özelliği kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.VisualBrush> yansımasını oluşturmak için bir <xref:System.Windows.Controls.Border> , çeşitli öğeleri içerir. Bu örneğin oluşturduğu çıktı aşağıda gösterilmiştir.  
  
 ![Bir görsel nesne yansıtılan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Yansıtılan bir görsel nesneyi  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Ekran bölümlerinin nasıl ve yansımaların nasıl oluşturulacağını gösteren örnekleri içeren, tam örnek için bkz [büyütüldüğünü](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.VisualBrush>  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
