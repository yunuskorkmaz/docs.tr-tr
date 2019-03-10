---
title: 'Nasıl yapılır: Ölçeklendirme sırasında görüntü kalitesini denetlemek için ilişkilendirme modunu kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 83f1e569f1fb1ae49143f4ed11837759df29fe79
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721963"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="6778d-102">Nasıl yapılır: Ölçeklendirme sırasında görüntü kalitesini denetlemek için ilişkilendirme modunu kullanma</span><span class="sxs-lookup"><span data-stu-id="6778d-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="6778d-103">İlişkilendirme modu bir <xref:System.Drawing.Graphics> nesnenin şeklini etkiler [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ölçeklendirir (uzatır ve küçülür) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6778d-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="6778d-104"><xref:System.Drawing.Drawing2D.InterpolationMode> Sabit listesi tanımlar birkaç ilişkilendirme modu, bazıları aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6778d-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="6778d-105">Görüntü esnetme için her piksel Orijinal görüntüdeki piksel cinsinden daha büyük resmi grubuna eşlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="6778d-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="6778d-106">Görüntü daraltmak için grupları piksel Orijinal görüntüdeki tek piksel cinsinden daha küçük resmi eşlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6778d-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="6778d-107">Bu eşlemeler gerçekleştiren algoritmalar verimliliğini ölçeklendirilmiş bir görüntü kalitesini belirler.</span><span class="sxs-lookup"><span data-stu-id="6778d-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="6778d-108">Daha fazla işleme süresi gerektirecek şekilde ölçeklenen daha kaliteli görüntüler oluşturan algoritmaları eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="6778d-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="6778d-109">Yukarıdaki listede <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> düşük kaliteli modudur ve <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> yüksek kaliteli modudur.</span><span class="sxs-lookup"><span data-stu-id="6778d-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="6778d-110">İlişkilendirme modu ayarlamak için üyeleri birini atamanız <xref:System.Drawing.Drawing2D.InterpolationMode> sabit listesine <xref:System.Drawing.Graphics.InterpolationMode%2A> özelliği bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="6778d-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6778d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6778d-111">Example</span></span>  
 <span data-ttu-id="6778d-112">Aşağıdaki örnek, bir resim çizer ve sonra üç farklı ilişkilendirme modu görüntüsüyle küçültür.</span><span class="sxs-lookup"><span data-stu-id="6778d-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="6778d-113">Aşağıdaki çizimde, orijinal görüntünün ve üç küçük resimleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6778d-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 <span data-ttu-id="6778d-114">![Görüntü çeşitli ilişkilendirme ayarlarla](./media/csgrapes1.png "csgrapes1")</span><span class="sxs-lookup"><span data-stu-id="6778d-114">![Image with Varied Interpolation Settings](./media/csgrapes1.png "csgrapes1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6778d-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6778d-115">Compiling the Code</span></span>  
 <span data-ttu-id="6778d-116">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6778d-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6778d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6778d-117">See also</span></span>
- [<span data-ttu-id="6778d-118">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6778d-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="6778d-119">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="6778d-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
