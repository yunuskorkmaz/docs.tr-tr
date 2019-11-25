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
ms.openlocfilehash: fabfd9a45d47cc1b881b3743181a03e89158f939
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346745"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="bfabb-102">ReDim Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfabb-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="bfabb-103">Reallocates storage space for an array variable.</span><span class="sxs-lookup"><span data-stu-id="bfabb-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfabb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfabb-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="bfabb-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bfabb-105">Parts</span></span>  
  
|<span data-ttu-id="bfabb-106">Terim</span><span class="sxs-lookup"><span data-stu-id="bfabb-106">Term</span></span>|<span data-ttu-id="bfabb-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="bfabb-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="bfabb-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bfabb-108">Optional.</span></span> <span data-ttu-id="bfabb-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span><span class="sxs-lookup"><span data-stu-id="bfabb-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="bfabb-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bfabb-110">Required.</span></span> <span data-ttu-id="bfabb-111">Name of the array variable.</span><span class="sxs-lookup"><span data-stu-id="bfabb-111">Name of the array variable.</span></span> <span data-ttu-id="bfabb-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="bfabb-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="bfabb-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bfabb-113">Required.</span></span> <span data-ttu-id="bfabb-114">List of bounds of each dimension of the redefined array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfabb-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfabb-115">Remarks</span></span>  
 <span data-ttu-id="bfabb-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span><span class="sxs-lookup"><span data-stu-id="bfabb-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="bfabb-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span><span class="sxs-lookup"><span data-stu-id="bfabb-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="bfabb-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span><span class="sxs-lookup"><span data-stu-id="bfabb-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="bfabb-119">The `ReDim` statement is intended only for arrays.</span><span class="sxs-lookup"><span data-stu-id="bfabb-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="bfabb-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span><span class="sxs-lookup"><span data-stu-id="bfabb-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="bfabb-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="bfabb-122">You can use `ReDim` only at procedure level.</span><span class="sxs-lookup"><span data-stu-id="bfabb-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="bfabb-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span><span class="sxs-lookup"><span data-stu-id="bfabb-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="bfabb-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bfabb-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bfabb-125">Kurallar</span><span class="sxs-lookup"><span data-stu-id="bfabb-125">Rules</span></span>  
  
- <span data-ttu-id="bfabb-126">**Multiple Variables.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-126">**Multiple Variables.**</span></span> <span data-ttu-id="bfabb-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span><span class="sxs-lookup"><span data-stu-id="bfabb-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="bfabb-128">Multiple variables are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="bfabb-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="bfabb-129">**Array Bounds.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-129">**Array Bounds.**</span></span> <span data-ttu-id="bfabb-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span><span class="sxs-lookup"><span data-stu-id="bfabb-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="bfabb-131">The lower bound is always 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="bfabb-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="bfabb-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span><span class="sxs-lookup"><span data-stu-id="bfabb-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="bfabb-133">The index for each dimension can vary from 0 through its upper bound value.</span><span class="sxs-lookup"><span data-stu-id="bfabb-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="bfabb-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="bfabb-135">**Data Types.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-135">**Data Types.**</span></span> <span data-ttu-id="bfabb-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span><span class="sxs-lookup"><span data-stu-id="bfabb-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="bfabb-137">**Initialization.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-137">**Initialization.**</span></span> <span data-ttu-id="bfabb-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span><span class="sxs-lookup"><span data-stu-id="bfabb-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="bfabb-139">**Rank.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-139">**Rank.**</span></span> <span data-ttu-id="bfabb-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="bfabb-141">**Resizing with Preserve.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="bfabb-142">If you use `Preserve`, you can resize only the last dimension of the array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="bfabb-143">For every other dimension, you must specify the bound of the existing array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="bfabb-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span><span class="sxs-lookup"><span data-stu-id="bfabb-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="bfabb-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="bfabb-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="bfabb-146">**Properties.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-146">**Properties.**</span></span> <span data-ttu-id="bfabb-147">You can use `ReDim` on a property that holds an array of values.</span><span class="sxs-lookup"><span data-stu-id="bfabb-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="bfabb-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="bfabb-148">Behavior</span></span>  
  
- <span data-ttu-id="bfabb-149">**Array Replacement.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-149">**Array Replacement.**</span></span> <span data-ttu-id="bfabb-150">`ReDim` releases the existing array and creates a new array with the same rank.</span><span class="sxs-lookup"><span data-stu-id="bfabb-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="bfabb-151">The new array replaces the released array in the array variable.</span><span class="sxs-lookup"><span data-stu-id="bfabb-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="bfabb-152">**Initialization without Preserve.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="bfabb-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span><span class="sxs-lookup"><span data-stu-id="bfabb-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="bfabb-154">**Initialization with Preserve.**</span><span class="sxs-lookup"><span data-stu-id="bfabb-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="bfabb-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfabb-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfabb-156">Example</span></span>  
 <span data-ttu-id="bfabb-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span><span class="sxs-lookup"><span data-stu-id="bfabb-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="bfabb-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span><span class="sxs-lookup"><span data-stu-id="bfabb-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="bfabb-159">The `Dim` statement creates a new array with three dimensions.</span><span class="sxs-lookup"><span data-stu-id="bfabb-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="bfabb-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span><span class="sxs-lookup"><span data-stu-id="bfabb-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="bfabb-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span><span class="sxs-lookup"><span data-stu-id="bfabb-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="bfabb-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span><span class="sxs-lookup"><span data-stu-id="bfabb-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="bfabb-163">`ReDim` copies all the elements from the existing array into the new array.</span><span class="sxs-lookup"><span data-stu-id="bfabb-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="bfabb-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span><span class="sxs-lookup"><span data-stu-id="bfabb-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="bfabb-165">The second `ReDim` creates another new array and copies all the elements that fit.</span><span class="sxs-lookup"><span data-stu-id="bfabb-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="bfabb-166">However, five columns are lost from the end of every row in every layer.</span><span class="sxs-lookup"><span data-stu-id="bfabb-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="bfabb-167">This is not a problem if you have finished using these columns.</span><span class="sxs-lookup"><span data-stu-id="bfabb-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="bfabb-168">Reducing the size of a large array can free up memory that you no longer need.</span><span class="sxs-lookup"><span data-stu-id="bfabb-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="bfabb-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span><span class="sxs-lookup"><span data-stu-id="bfabb-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="bfabb-170">This time it does not copy any existing elements.</span><span class="sxs-lookup"><span data-stu-id="bfabb-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="bfabb-171">This statement reverts the array to its original size.</span><span class="sxs-lookup"><span data-stu-id="bfabb-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="bfabb-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span><span class="sxs-lookup"><span data-stu-id="bfabb-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="bfabb-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfabb-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfabb-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfabb-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="bfabb-175">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="bfabb-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="bfabb-176">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="bfabb-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="bfabb-177">Erase Deyimi</span><span class="sxs-lookup"><span data-stu-id="bfabb-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)
- [<span data-ttu-id="bfabb-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="bfabb-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="bfabb-179">Diziler</span><span class="sxs-lookup"><span data-stu-id="bfabb-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
