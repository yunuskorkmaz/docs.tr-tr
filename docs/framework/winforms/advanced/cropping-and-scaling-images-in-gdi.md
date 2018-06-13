---
title: GDI+'da Görüntü Kırpma ve Ölçeklendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: 84e2e74e71c13593cb013849c07a6e904a4d2c14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521560"
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="4a0db-102">GDI+'da Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="4a0db-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="4a0db-103">Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> sınıf çizme ve vektör görüntüler ve ızgara görüntüleri getirin.</span><span class="sxs-lookup"><span data-stu-id="4a0db-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="4a0db-104"><xref:System.Drawing.Graphics.DrawImage%2A> bağımsız değişkenlerle tedarik çeşitli yollardan şekilde bir aşırı yüklenmiş yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="4a0db-105">DrawImage farklılıkları</span><span class="sxs-lookup"><span data-stu-id="4a0db-105">DrawImage Variations</span></span>  
 <span data-ttu-id="4a0db-106">Bir çeşitlemesi <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi alır bir <xref:System.Drawing.Bitmap> ve <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="4a0db-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="4a0db-107">Dikdörtgen çizme işleminin hedefi belirtir; diğer bir deyişle, resim çizmek dikdörtgen belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="4a0db-108">Hedef dikdörtgen boyutu özgün görüntüsüne boyutundan farklı ise, görüntüyü hedef dikdörtgen uyacak şekilde ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="4a0db-109">Aşağıdaki kod örneğinde, üç kez aynı resim çizmek gösterilmiştir: hiçbir ölçeklendirme ile bir kez, bir genişletme ile bir kez ve bir sıkıştırma ile bir kez:</span><span class="sxs-lookup"><span data-stu-id="4a0db-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="4a0db-110">Aşağıdaki çizim üç resim göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="4a0db-111">![Ölçeklendirme](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="4a0db-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="4a0db-112">Bazı varyasyonları <xref:System.Drawing.Graphics.DrawImage%2A> yöntemine sahip bir hedef dikdörtgen parametre yanı sıra, bir kaynak dikdörtgen parametre.</span><span class="sxs-lookup"><span data-stu-id="4a0db-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="4a0db-113">Kaynak dikdörtgen parametre çizmek için özgün görüntüsüne kısmını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="4a0db-114">Hedef dikdörtgen, söz konusu bölümü görüntünün çizmek dikdörtgen belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="4a0db-115">Hedef dikdörtgen boyutu kaynak dikdörtgen boyutundan farklı ise, resmi hedef dikdörtgen uyacak şekilde ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="4a0db-116">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösteren bir <xref:System.Drawing.Bitmap> Runner.jpg dosyasından.</span><span class="sxs-lookup"><span data-stu-id="4a0db-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="4a0db-117">Görüntünün tümünü hiçbir adresindeki ölçeklendirme ile çizilir (0, 0).</span><span class="sxs-lookup"><span data-stu-id="4a0db-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="4a0db-118">Görüntünün küçük bir kısmı iki kez çizilir sonra: bir kez bir sıkıştırma ile bir kez bir genişletme.</span><span class="sxs-lookup"><span data-stu-id="4a0db-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="4a0db-119">Aşağıdaki çizimde ölçeklendirilmemiş resim ve sıkıştırılmış ve genişletilmiş görüntü bölümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a0db-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="4a0db-120">![Kırpma ve ölçeklendirme](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="4a0db-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0db-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a0db-121">See Also</span></span>  
 [<span data-ttu-id="4a0db-122">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4a0db-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="4a0db-123">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="4a0db-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
