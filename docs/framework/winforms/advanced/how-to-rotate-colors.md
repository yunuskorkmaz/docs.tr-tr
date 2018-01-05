---
title: "Nasıl yapılır: Renkleri Döndürme"
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
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81b022011bd5613b8e956aa83482d2836508a4f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="e5802-102">Nasıl yapılır: Renkleri Döndürme</span><span class="sxs-lookup"><span data-stu-id="e5802-102">How to: Rotate Colors</span></span>
<span data-ttu-id="e5802-103">Four-dimensional renk alanını dönüş görselleştirmek zordur.</span><span class="sxs-lookup"><span data-stu-id="e5802-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="e5802-104">Biz, sabit renk bileşenlerden biri tutmak kabul ettiğinizi belirten tarafından döndürme görselleştirmek kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="e5802-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="e5802-105">1'den sabit alfa bileşeni (tamamıyla opak) tutmak kabul varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e5802-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="e5802-106">Sonra şu üç boyutlu renk alanını kırmızı, yeşil ve mavi eksenli aşağıdaki çizimde gösterildiği gibi görselleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5802-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="e5802-107">![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="e5802-107">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="e5802-108">Bir renk, 3B nokta olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="e5802-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="e5802-109">Örneğin, kırmızı renk alanı noktasında (1, 0, 0) gösteren ve noktasını (0, 1, 0) alanı yeşil rengi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5802-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="e5802-110">Aşağıdaki çizimde, 60 derece kırmızı yeşil düzlemi cinsinden açı aracılığıyla renk (1, 0, 0) döndürmek ne anlama geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5802-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="e5802-111">Düzlemi paralel kırmızı yeşil düzlem olarak döndürme, mavi ekseni etrafında döndürme olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="e5802-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="e5802-112">![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="e5802-112">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="e5802-113">Aşağıdaki çizimde, her üç koordinat eksen (kırmızı, yeşil, mavi) hakkında döndürmeleri gerçekleştirmek için renk matrisi başlatmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e5802-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="e5802-114">![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="e5802-114">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5802-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5802-115">Example</span></span>  
 <span data-ttu-id="e5802-116">Aşağıdaki örnek, tüm bir renk (1, 0, 0,6) ve mavi ekseni etrafında 60 derecelik döndürme geçerlidir bir görüntü alır.</span><span class="sxs-lookup"><span data-stu-id="e5802-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="e5802-117">Döndürme açısını çıkışı kırmızı yeşil düzlemi paralel bir düzlem olarak gözden geçirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e5802-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="e5802-118">Aşağıdaki çizimde, sol ve sağ taraftaki renk Döndürülmüş görüntü özgün görüntüsüne gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5802-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="e5802-119">![Renkleri döndürme](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="e5802-119">![Rotate Colors](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="e5802-120">Aşağıdaki kodda gerçekleştirilen renk döndürme görselleştirme aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5802-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="e5802-121">![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="e5802-121">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5802-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e5802-122">Compiling the Code</span></span>  
 <span data-ttu-id="e5802-123">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e5802-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="e5802-124">Değiştir `RotationInput.bmp` bir görüntü dosyası adı ve yolu, sisteminizde geçerli sahip.</span><span class="sxs-lookup"><span data-stu-id="e5802-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5802-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5802-125">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="e5802-126">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="e5802-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="e5802-127">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="e5802-127">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
