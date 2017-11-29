---
title: "Nasıl yapılır: Renkleri Bükme"
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
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f89bb5d87ef58c5ecda7be4cb9fb41da08e8a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="d1a51-102">Nasıl yapılır: Renkleri Bükme</span><span class="sxs-lookup"><span data-stu-id="d1a51-102">How to: Shear Colors</span></span>
<span data-ttu-id="d1a51-103">Yamultma artırır veya başka bir renk bileşenine orantılı bir miktar renk bileşeni azaltır.</span><span class="sxs-lookup"><span data-stu-id="d1a51-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="d1a51-104">Örneğin, burada kırmızı bileşenini yarısı değerle mavi bileşeninin artırılır dönüştürme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d1a51-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="d1a51-105">Bu tür bir dönüşüm altında rengi (0.2, 0,5, 1) duruma (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="d1a51-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="d1a51-106">Yeni kırmızı 0.2 bileşendir + (1/2)(1) 0,7 =.</span><span class="sxs-lookup"><span data-stu-id="d1a51-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1a51-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1a51-107">Example</span></span>  
 <span data-ttu-id="d1a51-108">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars4.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d1a51-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="d1a51-109">Ardından kod görüntüdeki her piksel önceki paragrafta açıklanan kesme dönüştürmesi uygular.</span><span class="sxs-lookup"><span data-stu-id="d1a51-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="d1a51-110">Aşağıdaki çizimde özgün resim soldaki ve yamultulmuş görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1a51-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="d1a51-111">![Renkleri bükme](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="d1a51-111">![Shear Colors](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="d1a51-112">Aşağıdaki tabloda, önce ve sonra kesme dönüştürme dört Çubuklar için renk vektörlerinin listeler.</span><span class="sxs-lookup"><span data-stu-id="d1a51-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="d1a51-113">Özgün</span><span class="sxs-lookup"><span data-stu-id="d1a51-113">Original</span></span>|<span data-ttu-id="d1a51-114">Yamultulmuş</span><span class="sxs-lookup"><span data-stu-id="d1a51-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="d1a51-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="d1a51-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="d1a51-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="d1a51-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="d1a51-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="d1a51-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="d1a51-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="d1a51-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="d1a51-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1a51-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d1a51-123">Compiling the Code</span></span>  
 <span data-ttu-id="d1a51-124">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d1a51-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="d1a51-125">Değiştir `ColorBars.bmp` bir görüntü adı ve yolu, sisteminizde geçerli.</span><span class="sxs-lookup"><span data-stu-id="d1a51-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a51-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1a51-126">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="d1a51-127">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="d1a51-127">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="d1a51-128">Görüntüleri yeniden renklendirme</span><span class="sxs-lookup"><span data-stu-id="d1a51-128">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
