---
title: ReDim Deyimi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 1252c9a93d9c37923b1fd2940a42f1a33b575b8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617332"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="38699-102">ReDim Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38699-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="38699-103">Bir dizi değişkeni için depolama alanını yeniden ayırır.</span><span class="sxs-lookup"><span data-stu-id="38699-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38699-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38699-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="38699-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="38699-105">Parts</span></span>  
  
|<span data-ttu-id="38699-106">Terim</span><span class="sxs-lookup"><span data-stu-id="38699-106">Term</span></span>|<span data-ttu-id="38699-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="38699-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="38699-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="38699-108">Optional.</span></span> <span data-ttu-id="38699-109">Değiştiricisi boyutu sadece son boyutu değiştirdiğinizde varolan dizedeki verileri korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38699-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="38699-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="38699-110">Required.</span></span> <span data-ttu-id="38699-111">Dizi değişkeni adı.</span><span class="sxs-lookup"><span data-stu-id="38699-111">Name of the array variable.</span></span> <span data-ttu-id="38699-112">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="38699-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="38699-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="38699-113">Required.</span></span> <span data-ttu-id="38699-114">Yeniden tanımlanan dizinin her boyutunun sınırlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="38699-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38699-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38699-115">Remarks</span></span>  
 <span data-ttu-id="38699-116">Kullanabileceğiniz `ReDim` bir veya daha fazla boyut zaten bildirilmiş bir dizinin boyutunu değiştirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="38699-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="38699-117">Uzun bir diziye sahip ve bazı alt öğeleri artık ihtiyacınız varsa `ReDim` dizi boyutu azaltarak belleği boşaltabilir.</span><span class="sxs-lookup"><span data-stu-id="38699-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="38699-118">Daha fazla öğe diziniz gerekiyorsa diğer yandan, `ReDim` bunları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38699-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="38699-119">`ReDim` Deyimi yalnızca diziler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="38699-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="38699-120">Skalerler (yalnızca tek bir değer içeren değişkenlerini), koleksiyonlar veya yapılar üzerinde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="38699-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="38699-121">Bir değişken türünde bildirmeniz gerçekleştiriyorsanız `Array`, `ReDim` deyimi, yeni bir dizi oluşturmak için yeterli tür bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="38699-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="38699-122">Kullanabileceğiniz `ReDim` yalnızca yordamı düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="38699-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="38699-123">Bu nedenle, bildirimi bağlam değişkeni için bir yordam olmalıdır; bir kaynak dosyası, bir ad alanı, bir arabirim, bir sınıf, yapı, modül veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="38699-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="38699-124">Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="38699-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="38699-125">Kurallar</span><span class="sxs-lookup"><span data-stu-id="38699-125">Rules</span></span>  
  
-   <span data-ttu-id="38699-126">**Birden fazla değişken.**</span><span class="sxs-lookup"><span data-stu-id="38699-126">**Multiple Variables.**</span></span> <span data-ttu-id="38699-127">Aynı bildirim deyiminde birden fazla dizi değişkenlerini yeniden boyutlandırma ve belirtin `name` ve `boundlist` bölümleri her değişken için.</span><span class="sxs-lookup"><span data-stu-id="38699-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="38699-128">Birden fazla değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="38699-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="38699-129">**Dizi sınırları.**</span><span class="sxs-lookup"><span data-stu-id="38699-129">**Array Bounds.**</span></span> <span data-ttu-id="38699-130">Her giriş `boundlist` alt ve söz konusu boyut üst sınırları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38699-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="38699-131">Her zaman alt sınır olan 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="38699-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="38699-132">Değil (Bu üst sınırı yanı sıra bir durumdur) boyutun uzunluğu o boyut için en yüksek olası dizin değeri üst sınırıdır.</span><span class="sxs-lookup"><span data-stu-id="38699-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="38699-133">Her boyutun dizini 0 ile üst sınır değeri arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="38699-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="38699-134">İçindeki boyutların sayısına `boundlist` dizi boyutları (derece) özgün sayısı ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="38699-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="38699-135">**Veri türleri.**</span><span class="sxs-lookup"><span data-stu-id="38699-135">**Data Types.**</span></span> <span data-ttu-id="38699-136">`ReDim` Deyimi bir diziye veya öğelerine veri türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="38699-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="38699-137">**Başlatma.**</span><span class="sxs-lookup"><span data-stu-id="38699-137">**Initialization.**</span></span> <span data-ttu-id="38699-138">`ReDim` Deyimi, dizi öğeleri için yeni başlangıç değerleri sağlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="38699-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="38699-139">**Boyut.**</span><span class="sxs-lookup"><span data-stu-id="38699-139">**Rank.**</span></span> <span data-ttu-id="38699-140">`ReDim` Deyimi (boyut sayısı) dizi boyut sayısını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="38699-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="38699-141">**Koruma ile yeniden boyutlandırma.**</span><span class="sxs-lookup"><span data-stu-id="38699-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="38699-142">Kullanırsanız `Preserve`, sadece son boyutu dizinin yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38699-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="38699-143">Diğer her bir boyut için var olan bir dizi sınırı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="38699-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="38699-144">Örneğin, yalnızca bir boyut diziniz varsa, boyut yeniden boyutlandırma ve yalnızca boyut ve son değiştirme çünkü hala dizinin tüm içerikleri korumak.</span><span class="sxs-lookup"><span data-stu-id="38699-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="38699-145">İki veya daha fazla boyuta diziniz varsa kullanırsanız ancak sadece son boyutu boyutunu değiştirebileceğiniz `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="38699-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="38699-146">**özellikleri.**</span><span class="sxs-lookup"><span data-stu-id="38699-146">**Properties.**</span></span> <span data-ttu-id="38699-147">Kullanabileceğiniz `ReDim` değerler dizisi tutan bir özellikte.</span><span class="sxs-lookup"><span data-stu-id="38699-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="38699-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="38699-148">Behavior</span></span>  
  
-   <span data-ttu-id="38699-149">**Dizi değiştirme.**</span><span class="sxs-lookup"><span data-stu-id="38699-149">**Array Replacement.**</span></span> <span data-ttu-id="38699-150">`ReDim` Varolan bir diziye serbest bırakır ve aynı dereceye yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38699-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="38699-151">Yeni bir dizi yayımlanan dizide dizi değişkenini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="38699-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="38699-152">**Başlatma olmadan korur.**</span><span class="sxs-lookup"><span data-stu-id="38699-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="38699-153">Siz belirtmezseniz `Preserve`, `ReDim` kendi veri türü için varsayılan değer kullanarak yeni bir dizi öğelerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="38699-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="38699-154">**Koruma ile başlatma.**</span><span class="sxs-lookup"><span data-stu-id="38699-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="38699-155">Belirtirseniz `Preserve`, Visual Basic mevcut bir diziden öğeleri için yeni bir diziye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="38699-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38699-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="38699-156">Example</span></span>  
 <span data-ttu-id="38699-157">Aşağıdaki örnek dizinin var olan veri kaybı olmadan son boyutu dinamik bir dizinin boyutunu artırır ve ardından kısmi veri kaybıyla sonuçlanan boyuta azaltır.</span><span class="sxs-lookup"><span data-stu-id="38699-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="38699-158">Son olarak, özgün değerine geri boyutunu azaltır ve tüm dizi öğeleri yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="38699-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 <span data-ttu-id="38699-159">`Dim` Deyimi üç boyut ile yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38699-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="38699-160">Her boyut için dizi dizini 0-10 aralığında, böylece her boyutun bağımlı 10 ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="38699-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="38699-161">Aşağıdaki tartışmada boyutların için katman, satır ve sütun adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="38699-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="38699-162">İlk `ReDim` değişkeni varolan dizide yerini alan yeni bir dizi oluşturur `intArray`.</span><span class="sxs-lookup"><span data-stu-id="38699-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="38699-163">`ReDim` tüm öğeleri mevcut bir diziden yeni bir diziye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="38699-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="38699-164">Ayrıca her katman içindeki her bir satırın sonuna 10 daha fazla sütun ekler ve bu yeni sütunların 0 öğeleri başlatır (varsayılan değeri `Integer`, dizinin öğe türü).</span><span class="sxs-lookup"><span data-stu-id="38699-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="38699-165">İkinci `ReDim` başka bir yeni bir dizi oluşturur ve uygun tüm öğeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="38699-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="38699-166">Bununla birlikte beş sütun her katmanında her satır sonundan kaybolur.</span><span class="sxs-lookup"><span data-stu-id="38699-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="38699-167">Bu sütunları kullanarak tamamlandıysa, bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="38699-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="38699-168">Uzun bir diziye boyutunu küçültmeyi artık gereksinim duymadığınız belleği boşaltmak.</span><span class="sxs-lookup"><span data-stu-id="38699-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="38699-169">Üçüncü `ReDim` başka bir yeni bir dizi oluşturur ve her katman içindeki her bir satırın son beş başka bir sütun kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38699-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="38699-170">Bu süre, var olan öğeleri kopyalamaz.</span><span class="sxs-lookup"><span data-stu-id="38699-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="38699-171">Bu ifade, dizinin özgün boyutuna döner.</span><span class="sxs-lookup"><span data-stu-id="38699-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="38699-172">Deyimi içermediği için `Preserve` özgün varsayılan değerlerine tüm dizi öğeleri ayarlar değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="38699-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="38699-173">Diğer örnekler için [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="38699-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38699-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38699-174">See also</span></span>
- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="38699-175">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="38699-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="38699-176">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="38699-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="38699-177">Erase Deyimi</span><span class="sxs-lookup"><span data-stu-id="38699-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)
- [<span data-ttu-id="38699-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="38699-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="38699-179">Diziler</span><span class="sxs-lookup"><span data-stu-id="38699-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
