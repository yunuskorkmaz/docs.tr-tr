---
title: '&gt;&gt;İşleci (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4eb0ed817c95905a679de5026bf6494eb72df078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="9a061-102">&gt;&gt;İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a061-102">&gt;&gt; Operator (Visual Basic)</span></span>
<span data-ttu-id="9a061-103">Bir bit desenine aritmetik sağa kaydırma uygular.</span><span class="sxs-lookup"><span data-stu-id="9a061-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a061-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a061-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="9a061-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9a061-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9a061-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9a061-106">Required.</span></span> <span data-ttu-id="9a061-107">Tam Sayı sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="9a061-107">Integral numeric value.</span></span> <span data-ttu-id="9a061-108">Bit desenini kaydırma sonucu.</span><span class="sxs-lookup"><span data-stu-id="9a061-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="9a061-109">Veri türü aynıdır `pattern`.</span><span class="sxs-lookup"><span data-stu-id="9a061-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="9a061-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9a061-110">Required.</span></span> <span data-ttu-id="9a061-111">Tam Sayı sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9a061-111">Integral numeric expression.</span></span> <span data-ttu-id="9a061-112">Değişebilir bit deseni.</span><span class="sxs-lookup"><span data-stu-id="9a061-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="9a061-113">Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="9a061-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="9a061-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9a061-114">Required.</span></span> <span data-ttu-id="9a061-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9a061-115">Numeric expression.</span></span> <span data-ttu-id="9a061-116">Bit desenini kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="9a061-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="9a061-117">Veri türü olmalıdır `Integer` veya için genişletmek `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9a061-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a061-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a061-118">Remarks</span></span>  
 <span data-ttu-id="9a061-119">Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil.</span><span class="sxs-lookup"><span data-stu-id="9a061-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="9a061-120">Aritmetik sağa kaydırma, en sağdaki bit konumu gölgeye BITS atılır ve soldaki (oturum) bit solda vacated bit konumları içine yayılır.</span><span class="sxs-lookup"><span data-stu-id="9a061-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="9a061-121">Bu olması durumunda gelir `pattern` negatif bir değere sahip vacated konumlar birine ayarlanır; Aksi takdirde sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9a061-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="9a061-122">Unutmayın veri türleri `Byte`, `UShort`, `UInteger`, ve `ULong` ; böylece yaymak için hiçbir oturum bit imzalanmamışsa.</span><span class="sxs-lookup"><span data-stu-id="9a061-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="9a061-123">Varsa `pattern` değil herhangi türü İmzasız, vacated konumlar her zaman sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9a061-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="9a061-124">Sonuç tutabileceğinden daha fazla BITS kaydırma önlemek için Visual Basic değerini maskeleri `amount` veri türü için karşılık gelen boyut maskesiyle `pattern`.</span><span class="sxs-lookup"><span data-stu-id="9a061-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="9a061-125">İkili ve bu değerleri shift tutarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a061-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="9a061-126">Boyutu maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a061-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="9a061-127">Veri türü`pattern`</span><span class="sxs-lookup"><span data-stu-id="9a061-127">Data type of `pattern`</span></span>|<span data-ttu-id="9a061-128">Boyutu maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="9a061-128">Size mask (decimal)</span></span>|<span data-ttu-id="9a061-129">Boyutu maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="9a061-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="9a061-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="9a061-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="9a061-131">7</span><span class="sxs-lookup"><span data-stu-id="9a061-131">7</span></span>|<span data-ttu-id="9a061-132">& H00000007</span><span class="sxs-lookup"><span data-stu-id="9a061-132">&H00000007</span></span>|  
|<span data-ttu-id="9a061-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="9a061-133">`Short`, `UShort`</span></span>|<span data-ttu-id="9a061-134">15</span><span class="sxs-lookup"><span data-stu-id="9a061-134">15</span></span>|<span data-ttu-id="9a061-135">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="9a061-135">&H0000000F</span></span>|  
|<span data-ttu-id="9a061-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="9a061-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="9a061-137">31</span><span class="sxs-lookup"><span data-stu-id="9a061-137">31</span></span>|<span data-ttu-id="9a061-138">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="9a061-138">&H0000001F</span></span>|  
|<span data-ttu-id="9a061-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="9a061-139">`Long`, `ULong`</span></span>|<span data-ttu-id="9a061-140">63</span><span class="sxs-lookup"><span data-stu-id="9a061-140">63</span></span>|<span data-ttu-id="9a061-141">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="9a061-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="9a061-142">Varsa `amount` sıfır, değeri olan `result` değerine aynıdır `pattern`.</span><span class="sxs-lookup"><span data-stu-id="9a061-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="9a061-143">Varsa `amount` olan negatif olduğundan imzasız bir değer olarak dikkate ve uygun boyutta maskesi ile maskelenir.</span><span class="sxs-lookup"><span data-stu-id="9a061-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="9a061-144">Aritmetik kaydırmalar hiçbir zaman taşma özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a061-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9a061-145">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9a061-145">Overloading</span></span>  
 <span data-ttu-id="9a061-146">`>>` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9a061-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9a061-147">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9a061-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9a061-148">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9a061-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a061-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a061-149">Example</span></span>  
 <span data-ttu-id="9a061-150">Aşağıdaki örnek kullanır `>>` aritmetik sağa kaydırmalar tam sayı değerleri üzerinde gerçekleştirilecek işleci.</span><span class="sxs-lookup"><span data-stu-id="9a061-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="9a061-151">Sonucu her zaman aynı veri, gölgeye ifade türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="9a061-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 <span data-ttu-id="9a061-152">Önceki örnekte sonuçlarını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a061-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="9a061-153">`result1`2560 (0000 1010 0000 0000) değil.</span><span class="sxs-lookup"><span data-stu-id="9a061-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="9a061-154">`result2`160 (0000 0000 1010 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="9a061-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="9a061-155">`result3`2 (0000 0000 0000 0010)'dir.</span><span class="sxs-lookup"><span data-stu-id="9a061-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="9a061-156">`result4`640 (0000 0010 1000 0000)'dır.</span><span class="sxs-lookup"><span data-stu-id="9a061-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="9a061-157">`result5`0 (ötelenen 15 basamağa sağa)'dır.</span><span class="sxs-lookup"><span data-stu-id="9a061-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="9a061-158">Shift tutarını `result4` 18 hesaplanır ve hangi eşittir 2 15.</span><span class="sxs-lookup"><span data-stu-id="9a061-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="9a061-159">Aşağıdaki örnek aritmetik kaydırmalar üzerinde negatif bir değer gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a061-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 <span data-ttu-id="9a061-160">Önceki örnekte sonuçlarını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a061-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="9a061-161">`negresult1`-512 (1111 1110 0000 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="9a061-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="9a061-162">`negresult2`(oturum bit yayılır) -1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9a061-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a061-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a061-163">See Also</span></span>  
 [<span data-ttu-id="9a061-164">Bit kaydırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="9a061-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="9a061-165">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9a061-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="9a061-166">>> = işleci</span><span class="sxs-lookup"><span data-stu-id="9a061-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [<span data-ttu-id="9a061-167">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="9a061-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="9a061-168">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="9a061-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="9a061-169">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="9a061-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
