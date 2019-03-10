---
title: 'Nasıl yapılır: Renkleri döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: cb3824d8a5a5674b83124301dbfbd5a3ba60effa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720624"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="5f119-102">Nasıl yapılır: Renkleri döndürme</span><span class="sxs-lookup"><span data-stu-id="5f119-102">How to: Rotate Colors</span></span>
<span data-ttu-id="5f119-103">Four-dimensional renk alanı dönüş görselleştirmek zordur.</span><span class="sxs-lookup"><span data-stu-id="5f119-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="5f119-104">Biz, renk bileşenlerinden sabit tutmak kabul ederek döndürme görselleştirmek kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="5f119-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="5f119-105">1 sabit alfa bileşeni (tam opak) tutun kabul varsayalım.</span><span class="sxs-lookup"><span data-stu-id="5f119-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="5f119-106">Ardından şu üç boyutlu renk alanı kırmızı, yeşil ve mavi eksenli aşağıdaki çizimde gösterildiği gibi görselleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f119-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="5f119-107">![Yeniden renklendirme](./media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="5f119-107">![Recoloring](./media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="5f119-108">Bir renk, 3B nokta olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="5f119-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="5f119-109">Örneğin, kırmızı renk alanı noktasında (1, 0, 0) temsil eder ve yeşil renk alanı noktasında (0, 1, 0) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f119-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="5f119-110">Aşağıdaki çizimde, kırmızı-yeşil masasında 60 derecenin açı aracılığıyla rengi (1, 0, 0) döndürme ne demek gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f119-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="5f119-111">Döndürme düzlemin paralel kırmızı-yeşil düzlemine, döndürme ise mavi eksen olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="5f119-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="5f119-112">![Yeniden renklendirme](./media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="5f119-112">![Recoloring](./media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="5f119-113">Aşağıdaki çizimde, her üç koordinat ekseni (kırmızı, yeşil, mavi) hakkında dönüşümüne gerçekleştirmek için renk matrisi başlatmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5f119-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="5f119-114">![Yeniden renklendirme](./media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="5f119-114">![Recoloring](./media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f119-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f119-115">Example</span></span>  
 <span data-ttu-id="5f119-116">Aşağıdaki örnek, tüm bir renk (1, 0, 0,6) ve mavi eksen hakkında bir 60 derece döndürme uygular bir görüntü alır.</span><span class="sxs-lookup"><span data-stu-id="5f119-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="5f119-117">Döndürme açısı kullanıma kırmızı-yeşil düzlem için paralel bir masasında gözden geçirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5f119-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="5f119-118">Aşağıdaki çizim özgün resmin sol ve sağ taraftaki renk Döndürülmüş görüntü gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f119-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="5f119-119">![Renkleri döndürme](./media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="5f119-119">![Rotate Colors](./media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="5f119-120">Aşağıdaki kodda gerçekleştirilen renk döndürme bir görselleştirme aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5f119-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="5f119-121">![Yeniden renklendirme](./media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="5f119-121">![Recoloring](./media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f119-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5f119-122">Compiling the Code</span></span>  
 <span data-ttu-id="5f119-123">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5f119-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="5f119-124">Değiştirin `RotationInput.bmp` bir resim dosyası adı ve yolu sisteminize göre geçerli.</span><span class="sxs-lookup"><span data-stu-id="5f119-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f119-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f119-125">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="5f119-126">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="5f119-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="5f119-127">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="5f119-127">Recoloring Images</span></span>](recoloring-images.md)
