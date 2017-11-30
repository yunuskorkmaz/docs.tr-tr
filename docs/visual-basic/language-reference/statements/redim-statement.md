---
title: ReDim Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cec66ee33bfd82b3abd623a0130f5635aa3d1d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="9288c-102">ReDim Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9288c-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="9288c-103">Depolama alanı için bir dizi değişkeni yeniden ayırır.</span><span class="sxs-lookup"><span data-stu-id="9288c-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9288c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9288c-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9288c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9288c-105">Parts</span></span>  
  
|<span data-ttu-id="9288c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="9288c-106">Term</span></span>|<span data-ttu-id="9288c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="9288c-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="9288c-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9288c-108">Optional.</span></span> <span data-ttu-id="9288c-109">Yalnızca son boyut boyutunu değiştirdiğinizde, var olan dizideki verileri korumak için kullanılan değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="9288c-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="9288c-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9288c-110">Required.</span></span> <span data-ttu-id="9288c-111">Dizi değişkeni adı.</span><span class="sxs-lookup"><span data-stu-id="9288c-111">Name of the array variable.</span></span> <span data-ttu-id="9288c-112">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9288c-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="9288c-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9288c-113">Required.</span></span> <span data-ttu-id="9288c-114">Yeniden tanımlanan dizinin her boyut sınırları listesi.</span><span class="sxs-lookup"><span data-stu-id="9288c-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9288c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9288c-115">Remarks</span></span>  
 <span data-ttu-id="9288c-116">Kullanabileceğiniz `ReDim` dizi önceden tanımlanmış bir veya daha fazla boyutları boyutunu değiştirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="9288c-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="9288c-117">Uzun bir diziye sahip ve bazı öğeleri, artık ihtiyacınız varsa `ReDim` dizi boyutu azaltarak belleği boşaltmak.</span><span class="sxs-lookup"><span data-stu-id="9288c-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="9288c-118">Daha fazla öğe dizinizi gerekirse diğer yandan, `ReDim` bunları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9288c-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="9288c-119">`ReDim` Deyimi yalnızca diziler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9288c-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="9288c-120">Skalerler (yalnızca tek bir değer içermesi değişkenler), koleksiyon veya yapıları geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="9288c-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="9288c-121">Türünde olması için bir değişken bildirirseniz unutmayın `Array`, `ReDim` deyimi, yeni bir dizi oluşturmak için yeterli türü bilgileri yok.</span><span class="sxs-lookup"><span data-stu-id="9288c-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="9288c-122">Kullanabileceğiniz `ReDim` yalnızca yordamı düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="9288c-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="9288c-123">Bu nedenle, değişken bildirimi bağlamının bir yordam olmalıdır; bir kaynak dosyası, bir ad alanı, bir arabirim, bir sınıf, bir yapı, bir modül veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="9288c-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="9288c-124">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9288c-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9288c-125">Kurallar</span><span class="sxs-lookup"><span data-stu-id="9288c-125">Rules</span></span>  
  
-   <span data-ttu-id="9288c-126">**Birden çok değişkenleri.**</span><span class="sxs-lookup"><span data-stu-id="9288c-126">**Multiple Variables.**</span></span> <span data-ttu-id="9288c-127">Aynı bildirimi deyiminde birden fazla dizi değişkenleri yeniden boyutlandırma ve belirtin `name` ve `boundlist` bölümleri her değişken için.</span><span class="sxs-lookup"><span data-stu-id="9288c-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="9288c-128">Birden çok değişkenleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9288c-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="9288c-129">**Dizi sınırları.**</span><span class="sxs-lookup"><span data-stu-id="9288c-129">**Array Bounds.**</span></span> <span data-ttu-id="9288c-130">Her giriş `boundlist` alt ve üst sınırlarını bu boyutun belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9288c-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="9288c-131">Alt sınır olan her zaman 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="9288c-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="9288c-132">Bu boyut yok (olan üst sınır artı bir taneyi) boyutun uzunluğu için en yüksek olası dizin değeri üst sınırdır.</span><span class="sxs-lookup"><span data-stu-id="9288c-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="9288c-133">Her boyut dizini 0'dan üst sınır değeri farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9288c-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="9288c-134">Boyutlar sayısı `boundlist` dizi boyutları (derece) özgün sayısı aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9288c-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="9288c-135">**Veri türleri.**</span><span class="sxs-lookup"><span data-stu-id="9288c-135">**Data Types.**</span></span> <span data-ttu-id="9288c-136">`ReDim` Deyimi, bir dizi değişkeni veya öğelerini veri türünü değiştiremiyor.</span><span class="sxs-lookup"><span data-stu-id="9288c-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="9288c-137">**Başlatma.**</span><span class="sxs-lookup"><span data-stu-id="9288c-137">**Initialization.**</span></span> <span data-ttu-id="9288c-138">`ReDim` Deyimi dizi öğeleri için yeni başlatma değerleri sağlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9288c-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="9288c-139">**RANK.**</span><span class="sxs-lookup"><span data-stu-id="9288c-139">**Rank.**</span></span> <span data-ttu-id="9288c-140">`ReDim` Deyimi dizi (dimensions sayısı) derecesini değiştiremiyor.</span><span class="sxs-lookup"><span data-stu-id="9288c-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="9288c-141">**Koru ile yeniden boyutlandırma.**</span><span class="sxs-lookup"><span data-stu-id="9288c-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="9288c-142">Kullanırsanız `Preserve`, yalnızca son boyut dizinin yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9288c-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="9288c-143">Diğer her bir boyut için mevcut dizisini bağlı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9288c-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="9288c-144">Örneğin, yalnızca bir boyut diziniz varsa, bu boyut yeniden boyutlandırabilir ve yalnızca boyut ve son değiştirme olduğundan hala dizi tüm içeriğini korumak.</span><span class="sxs-lookup"><span data-stu-id="9288c-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="9288c-145">İki veya daha fazla boyutları diziniz varsa, kullanırsanız, ancak, yalnızca son boyut boyutunu değiştirebilirsiniz `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="9288c-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="9288c-146">**Özellikler.**</span><span class="sxs-lookup"><span data-stu-id="9288c-146">**Properties.**</span></span> <span data-ttu-id="9288c-147">Kullanabileceğiniz `ReDim` değerleri dizisi tutan bir özelliğe.</span><span class="sxs-lookup"><span data-stu-id="9288c-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9288c-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="9288c-148">Behavior</span></span>  
  
-   <span data-ttu-id="9288c-149">**Dizi değiştirme.**</span><span class="sxs-lookup"><span data-stu-id="9288c-149">**Array Replacement.**</span></span> <span data-ttu-id="9288c-150">`ReDim`Mevcut dizisini serbest bırakır ve aynı dereceye yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9288c-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="9288c-151">Yeni bir dizi dizi değişkeni yayımlanan dizisinde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9288c-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="9288c-152">**Koruma olmadan başlatma.**</span><span class="sxs-lookup"><span data-stu-id="9288c-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="9288c-153">Belirtmezseniz, `Preserve`, `ReDim` kendi veri türü için varsayılan değer kullanarak yeni bir dizi öğelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="9288c-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="9288c-154">**Koru ile başlatma.**</span><span class="sxs-lookup"><span data-stu-id="9288c-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="9288c-155">Belirtirseniz `Preserve`, Visual Basic varolan diziden öğeleri yeni diziye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="9288c-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9288c-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="9288c-156">Example</span></span>  
 <span data-ttu-id="9288c-157">Aşağıdaki örnek, mevcut verilerin herhangi biri dizisindeki kaybetmeden dinamik dizinin son boyutu boyutu artar ve kısmi veri kaybı boyutuyla azaltır.</span><span class="sxs-lookup"><span data-stu-id="9288c-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="9288c-158">Son olarak, boyutu özgün değeri azaltır ve tüm dizi öğeleri yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="9288c-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 <span data-ttu-id="9288c-159">`Dim` Deyim üç boyutlarla yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9288c-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="9288c-160">Dizi dizini her boyut için 0 ile 10 arası değişebilir şekilde her boyut sınır 10 değeri ile bildirildi.</span><span class="sxs-lookup"><span data-stu-id="9288c-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="9288c-161">Aşağıdaki tartışmada boyutların için katman, satır ve sütun adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9288c-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="9288c-162">İlk `ReDim` değişkeninde varolan dizi yerini alacak yeni bir dizi oluşturur `intArray`.</span><span class="sxs-lookup"><span data-stu-id="9288c-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="9288c-163">`ReDim`tüm öğeleri varolan diziden yeni diziye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="9288c-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="9288c-164">Ayrıca her katmandaki her satırın sonuna 10 daha fazla sütun ekler ve bu yeni sütunlar 0 öğelerinde başlatır (varsayılan değeri `Integer`, dizi öğesi türü olduğu).</span><span class="sxs-lookup"><span data-stu-id="9288c-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="9288c-165">İkinci `ReDim` başka bir yeni bir dizi oluşturur ve uyan tüm öğeler kopyalar.</span><span class="sxs-lookup"><span data-stu-id="9288c-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="9288c-166">Ancak, beş sütun her katmandaki her satır sonundan kaybolur.</span><span class="sxs-lookup"><span data-stu-id="9288c-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="9288c-167">Bu sütunları kullanarak tamamladığınızda bu bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="9288c-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="9288c-168">Uzun bir diziye boyutunun azaltılması, artık gereken belleği boşaltmak.</span><span class="sxs-lookup"><span data-stu-id="9288c-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="9288c-169">Üçüncü `ReDim` başka bir yeni bir dizi oluşturur ve her katmandaki her satır sonu başka bir beş sütun kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9288c-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="9288c-170">Bu süre, var olan öğeleri kopyalamaz.</span><span class="sxs-lookup"><span data-stu-id="9288c-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="9288c-171">Bu bildirimi özgün boyutuna diziye döner.</span><span class="sxs-lookup"><span data-stu-id="9288c-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="9288c-172">Deyim içermediği için `Preserve` değiştiricisi, bu ayarlar tüm dizi öğeleri özgün varsayılan değerlerine.</span><span class="sxs-lookup"><span data-stu-id="9288c-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="9288c-173">Ek örnekler için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9288c-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9288c-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9288c-174">See Also</span></span>  
 <xref:System.IndexOutOfRangeException>  
 [<span data-ttu-id="9288c-175">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="9288c-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="9288c-176">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="9288c-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="9288c-177">Erase deyimi</span><span class="sxs-lookup"><span data-stu-id="9288c-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [<span data-ttu-id="9288c-178">Hiçbir şey</span><span class="sxs-lookup"><span data-stu-id="9288c-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="9288c-179">Diziler</span><span class="sxs-lookup"><span data-stu-id="9288c-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
