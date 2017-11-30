---
title: "Dönüşümlerin Matrisle Temsili"
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
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10babac22fd94bd00b14b7f861fe99469d3ecbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="matrix-representation-of-transformations"></a><span data-ttu-id="1e202-102">Dönüşümlerin Matrisle Temsili</span><span class="sxs-lookup"><span data-stu-id="1e202-102">Matrix Representation of Transformations</span></span>
<span data-ttu-id="1e202-103">Bir m × n matris m satır ve n sütunlarda düzenlenmiş numaraları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="1e202-103">An m×n matrix is a set of numbers arranged in m rows and n columns.</span></span> <span data-ttu-id="1e202-104">Aşağıda birkaç matrisleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e202-104">The following illustration shows several matrices.</span></span>  
  
 <span data-ttu-id="1e202-105">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")</span><span class="sxs-lookup"><span data-stu-id="1e202-105">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")</span></span>  
  
 <span data-ttu-id="1e202-106">Ayrı ayrı öğeler ekleyerek aynı boyutta iki matrisi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e202-106">You can add two matrices of the same size by adding individual elements.</span></span> <span data-ttu-id="1e202-107">Matris toplama iki örnekleri aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e202-107">The following illustration shows two examples of matrix addition.</span></span>  
  
 <span data-ttu-id="1e202-108">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")</span><span class="sxs-lookup"><span data-stu-id="1e202-108">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")</span></span>  
  
 <span data-ttu-id="1e202-109">Bir m × n matris n × p matris tarafından çarpılacağı ve m × p matris sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1e202-109">An m×n matrix can be multiplied by an n×p matrix, and the result is an m×p matrix.</span></span> <span data-ttu-id="1e202-110">İlk Matristeki sütun sayısı ikinci matrisin satır sayısı ile aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e202-110">The number of columns in the first matrix must be the same as the number of rows in the second matrix.</span></span> <span data-ttu-id="1e202-111">Örneğin, bir 4 × 2 matris 4 × 3 matris üretmek için 2 bir × 3 matris tarafından çarpılan.</span><span class="sxs-lookup"><span data-stu-id="1e202-111">For example, a 4×2 matrix can be multiplied by a 2×3 matrix to produce a 4×3 matrix.</span></span>  
  
 <span data-ttu-id="1e202-112">Düzlemi ve satırları ve sütunları matrisin noktaları, vektörleri olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="1e202-112">Points in the plane and rows and columns of a matrix can be thought of as vectors.</span></span> <span data-ttu-id="1e202-113">Örneğin, (2, 5) olan bir vektör iki bileşenlerle ve (3, 7, 1) üç bileşenlerle vektör.</span><span class="sxs-lookup"><span data-stu-id="1e202-113">For example, (2, 5) is a vector with two components, and (3, 7, 1) is a vector with three components.</span></span> <span data-ttu-id="1e202-114">İki vektör nokta çarpımını şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="1e202-114">The dot product of two vectors is defined as follows:</span></span>  
  
 <span data-ttu-id="1e202-115">(a, b) • (c d) = ac + bd</span><span class="sxs-lookup"><span data-stu-id="1e202-115">(a, b) • (c, d) = ac + bd</span></span>  
  
 <span data-ttu-id="1e202-116">(a, b, c) • (d, e, f) ad = + olması + cf</span><span class="sxs-lookup"><span data-stu-id="1e202-116">(a, b, c) • (d, e, f) = ad + be + cf</span></span>  
  
 <span data-ttu-id="1e202-117">Örneğin, nokta çarpımını (2, 3) ve (5, 4) olan (2)(5) + (3)(4) = 22.</span><span class="sxs-lookup"><span data-stu-id="1e202-117">For example, the dot product of (2, 3) and (5, 4) is (2)(5) + (3)(4) = 22.</span></span> <span data-ttu-id="1e202-118">Nokta ürün (2, 5, 1) ve (4, 3, 1) olan (2)(4) + (5)(3) + (1)(1) = 24.</span><span class="sxs-lookup"><span data-stu-id="1e202-118">The dot product of (2, 5, 1) and (4, 3, 1) is (2)(4) + (5)(3) + (1)(1) = 24.</span></span> <span data-ttu-id="1e202-119">İki vektör nokta çarpımını bir sayı değil başka bir vektör olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1e202-119">Note that the dot product of two vectors is a number, not another vector.</span></span> <span data-ttu-id="1e202-120">Ayrıca, yalnızca iki vektörü bileşenleri aynı sayıda varsa nokta ürün hesaplayabilirsiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1e202-120">Also note that you can calculate the dot product only if the two vectors have the same number of components.</span></span>  
  
 <span data-ttu-id="1e202-121">Let A(i, j) i satır ve jth sütunda bir matris girişi olması.</span><span class="sxs-lookup"><span data-stu-id="1e202-121">Let A(i, j) be the entry in matrix A in the ith row and the jth column.</span></span> <span data-ttu-id="1e202-122">Örneğin bir (3, 2) 3 satır ve 2 sütun A Matristeki giriştir.</span><span class="sxs-lookup"><span data-stu-id="1e202-122">For example A(3, 2) is the entry in matrix A in the 3rd row and the 2nd column.</span></span> <span data-ttu-id="1e202-123">A, B ve C matrisleri ve AB olan varsayalım c = C girişlerinin şöyle hesaplanmıştır:</span><span class="sxs-lookup"><span data-stu-id="1e202-123">Suppose A, B, and C are matrices, and AB = C. The entries of C are calculated as follows:</span></span>  
  
 <span data-ttu-id="1e202-124">C (i, j) = (satır i a) • (sütun j b)</span><span class="sxs-lookup"><span data-stu-id="1e202-124">C(i, j) = (row i of A) • (column j of B)</span></span>  
  
 <span data-ttu-id="1e202-125">Matris çarpım bazı örnekleri aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e202-125">The following illustration shows several examples of matrix multiplication.</span></span>  
  
 <span data-ttu-id="1e202-126">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")</span><span class="sxs-lookup"><span data-stu-id="1e202-126">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")</span></span>  
  
 <span data-ttu-id="1e202-127">1 matris × 2 düzlemi bir noktanın düşünüyorsanız, bu noktadan 2 × 2 matris tarafından çarparak dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e202-127">If you think of a point in a plane as a 1×2 matrix, you can transform that point by multiplying it by a 2×2 matrix.</span></span> <span data-ttu-id="1e202-128">Aşağıdaki çizimde, (2, 1) noktasına uygulanan birkaç dönüşümler gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e202-128">The following illustration shows several transformations applied to the point (2, 1).</span></span>  
  
 <span data-ttu-id="1e202-129">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")</span><span class="sxs-lookup"><span data-stu-id="1e202-129">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")</span></span>  
  
 <span data-ttu-id="1e202-130">Yukarıdaki şekilde gösterildiği dönüşümleri doğrusal dönüşümler tümü.</span><span class="sxs-lookup"><span data-stu-id="1e202-130">All of the transformations shown in the preceding figure are linear transformations.</span></span> <span data-ttu-id="1e202-131">Çeviri gibi diğer bazı dönüşümleri doğrusal değildir ve tarafından 2 × 2 matris çarpım olarak ifade olamaz.</span><span class="sxs-lookup"><span data-stu-id="1e202-131">Certain other transformations, such as translation, are not linear, and cannot be expressed as multiplication by a 2×2 matrix.</span></span> <span data-ttu-id="1e202-132">İstediğiniz varsayalım başlamak noktası (2, 1), 90 derece döndürün, x yönünde 3 birimlerinde Çevir ve y yönünde 4 birimlerinde çevir.</span><span class="sxs-lookup"><span data-stu-id="1e202-132">Suppose you want to start with the point (2, 1), rotate it 90 degrees, translate it 3 units in the x direction, and translate it 4 units in the y direction.</span></span> <span data-ttu-id="1e202-133">Bu, bir matris ekleyerek ve ardından bir matris çarpım kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e202-133">You can accomplish this by using a matrix multiplication followed by a matrix addition.</span></span>  
  
 <span data-ttu-id="1e202-134">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")</span><span class="sxs-lookup"><span data-stu-id="1e202-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")</span></span>  
  
 <span data-ttu-id="1e202-135">Bir çeviri (1 × 2 matris eklenmesi) ve ardından doğrusal dönüştürme (2 × 2 matris tarafından çarpma) bir afin dönüşümü adı verilir.</span><span class="sxs-lookup"><span data-stu-id="1e202-135">A linear transformation (multiplication by a 2×2 matrix) followed by a translation (addition of a 1×2 matrix) is called an affine transformation.</span></span> <span data-ttu-id="1e202-136">Afin bir dönüştürme matrisi (bir doğrusal bölümü için) ve bir çeviri için bir çift depolamak için tüm dönüştürme 3 × 3 matrisinde depolamak için alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="1e202-136">An alternative to storing an affine transformation in a pair of matrices (one for the linear part and one for the translation) is to store the entire transformation in a 3×3 matrix.</span></span> <span data-ttu-id="1e202-137">Bunun çalışmasını sağlamak için düzlemi noktasında kukla 3 koordinat ile 1 × 3 Matristeki depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e202-137">To make this work, a point in the plane must be stored in a 1×3 matrix with a dummy 3rd coordinate.</span></span> <span data-ttu-id="1e202-138">Her zamanki teknik tüm 3 koordinatları 1'e eşit olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1e202-138">The usual technique is to make all 3rd coordinates equal to 1.</span></span> <span data-ttu-id="1e202-139">Örneğin, (2, 1) noktası [2 1 1] matris temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="1e202-139">For example, the point (2, 1) is represented by the matrix [2 1 1].</span></span> <span data-ttu-id="1e202-140">Aşağıdaki çizimde bir afin dönüşümü gösterir (90 derece döndürün; Çevir 3 birimleri x yönünde, y yönünde 4 birimleri) tarafından tek 3 × 3 matris çarpım olarak ifade edilen.</span><span class="sxs-lookup"><span data-stu-id="1e202-140">The following illustration shows an affine transformation (rotate 90 degrees; translate 3 units in the x direction, 4 units in the y direction) expressed as multiplication by a single 3×3 matrix.</span></span>  
  
 <span data-ttu-id="1e202-141">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")</span><span class="sxs-lookup"><span data-stu-id="1e202-141">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")</span></span>  
  
 <span data-ttu-id="1e202-142">Önceki örnekte, (2, 1) noktası (2, 6) noktasına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="1e202-142">In the preceding example, the point (2, 1) is mapped to the point (2, 6).</span></span> <span data-ttu-id="1e202-143">3 × 3 matrisi üçüncü sütun sayıları 0, 0, 1 içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1e202-143">Note that the third column of the 3×3 matrix contains the numbers 0, 0, 1.</span></span> <span data-ttu-id="1e202-144">Bu, her zaman bir afin dönüşümü 3 × 3 matrisin durumunda olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1e202-144">This will always be the case for the 3×3 matrix of an affine transformation.</span></span> <span data-ttu-id="1e202-145">1 ve 2 sütunlardaki altı sayıları önemli numaralarıdır.</span><span class="sxs-lookup"><span data-stu-id="1e202-145">The important numbers are the six numbers in columns 1 and 2.</span></span> <span data-ttu-id="1e202-146">Sol üst 2 × 2 kısmını matris dönüştürme doğrusal bir parçası ve 3 satır ilk iki girdileri çeviri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e202-146">The upper-left 2×2 portion of the matrix represents the linear part of the transformation, and the first two entries in the 3rd row represent the translation.</span></span>  
  
 <span data-ttu-id="1e202-147">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")</span><span class="sxs-lookup"><span data-stu-id="1e202-147">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")</span></span>  
  
 <span data-ttu-id="1e202-148">İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] afin dönüşümünde depolayabilir bir <xref:System.Drawing.Drawing2D.Matrix> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1e202-148">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can store an affine transformation in a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="1e202-149">Afin dönüşüm temsil eden bir matris üçüncü sütun her zaman olduğundan (0, 0, 1), yapısı oluştururken ilk iki sütunu yalnızca altı sayıları belirtmek bir <xref:System.Drawing.Drawing2D.Matrix> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1e202-149">Because the third column of a matrix that represents an affine transformation is always (0, 0, 1), you specify only the six numbers in the first two columns when you construct a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="1e202-150">Deyim `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` Yukarıdaki çizimde gösterilen matris oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e202-150">The statement `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` constructs the matrix shown in the preceding figure.</span></span>  
  
## <a name="composite-transformations"></a><span data-ttu-id="1e202-151">Bileşik dönüşümler</span><span class="sxs-lookup"><span data-stu-id="1e202-151">Composite Transformations</span></span>  
 <span data-ttu-id="1e202-152">Bileşik dönüştürme dönüşümleri, biri tarafından izlenen bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="1e202-152">A composite transformation is a sequence of transformations, one followed by the other.</span></span> <span data-ttu-id="1e202-153">Matrisleri ve aşağıdaki listede dönüştürmeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1e202-153">Consider the matrices and transformations in the following list:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e202-154">Matris A</span><span class="sxs-lookup"><span data-stu-id="1e202-154">Matrix A</span></span>|<span data-ttu-id="1e202-155">90 derece döndürün</span><span class="sxs-lookup"><span data-stu-id="1e202-155">Rotate 90 degrees</span></span>|  
|<span data-ttu-id="1e202-156">Matris B</span><span class="sxs-lookup"><span data-stu-id="1e202-156">Matrix B</span></span>|<span data-ttu-id="1e202-157">2 x yönünde faktörüyle ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="1e202-157">Scale by a factor of 2 in the x direction</span></span>|  
|<span data-ttu-id="1e202-158">Matris C</span><span class="sxs-lookup"><span data-stu-id="1e202-158">Matrix C</span></span>|<span data-ttu-id="1e202-159">Y yönünde 3 birimlerinde Çevir</span><span class="sxs-lookup"><span data-stu-id="1e202-159">Translate 3 units in the y direction</span></span>|  
  
 <span data-ttu-id="1e202-160">Biz noktası (2, 1) ile başlatırsanız — [2 1 1] matris tarafından temsil edilen — ve C, listelenen sırayla üç Dönüşümleri (2, 1) noktası yapılacaktır sonra A, ardından B tarafından çarpın.</span><span class="sxs-lookup"><span data-stu-id="1e202-160">If we start with the point (2, 1) — represented by the matrix [2 1 1] — and multiply by A, then B, then C, the point (2, 1) will undergo the three transformations in the order listed.</span></span>  
  
 <span data-ttu-id="1e202-161">[2 1 1] ABC = [-2, 5, 1]</span><span class="sxs-lookup"><span data-stu-id="1e202-161">[2 1 1]ABC = [-2 5 1]</span></span>  
  
 <span data-ttu-id="1e202-162">Bunun yerine bileşik dönüştürme üç bölümden içinde üç ayrı matrisleri depoladığınızdan, A çarpabilirsiniz B ve C birlikte tüm bileşik dönüştürme depolar tek bir 3 × 3 matris alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="1e202-162">Rather than store the three parts of the composite transformation in three separate matrices, you can multiply A, B, and C together to get a single 3×3 matrix that stores the entire composite transformation.</span></span> <span data-ttu-id="1e202-163">ABC varsayalım D. = Ardından D çarpılan bir noktası A, ardından B, ardından C. çarpılan noktası aynı sonucu verir</span><span class="sxs-lookup"><span data-stu-id="1e202-163">Suppose ABC = D. Then a point multiplied by D gives the same result as a point multiplied by A, then B, then C.</span></span>  
  
 <span data-ttu-id="1e202-164">[2 1 1] D = [-2, 5, 1]</span><span class="sxs-lookup"><span data-stu-id="1e202-164">[2 1 1]D = [-2 5 1]</span></span>  
  
 <span data-ttu-id="1e202-165">Aşağıdaki çizimde A, B, C ve D. matrisleri gösterir</span><span class="sxs-lookup"><span data-stu-id="1e202-165">The following illustration shows the matrices A, B, C, and D.</span></span>  
  
 <span data-ttu-id="1e202-166">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")</span><span class="sxs-lookup"><span data-stu-id="1e202-166">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")</span></span>  
  
 <span data-ttu-id="1e202-167">Afin dönüşümler herhangi bir dizi tek bir depolanabilir bileşik bir dönüştürme matrisi tek tek Dönüştürme Matrislerini çarparak oluşturulmuş olduğunu olgu anlamına gelir <xref:System.Drawing.Drawing2D.Matrix> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1e202-167">The fact that the matrix of a composite transformation can be formed by multiplying the individual transformation matrices means that any sequence of affine transformations can be stored in a single <xref:System.Drawing.Drawing2D.Matrix> object.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1e202-168">Bileşik dönüştürme sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1e202-168">The order of a composite transformation is important.</span></span> <span data-ttu-id="1e202-169">Genel olarak, döndürme, Ölçek, sonra aynı olan Çevir ölçek olarak döndürme, sonra çevir.</span><span class="sxs-lookup"><span data-stu-id="1e202-169">In general, rotate, then scale, then translate is not the same as scale, then rotate, then translate.</span></span> <span data-ttu-id="1e202-170">Benzer şekilde, matris çarpım sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1e202-170">Similarly, the order of matrix multiplication is important.</span></span> <span data-ttu-id="1e202-171">Genel olarak, ABC İCLOU ile aynı değil.</span><span class="sxs-lookup"><span data-stu-id="1e202-171">In general, ABC is not the same as BAC.</span></span>  
  
 <span data-ttu-id="1e202-172"><xref:System.Drawing.Drawing2D.Matrix> Sınıfı, bileşik bir dönüşüm oluşturmaya yönelik birkaç yöntem sağlar: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, ve <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e202-172">The <xref:System.Drawing.Drawing2D.Matrix> class provides several methods for building a composite transformation: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, and <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>.</span></span> <span data-ttu-id="1e202-173">Aşağıdaki örnek, ilk 30 derece döner sonra 2. y yönünde faktörüyle ölçeklendirir ve 5 birim x yönünde çevirir bileşik bir dönüştürme matrisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1e202-173">The following example creates the matrix of a composite transformation that first rotates 30 degrees, then scales by a factor of 2 in the y direction, and then translates 5 units in the x direction:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 <span data-ttu-id="1e202-174">Aşağıdaki çizimde matrisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e202-174">The following illustration shows the matrix.</span></span>  
  
 <span data-ttu-id="1e202-175">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")</span><span class="sxs-lookup"><span data-stu-id="1e202-175">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e202-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e202-176">See Also</span></span>  
 [<span data-ttu-id="1e202-177">Koordinat sistemleri ve dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="1e202-177">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="1e202-178">Yönetilen GDI +'da dönüştürmeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="1e202-178">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
