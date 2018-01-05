---
title: "Nasıl yapılır: Yeniden Renk Eşleme Tablosu Kullanma"
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e208aa9c98c1ca19baee83760cfd0f75972ecfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="d7509-102">Nasıl yapılır: Yeniden Renk Eşleme Tablosu Kullanma</span><span class="sxs-lookup"><span data-stu-id="d7509-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="d7509-103">Yeniden eşleme yeniden renk eşleme tablosu göre görüntüdeki renkleri dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="d7509-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="d7509-104">Renk eşleme tablosu dizisidir <xref:System.Drawing.Imaging.ColorMap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d7509-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="d7509-105">Her <xref:System.Drawing.Imaging.ColorMap> dizi nesnesi bir <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> özelliği ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d7509-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="d7509-106">Zaman [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizer resim, resmin her piksel bir eski renkleri dizisi karşılaştırılan.</span><span class="sxs-lookup"><span data-stu-id="d7509-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="d7509-107">Bir piksel renk eski bir renk eşleşirse, rengini karşılık gelen yeni renge değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="d7509-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="d7509-108">Renkleri işleme için yalnızca değiştirilen — görüntü renk değerlerini (depolanan bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> nesnesi) değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="d7509-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="d7509-109">Remapped resim çizmek için bir dizi başlatma <xref:System.Drawing.Imaging.ColorMap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d7509-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="d7509-110">Bu diziye geçirmek <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> yöntemi bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesini genişletin ve ardından geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d7509-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7509-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7509-111">Example</span></span>  
 <span data-ttu-id="d7509-112">Aşağıdaki örnekte bir <xref:System.Drawing.Image> RemapInput.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d7509-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="d7509-113">Kod bir tek oluşur yeniden renk eşleme tablosu oluşturur <xref:System.Drawing.Imaging.ColorMap> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d7509-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="d7509-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Özelliği `ColorRemap` nesne kırmızıdır ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliktir mavi.</span><span class="sxs-lookup"><span data-stu-id="d7509-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="d7509-115">Yeniden eşleme ile yeniden eşleme olmadan çizilmiş bir kez de görüntüdür.</span><span class="sxs-lookup"><span data-stu-id="d7509-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="d7509-116">Yeniden eşleme işlemi mavi ve kırmızı tüm pikselleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d7509-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="d7509-117">Aşağıdaki çizimde özgün resim soldaki ve remapped görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7509-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="d7509-118">![Renk eşleme](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="d7509-118">![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7509-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d7509-119">Compiling the Code</span></span>  
 <span data-ttu-id="d7509-120">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d7509-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7509-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7509-121">See Also</span></span>  
 [<span data-ttu-id="d7509-122">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="d7509-122">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="d7509-123">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d7509-123">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
