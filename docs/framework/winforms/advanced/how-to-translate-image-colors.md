---
title: "Nasıl yapılır: Görüntü Renklerini Çevirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c21d20b631d8e0cf68e370dd43b3f5e92144b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="12ba6-102">Nasıl yapılır: Görüntü Renklerini Çevirme</span><span class="sxs-lookup"><span data-stu-id="12ba6-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="12ba6-103">Çeviri bir veya daha fazla dört renk bileşenleri için bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="12ba6-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="12ba6-104">Çeviriler temsil eden renk matrisi girişi aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="12ba6-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="12ba6-105">Çevrilecek bileşeni</span><span class="sxs-lookup"><span data-stu-id="12ba6-105">Component to be translated</span></span>|<span data-ttu-id="12ba6-106">Matris giriş</span><span class="sxs-lookup"><span data-stu-id="12ba6-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="12ba6-107">kırmızı</span><span class="sxs-lookup"><span data-stu-id="12ba6-107">Red</span></span>|<span data-ttu-id="12ba6-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="12ba6-108">[4][0]</span></span>|  
|<span data-ttu-id="12ba6-109">Yeşil</span><span class="sxs-lookup"><span data-stu-id="12ba6-109">Green</span></span>|<span data-ttu-id="12ba6-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="12ba6-110">[4][1]</span></span>|  
|<span data-ttu-id="12ba6-111">Mavi</span><span class="sxs-lookup"><span data-stu-id="12ba6-111">Blue</span></span>|<span data-ttu-id="12ba6-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="12ba6-112">[4][2]</span></span>|  
|<span data-ttu-id="12ba6-113">Alfa</span><span class="sxs-lookup"><span data-stu-id="12ba6-113">Alpha</span></span>|<span data-ttu-id="12ba6-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="12ba6-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="12ba6-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="12ba6-115">Example</span></span>  
 <span data-ttu-id="12ba6-116">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="12ba6-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="12ba6-117">Ardından kod görüntüdeki her piksel kırmızı bileşeninin 0,75 ekler.</span><span class="sxs-lookup"><span data-stu-id="12ba6-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="12ba6-118">Özgün görüntüsüne dönüştürülmüş yansımasının yanında çizilir.</span><span class="sxs-lookup"><span data-stu-id="12ba6-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="12ba6-119">Aşağıdaki çizimde özgün resim soldaki ve dönüştürülen görüntünün sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="12ba6-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="12ba6-120">![Renklerini çevirme](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="12ba6-120">![Translate Colors](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="12ba6-121">Aşağıdaki tabloda, önce ve sonra kırmızı çeviri dört Çubuklar için renk vektörlerinin listeler.</span><span class="sxs-lookup"><span data-stu-id="12ba6-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="12ba6-122">Renk bileşeni için maksimum değeri 1 olduğundan, ikinci satırında kırmızı bileşen değişmeyen olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12ba6-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="12ba6-123">(Benzer şekilde, bir renk bileşeni için en düşük değer 0'dır.)</span><span class="sxs-lookup"><span data-stu-id="12ba6-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="12ba6-124">Özgün</span><span class="sxs-lookup"><span data-stu-id="12ba6-124">Original</span></span>|<span data-ttu-id="12ba6-125">Çevrilmiş</span><span class="sxs-lookup"><span data-stu-id="12ba6-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="12ba6-126">Siyah (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="12ba6-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="12ba6-128">Kırmızı (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="12ba6-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="12ba6-130">Yeşil (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="12ba6-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="12ba6-132">Mavi (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="12ba6-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="12ba6-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12ba6-134">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="12ba6-134">Compiling the Code</span></span>  
 <span data-ttu-id="12ba6-135">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="12ba6-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="12ba6-136">Değiştir `ColorBars.bmp` bir görüntü dosyası adı ve, sisteminizde geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="12ba6-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ba6-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12ba6-137">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="12ba6-138">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="12ba6-138">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="12ba6-139">Görüntüleri yeniden renklendirme</span><span class="sxs-lookup"><span data-stu-id="12ba6-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
