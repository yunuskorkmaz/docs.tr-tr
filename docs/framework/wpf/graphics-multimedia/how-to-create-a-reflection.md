---
title: "Nasıl yapılır: Yansıma Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3032f46843c6d8efc53c45a927feae7068c3eb5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="f6482-102">Nasıl yapılır: Yansıma Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6482-102">How to: Create a Reflection</span></span>
<span data-ttu-id="f6482-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.VisualBrush> yansımasını oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f6482-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="f6482-104">Çünkü bir <xref:System.Windows.Media.VisualBrush> varolan görseli görüntüleyebilir, yansıma ve büyütme gibi ilginç görsel efektler üretmek için bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6482-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6482-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6482-105">Example</span></span>  
 <span data-ttu-id="f6482-106">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.VisualBrush> yansımasını oluşturmak için bir <xref:System.Windows.Controls.Border> çeşitli öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f6482-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="f6482-107">Bu örneğin oluşturduğu çıktı aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6482-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="f6482-108">![Bir görsel nesne yansıtılan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="f6482-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="f6482-109">Yansıtılan Visual nesnesi</span><span class="sxs-lookup"><span data-stu-id="f6482-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="f6482-110">Ekran bölümlerinin nasıl ve yansımaların nasıl oluşturulduğunu gösteren örnekleri içeren, tam örnek için bkz: [büyütüleceğini](http://go.microsoft.com/fwlink/?LinkID=160049).</span><span class="sxs-lookup"><span data-stu-id="f6482-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6482-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6482-111">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="f6482-112">Görüntüleri, çizimler ve görsellerle boyama</span><span class="sxs-lookup"><span data-stu-id="f6482-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
