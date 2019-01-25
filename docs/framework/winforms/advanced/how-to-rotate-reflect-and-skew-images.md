---
title: 'Nasıl yapılır: Döndürme, yansıtma ve eğme görüntüleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 2150e7797095b88227b499ec5481a3ce521270e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667917"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="13652-102">Nasıl yapılır: Döndürme, yansıtma ve eğme görüntüleri</span><span class="sxs-lookup"><span data-stu-id="13652-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="13652-103">Döndürme, yansıtma ve özgün resmin sol, sağ ve sol alt köşeler için hedef noktaları belirleyerek görüntü eğme.</span><span class="sxs-lookup"><span data-stu-id="13652-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="13652-104">Üç hedef noktaları özgün dikdörtgen görüntü için bir eğdiğinizde Paralel Kenar eşleyen bir ilişkili dönüşümü belirler.</span><span class="sxs-lookup"><span data-stu-id="13652-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13652-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="13652-105">Example</span></span>  
 <span data-ttu-id="13652-106">Örneğin, özgün resmin sol üst köşesinde bir dikdörtgen olduğunu varsayın (0, 0), sağ üst köşede (100, 0) ve sol alt köşede (0, 50).</span><span class="sxs-lookup"><span data-stu-id="13652-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="13652-107">Bu harita varsayalım artık üç hedef noktalarına gibi işaret eder.</span><span class="sxs-lookup"><span data-stu-id="13652-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="13652-108">Özgün noktası</span><span class="sxs-lookup"><span data-stu-id="13652-108">Original point</span></span>|<span data-ttu-id="13652-109">Hedef noktası</span><span class="sxs-lookup"><span data-stu-id="13652-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="13652-110">Sol (0, 0)</span><span class="sxs-lookup"><span data-stu-id="13652-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="13652-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="13652-111">(200, 20)</span></span>|  
|<span data-ttu-id="13652-112">Sağ üst köşede (100, 0)</span><span class="sxs-lookup"><span data-stu-id="13652-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="13652-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="13652-113">(110, 100)</span></span>|  
|<span data-ttu-id="13652-114">Sol (0, 50)</span><span class="sxs-lookup"><span data-stu-id="13652-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="13652-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="13652-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="13652-116">Aşağıdaki çizimde, özgün resmin ve için eğdiğinizde Paralel Kenar eşlenen görüntüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="13652-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="13652-117">Özgün resmin dengesiz, yansıtılan, döndürülen, çevrilmiş ve.</span><span class="sxs-lookup"><span data-stu-id="13652-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="13652-118">X ekseni orijinal görüntünün üst kenarı boyunca çalıştırılma satıra eşlendi (200, 20) ve (110, 100).</span><span class="sxs-lookup"><span data-stu-id="13652-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="13652-119">Y ekseni özgün resmin sol kenarda çalıştırılma satıra eşlendi (200, 20) ve (250, 30).</span><span class="sxs-lookup"><span data-stu-id="13652-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="13652-120">![Şeritler](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="13652-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="13652-121">Aşağıdaki çizimde, bir fotoğraf görüntüsüne uygulanacağı benzer bir dönüştürmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="13652-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="13652-122">![Dönüştürülen Tırmanıcı](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="13652-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="13652-123">Aşağıdaki çizim, meta dosyası için uygulanan benzer bir dönüştürmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="13652-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="13652-124">![Dönüştürülmüş meta](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="13652-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="13652-125">Aşağıdaki örnek ilk çizimde gösterilen görüntüleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13652-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13652-126">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="13652-126">Compiling the Code</span></span>  
 <span data-ttu-id="13652-127">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="13652-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="13652-128">Değiştirdiğinizden emin olun `Stripes.bmp` yoluyla sisteminize göre geçerli bir görüntü.</span><span class="sxs-lookup"><span data-stu-id="13652-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13652-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13652-129">See also</span></span>
- [<span data-ttu-id="13652-130">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="13652-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
