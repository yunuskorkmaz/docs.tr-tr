---
title: 'Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 9cff13cabb0cd496ee4e628664e4b92bd9e60808
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063730"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="663fb-102">Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="663fb-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="663fb-103">sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve bu görüntüleri düzenleme için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="663fb-103">provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="663fb-104"><xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> 32 bit bir sayı nesneleri depolamak her piksel rengi: 8 bitlik her kırmızı, yeşil, mavi ve alfa için.</span><span class="sxs-lookup"><span data-stu-id="663fb-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="663fb-105">Her biri dört bileşen, 0 ile hiçbir yoğunluğu ve tam bir yoğunluğu temsil eden 255 temsil eden 0 ile 255 arasında bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="663fb-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="663fb-106">Alfa bileşeni rengini, saydamlığını belirtir: 0 tamamen saydamdır ve tam opak 255'tir.</span><span class="sxs-lookup"><span data-stu-id="663fb-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="663fb-107">4 bölütlü (kırmızı, yeşil, mavi, alfa) biçiminde bir renk vektördür.</span><span class="sxs-lookup"><span data-stu-id="663fb-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="663fb-108">Örneğin, (0, 255, 0, 255) renk vektör kırmızı veya mavi olmayan, ancak tam yoğunlukta yeşil sahip donuk bir rengi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="663fb-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="663fb-109">Renkleri temsil eden başka bir kural 1 sayısı için tam yoğunluğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="663fb-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="663fb-110">Bu kuralı kullanarak, önceki paragrafta açıklanan rengi (0, 1, 0, 1) vektörü ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="663fb-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="663fb-111">renk dönüştürmeleri gerçekleştirdiğinde kuralı 1 tam yoğunluğu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="663fb-111">uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="663fb-112">Renk vektör 4 x 4 matris tarafından çarpılarak renk vektörlerinin doğrusal Dönüşümler (döndürme, ölçeklendirme ve benzeri) uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="663fb-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="663fb-113">Ancak, bir çeviri (doğrusal) gerçekleştirmek için 4 x 4 matris kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="663fb-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="663fb-114">İşlevsiz beşinci koordinat (örneğin, 1 sayı) her renk vektörleri eklerseniz, herhangi bir birleşimini doğrusal dönüşümler ve çevirileri uygulamak için 5 × 5 matris kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="663fb-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="663fb-115">Bir çeviri tarafından izlenen bir doğrusal dönüştürme oluşan bir dönüştürme afin bir dönüştürme çağrılır.</span><span class="sxs-lookup"><span data-stu-id="663fb-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="663fb-116">Örneğin, rengi (0.2, 0.0, 0.4, 1.0) ile başlatın ve aşağıdaki dönüştürmeleri istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="663fb-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1. <span data-ttu-id="663fb-117">Çift kırmızı bileşeni</span><span class="sxs-lookup"><span data-stu-id="663fb-117">Double the red component</span></span>  
  
2. <span data-ttu-id="663fb-118">0,2 kırmızı, yeşil ve mavi bileşenlere ekleme</span><span class="sxs-lookup"><span data-stu-id="663fb-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="663fb-119">Aşağıdaki matris çarpım dönüşümleri çiftinin listelenen sırayla gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="663fb-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 ![Bir dönüştürme çarpma matrisi ekran görüntüsü.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/multiplication-color-matrix.gif)
  
 <span data-ttu-id="663fb-121">Renk Matrisi öğelerini (sıfır tabanlı) satır ve ardından sütun tarafından dizine eklenir.</span><span class="sxs-lookup"><span data-stu-id="663fb-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="663fb-122">Örneğin, üçüncü sütunda matris M ve beşinci satır girişi M [4] [2] belirtilir.</span><span class="sxs-lookup"><span data-stu-id="663fb-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="663fb-123">5 × 5 kimlik matrisi (aşağıda gösterilmiştir) üzerinde çapraz 1s ve her yerde başka 0s sahiptir.</span><span class="sxs-lookup"><span data-stu-id="663fb-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="663fb-124">Bir renk vektör tarafından kimlik matrisi çarpın, renk vektör değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="663fb-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="663fb-125">Bir renk dönüştürme matrisini oluşturmak için bir kimlik matris başlatmak ve istenen dönüşümü üretir küçük bir değişiklik yapmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="663fb-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 ![5 x 5 kimlik matrisi renk dönüştürme için ekran görüntüsü.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/5x5-identity-matrix-color-transformation.gif)  
  
 <span data-ttu-id="663fb-127">Matrisler ve dönüşümleri daha ayrıntılı bir açıklaması için bkz. [koordinat sistemleri ve dönüştürmeler](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="663fb-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="663fb-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="663fb-128">Example</span></span>  
 <span data-ttu-id="663fb-129">Aşağıdaki örnek, tüm bir renk (0.2, 0.0, 0.4, 1.0) ve önceki paragrafta açıklanan dönüştürme geçerli bir görüntüsünü alır.</span><span class="sxs-lookup"><span data-stu-id="663fb-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="663fb-130">Aşağıdaki çizimde, sol taraftaki özgün görüntü ve dönüştürülen görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="663fb-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 ![Sol ve sağ taraftaki Fuşya kare mor bir kare.](./media/how-to-use-a-color-matrix-to-transform-a-single-color/color-transformation.png)  
  
 <span data-ttu-id="663fb-132">Aşağıdaki örnek kodda, yeniden renklendirme gerçekleştirmek için aşağıdaki adımları kullanır:</span><span class="sxs-lookup"><span data-stu-id="663fb-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1. <span data-ttu-id="663fb-133">Başlatma bir <xref:System.Drawing.Imaging.ColorMatrix> nesne.</span><span class="sxs-lookup"><span data-stu-id="663fb-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2. <span data-ttu-id="663fb-134">Oluşturma bir <xref:System.Drawing.Imaging.ImageAttributes> nesne ve geçirin <xref:System.Drawing.Imaging.ColorMatrix> nesnesini <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesne.</span><span class="sxs-lookup"><span data-stu-id="663fb-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3. <span data-ttu-id="663fb-135">Geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="663fb-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="663fb-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="663fb-136">Compiling the Code</span></span>  
 <span data-ttu-id="663fb-137">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="663fb-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663fb-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="663fb-138">See also</span></span>

- [<span data-ttu-id="663fb-139">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="663fb-139">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="663fb-140">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="663fb-140">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
