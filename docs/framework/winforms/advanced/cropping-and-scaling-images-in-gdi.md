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
ms.openlocfilehash: c3cdb06e99770808461f9266fb5f07df9074149b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183735"
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="04c9a-102">GDI+'da Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="04c9a-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="04c9a-103">Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> çizmek ve vektör görüntüleri ve ızgara resimlerin konumlandırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="04c9a-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="04c9a-104"><xref:System.Drawing.Graphics.DrawImage%2A> bağımsız değişkenleriyle sağlayabilirsiniz birkaç yolu olduğundan aşırı yüklü bir yönteminiz var.</span><span class="sxs-lookup"><span data-stu-id="04c9a-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="04c9a-105">DrawImage farklılıkları</span><span class="sxs-lookup"><span data-stu-id="04c9a-105">DrawImage Variations</span></span>  
 <span data-ttu-id="04c9a-106">Bir çeşitlemesi <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi alır bir <xref:System.Drawing.Bitmap> ve <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="04c9a-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="04c9a-107">Dikdörtgen çizme işlemi için hedef belirtir. diğer bir deyişle, hangi görüntü çizme dikdörtgen belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c9a-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="04c9a-108">Hedef dikdörtgenin boyut orijinal görüntünün boyutundan farklıysa, hedef dikdörtgenin sığacak şekilde ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="04c9a-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="04c9a-109">Aşağıdaki kod örneği, üç kez aynı görüntü çizmek gösterilmektedir: hiçbir ölçeklendirme ile bir kez, bir genişletme ile bir kez ve bir sıkıştırma ile bir kez:</span><span class="sxs-lookup"><span data-stu-id="04c9a-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="04c9a-110">Aşağıdaki çizim üç resimleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="04c9a-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="04c9a-111">![Ölçeklendirme](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="04c9a-111">![Scaling](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="04c9a-112">Bazı çeşitleri <xref:System.Drawing.Graphics.DrawImage%2A> yöntemine sahip bir hedef dikdörtgenin parametre yanı sıra kaynak dikdörtgenin parametresi.</span><span class="sxs-lookup"><span data-stu-id="04c9a-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="04c9a-113">Kaynak dikdörtgenin parametresi çizmek için özgün görüntü kısmı belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c9a-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="04c9a-114">Hedef dikdörtgenin kaydedileceği görüntünün kısmı çizmek dikdörtgen belirtir.</span><span class="sxs-lookup"><span data-stu-id="04c9a-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="04c9a-115">Hedef dikdörtgenin boyutu kaynak dikdörtgenin boyutundan farklı ise, resmi hedef dikdörtgenin sığacak şekilde ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="04c9a-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="04c9a-116">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Drawing.Bitmap> Runner.jpg dosyasından.</span><span class="sxs-lookup"><span data-stu-id="04c9a-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="04c9a-117">Ölçeklendirme yok, görüntünün çizilir (0, 0).</span><span class="sxs-lookup"><span data-stu-id="04c9a-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="04c9a-118">Görüntünün küçük bir kısmını iki kez çizilir sonra: bir kez bir sıkıştırma ile bir kez bir genişletme.</span><span class="sxs-lookup"><span data-stu-id="04c9a-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="04c9a-119">Ölçeklendirilmemiş resim ve görüntü sıkıştırılmış ve genişletilmiş bölümleri aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="04c9a-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="04c9a-120">![Kırpma ve ölçeklendirme](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="04c9a-120">![Cropping and Scaling](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c9a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04c9a-121">See also</span></span>

- [<span data-ttu-id="04c9a-122">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="04c9a-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="04c9a-123">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="04c9a-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
