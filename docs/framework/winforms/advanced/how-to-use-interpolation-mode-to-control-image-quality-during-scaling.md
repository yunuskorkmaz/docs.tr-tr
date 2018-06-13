---
title: 'Nasıl yapılır: Ölçeklendirme Sırasında Görüntü Kalitesini Denetlemek için İlişkilendirme Modunu Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 72a9cb3a19f0d449dcb376a65f1734b79ed61ab9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522365"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="5cf15-102">Nasıl yapılır: Ölçeklendirme Sırasında Görüntü Kalitesini Denetlemek için İlişkilendirme Modunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="5cf15-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="5cf15-103">İlişkilendirme modunu bir <xref:System.Drawing.Graphics> nesne şeklini etkiler [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ölçekler (uzatır ve küçültür) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5cf15-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="5cf15-104"><xref:System.Drawing.Drawing2D.InterpolationMode> Numaralandırma aşağıdaki listede gösterildiği bazıları birkaç ilişkilendirme modu tanımlar:</span><span class="sxs-lookup"><span data-stu-id="5cf15-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="5cf15-105">Bir görüntü uzatmak için Orijinal görüntüdeki her piksel piksel cinsinden büyük görüntü grubuna eşlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cf15-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="5cf15-106">Görüntüyü daraltmak için Orijinal görüntüdeki piksel grupları tek piksel cinsinden daha küçük resim eşlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cf15-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="5cf15-107">Bu eşlemeler gerçekleştirmek algoritmaları verimliliğini ölçeklendirilmiş bir görüntü kalitesini belirler.</span><span class="sxs-lookup"><span data-stu-id="5cf15-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="5cf15-108">Daha fazla işleme süresi gerektirecek şekilde daha yüksek kaliteli ölçeklenen görüntüler oluşturmak algoritmaları eğilimlidir.</span><span class="sxs-lookup"><span data-stu-id="5cf15-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="5cf15-109">Yukarıdaki listede <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> düşük kaliteli modudur ve <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> yüksek kaliteli modudur.</span><span class="sxs-lookup"><span data-stu-id="5cf15-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="5cf15-110">İlişkilendirme modu ayarlamak için üyelerinden birinde atamak <xref:System.Drawing.Drawing2D.InterpolationMode> numaralandırma <xref:System.Drawing.Graphics.InterpolationMode%2A> özelliği bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5cf15-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cf15-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cf15-111">Example</span></span>  
 <span data-ttu-id="5cf15-112">Aşağıdaki örnek, bir resim çizer ve üç farklı ilişkilendirme modu görüntüsüyle küçültür.</span><span class="sxs-lookup"><span data-stu-id="5cf15-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="5cf15-113">Aşağıdaki çizimde özgün resim ve üç küçük resimleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cf15-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 <span data-ttu-id="5cf15-114">![Çeşitli ilişkilendirme ayarlarını görüntüsüyle](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span><span class="sxs-lookup"><span data-stu-id="5cf15-114">![Image with Varied Interpolation Settings](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cf15-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5cf15-115">Compiling the Code</span></span>  
 <span data-ttu-id="5cf15-116">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5cf15-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf15-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cf15-117">See Also</span></span>  
 [<span data-ttu-id="5cf15-118">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5cf15-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="5cf15-119">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="5cf15-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
