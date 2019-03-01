---
title: '>> İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 46bc87c653742c8469ffaff1decb9549a29feaeb
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972085"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="26ffd-102">>> İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26ffd-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="26ffd-103">Bir bit desenine aritmetik sağa kaydırma uygular.</span><span class="sxs-lookup"><span data-stu-id="26ffd-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ffd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26ffd-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="26ffd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="26ffd-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="26ffd-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="26ffd-106">Required.</span></span> <span data-ttu-id="26ffd-107">Tamsayı sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="26ffd-107">Integral numeric value.</span></span> <span data-ttu-id="26ffd-108">Bit deseninin kaydırma sonucu.</span><span class="sxs-lookup"><span data-stu-id="26ffd-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="26ffd-109">Veri türü, aynı olduğu `pattern`.</span><span class="sxs-lookup"><span data-stu-id="26ffd-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="26ffd-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="26ffd-110">Required.</span></span> <span data-ttu-id="26ffd-111">Tamsayı sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="26ffd-111">Integral numeric expression.</span></span> <span data-ttu-id="26ffd-112">Kaydırılmasına bit deseni.</span><span class="sxs-lookup"><span data-stu-id="26ffd-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="26ffd-113">Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="26ffd-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="26ffd-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="26ffd-114">Required.</span></span> <span data-ttu-id="26ffd-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="26ffd-115">Numeric expression.</span></span> <span data-ttu-id="26ffd-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="26ffd-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="26ffd-117">Veri türü olmalıdır `Integer` veya genişletmek için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="26ffd-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26ffd-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26ffd-118">Remarks</span></span>  
 <span data-ttu-id="26ffd-119">Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir.</span><span class="sxs-lookup"><span data-stu-id="26ffd-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="26ffd-120">Aritmetik sağa kaydırma, en sağdaki bit ötesindeki kaydırılacak bitlerin atılır ve soldaki (imzala) bit içine solda işleci boşaltılmış bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="26ffd-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="26ffd-121">Olması durumunda başka bir deyişle `pattern` negatif bir değere sahip boşaltılmış konumları birine ayarlanır; Aksi halde sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="26ffd-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="26ffd-122">Unutmayın veri türlerini `Byte`, `UShort`, `UInteger`, ve `ULong` yaymak için hiç imza biti olduğundan imzalanmamışsa.</span><span class="sxs-lookup"><span data-stu-id="26ffd-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="26ffd-123">Varsa `pattern` değil herhangi bir türü imzalanmamış, boşaltılmış konumları her zaman sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="26ffd-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="26ffd-124">Sonuç tutabileceğinden daha fazla bit kaydırma önlemek için Visual Basic değerini maskeleri `amount` veri türü için karşılık gelen bir boyut maskesiyle `pattern`.</span><span class="sxs-lookup"><span data-stu-id="26ffd-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="26ffd-125">İkili ve bu değerleri değiştirme miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26ffd-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="26ffd-126">Boyutu maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="26ffd-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="26ffd-127">Veri türü `pattern`</span><span class="sxs-lookup"><span data-stu-id="26ffd-127">Data type of `pattern`</span></span>|<span data-ttu-id="26ffd-128">Boyutu maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="26ffd-128">Size mask (decimal)</span></span>|<span data-ttu-id="26ffd-129">Boyutu maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="26ffd-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="26ffd-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="26ffd-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="26ffd-131">7</span><span class="sxs-lookup"><span data-stu-id="26ffd-131">7</span></span>|<span data-ttu-id="26ffd-132">&AMP; H00000007</span><span class="sxs-lookup"><span data-stu-id="26ffd-132">&H00000007</span></span>|  
|<span data-ttu-id="26ffd-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="26ffd-133">`Short`, `UShort`</span></span>|<span data-ttu-id="26ffd-134">15</span><span class="sxs-lookup"><span data-stu-id="26ffd-134">15</span></span>|<span data-ttu-id="26ffd-135">&AMP; H0000000F</span><span class="sxs-lookup"><span data-stu-id="26ffd-135">&H0000000F</span></span>|  
|<span data-ttu-id="26ffd-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="26ffd-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="26ffd-137">31</span><span class="sxs-lookup"><span data-stu-id="26ffd-137">31</span></span>|<span data-ttu-id="26ffd-138">&AMP; H0000001F</span><span class="sxs-lookup"><span data-stu-id="26ffd-138">&H0000001F</span></span>|  
|<span data-ttu-id="26ffd-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="26ffd-139">`Long`, `ULong`</span></span>|<span data-ttu-id="26ffd-140">63</span><span class="sxs-lookup"><span data-stu-id="26ffd-140">63</span></span>|<span data-ttu-id="26ffd-141">&AMP; H0000003F</span><span class="sxs-lookup"><span data-stu-id="26ffd-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="26ffd-142">Varsa `amount` değeri sıfır olan `result` değeri olarak aynı `pattern`.</span><span class="sxs-lookup"><span data-stu-id="26ffd-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="26ffd-143">Varsa `amount` olan negatif, işaretsiz bir değer olarak yapılan ve uygun boyutta maske ile maskelenir.</span><span class="sxs-lookup"><span data-stu-id="26ffd-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="26ffd-144">Aritmetik kaydırmalar hiçbir zaman taşması özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26ffd-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="26ffd-145">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="26ffd-145">Overloading</span></span>  
 <span data-ttu-id="26ffd-146">`>>` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="26ffd-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="26ffd-147">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="26ffd-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="26ffd-148">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="26ffd-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26ffd-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="26ffd-149">Example</span></span>  
 <span data-ttu-id="26ffd-150">Aşağıdaki örnekte `>>` tam sayı değerleri üzerinde aritmetik sağa kaydırmalar gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="26ffd-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="26ffd-151">Sonucu her zaman aynı veri türüne, kaydırılacak ifade sahiptir.</span><span class="sxs-lookup"><span data-stu-id="26ffd-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="26ffd-152">Yukarıdaki örnekte sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="26ffd-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="26ffd-153">`result1` 2560 (0000 1010 0000 0000) olan.</span><span class="sxs-lookup"><span data-stu-id="26ffd-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="26ffd-154">`result2` 160 (0000 0000 1010 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="26ffd-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="26ffd-155">`result3` 2 (0000 0000 0000 0010)'dir.</span><span class="sxs-lookup"><span data-stu-id="26ffd-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="26ffd-156">`result4` 640 (0000 0010 1000 0000)'dır.</span><span class="sxs-lookup"><span data-stu-id="26ffd-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="26ffd-157">`result5` (sağ ötelenen 15 basamak) 0'dır.</span><span class="sxs-lookup"><span data-stu-id="26ffd-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="26ffd-158">Değiştirme miktarı için `result4` 18 hesaplanır ve hangi eşittir 2 15.</span><span class="sxs-lookup"><span data-stu-id="26ffd-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="26ffd-159">Aşağıdaki örnek, negatif bir değer üzerinde aritmetik kaydırmalar gösterir.</span><span class="sxs-lookup"><span data-stu-id="26ffd-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="26ffd-160">Yukarıdaki örnekte sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="26ffd-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="26ffd-161">`negresult1` -512 (1111 1110 0000 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="26ffd-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="26ffd-162">`negresult2` -1 (imza biti yayılır) olur.</span><span class="sxs-lookup"><span data-stu-id="26ffd-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ffd-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26ffd-163">See also</span></span>
- [<span data-ttu-id="26ffd-164">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="26ffd-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="26ffd-165">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="26ffd-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="26ffd-166">>>= İşleci</span><span class="sxs-lookup"><span data-stu-id="26ffd-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="26ffd-167">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="26ffd-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="26ffd-168">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="26ffd-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="26ffd-169">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="26ffd-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
