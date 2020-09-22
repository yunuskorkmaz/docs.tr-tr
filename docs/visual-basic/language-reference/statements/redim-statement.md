---
title: ReDim Deyimi
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
ms.openlocfilehash: 17bc806f2e92c61f1dd7425de40b1a68f926a583
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872028"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="78d78-102">ReDim Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78d78-102">ReDim Statement (Visual Basic)</span></span>

<span data-ttu-id="78d78-103">, Bir dizi değişkeni için depolama alanını yeniden konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="78d78-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78d78-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78d78-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="78d78-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="78d78-105">Parts</span></span>  
  
|<span data-ttu-id="78d78-106">Terim</span><span class="sxs-lookup"><span data-stu-id="78d78-106">Term</span></span>|<span data-ttu-id="78d78-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="78d78-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="78d78-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="78d78-108">Optional.</span></span> <span data-ttu-id="78d78-109">Yalnızca son boyutun boyutunu değiştirirken mevcut dizideki verileri korumak için kullanılan değiştirici.</span><span class="sxs-lookup"><span data-stu-id="78d78-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="78d78-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="78d78-110">Required.</span></span> <span data-ttu-id="78d78-111">Dizi değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="78d78-111">Name of the array variable.</span></span> <span data-ttu-id="78d78-112">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="78d78-112">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="78d78-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="78d78-113">Required.</span></span> <span data-ttu-id="78d78-114">Yeniden tanımlanmış dizinin her boyutunun sınırları listesi.</span><span class="sxs-lookup"><span data-stu-id="78d78-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78d78-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78d78-115">Remarks</span></span>  

 <span data-ttu-id="78d78-116">`ReDim`Önceden tanımlanmış bir dizinin bir veya daha fazla boyutunun boyutunu değiştirmek için ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="78d78-117">Büyük bir diziniz varsa ve bazı öğeleri artık gerekmiyorsa, `ReDim` dizi boyutunu azaltarak belleği serbest bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="78d78-118">Öte yandan, dizide daha fazla öğe gerekiyorsa, `ReDim` bunları ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="78d78-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="78d78-119">`ReDim`İfade yalnızca diziler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="78d78-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="78d78-120">Yapı değerleri (yalnızca tek bir değer içeren değişkenler), koleksiyonlar veya yapılar üzerinde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="78d78-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="78d78-121">Türünde bir değişken bildirirseniz `Array` , `ReDim` deyimin yeni diziyi oluşturmak için yeterli tür bilgilerine sahip olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="78d78-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="78d78-122">`ReDim`Yalnızca yordam düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="78d78-123">Bu nedenle, değişken için bildirim bağlamı bir yordam olmalıdır; Kaynak dosya, ad alanı, arabirim, sınıf, yapı, modül veya blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="78d78-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="78d78-124">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="78d78-124">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="78d78-125">Kurallar</span><span class="sxs-lookup"><span data-stu-id="78d78-125">Rules</span></span>  
  
- <span data-ttu-id="78d78-126">**Birden çok değişken.**</span><span class="sxs-lookup"><span data-stu-id="78d78-126">**Multiple Variables.**</span></span> <span data-ttu-id="78d78-127">Aynı bildirim deyimindeki birkaç dizi değişkenini yeniden boyutlandırabilir ve `name` `boundlist` her değişken için ve parçalarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="78d78-128">Birden çok değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="78d78-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="78d78-129">**Dizi sınırları.**</span><span class="sxs-lookup"><span data-stu-id="78d78-129">**Array Bounds.**</span></span> <span data-ttu-id="78d78-130">İçindeki her giriş `boundlist` , bu boyutun alt ve üst sınırlarını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="78d78-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="78d78-131">Alt sınır her zaman 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="78d78-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="78d78-132">Üst sınır, boyutun uzunluğunu değil, bu boyut için mümkün olan en yüksek dizin değeridir (üst sınır artı bir değerdir).</span><span class="sxs-lookup"><span data-stu-id="78d78-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="78d78-133">Her boyutun dizini, üst sınır değeri ile 0 arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="78d78-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="78d78-134">İçindeki boyutların sayısı, `boundlist` dizinin orijinal boyut (derece) sayısıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="78d78-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="78d78-135">**Veri türleri.**</span><span class="sxs-lookup"><span data-stu-id="78d78-135">**Data Types.**</span></span> <span data-ttu-id="78d78-136">`ReDim`İfade, bir dizi değişkeninin veya öğelerinin veri türünü değiştiremiyor.</span><span class="sxs-lookup"><span data-stu-id="78d78-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="78d78-137">**Başlatılmasında.**</span><span class="sxs-lookup"><span data-stu-id="78d78-137">**Initialization.**</span></span> <span data-ttu-id="78d78-138">`ReDim`İfade, dizi öğeleri için yeni başlatma değerleri sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="78d78-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="78d78-139">**Sırası.**</span><span class="sxs-lookup"><span data-stu-id="78d78-139">**Rank.**</span></span> <span data-ttu-id="78d78-140">`ReDim`İfade, dizinin derecesini (boyut sayısı) değiştiremiyor.</span><span class="sxs-lookup"><span data-stu-id="78d78-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="78d78-141">**Preserve ile yeniden boyutlandırma.**</span><span class="sxs-lookup"><span data-stu-id="78d78-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="78d78-142">Kullanırsanız `Preserve` , yalnızca dizinin son boyutunu yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="78d78-143">Diğer tüm boyutlar için, var olan dizinin bir ilişkisini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="78d78-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="78d78-144">Örneğin, dizide yalnızca bir boyut varsa, en son ve yalnızca boyutu değiştirdiğiniz için bu boyutu yeniden boyutlandırabilir ve dizinin tüm içeriğini koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="78d78-145">Ancak, dizide iki veya daha fazla boyut varsa, kullanırsanız yalnızca son boyutun boyutunu değiştirebilirsiniz `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="78d78-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="78d78-146">**Özelliklerinin.**</span><span class="sxs-lookup"><span data-stu-id="78d78-146">**Properties.**</span></span> <span data-ttu-id="78d78-147">`ReDim`Bir değer dizisini tutan bir özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="78d78-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="78d78-148">Behavior</span></span>  
  
- <span data-ttu-id="78d78-149">**Dizi değiştirme.**</span><span class="sxs-lookup"><span data-stu-id="78d78-149">**Array Replacement.**</span></span> <span data-ttu-id="78d78-150">`ReDim` Mevcut diziyi serbest bırakır ve aynı dereceye sahip yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78d78-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="78d78-151">Yeni dizi, dizi değişkeninde yayınlanan dizinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="78d78-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="78d78-152">**Preserve olmadan başlatma.**</span><span class="sxs-lookup"><span data-stu-id="78d78-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="78d78-153">Belirtmezseniz `Preserve` , `ReDim` Yeni dizinin öğelerini, veri türleri için varsayılan değeri kullanarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="78d78-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="78d78-154">**Preserve ile başlatma.**</span><span class="sxs-lookup"><span data-stu-id="78d78-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="78d78-155">Belirtirseniz `Preserve` , Visual Basic öğeleri varolan diziden yeni diziye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="78d78-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78d78-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="78d78-156">Example</span></span>  

 <span data-ttu-id="78d78-157">Aşağıdaki örnek, dizideki mevcut verileri kaybetmeden dinamik bir dizinin en son boyutunun boyutunu artırır ve sonra boyutu kısmi veri kaybıyla azaltır.</span><span class="sxs-lookup"><span data-stu-id="78d78-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="78d78-158">Son olarak, boyutu özgün değerine geri düşürür ve tüm dizi öğelerini yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="78d78-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="78d78-159">`Dim`İfade üç boyutlu yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78d78-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="78d78-160">Her boyut 10 ' un bir bağı ile bildirildiği için her boyutun dizi dizini 0 ile 10 arasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="78d78-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="78d78-161">Aşağıdaki tartışmada, üç boyut katman, satır ve sütun olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="78d78-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="78d78-162">İlki, `ReDim` değişkende var olan dizinin yerini alan yeni bir dizi oluşturur `intArray` .</span><span class="sxs-lookup"><span data-stu-id="78d78-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="78d78-163">`ReDim` Varolan dizideki tüm öğeleri yeni diziye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="78d78-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="78d78-164">Ayrıca, her katmandaki her satırın sonuna 10 daha fazla sütun ekler ve bu yeni sütunlardaki öğeleri 0 ' a ( `Integer` dizinin öğe türü olan varsayılan değeri) başlatır.</span><span class="sxs-lookup"><span data-stu-id="78d78-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="78d78-165">İkincisi `ReDim` başka bir yeni dizi oluşturur ve uygun olan tüm öğeleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="78d78-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="78d78-166">Ancak, her katmandaki her satırın sonundan beş sütun kaybolur.</span><span class="sxs-lookup"><span data-stu-id="78d78-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="78d78-167">Bu sütunları kullanmayı bitirdiğinizde bu bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="78d78-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="78d78-168">Büyük bir dizinin boyutunu azaltmak artık ihtiyaç duymayacak belleği serbest bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78d78-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="78d78-169">Üçüncü, `ReDim` Yeni bir dizi oluşturur ve her katmandaki her satırın sonundan başka beş sütunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="78d78-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="78d78-170">Bu kez, var olan herhangi bir öğeyi kopyalamaz.</span><span class="sxs-lookup"><span data-stu-id="78d78-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="78d78-171">Bu ifade, diziyi özgün boyutuna geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="78d78-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="78d78-172">İfadeyi `Preserve` değiştirici içermediğinden, tüm dizi öğelerini özgün varsayılan değerlerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="78d78-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="78d78-173">Daha fazla örnek için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="78d78-173">For additional examples, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d78-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78d78-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="78d78-175">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="78d78-175">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="78d78-176">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="78d78-176">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="78d78-177">Erase Deyimi</span><span class="sxs-lookup"><span data-stu-id="78d78-177">Erase Statement</span></span>](erase-statement.md)
- [<span data-ttu-id="78d78-178">Yapma</span><span class="sxs-lookup"><span data-stu-id="78d78-178">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="78d78-179">Diziler</span><span class="sxs-lookup"><span data-stu-id="78d78-179">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
