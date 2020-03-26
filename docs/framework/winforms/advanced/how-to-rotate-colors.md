---
title: 'Nasıl yapılır: Renkleri Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111341"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="5cd17-102">Nasıl yapılır: Renkleri Döndürme</span><span class="sxs-lookup"><span data-stu-id="5cd17-102">How to: Rotate Colors</span></span>
<span data-ttu-id="5cd17-103">Dört boyutlu bir renk alanında döndürmeyi görselleştirmek zordur.</span><span class="sxs-lookup"><span data-stu-id="5cd17-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="5cd17-104">Renk bileşenlerinden birini sabit tutmayı kabul ederek döndürmeyi görselleştirmeyi kolaylaştırabiliriz.</span><span class="sxs-lookup"><span data-stu-id="5cd17-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="5cd17-105">Alfa bileşenini 1'de sabit tutmayı kabul ettiğimizi varsayalım (tamamen opak).</span><span class="sxs-lookup"><span data-stu-id="5cd17-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="5cd17-106">Daha sonra aşağıdaki resimde gösterildiği gibi kırmızı, yeşil ve mavi eksenler ile üç boyutlu bir renk alanı görselleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cd17-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![Kırmızı, yeşil ve mavi eksenlerle döndürme yi gösteren çizim.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="5cd17-108">Bir renk 3B alanda bir nokta olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="5cd17-108">A color can be thought of as a point in 3D space.</span></span> <span data-ttu-id="5cd17-109">Örneğin, boşluktaki nokta (1, 0, 0) kırmızı rengi, boşluktaki nokta (0, 1, 0) ise yeşil rengi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5cd17-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="5cd17-110">Aşağıdaki resimde, kırmızı-yeşil düzlemde 60 derecelik bir açı yla renk (1, 0, 0) döndürmek için ne anlama geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cd17-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="5cd17-111">Kırmızı-Yeşil düzleme paralel bir düzlemde dönüş mavi eksen etrafında dönüş olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="5cd17-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![Mavi eksen hakkında döndürme gösteren çizim.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="5cd17-113">Aşağıdaki resimde, üç koordinat ekseninin (kırmızı, yeşil, mavi) her biri hakkında döndürmeler gerçekleştirmek için bir renk matrisinin nasıl başlağize edilebildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5cd17-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![Üç eksen hakkında döndürmeler gerçekleştirmek için bir renk matrisini başlatma.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="5cd17-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cd17-115">Example</span></span>  
 <span data-ttu-id="5cd17-116">Aşağıdaki örnek, tek renk (1, 0, 0,6) olan bir görüntü alır ve mavi eksen hakkında 60 derecelik bir döndürme uygular.</span><span class="sxs-lookup"><span data-stu-id="5cd17-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="5cd17-117">Dönüş açısı kırmızı-yeşil düzleme paralel bir düzlemde süpürülür.</span><span class="sxs-lookup"><span data-stu-id="5cd17-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="5cd17-118">Aşağıdaki resimde soldaki orijinal görüntü ve sağdaki renk döndürülmüş görüntü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5cd17-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![Orijinal görüntüyü ve renk döndürülen görüntüyü gösteren çizim.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="5cd17-120">Aşağıdaki resimde, aşağıdaki kodda gerçekleştirilen renk döndürmenin görselleştirilmesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5cd17-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![Renk döndürmenin görselleştirilmesini gösteren çizim.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cd17-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5cd17-122">Compiling the Code</span></span>  
 <span data-ttu-id="5cd17-123">Önceki örnek, Windows Formları ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan , gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5cd17-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="5cd17-124">Sisteminizde geçerli bir resim dosyası adı ve yolu ile değiştirin. `RotationInput.bmp`</span><span class="sxs-lookup"><span data-stu-id="5cd17-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd17-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cd17-125">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="5cd17-126">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="5cd17-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="5cd17-127">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="5cd17-127">Recoloring Images</span></span>](recoloring-images.md)
