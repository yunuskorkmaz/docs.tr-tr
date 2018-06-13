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
ms.openlocfilehash: 4efecc3c8083396d4c06d86d9ece01bd584a1c6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560964"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="01d38-102">Nasıl yapılır: Görüntü ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="01d38-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="01d38-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.ImageBrush> alanı bir görüntü ile boyamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="01d38-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="01d38-104">Bir <xref:System.Windows.Media.ImageBrush> tarafından belirtilen tek bir resmi görüntüler kendi <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="01d38-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d38-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="01d38-105">Example</span></span>  
 <span data-ttu-id="01d38-106">Aşağıdaki örnek paints <xref:System.Windows.Controls.Control.Background%2A> kullanarak düğmesinin bir <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="01d38-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="01d38-107">Varsayılan olarak, bir <xref:System.Windows.Media.ImageBrush> boyama alanını tamamen doldurmak için kendi resmini uzatır.</span><span class="sxs-lookup"><span data-stu-id="01d38-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="01d38-108">Önceki örnekte, görüntü, büyük olasılıkla resim bozulur düğmesi, dolduracak şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="01d38-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="01d38-109">Bu davranış ayarlayarak denetleyebilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği <xref:System.Windows.Media.TileBrush> için <xref:System.Windows.Media.Stretch.Uniform> veya <xref:System.Windows.Media.Stretch.UniformToFill>, resmin oranını korumak fırça neden olur.</span><span class="sxs-lookup"><span data-stu-id="01d38-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="01d38-110">Ayarlarsanız <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliklerini bir <xref:System.Windows.Media.ImageBrush>, yinelenen bir desen oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d38-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="01d38-111">Aşağıdaki örnek, bir görüntüden oluşturulan bir desen kullanılarak bir düğme boyar.</span><span class="sxs-lookup"><span data-stu-id="01d38-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="01d38-112">Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> sınıfı için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="01d38-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="01d38-113">Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.ImageBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01d38-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="01d38-114">Tam bir örnek için bkz: [ImageBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="01d38-114">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d38-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01d38-115">See Also</span></span>  
 [<span data-ttu-id="01d38-116">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="01d38-116">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
