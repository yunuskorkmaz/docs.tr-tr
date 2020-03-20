---
title: 'Nasıl yapılır: Renkleri Bükme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142400"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="35dd4-102">Nasıl yapılır: Renkleri Bükme</span><span class="sxs-lookup"><span data-stu-id="35dd4-102">How to: Shear Colors</span></span>
<span data-ttu-id="35dd4-103">Yamultma, bir renk bileşenini başka bir renk bileşeniyle orantılı bir miktar artırır veya azaltır.</span><span class="sxs-lookup"><span data-stu-id="35dd4-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="35dd4-104">Örneğin, kırmızı bileşenin mavi bileşenin yarısı kadar artırıldığı dönüşümü göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="35dd4-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="35dd4-105">Böyle bir dönüşüm altında renk (0.2, 0.5, 1) (0.7, 0.5, 1) olur.</span><span class="sxs-lookup"><span data-stu-id="35dd4-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="35dd4-106">Yeni kırmızı bileşen 0,2 + (1/2)(1) = 0,7'dir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35dd4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="35dd4-107">Example</span></span>  
 <span data-ttu-id="35dd4-108">Aşağıdaki örnek, ColorBars4.bmp dosyasından bir <xref:System.Drawing.Image> nesne oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="35dd4-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="35dd4-109">Ardından kod, önceki paragrafta açıklanan kesme dönüşümünü görüntüdeki her piksele uygular.</span><span class="sxs-lookup"><span data-stu-id="35dd4-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="35dd4-110">Aşağıdaki resimde soldaki orijinal görüntü ve sağdaki yıkıntılmış görüntü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="35dd4-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span>
  
 ![Orijinal görüntüyü ve yıyıkgörüntüyü gösteren renkli çizgili iki kare yan yana.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="35dd4-112">Aşağıdaki tabloda, kesme dönüşümünden önce ve sonra dört çubuk için renk vektörleri listelenir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="35dd4-113">Özgün</span><span class="sxs-lookup"><span data-stu-id="35dd4-113">Original</span></span>|<span data-ttu-id="35dd4-114">Sheared</span><span class="sxs-lookup"><span data-stu-id="35dd4-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="35dd4-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="35dd4-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="35dd4-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="35dd4-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="35dd4-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="35dd4-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="35dd4-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="35dd4-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="35dd4-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35dd4-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="35dd4-123">Compiling the Code</span></span>  
 <span data-ttu-id="35dd4-124">Önceki örnek, Windows Formları ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan , gerektirir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="35dd4-125">Sisteminizde geçerli bir görüntü adı ve yol ile değiştirin. `ColorBars.bmp`</span><span class="sxs-lookup"><span data-stu-id="35dd4-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35dd4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35dd4-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="35dd4-127">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="35dd4-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="35dd4-128">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="35dd4-128">Recoloring Images</span></span>](recoloring-images.md)
