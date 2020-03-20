---
title: 'Nasıl yapılır: Bir Öğeyi Eğme'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 370ac28b07427345b52822133b5414b45d4462eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187658"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="b59d1-102">Nasıl yapılır: Bir Öğeyi Eğme</span><span class="sxs-lookup"><span data-stu-id="b59d1-102">How to: Skew an Element</span></span>
<span data-ttu-id="b59d1-103">Bu örnek, bir <xref:System.Windows.Media.SkewTransform> öğeyi eğriltmek için a'nın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b59d1-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="b59d1-104">Bir eğrilik, aynı zamanda bir yama olarak bilinen, olmayan bir üniforma şekilde koordinat alanı uzanan bir dönüşümdür.</span><span class="sxs-lookup"><span data-stu-id="b59d1-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="b59d1-105">A'nın <xref:System.Windows.Media.SkewTransform> tipik kullanımlarından biri, 2-B nesnelerde 3-B derinliğinin simüle edilmesidir.</span><span class="sxs-lookup"><span data-stu-id="b59d1-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="b59d1-106">'nin <xref:System.Windows.Media.SkewTransform.CenterX%2A> <xref:System.Windows.Media.SkewTransform.CenterY%2A> merkez noktasını belirtmek için ve özelliklerini kullanın. <xref:System.Windows.Media.SkewTransform></span><span class="sxs-lookup"><span data-stu-id="b59d1-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="b59d1-107">X <xref:System.Windows.Media.SkewTransform.AngleX%2A> ekseni ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> y ekseninin çarpık açısını belirtmek ve bu eksenler boyunca geçerli koordinat sistemini eğriltmek için ve özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="b59d1-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="b59d1-108">Çarpık dönüşümün etkisini tahmin etmek için, <xref:System.Windows.Media.SkewTransform.AngleX%2A> x ekseni değerlerini özgün koordinat sistemine göre çarpıtmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b59d1-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="b59d1-109">Bu nedenle, <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30'lu bir için y ekseni menşei boyunca 30 derece döner ve x-'deki değerleri bu kaynaktan 30 derece eğritir.</span><span class="sxs-lookup"><span data-stu-id="b59d1-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="b59d1-110">Aynı şekilde, <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30'dan biri şeklin y değerlerini kökenden 30 derece eğriltiyor.</span><span class="sxs-lookup"><span data-stu-id="b59d1-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="b59d1-111">Bunun koordinat sistemini x veya y-'de 30 derece çevirmek (taşımak) ile aynı etkiyi yaratmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b59d1-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="b59d1-112">Aşağıdaki örnek, (0,0) bir merkez noktasından <xref:System.Windows.Shapes.Rectangle> a 45 derecelik yatay bir eğrilik uygular.</span><span class="sxs-lookup"><span data-stu-id="b59d1-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b59d1-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b59d1-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="b59d1-114">Aşağıdaki örnek, (25,25) bir merkez <xref:System.Windows.Shapes.Rectangle> noktasından a için 45 derecelik yatay bir eğrilik uygular.</span><span class="sxs-lookup"><span data-stu-id="b59d1-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="b59d1-115">Aşağıdaki örnek, (25,25) bir merkez <xref:System.Windows.Shapes.Rectangle> noktasından a için 45 derecelik dikey bir eğrilik uygular.</span><span class="sxs-lookup"><span data-stu-id="b59d1-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="b59d1-116">Aşağıdaki resimde, bu örnekte kullanılan farklı eğrilikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b59d1-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="b59d1-117">![SkewTransform örnekleri](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="b59d1-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="b59d1-118">Üç SkewTransform örnekleri resimli</span><span class="sxs-lookup"><span data-stu-id="b59d1-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="b59d1-119">Numunenin tamamı için [2-B Dönüşüm Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.</span><span class="sxs-lookup"><span data-stu-id="b59d1-119">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59d1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b59d1-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="b59d1-121">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b59d1-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="b59d1-122">Nasıl Dır Konular</span><span class="sxs-lookup"><span data-stu-id="b59d1-122">How-to Topics</span></span>](transformations-how-to-topics.md)
