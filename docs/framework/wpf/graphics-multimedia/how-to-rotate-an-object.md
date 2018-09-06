---
title: 'Nasıl yapılır: Nesne Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: b5a954158388e8b85589042e9d1f3b82c1747e30
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799690"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="a1c35-102">Nasıl yapılır: Nesne Döndürme</span><span class="sxs-lookup"><span data-stu-id="a1c35-102">How to: Rotate an Object</span></span>
<span data-ttu-id="a1c35-103">Bu örnek, bir nesnenin nasıl döndürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1c35-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="a1c35-104">Örneğin ilk oluşturur bir <xref:System.Windows.Media.RotateTransform> ve ardından belirtir, <xref:System.Windows.Media.RotateTransform.Angle%2A> derece cinsinden.</span><span class="sxs-lookup"><span data-stu-id="a1c35-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="a1c35-105">Aşağıdaki örnek döndürür bir <xref:System.Windows.Shapes.Polyline> kendi üst sol löşede 45 derece nesne.</span><span class="sxs-lookup"><span data-stu-id="a1c35-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1c35-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1c35-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="a1c35-107"><xref:System.Windows.Media.RotateTransform.CenterX%2A> Ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini <xref:System.Windows.Media.RotateTransform> nesne döndürüldüğü noktasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a1c35-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="a1c35-108">Bu merkez noktasını dönüştürülür öğenin koordinat ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="a1c35-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="a1c35-109">Varsayılan olarak, döndürme (0,0), sol üst köşesinin dönüştürmek için nesnenin olduğu uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a1c35-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="a1c35-110">Sonraki örnekte döndürür bir <xref:System.Windows.Shapes.Polyline> noktası (25,50) 45 derece saat yönünde nesne.</span><span class="sxs-lookup"><span data-stu-id="a1c35-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="a1c35-111">Uygulama sonuçlarını aşağıdaki çizimde bir <xref:System.Windows.Media.Transform> iki nesne için.</span><span class="sxs-lookup"><span data-stu-id="a1c35-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="a1c35-112">![farklı merkezi noktalarıyla 45 derece döndürme](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="a1c35-112">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="a1c35-113">Döngüsel 45 derece farklı döndürmek iki nesne merkezleri</span><span class="sxs-lookup"><span data-stu-id="a1c35-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="a1c35-114"><xref:System.Windows.Shapes.Polyline> Önceki örneklerde olduğu bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="a1c35-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="a1c35-115">Uyguladığınızda bir <xref:System.Windows.Media.Transform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği bir <xref:System.Windows.UIElement>, kullanabileceğiniz <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliği için bir kaynak belirtmek için her <xref:System.Windows.Media.Transform> öğeye uygulanacak.</span><span class="sxs-lookup"><span data-stu-id="a1c35-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="a1c35-116">Çünkü <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliği kullanan göreli koordinatlarda, boyutuna sahibi olmasanız bile, bir dönüştürme öğesinin merkezine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1c35-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="a1c35-117">Daha fazla bilgi ve örnek için bkz: [göreli değerler kullanarak dönüşümün kaynağını belirtme](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="a1c35-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="a1c35-118">Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="a1c35-118">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c35-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1c35-119">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="a1c35-120">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1c35-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="a1c35-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a1c35-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
