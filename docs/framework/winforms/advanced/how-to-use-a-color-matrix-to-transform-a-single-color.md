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
ms.openlocfilehash: 78fc498b0689026fb74ec0c422948c1879495560
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342862"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="7e485-102">Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="7e485-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="7e485-103">sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve bu görüntüleri düzenleme için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="7e485-103">provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <xref:System.Drawing.Image> <span data-ttu-id="7e485-104">ve <xref:System.Drawing.Bitmap> 32 bit bir sayı nesneleri depolamak her piksel rengi: 8 bitlik her kırmızı, yeşil, mavi ve alfa için.</span><span class="sxs-lookup"><span data-stu-id="7e485-104">and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="7e485-105">Her biri dört bileşen, 0 ile hiçbir yoğunluğu ve tam bir yoğunluğu temsil eden 255 temsil eden 0 ile 255 arasında bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="7e485-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="7e485-106">Alfa bileşeni rengini, saydamlığını belirtir: 0 tamamen saydamdır ve tam opak 255'tir.</span><span class="sxs-lookup"><span data-stu-id="7e485-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="7e485-107">4 bölütlü (kırmızı, yeşil, mavi, alfa) biçiminde bir renk vektördür.</span><span class="sxs-lookup"><span data-stu-id="7e485-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="7e485-108">Örneğin, (0, 255, 0, 255) renk vektör kırmızı veya mavi olmayan, ancak tam yoğunlukta yeşil sahip donuk bir rengi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7e485-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="7e485-109">Renkleri temsil eden başka bir kural 1 sayısı için tam yoğunluğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="7e485-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="7e485-110">Bu kuralı kullanarak, önceki paragrafta açıklanan rengi (0, 1, 0, 1) vektörü ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7e485-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="7e485-111">renk dönüştürmeleri gerçekleştirdiğinde kuralı 1 tam yoğunluğu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e485-111">uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="7e485-112">Renk vektör 4 x 4 matris tarafından çarpılarak renk vektörlerinin doğrusal Dönüşümler (döndürme, ölçeklendirme ve benzeri) uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e485-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="7e485-113">Ancak, bir çeviri (doğrusal) gerçekleştirmek için 4 x 4 matris kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7e485-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="7e485-114">İşlevsiz beşinci koordinat (örneğin, 1 sayı) her renk vektörleri eklerseniz, herhangi bir birleşimini doğrusal dönüşümler ve çevirileri uygulamak için 5 × 5 matris kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e485-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="7e485-115">Bir çeviri tarafından izlenen bir doğrusal dönüştürme oluşan bir dönüştürme afin bir dönüştürme çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7e485-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="7e485-116">Örneğin, rengi (0.2, 0.0, 0.4, 1.0) ile başlatın ve aşağıdaki dönüştürmeleri istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="7e485-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1. <span data-ttu-id="7e485-117">Çift kırmızı bileşeni</span><span class="sxs-lookup"><span data-stu-id="7e485-117">Double the red component</span></span>  
  
2. <span data-ttu-id="7e485-118">0,2 kırmızı, yeşil ve mavi bileşenlere ekleme</span><span class="sxs-lookup"><span data-stu-id="7e485-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="7e485-119">Aşağıdaki matris çarpım dönüşümleri çiftinin listelenen sırayla gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7e485-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="7e485-120">![Yeniden renklendirme](./media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="7e485-120">![Recoloring](./media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="7e485-121">Renk Matrisi öğelerini (sıfır tabanlı) satır ve ardından sütun tarafından dizine eklenir.</span><span class="sxs-lookup"><span data-stu-id="7e485-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="7e485-122">Örneğin, üçüncü sütunda matris M ve beşinci satır girişi M [4] [2] belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7e485-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="7e485-123">5 × 5 kimlik matrisi (aşağıda gösterilmiştir) üzerinde çapraz 1s ve her yerde başka 0s sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7e485-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="7e485-124">Bir renk vektör tarafından kimlik matrisi çarpın, renk vektör değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="7e485-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="7e485-125">Bir renk dönüştürme matrisini oluşturmak için bir kimlik matris başlatmak ve istenen dönüşümü üretir küçük bir değişiklik yapmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="7e485-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="7e485-126">![Yeniden renklendirme](./media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="7e485-126">![Recoloring](./media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="7e485-127">Matrisler ve dönüşümleri daha ayrıntılı bir açıklaması için bkz. [koordinat sistemleri ve dönüştürmeler](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="7e485-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e485-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e485-128">Example</span></span>  
 <span data-ttu-id="7e485-129">Aşağıdaki örnek, tüm bir renk (0.2, 0.0, 0.4, 1.0) ve önceki paragrafta açıklanan dönüştürme geçerli bir görüntüsünü alır.</span><span class="sxs-lookup"><span data-stu-id="7e485-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="7e485-130">Aşağıdaki çizimde, sol taraftaki özgün görüntü ve dönüştürülen görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e485-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="7e485-131">![Renkleri](./media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="7e485-131">![Colors](./media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="7e485-132">Aşağıdaki örnek kodda, yeniden renklendirme gerçekleştirmek için aşağıdaki adımları kullanır:</span><span class="sxs-lookup"><span data-stu-id="7e485-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1. <span data-ttu-id="7e485-133">Başlatma bir <xref:System.Drawing.Imaging.ColorMatrix> nesne.</span><span class="sxs-lookup"><span data-stu-id="7e485-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2. <span data-ttu-id="7e485-134">Oluşturma bir <xref:System.Drawing.Imaging.ImageAttributes> nesne ve geçirin <xref:System.Drawing.Imaging.ColorMatrix> nesnesini <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesne.</span><span class="sxs-lookup"><span data-stu-id="7e485-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3. <span data-ttu-id="7e485-135">Geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="7e485-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e485-136">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7e485-136">Compiling the Code</span></span>  
 <span data-ttu-id="7e485-137">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7e485-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e485-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e485-138">See also</span></span>

- [<span data-ttu-id="7e485-139">Resimleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="7e485-139">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="7e485-140">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="7e485-140">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
