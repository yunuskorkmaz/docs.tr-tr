---
title: Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: ff6172d571a7ca449ab21d1f7a7f9a699bf40f8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737981"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="de44c-102">Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="de44c-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="de44c-103">Ölçekleme dönüşümü bir veya daha fazla bir sayıyla dört renk bileşenlerine çarpar.</span><span class="sxs-lookup"><span data-stu-id="de44c-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="de44c-104">Ölçeklendirme temsil eden renk matrisi girişleri aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="de44c-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="de44c-105">Bileşen ölçeklendirilmesi</span><span class="sxs-lookup"><span data-stu-id="de44c-105">Component to be scaled</span></span>|<span data-ttu-id="de44c-106">Matris giriş</span><span class="sxs-lookup"><span data-stu-id="de44c-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="de44c-107">Kırmızı</span><span class="sxs-lookup"><span data-stu-id="de44c-107">Red</span></span>|<span data-ttu-id="de44c-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="de44c-108">[0][0]</span></span>|  
|<span data-ttu-id="de44c-109">Yeşil</span><span class="sxs-lookup"><span data-stu-id="de44c-109">Green</span></span>|<span data-ttu-id="de44c-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="de44c-110">[1][1]</span></span>|  
|<span data-ttu-id="de44c-111">Mavi</span><span class="sxs-lookup"><span data-stu-id="de44c-111">Blue</span></span>|<span data-ttu-id="de44c-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="de44c-112">[2][2]</span></span>|  
|<span data-ttu-id="de44c-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="de44c-113">Alpha</span></span>|<span data-ttu-id="de44c-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="de44c-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="de44c-115">Bir renk ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="de44c-115">Scaling One Color</span></span>  
 <span data-ttu-id="de44c-116">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="de44c-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="de44c-117">Ardından kod, her pikselin mavi bileşeni görüntüde 2 faktörüyle ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="de44c-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="de44c-118">Özgün resmin dönüştürülmüş görüntünün yanı sıra çizilir.</span><span class="sxs-lookup"><span data-stu-id="de44c-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="de44c-119">Aşağıdaki çizimde, sol taraftaki özgün görüntü ve ölçeklendirilmiş görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="de44c-119">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="de44c-120">![Renkleri ölçeklendirmek](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span><span class="sxs-lookup"><span data-stu-id="de44c-120">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span></span>  
  
 <span data-ttu-id="de44c-121">Aşağıdaki tabloda önceki ve sonraki mavi ölçeklendirme dört Çubuklar için rengi vektörleri listeler.</span><span class="sxs-lookup"><span data-stu-id="de44c-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="de44c-122">Dördüncü renk çubuğu mavi bileşeni 0.8 0,6 için gönderilmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="de44c-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="de44c-123">Çünkü [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sonucu yalnızca kesirli kısmını korur.</span><span class="sxs-lookup"><span data-stu-id="de44c-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="de44c-124">Örneğin, (2)(0.8) 1.6, = ve kesirli 1.6 0,6 parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="de44c-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="de44c-125">Yalnızca kesirli bölümü koruma sonucu her zaman [0, 1] aralığında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="de44c-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="de44c-126">Özgün</span><span class="sxs-lookup"><span data-stu-id="de44c-126">Original</span></span>|<span data-ttu-id="de44c-127">Ölçeği genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="de44c-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="de44c-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="de44c-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="de44c-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="de44c-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="de44c-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="de44c-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="de44c-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="de44c-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="de44c-136">Birden çok renkleri ölçekleme</span><span class="sxs-lookup"><span data-stu-id="de44c-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="de44c-137">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="de44c-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="de44c-138">Ardından kod her piksel kırmızı, yeşil ve mavi bileşenlerinin görüntüde ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="de44c-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="de44c-139">Kırmızı bileşenleri yüzde 25 ölçeklenir yeşil bileşenleri yüzde 35 ölçeklenir ve mavi bileşenlerinin yüzde 50 ölçeklenir.</span><span class="sxs-lookup"><span data-stu-id="de44c-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="de44c-140">Aşağıdaki çizimde, sol taraftaki özgün görüntü ve ölçeklendirilmiş görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="de44c-140">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="de44c-141">![Renkleri ölçeklendirmek](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span><span class="sxs-lookup"><span data-stu-id="de44c-141">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span></span>  
  
 <span data-ttu-id="de44c-142">Aşağıdaki tabloda dört Çubuklar için rengi vektörleri önce ve sonra kırmızı, yeşil ve mavi ölçeklendirme listeler.</span><span class="sxs-lookup"><span data-stu-id="de44c-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="de44c-143">Özgün</span><span class="sxs-lookup"><span data-stu-id="de44c-143">Original</span></span>|<span data-ttu-id="de44c-144">Ölçeği genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="de44c-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="de44c-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="de44c-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="de44c-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="de44c-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="de44c-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="de44c-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="de44c-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="de44c-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="de44c-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de44c-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de44c-153">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="de44c-154">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="de44c-154">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="de44c-155">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="de44c-155">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
