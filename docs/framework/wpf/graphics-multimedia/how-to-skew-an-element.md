---
title: 'Nasıl yapılır: Bir Öğeyi Eğme'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: fec3ec38a19b552e988d26ea57c6f9beed6ce06e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359382"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="9cc0f-102">Nasıl yapılır: Bir Öğeyi Eğme</span><span class="sxs-lookup"><span data-stu-id="9cc0f-102">How to: Skew an Element</span></span>
<span data-ttu-id="9cc0f-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.SkewTransform> bir öğeyi eğme için.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="9cc0f-104">Olarak da bilinen bir yamultma olan bir eğme koordinat bir Tekdüzen olmayan şekilde uzatır bir dönüşümdür.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="9cc0f-105">Tipik bir kullanımı, bir <xref:System.Windows.Media.SkewTransform> benzetimi için olduğu [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] derinlik [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="9cc0f-106">Kullanım <xref:System.Windows.Media.SkewTransform.CenterX%2A> ve <xref:System.Windows.Media.SkewTransform.CenterY%2A> merkezi belirtmek için özellikleri noktasını <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="9cc0f-107">Kullanım <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> eğme açısı x ve y ekseni belirtin ve bu eksen boyunca geçerli koordinat sistemini eğriltmek için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="9cc0f-108">Bir eğme dönüştürmesi etkisini tahmin etmek için göz önünde bulundurun <xref:System.Windows.Media.SkewTransform.AngleX%2A> özgün koordinat sistemi x ekseni değerlerini eğriltir.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="9cc0f-109">Bu nedenle, bir <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30 y kaynağı üzerinden 30 derece çevirir ve değerleri x-30 derece kaynağından eğriltir.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="9cc0f-110">Benzer şekilde, bir <xref:System.Windows.Media.SkewTransform.AngleY%2A> şeklin y değerlerinin kaynaktan 30 derece 30 Eğer.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="9cc0f-111">Bu (taşıma) çevirme aynı etkiyi olmadığını unutmayın x veya y - 30 derece koordinat sistemi.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="9cc0f-112">Aşağıdaki örnekte yatay eğme açısını 45 derecenin için geçerli bir <xref:System.Windows.Shapes.Rectangle> bir merkez noktadan (0,0).</span><span class="sxs-lookup"><span data-stu-id="9cc0f-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cc0f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="9cc0f-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="9cc0f-114">Aşağıdaki örnekte yatay eğme açısını 45 derecenin için geçerli bir <xref:System.Windows.Shapes.Rectangle> bir merkez noktadan (25,25).</span><span class="sxs-lookup"><span data-stu-id="9cc0f-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="9cc0f-115">Aşağıdaki örnekte dikey eğme açısını 45 derecenin için geçerli bir <xref:System.Windows.Shapes.Rectangle> bir merkez noktadan (25,25).</span><span class="sxs-lookup"><span data-stu-id="9cc0f-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="9cc0f-116">Aşağıdaki çizimde, bu örnekte kullanılan farklı farklarından gösterir.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="9cc0f-117">![SkewTransform örneği](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="9cc0f-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="9cc0f-118">Gösterilen üç SkewTransform örneği</span><span class="sxs-lookup"><span data-stu-id="9cc0f-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="9cc0f-119">Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="9cc0f-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc0f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-120">See also</span></span>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="9cc0f-121">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9cc0f-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="9cc0f-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9cc0f-122">How-to Topics</span></span>](transformations-how-to-topics.md)
