---
title: "Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma"
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
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60da29b60d2b9b5b98c76a0a9c3ae73ac9142bbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="a2ba0-102">Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="a2ba0-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a2ba0-103">sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve görüntüleri düzenleme için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-103"> provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="a2ba0-104"><xref:System.Drawing.Image>ve <xref:System.Drawing.Bitmap> 32 bitlik bir sayı nesneleri depolamak her piksel rengi: 8 bit her kırmızı, yeşil, mavi ve alfa için.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="a2ba0-105">Dört bileşenlerinden her biri, 0-hiçbir yoğunluğu ve tam yoğunluğu temsil eden 255 temsil eden 0 ile 255 arasında bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="a2ba0-106">Renk saydam alfa bileşeni belirtir: 0 tamamen saydamdır ve 255'tir tamamıyla opak.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="a2ba0-107">Bir renk vektör 4 bölütlü (kırmızı, yeşil, mavi, alfa) biçiminde olur.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="a2ba0-108">Örneğin, renk vektör (0, 255, 0, 255) hiçbir kırmızı veya mavi sahiptir, ancak tam yoğunlukta yeşil sahip bir opak rengi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="a2ba0-109">Renkleri temsil etmek için başka bir kuralı 1 numaralı tam yoğunluğu için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="a2ba0-110">Bu kuralı kullanarak, önceki paragrafta açıklanan rengi (0, 1, 0, 1) vektörü ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a2ba0-111">renk dönüştürmeleri gerçekleştirdiğinde kuralı 1 tam yoğunluğu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-111"> uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="a2ba0-112">Doğrusal Dönüşümler (döndürme, ölçeklendirme ve benzeri) 4 × 4 matris tarafından renk vektörlerinin çarparak renk vektörlerinin uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="a2ba0-113">Ancak, bir çeviri (doğrusal) gerçekleştirmek için 4 × 4 matris kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="a2ba0-114">Her renk vektörlerinin kukla beşinci koordinat (örneğin, 1 sayı) eklerseniz, doğrusal dönüşümler ve çevirileri herhangi bir bileşimini uygulamak için 5 × 5 matris kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="a2ba0-115">Bir çeviri tarafından izlenen bir doğrusal dönüştürmesi oluşan bir dönüşüm afin dönüştürme adı verilir.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="a2ba0-116">Örneğin, renk (0.2, 0.0, 0.4, 1.0) başlatın ve aşağıdaki dönüştürmeleri istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="a2ba0-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1.  <span data-ttu-id="a2ba0-117">Çift kırmızı bileşeni</span><span class="sxs-lookup"><span data-stu-id="a2ba0-117">Double the red component</span></span>  
  
2.  <span data-ttu-id="a2ba0-118">Kırmızı, yeşil ve mavi bileşenlere 0.2 ekleme</span><span class="sxs-lookup"><span data-stu-id="a2ba0-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="a2ba0-119">Aşağıdaki matris çarpım dönüşümleri çiftinin listelenen sırayla gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="a2ba0-120">![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="a2ba0-120">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="a2ba0-121">Bir renk matrisi öğelerini (sıfır tabanlı) satır ve ardından sütun tarafından dizinlenir.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="a2ba0-122">Örneğin, beşinci satır ve üçüncü sütun matrisi M girişi M [4] [2] tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="a2ba0-123">5 × 5 kimlik matris (aşağıda gösterilen) 1'ler üzerinde çapraz ve 0'lar her yerde başka sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="a2ba0-124">Bir renk vektör tarafından kimlik matris Çarp, renk vektör değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="a2ba0-125">Bir renk dönüştürme matrisi oluşturmak için bir kimlik matrisi başlatmak ve istenen dönüştürme üreten küçük değişiklikler yapmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="a2ba0-126">![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="a2ba0-126">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="a2ba0-127">Matrisleri ve dönüştürmeler daha ayrıntılı bir tartışma için bkz [koordinat sistemleri ve dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="a2ba0-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2ba0-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2ba0-128">Example</span></span>  
 <span data-ttu-id="a2ba0-129">Aşağıdaki örnek, tüm bir renk (0.2, 0.0, 0.4, 1.0) ve önceki paragrafta açıklanan dönüştürmesi uygular bir görüntüsünü alır.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="a2ba0-130">Aşağıdaki çizimde özgün resim soldaki ve dönüştürülen görüntünün sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="a2ba0-131">![Renkleri](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="a2ba0-131">![Colors](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="a2ba0-132">Aşağıdaki örnek kodda yeniden renklendirme gerçekleştirmek için aşağıdaki adımları kullanır:</span><span class="sxs-lookup"><span data-stu-id="a2ba0-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1.  <span data-ttu-id="a2ba0-133">Başlatma bir <xref:System.Drawing.Imaging.ColorMatrix> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2.  <span data-ttu-id="a2ba0-134">Oluşturma bir <xref:System.Drawing.Imaging.ImageAttributes> nesne ve geçirin <xref:System.Drawing.Imaging.ColorMatrix> nesnesini <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3.  <span data-ttu-id="a2ba0-135">Geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2ba0-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a2ba0-136">Compiling the Code</span></span>  
 <span data-ttu-id="a2ba0-137">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ba0-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ba0-138">See Also</span></span>  
 [<span data-ttu-id="a2ba0-139">Görüntüleri yeniden renklendirme</span><span class="sxs-lookup"><span data-stu-id="a2ba0-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="a2ba0-140">Koordinat sistemleri ve dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="a2ba0-140">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
