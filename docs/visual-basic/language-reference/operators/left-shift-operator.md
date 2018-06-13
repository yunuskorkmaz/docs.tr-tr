---
title: '&lt;&lt; İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: bdec015309526aeac2499bc7b459b6ccab6f1e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604464"
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="6e209-102">&lt;&lt; İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e209-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="6e209-103">Bir bit desenine aritmetik sola kaydırma uygular.</span><span class="sxs-lookup"><span data-stu-id="6e209-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e209-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e209-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="6e209-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6e209-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6e209-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6e209-106">Required.</span></span> <span data-ttu-id="6e209-107">Tam Sayı sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="6e209-107">Integral numeric value.</span></span> <span data-ttu-id="6e209-108">Bit desenini kaydırma sonucu.</span><span class="sxs-lookup"><span data-stu-id="6e209-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="6e209-109">Veri türü aynıdır `pattern`.</span><span class="sxs-lookup"><span data-stu-id="6e209-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="6e209-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6e209-110">Required.</span></span> <span data-ttu-id="6e209-111">Tam Sayı sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="6e209-111">Integral numeric expression.</span></span> <span data-ttu-id="6e209-112">Değişebilir bit deseni.</span><span class="sxs-lookup"><span data-stu-id="6e209-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="6e209-113">Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="6e209-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="6e209-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6e209-114">Required.</span></span> <span data-ttu-id="6e209-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="6e209-115">Numeric expression.</span></span> <span data-ttu-id="6e209-116">Bit desenini kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="6e209-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="6e209-117">Veri türü olmalıdır `Integer` veya için genişletmek `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6e209-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e209-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e209-118">Remarks</span></span>  
 <span data-ttu-id="6e209-119">Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil.</span><span class="sxs-lookup"><span data-stu-id="6e209-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="6e209-120">Aritmetik sola kaydırma, sonuç veri türü aralık dışında gölgeye BITS atılır ve sağ taraftaki vacated bit konumları sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6e209-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="6e209-121">Shift sonucu tutabileceğinden daha fazla BITS tarafından önlemek için Visual Basic değerini maskeleri `amount` veri türüne karşılık gelen boyut maskesiyle `pattern`.</span><span class="sxs-lookup"><span data-stu-id="6e209-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="6e209-122">İkili ve bu değerleri shift tutarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e209-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="6e209-123">Boyutu maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6e209-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="6e209-124">Veri türü `pattern`</span><span class="sxs-lookup"><span data-stu-id="6e209-124">Data type of `pattern`</span></span>|<span data-ttu-id="6e209-125">Boyutu maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="6e209-125">Size mask (decimal)</span></span>|<span data-ttu-id="6e209-126">Boyutu maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="6e209-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="6e209-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="6e209-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="6e209-128">7</span><span class="sxs-lookup"><span data-stu-id="6e209-128">7</span></span>|<span data-ttu-id="6e209-129">&AMP; H00000007</span><span class="sxs-lookup"><span data-stu-id="6e209-129">&H00000007</span></span>|  
|<span data-ttu-id="6e209-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="6e209-130">`Short`, `UShort`</span></span>|<span data-ttu-id="6e209-131">15</span><span class="sxs-lookup"><span data-stu-id="6e209-131">15</span></span>|<span data-ttu-id="6e209-132">&AMP; H0000000F</span><span class="sxs-lookup"><span data-stu-id="6e209-132">&H0000000F</span></span>|  
|<span data-ttu-id="6e209-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="6e209-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="6e209-134">31</span><span class="sxs-lookup"><span data-stu-id="6e209-134">31</span></span>|<span data-ttu-id="6e209-135">&AMP; H0000001F</span><span class="sxs-lookup"><span data-stu-id="6e209-135">&H0000001F</span></span>|  
|<span data-ttu-id="6e209-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="6e209-136">`Long`, `ULong`</span></span>|<span data-ttu-id="6e209-137">63</span><span class="sxs-lookup"><span data-stu-id="6e209-137">63</span></span>|<span data-ttu-id="6e209-138">&AMP; H0000003F</span><span class="sxs-lookup"><span data-stu-id="6e209-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="6e209-139">Varsa `amount` sıfır, değeri olan `result` değerine aynıdır `pattern`.</span><span class="sxs-lookup"><span data-stu-id="6e209-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="6e209-140">Varsa `amount` olan negatif olduğundan imzasız bir değer olarak dikkate ve uygun boyutta maskesi ile maskelenir.</span><span class="sxs-lookup"><span data-stu-id="6e209-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="6e209-141">Aritmetik kaydırmalar hiçbir zaman taşma özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e209-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e209-142">`<<` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e209-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6e209-143">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6e209-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="6e209-144">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6e209-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e209-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e209-145">Example</span></span>  
 <span data-ttu-id="6e209-146">Aşağıdaki örnek kullanır `<<` tam sayı değerleri üzerinde kaydırmalar sol aritmetik gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="6e209-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="6e209-147">Sonucu her zaman aynı veri, gölgeye ifade türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="6e209-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="6e209-148">Önceki örneği sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6e209-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="6e209-149">`result1` 192 (0000 0000 1100 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="6e209-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="6e209-150">`result2` 3072 (0000 1100 0000 0000) değil.</span><span class="sxs-lookup"><span data-stu-id="6e209-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="6e209-151">`result3` -32768 (1000 0000 0000 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="6e209-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="6e209-152">`result4` 384 (0000 0001 1000 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="6e209-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="6e209-153">`result5` 0 (sol ötelenen 15 basamak)'dır.</span><span class="sxs-lookup"><span data-stu-id="6e209-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="6e209-154">Shift tutarını `result4` 17 hesaplanır ve hangi eşittir 1 15.</span><span class="sxs-lookup"><span data-stu-id="6e209-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e209-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e209-155">See Also</span></span>  
 [<span data-ttu-id="6e209-156">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6e209-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="6e209-157">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6e209-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="6e209-158"><<= İşleci</span><span class="sxs-lookup"><span data-stu-id="6e209-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [<span data-ttu-id="6e209-159">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="6e209-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="6e209-160">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="6e209-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="6e209-161">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="6e209-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
