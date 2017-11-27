---
title: "Nasıl yapılır: Görüntüleri Döndürme, Yansıtma ve Eğme"
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
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaa6286731d196dad387e1648644ca3e8103da03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="bf17d-102">Nasıl yapılır: Görüntüleri Döndürme, Yansıtma ve Eğme</span><span class="sxs-lookup"><span data-stu-id="bf17d-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="bf17d-103">Döndürme, yansıtma ve orijinal görüntünün sol üst, sağ üst ve alt sol köşe için hedef noktalarını belirterek bir görüntü eğme.</span><span class="sxs-lookup"><span data-stu-id="bf17d-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="bf17d-104">Üç hedef noktaları bir paralel kenarı özgün dikdörtgen resmin eşleştirir bir afin dönüşümü belirler.</span><span class="sxs-lookup"><span data-stu-id="bf17d-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf17d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf17d-105">Example</span></span>  
 <span data-ttu-id="bf17d-106">Örneğin, özgün resim sol üst köşede bir dikdörtgen olduğunu varsayın (0, 0), sağ üst köşede (100, 0) ve sol alt köşede (0, 50).</span><span class="sxs-lookup"><span data-stu-id="bf17d-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="bf17d-107">Bu harita varsayalım artık üç hedef noktalarına gibi işaret eder.</span><span class="sxs-lookup"><span data-stu-id="bf17d-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="bf17d-108">Özgün noktası</span><span class="sxs-lookup"><span data-stu-id="bf17d-108">Original point</span></span>|<span data-ttu-id="bf17d-109">Hedef noktası</span><span class="sxs-lookup"><span data-stu-id="bf17d-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="bf17d-110">Sol üst (0, 0)</span><span class="sxs-lookup"><span data-stu-id="bf17d-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="bf17d-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="bf17d-111">(200, 20)</span></span>|  
|<span data-ttu-id="bf17d-112">Sağ üst köşede (100, 0)</span><span class="sxs-lookup"><span data-stu-id="bf17d-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="bf17d-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="bf17d-113">(110, 100)</span></span>|  
|<span data-ttu-id="bf17d-114">Sol alt (0, 50)</span><span class="sxs-lookup"><span data-stu-id="bf17d-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="bf17d-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="bf17d-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="bf17d-116">Aşağıdaki çizimde özgün resim ve paralel kenarı için eşlenen görüntü gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf17d-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="bf17d-117">Özgün görüntüsüne eğri, yansıtılan, döndürülmüş, çevrilen ve kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="bf17d-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="bf17d-118">Özgün görüntünün üst kenarı eksenindeki çalıştıran aracılığıyla bir satıra eşlendi (200, 20) ve (110, 100).</span><span class="sxs-lookup"><span data-stu-id="bf17d-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="bf17d-119">Y ekseni boyunca özgün görüntüsüne sol kenarı çalıştıran aracılığıyla bir satıra eşlendi (200, 20) ve (250, 30).</span><span class="sxs-lookup"><span data-stu-id="bf17d-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="bf17d-120">![Şeritler](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="bf17d-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="bf17d-121">Aşağıdaki çizimde bir fotoğraf görüntüye uygulanan benzer bir dönüşüm gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf17d-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="bf17d-122">![Dönüştürülen Tırmanıcı](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="bf17d-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="bf17d-123">Aşağıdaki çizimde bir meta dosyası uygulanan benzer bir dönüşüm gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf17d-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="bf17d-124">![Dönüştürülen meta dosyası](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="bf17d-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="bf17d-125">Aşağıdaki örnek ilk çizimde gösterilen görüntüleri üretir.</span><span class="sxs-lookup"><span data-stu-id="bf17d-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf17d-126">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bf17d-126">Compiling the Code</span></span>  
 <span data-ttu-id="bf17d-127">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="bf17d-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="bf17d-128">Değiştirdiğinizden emin olun `Stripes.bmp` , sisteminizde geçerli bir görüntü yolu ile.</span><span class="sxs-lookup"><span data-stu-id="bf17d-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf17d-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf17d-129">See Also</span></span>  
 [<span data-ttu-id="bf17d-130">Resimler, bit eşlemler, simgeler ve meta dosyaları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="bf17d-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
