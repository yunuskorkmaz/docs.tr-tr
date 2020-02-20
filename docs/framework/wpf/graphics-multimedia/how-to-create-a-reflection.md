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
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="6545d-102">Nasıl yapılır: Yansıma Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6545d-102">How to: Create a Reflection</span></span>
<span data-ttu-id="6545d-103">Bu örnek, yansıma oluşturmak için bir <xref:System.Windows.Media.VisualBrush> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6545d-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="6545d-104"><xref:System.Windows.Media.VisualBrush> var olan bir görseli görüntüleyebilmesi nedeniyle, bu özelliği kullanarak, yansıma ve büyütme gibi ilginç görsel etkiler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6545d-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6545d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="6545d-105">Example</span></span>  
 <span data-ttu-id="6545d-106">Aşağıdaki örnek, birkaç öğe içeren bir <xref:System.Windows.Controls.Border> yansımasını oluşturmak için bir <xref:System.Windows.Media.VisualBrush> kullanır.</span><span class="sxs-lookup"><span data-stu-id="6545d-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="6545d-107">Aşağıdaki çizim, bu örneğin oluşturduğu çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6545d-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="6545d-108">![Yansıtılan bir görsel nesne](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="6545d-108">![A reflected Visual object](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="6545d-109">Yansıtılan bir görsel nesne</span><span class="sxs-lookup"><span data-stu-id="6545d-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="6545d-110">Ekranın parçalarını büyütme ve yansıma oluşturma işlemlerinin nasıl yapılacağını gösteren örnekleri içeren tüm örnek için bkz. [VisualBrush örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span><span class="sxs-lookup"><span data-stu-id="6545d-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6545d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6545d-111">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="6545d-112">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="6545d-112">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
