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
ms.openlocfilehash: 8a5ed345c0aa25312bd74799264e1f66ab4554e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452064"
---
# <a name="how-to-create-a-reflection"></a>Nasıl yapılır: Yansıma Oluşturma
Bu örnek, yansıma oluşturmak için bir <xref:System.Windows.Media.VisualBrush> nasıl kullanacağınızı gösterir. <xref:System.Windows.Media.VisualBrush> var olan bir görseli görüntüleyebilmesi nedeniyle, bu özelliği kullanarak, yansıma ve büyütme gibi ilginç görsel etkiler oluşturabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birkaç öğe içeren bir <xref:System.Windows.Controls.Border> yansımasını oluşturmak için bir <xref:System.Windows.Media.VisualBrush> kullanır. Aşağıdaki çizim, bu örneğin oluşturduğu çıktıyı gösterir.  
  
 ![Yansıtılan bir görsel nesne](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Yansıtılan bir görsel nesne  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Ekranın parçalarını büyütme ve yansıma oluşturma işlemlerinin nasıl yapılacağını gösteren örnekleri içeren tüm örnek için bkz. [VisualBrush örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.VisualBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
