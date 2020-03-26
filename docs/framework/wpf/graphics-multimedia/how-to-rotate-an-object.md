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
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112069"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="45465-102">Nasıl yapılır: Nesne Döndürme</span><span class="sxs-lookup"><span data-stu-id="45465-102">How to: Rotate an Object</span></span>
<span data-ttu-id="45465-103">Bu örnek, bir nesnenin nasıl döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="45465-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="45465-104">Örnek önce bir <xref:System.Windows.Media.RotateTransform> oluşturur ve sonra <xref:System.Windows.Media.RotateTransform.Angle%2A> derece olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="45465-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="45465-105">Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Polyline> nesneyi sol üst köşesinde 45 derece döndürür.</span><span class="sxs-lookup"><span data-stu-id="45465-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45465-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="45465-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="45465-107">Nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> döndürüldettiği noktayı belirtin. <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterY%2A></span><span class="sxs-lookup"><span data-stu-id="45465-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="45465-108">Bu merkez noktası dönüştürülen öğenin koordinat alanında ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="45465-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="45465-109">Varsayılan olarak, döndürme (0,0), dönüştürmek için nesnenin sol üst köşesi olan uygulanır.</span><span class="sxs-lookup"><span data-stu-id="45465-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="45465-110">Sonraki örnek, nesneyi <xref:System.Windows.Shapes.Polyline> saat yönünde 45 derece olarak nokta (25,50) döndürür.</span><span class="sxs-lookup"><span data-stu-id="45465-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="45465-111">Aşağıdaki resimde iki nesneye a <xref:System.Windows.Media.Transform> uygulamanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="45465-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="45465-112">![Farklı merkez noktaları ile 45 derece rotasyonlar](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="45465-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="45465-113">Farklı dönme merkezlerinden 45 derece dönen iki nesne</span><span class="sxs-lookup"><span data-stu-id="45465-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="45465-114">Önceki <xref:System.Windows.Shapes.Polyline> örneklerde bir <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="45465-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="45465-115">Bir <xref:System.Windows.Media.Transform> <xref:System.Windows.UIElement.RenderTransform%2A> <xref:System.Windows.UIElement>özelliğine a uyguladığınız zaman, öğeye uyguladığınız her <xref:System.Windows.Media.Transform> bir kaynak için bir kaynak belirtmek için <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45465-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="45465-116">Özellik <xref:System.Windows.UIElement.RenderTransformOrigin%2A> göreli koordinatlar kullandığından, boyutunu bilmeseniz bile öğenin merkezine dönüşüm uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45465-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="45465-117">Daha fazla bilgi ve örnek için bkz. [Göreli Değerleri Kullanarak Dönüşümün Kaynağını Belirtin.](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)</span><span class="sxs-lookup"><span data-stu-id="45465-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="45465-118">Tam örnek için [2B Dönüşümler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.</span><span class="sxs-lookup"><span data-stu-id="45465-118">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45465-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45465-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="45465-120">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="45465-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="45465-121">Nasıl Dır Konular</span><span class="sxs-lookup"><span data-stu-id="45465-121">How-to Topics</span></span>](transformations-how-to-topics.md)
