---
title: 'Nasıl yapılır: Görüntü renklerini çevirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 81aecddb28903649ff2d59e80fc90368df5e2db4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703029"
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="e8276-102">Nasıl yapılır: Görüntü renklerini çevirme</span><span class="sxs-lookup"><span data-stu-id="e8276-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="e8276-103">Bir çeviri, bir veya daha fazla dört renk bileşeni için bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="e8276-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="e8276-104">Çevirileri temsil eden renk matrisi girişleri aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8276-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="e8276-105">Çevrilecek bileşeni</span><span class="sxs-lookup"><span data-stu-id="e8276-105">Component to be translated</span></span>|<span data-ttu-id="e8276-106">Matris giriş</span><span class="sxs-lookup"><span data-stu-id="e8276-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="e8276-107">Kırmızı</span><span class="sxs-lookup"><span data-stu-id="e8276-107">Red</span></span>|<span data-ttu-id="e8276-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="e8276-108">[4][0]</span></span>|  
|<span data-ttu-id="e8276-109">Yeşil</span><span class="sxs-lookup"><span data-stu-id="e8276-109">Green</span></span>|<span data-ttu-id="e8276-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="e8276-110">[4][1]</span></span>|  
|<span data-ttu-id="e8276-111">Mavi</span><span class="sxs-lookup"><span data-stu-id="e8276-111">Blue</span></span>|<span data-ttu-id="e8276-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="e8276-112">[4][2]</span></span>|  
|<span data-ttu-id="e8276-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="e8276-113">Alpha</span></span>|<span data-ttu-id="e8276-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="e8276-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e8276-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8276-115">Example</span></span>  
 <span data-ttu-id="e8276-116">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e8276-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="e8276-117">Ardından kod 0,75 görüntüde her pikselin kırmızı bileşeni ekler.</span><span class="sxs-lookup"><span data-stu-id="e8276-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="e8276-118">Özgün resmin dönüştürülmüş görüntünün yanı sıra çizilir.</span><span class="sxs-lookup"><span data-stu-id="e8276-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="e8276-119">Aşağıdaki çizimde, sol taraftaki özgün görüntü ve dönüştürülen görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8276-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="e8276-120">![Renklerini çevirme](./media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="e8276-120">![Translate Colors](./media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="e8276-121">Aşağıdaki tabloda dört Çubuklar için rengi vektörleri önce ve sonra kırmızı çeviri listeler.</span><span class="sxs-lookup"><span data-stu-id="e8276-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="e8276-122">Renk bileşeni için maksimum değeri 1 olduğundan, kırmızı bileşeni ikinci satıra değil değiştiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e8276-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="e8276-123">(Benzer şekilde, bir renk bileşeni için en düşük değer 0'dır.)</span><span class="sxs-lookup"><span data-stu-id="e8276-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="e8276-124">Özgün</span><span class="sxs-lookup"><span data-stu-id="e8276-124">Original</span></span>|<span data-ttu-id="e8276-125">Çevrilmiş</span><span class="sxs-lookup"><span data-stu-id="e8276-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="e8276-126">Siyah (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="e8276-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="e8276-128">Kırmızı (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="e8276-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="e8276-130">Yeşil (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="e8276-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="e8276-132">Mavi (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="e8276-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="e8276-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8276-134">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e8276-134">Compiling the Code</span></span>  
 <span data-ttu-id="e8276-135">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e8276-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="e8276-136">Değiştirin `ColorBars.bmp` bir resim dosyası adı ve sisteminize göre geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="e8276-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8276-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8276-137">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="e8276-138">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="e8276-138">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="e8276-139">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="e8276-139">Recoloring Images</span></span>](recoloring-images.md)
