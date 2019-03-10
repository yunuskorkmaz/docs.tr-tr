---
title: 'Nasıl yapılır: Renkleri bükme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: eff468e5761038723e16eddf84bdcf8849ac30d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720231"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="dc449-102">Nasıl yapılır: Renkleri bükme</span><span class="sxs-lookup"><span data-stu-id="dc449-102">How to: Shear Colors</span></span>
<span data-ttu-id="dc449-103">Yamultma artırır veya bir renk bileşeni için başka bir renk bileşeni orantılı bir miktar azaltır.</span><span class="sxs-lookup"><span data-stu-id="dc449-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="dc449-104">Örneğin, kırmızı bileşeni mavi bileşeni değeriyle yarısı burada artırılır dönüştürmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="dc449-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="dc449-105">Bu tür bir dönüştürme altında (0.2, 0,5, 1) rengi (0,7, 0,5, 1) olacak.</span><span class="sxs-lookup"><span data-stu-id="dc449-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="dc449-106">Yeni kırmızı 0.2 bileşendir + (1/2)(1) 0,7 =.</span><span class="sxs-lookup"><span data-stu-id="dc449-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc449-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc449-107">Example</span></span>  
 <span data-ttu-id="dc449-108">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars4.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="dc449-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="dc449-109">Ardından kod, resimdeki her piksele önceki paragrafta açıklanan kesme dönüşümü uygular.</span><span class="sxs-lookup"><span data-stu-id="dc449-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="dc449-110">Aşağıdaki çizimde, sol taraftaki özgün görüntü ve yamultulmuş görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc449-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="dc449-111">![Renkleri bükme](./media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="dc449-111">![Shear Colors](./media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="dc449-112">Aşağıdaki tabloda önceki ve sonraki kesme dönüşümü dört Çubuklar için rengi vektörleri listeler.</span><span class="sxs-lookup"><span data-stu-id="dc449-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="dc449-113">Özgün</span><span class="sxs-lookup"><span data-stu-id="dc449-113">Original</span></span>|<span data-ttu-id="dc449-114">Yamulttuysanız</span><span class="sxs-lookup"><span data-stu-id="dc449-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="dc449-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="dc449-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="dc449-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="dc449-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="dc449-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="dc449-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="dc449-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="dc449-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="dc449-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dc449-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="dc449-123">Compiling the Code</span></span>  
 <span data-ttu-id="dc449-124">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="dc449-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="dc449-125">Değiştirin `ColorBars.bmp` bir görüntü adı ve yolu sisteminize göre geçerli.</span><span class="sxs-lookup"><span data-stu-id="dc449-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc449-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc449-126">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="dc449-127">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="dc449-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="dc449-128">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="dc449-128">Recoloring Images</span></span>](recoloring-images.md)
