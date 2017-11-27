---
title: "Nasıl yapılır: Göreli Değerler Kullanarak Dönüşümün Kaynağını Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec61fdedc78b785dccf2c235cd17fd20b6d5abc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="57524-102">Nasıl yapılır: Göreli Değerler Kullanarak Dönüşümün Kaynağını Belirtme</span><span class="sxs-lookup"><span data-stu-id="57524-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="57524-103">Bu örnek göreli değerlerin kökenini belirlemek için nasıl kullanılacağını gösterir bir <xref:System.Windows.UIElement.RenderTransform%2A> için uygulanan bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="57524-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="57524-104">Ne zaman döndürme, ölçeklendirme veya eğme bir <xref:System.Windows.FrameworkElement> kullanarak <xref:System.Windows.UIElement.RenderTransform%2A> özelliği, varsayılan ayar, öğenin sol üst köşesindeki dönüştürme uygulanır.</span><span class="sxs-lookup"><span data-stu-id="57524-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="57524-105">Döndürme, ölçeklendirme veya öğenin Merkezi'nden eğme istiyorsanız, öğenin merkezine dönüştürme merkezi ayarlayarak dengeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57524-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="57524-106">Ancak, bu çözüm öğe boyutunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="57524-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="57524-107">Ayarlamak için öğenin merkezine dönüşüm uygulamanın daha kolay bir yoludur kendi <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliğine (0,5, 0,5) dönüştürme üzerinde merkez değerini ayarlamak yerine.</span><span class="sxs-lookup"><span data-stu-id="57524-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57524-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="57524-108">Example</span></span>  
 <span data-ttu-id="57524-109">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Controls.Button> 45 derece saat yönünde.</span><span class="sxs-lookup"><span data-stu-id="57524-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="57524-110">Örnek bir merkezi belirtmediğinden düğmesi, sol üst köşe noktası hakkında (0, 0) döndürür.</span><span class="sxs-lookup"><span data-stu-id="57524-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="57524-111"><xref:System.Windows.Media.RotateTransform> Uygulanan <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="57524-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="57524-112">Aşağıdaki çizimde, izleyen örnek için dönüşüm sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="57524-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="57524-113">![RenderTransform kullanılarak dönüştürülen düğme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="57524-113">![A button transformed using RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="57524-114">RenderTransform özelliğini kullanarak 45 derece saat yönünde bir döndürme</span><span class="sxs-lookup"><span data-stu-id="57524-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="57524-115">Aşağıdaki örnekte de kullanan bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Controls.Button> 45 derece saat yönünde; ancak, bu örnek ayarlar <xref:System.Windows.UIElement.RenderTransformOrigin%2A> için düğmesinin (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="57524-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="57524-116">Sonuç olarak, döndürme, sol üst köşe yerine düğmenin merkezine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="57524-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="57524-117">Aşağıdaki çizimde, izleyen örnek için dönüşüm sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="57524-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="57524-118">![Ortasından dönüştürülen düğme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="57524-118">![A button transformed about its center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="57524-119">RenderTransformOrigin'i ile RenderTransform özelliğini kullanarak 45 derece döndürme (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="57524-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="57524-120">Dönüştürme hakkında daha fazla bilgi için <xref:System.Windows.FrameworkElement> nesneleri bkz [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="57524-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57524-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57524-121">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="57524-122">Dönüşümler genel bakış</span><span class="sxs-lookup"><span data-stu-id="57524-122">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="57524-123">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="57524-123">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
