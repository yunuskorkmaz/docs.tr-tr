---
title: "Nasıl yapılır: Nesne Döndürme"
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
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b356ef1782ec5bba4f7288644a0802f029456bbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="68713-102">Nasıl yapılır: Nesne Döndürme</span><span class="sxs-lookup"><span data-stu-id="68713-102">How to: Rotate an Object</span></span>
<span data-ttu-id="68713-103">Bu örnek bir nesnenin nasıl döndürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="68713-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="68713-104">Örnek ilk oluşturur bir <xref:System.Windows.Media.RotateTransform> ve ardından belirtir, <xref:System.Windows.Media.RotateTransform.Angle%2A> derece cinsinden.</span><span class="sxs-lookup"><span data-stu-id="68713-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="68713-105">Aşağıdaki örnek döndüğü bir <xref:System.Windows.Shapes.Polyline> , sol üst köşesindeki 45 derece nesne.</span><span class="sxs-lookup"><span data-stu-id="68713-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68713-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="68713-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="68713-107"><xref:System.Windows.Media.RotateTransform.CenterX%2A> Ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini <xref:System.Windows.Media.RotateTransform> nesne döndürüldüğü noktasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="68713-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="68713-108">Bu merkez nokta dönüştürülen öğenin koordinat ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="68713-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="68713-109">Varsayılan olarak, döndürme (0,0), sol üst köşesindeki dönüştürmek için nesnenin olduğu uygulanır.</span><span class="sxs-lookup"><span data-stu-id="68713-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="68713-110">Sonraki örnek döndüğü bir <xref:System.Windows.Shapes.Polyline> (25,50) noktasına saat yönünde 45 dereceyi nesne.</span><span class="sxs-lookup"><span data-stu-id="68713-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="68713-111">Aşağıdaki çizimde uygulama sonuçlarını gösterir bir <xref:System.Windows.Media.Transform> iki nesne için.</span><span class="sxs-lookup"><span data-stu-id="68713-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="68713-112">![farklı merkez nokta 45 derece döndürmeler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="68713-112">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="68713-113">Dönme 45 derece farklı döndürmek iki nesne merkezleri</span><span class="sxs-lookup"><span data-stu-id="68713-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="68713-114"><xref:System.Windows.Shapes.Polyline> Önceki örneklerde olduğu bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="68713-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="68713-115">Uyguladığınızda bir <xref:System.Windows.Media.Transform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği bir <xref:System.Windows.UIElement>, kullanabileceğiniz <xref:System.Windows.UIElement.RenderTransformOrigin%2A> noktanız için bir kaynak belirtmek üzere özelliğini her <xref:System.Windows.Media.Transform> öğesine uyguladığınız.</span><span class="sxs-lookup"><span data-stu-id="68713-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="68713-116">Çünkü <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliği kullanan koordinatlara göre boyutuna bilmiyorsanız bile öğenin merkezine dönüşüm uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68713-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="68713-117">Daha fazla bilgi ve bir örnek için bkz: [bir dönüşüm tarafından göreli değerlerini kullanarak kaynağını belirtmek](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="68713-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="68713-118">Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="68713-118">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68713-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68713-119">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="68713-120">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="68713-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="68713-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="68713-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
