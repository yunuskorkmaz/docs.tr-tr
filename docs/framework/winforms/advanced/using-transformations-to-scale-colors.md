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
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107994"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="a2b00-102">Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a2b00-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="a2b00-103">Ölçekleme dönüşümü bir veya daha fazla bir sayıyla dört renk bileşenlerine çarpar.</span><span class="sxs-lookup"><span data-stu-id="a2b00-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="a2b00-104">Ölçeklendirme temsil eden renk matrisi girişleri aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a2b00-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="a2b00-105">Bileşen ölçeklendirilmesi</span><span class="sxs-lookup"><span data-stu-id="a2b00-105">Component to be scaled</span></span>|<span data-ttu-id="a2b00-106">Matris giriş</span><span class="sxs-lookup"><span data-stu-id="a2b00-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="a2b00-107">Kırmızı</span><span class="sxs-lookup"><span data-stu-id="a2b00-107">Red</span></span>|<span data-ttu-id="a2b00-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="a2b00-108">[0][0]</span></span>|  
|<span data-ttu-id="a2b00-109">Yeşil</span><span class="sxs-lookup"><span data-stu-id="a2b00-109">Green</span></span>|<span data-ttu-id="a2b00-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="a2b00-110">[1][1]</span></span>|  
|<span data-ttu-id="a2b00-111">Mavi</span><span class="sxs-lookup"><span data-stu-id="a2b00-111">Blue</span></span>|<span data-ttu-id="a2b00-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="a2b00-112">[2][2]</span></span>|  
|<span data-ttu-id="a2b00-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="a2b00-113">Alpha</span></span>|<span data-ttu-id="a2b00-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="a2b00-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="a2b00-115">Bir renk ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="a2b00-115">Scaling One Color</span></span>  
 <span data-ttu-id="a2b00-116">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2b00-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="a2b00-117">Ardından kod, her pikselin mavi bileşeni görüntüde 2 faktörüyle ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="a2b00-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="a2b00-118">Özgün resmin dönüştürülmüş görüntünün yanı sıra çizilir.</span><span class="sxs-lookup"><span data-stu-id="a2b00-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="a2b00-119">Aşağıdaki resimde, sağ tarafta sol taraftaki özgün görüntü ve ölçeklendirilmiş görüntü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a2b00-119">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Özgün ve ölçeklendirilmiş renkleri karşılaştıran ekran görüntüsü.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 <span data-ttu-id="a2b00-121">Aşağıdaki tabloda önceki ve sonraki mavi ölçeklendirme dört Çubuklar için rengi vektörleri listeler.</span><span class="sxs-lookup"><span data-stu-id="a2b00-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="a2b00-122">Dördüncü renk çubuğu mavi bileşeni 0.8 0,6 için gönderilmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a2b00-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="a2b00-123">Çünkü [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sonucu yalnızca kesirli kısmını korur.</span><span class="sxs-lookup"><span data-stu-id="a2b00-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="a2b00-124">Örneğin, (2)(0.8) 1.6, = ve kesirli 1.6 0,6 parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a2b00-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="a2b00-125">Yalnızca kesirli bölümü koruma sonucu her zaman [0, 1] aralığında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2b00-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="a2b00-126">Özgün</span><span class="sxs-lookup"><span data-stu-id="a2b00-126">Original</span></span>|<span data-ttu-id="a2b00-127">Ölçeği genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="a2b00-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="a2b00-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="a2b00-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="a2b00-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="a2b00-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="a2b00-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="a2b00-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="a2b00-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="a2b00-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="a2b00-136">Birden çok renkleri ölçekleme</span><span class="sxs-lookup"><span data-stu-id="a2b00-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="a2b00-137">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2b00-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="a2b00-138">Ardından kod her piksel kırmızı, yeşil ve mavi bileşenlerinin görüntüde ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="a2b00-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="a2b00-139">Kırmızı bileşenleri yüzde 25 ölçeklenir yeşil bileşenleri yüzde 35 ölçeklenir ve mavi bileşenlerinin yüzde 50 ölçeklenir.</span><span class="sxs-lookup"><span data-stu-id="a2b00-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="a2b00-140">Aşağıdaki resimde, sağ tarafta sol taraftaki özgün görüntü ve ölçeklendirilmiş görüntü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a2b00-140">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Özgün ve ölçeklendirilmiş renkleri karşılaştıran ekran görüntüsü.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 <span data-ttu-id="a2b00-142">Aşağıdaki tabloda dört Çubuklar için rengi vektörleri önce ve sonra kırmızı, yeşil ve mavi ölçeklendirme listeler.</span><span class="sxs-lookup"><span data-stu-id="a2b00-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="a2b00-143">Özgün</span><span class="sxs-lookup"><span data-stu-id="a2b00-143">Original</span></span>|<span data-ttu-id="a2b00-144">Ölçeği genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="a2b00-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="a2b00-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="a2b00-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="a2b00-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="a2b00-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="a2b00-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="a2b00-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="a2b00-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="a2b00-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="a2b00-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2b00-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b00-153">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="a2b00-154">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="a2b00-154">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="a2b00-155">Resimleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="a2b00-155">Recoloring Images</span></span>](recoloring-images.md)
