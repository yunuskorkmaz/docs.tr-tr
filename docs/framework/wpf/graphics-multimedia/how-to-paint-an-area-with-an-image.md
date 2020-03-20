---
title: 'Nasıl yapılır: Görüntü ile bir Alanı Boyama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186059"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="a9d6e-102">Nasıl yapılır: Görüntü ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="a9d6e-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="a9d6e-103">Bu örnek, bir <xref:System.Windows.Media.ImageBrush> alanı görüntüyle boyamak için sınıfın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="a9d6e-104">Bir <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği tarafından belirtilen tek bir görüntü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9d6e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9d6e-105">Example</span></span>  
 <span data-ttu-id="a9d6e-106">Aşağıdaki örnekte bir <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Media.ImageBrush>düğmenin bir .</span><span class="sxs-lookup"><span data-stu-id="a9d6e-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="a9d6e-107">Varsayılan olarak, <xref:System.Windows.Media.ImageBrush> bir resim tamamen boyama alanı doldurmak için kendi görüntü uzanır.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="a9d6e-108">Önceki örnekte, görüntü düğmeyi doldurmak için gerilmiş ve büyük olasılıkla görüntüyü bozuyor.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="a9d6e-109">Fırçanın <xref:System.Windows.Media.TileBrush.Stretch%2A> görüntünün en boy <xref:System.Windows.Media.TileBrush> oranını <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>korumasına neden olan özelliğini ayarlayarak bu davranışı denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="a9d6e-110">Bir <xref:System.Windows.Media.TileBrush.Viewport%2A> ,'nin <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliklerini <xref:System.Windows.Media.ImageBrush>ve özelliklerini ayarlarsanız, yinelenen bir desen oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="a9d6e-111">Aşağıdaki örnek, görüntüden oluşturulan bir desen kullanarak bir düğmeyi boyar.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="a9d6e-112"><xref:System.Windows.Media.ImageBrush> Sınıf hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama'ya](painting-with-images-drawings-and-visuals.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="a9d6e-113">Bu kod örneği, <xref:System.Windows.Media.ImageBrush> sınıf için sağlanan daha büyük bir örneğin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="a9d6e-114">Tam örnek için [ImageBrush Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)bakın.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-114">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d6e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9d6e-115">See also</span></span>

- [<span data-ttu-id="a9d6e-116">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="a9d6e-116">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
