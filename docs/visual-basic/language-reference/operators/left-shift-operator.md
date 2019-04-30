---
title: << İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 75c16c27dc919ba365cbe3c28c61a1e46496b0ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768296"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="69ada-102">\<\< İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69ada-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="69ada-103">Bir bit desenine aritmetik sola kaydırma uygular.</span><span class="sxs-lookup"><span data-stu-id="69ada-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69ada-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69ada-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="69ada-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="69ada-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="69ada-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="69ada-106">Required.</span></span> <span data-ttu-id="69ada-107">Tamsayı sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="69ada-107">Integral numeric value.</span></span> <span data-ttu-id="69ada-108">Bit deseninin kaydırma sonucu.</span><span class="sxs-lookup"><span data-stu-id="69ada-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="69ada-109">Veri türü, aynı olduğu `pattern`.</span><span class="sxs-lookup"><span data-stu-id="69ada-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="69ada-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="69ada-110">Required.</span></span> <span data-ttu-id="69ada-111">Tamsayı sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="69ada-111">Integral numeric expression.</span></span> <span data-ttu-id="69ada-112">Kaydırılmasına bit deseni.</span><span class="sxs-lookup"><span data-stu-id="69ada-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="69ada-113">Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="69ada-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="69ada-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="69ada-114">Required.</span></span> <span data-ttu-id="69ada-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="69ada-115">Numeric expression.</span></span> <span data-ttu-id="69ada-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="69ada-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="69ada-117">Veri türü olmalıdır `Integer` veya genişletmek için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="69ada-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69ada-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69ada-118">Remarks</span></span>  
 <span data-ttu-id="69ada-119">Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir.</span><span class="sxs-lookup"><span data-stu-id="69ada-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="69ada-120">Aritmetik sola kaydırma, sonuç veri türü aralığının dışında kaydırılacak bitlerin atılır ve sağ tarafta işleci boşaltılmış bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="69ada-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="69ada-121">Bir sonuç tutabileceğinden daha fazla bit kaydırma önlemek için Visual Basic değerini maskeleri `amount` veri türüne karşılık gelen bir boyut maskesiyle `pattern`.</span><span class="sxs-lookup"><span data-stu-id="69ada-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="69ada-122">İkili ve bu değerleri değiştirme miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69ada-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="69ada-123">Boyutu maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="69ada-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="69ada-124">Veri türü `pattern`</span><span class="sxs-lookup"><span data-stu-id="69ada-124">Data type of `pattern`</span></span>|<span data-ttu-id="69ada-125">Boyutu maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="69ada-125">Size mask (decimal)</span></span>|<span data-ttu-id="69ada-126">Boyutu maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="69ada-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="69ada-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="69ada-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="69ada-128">7</span><span class="sxs-lookup"><span data-stu-id="69ada-128">7</span></span>|<span data-ttu-id="69ada-129">&AMP; H00000007</span><span class="sxs-lookup"><span data-stu-id="69ada-129">&H00000007</span></span>|  
|<span data-ttu-id="69ada-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="69ada-130">`Short`, `UShort`</span></span>|<span data-ttu-id="69ada-131">15</span><span class="sxs-lookup"><span data-stu-id="69ada-131">15</span></span>|<span data-ttu-id="69ada-132">&AMP; H0000000F</span><span class="sxs-lookup"><span data-stu-id="69ada-132">&H0000000F</span></span>|  
|<span data-ttu-id="69ada-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="69ada-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="69ada-134">31</span><span class="sxs-lookup"><span data-stu-id="69ada-134">31</span></span>|<span data-ttu-id="69ada-135">&AMP; H0000001F</span><span class="sxs-lookup"><span data-stu-id="69ada-135">&H0000001F</span></span>|  
|<span data-ttu-id="69ada-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="69ada-136">`Long`, `ULong`</span></span>|<span data-ttu-id="69ada-137">63</span><span class="sxs-lookup"><span data-stu-id="69ada-137">63</span></span>|<span data-ttu-id="69ada-138">&AMP; H0000003F</span><span class="sxs-lookup"><span data-stu-id="69ada-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="69ada-139">Varsa `amount` değeri sıfır olan `result` değeri olarak aynı `pattern`.</span><span class="sxs-lookup"><span data-stu-id="69ada-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="69ada-140">Varsa `amount` olan negatif, işaretsiz bir değer olarak yapılan ve uygun boyutta maske ile maskelenir.</span><span class="sxs-lookup"><span data-stu-id="69ada-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="69ada-141">Aritmetik kaydırmalar hiçbir zaman taşması özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69ada-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69ada-142">`<<` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="69ada-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="69ada-143">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="69ada-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="69ada-144">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="69ada-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69ada-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="69ada-145">Example</span></span>  
 <span data-ttu-id="69ada-146">Aşağıdaki örnekte `<<` kaydırmalar sol tam sayı değerleri üzerinde aritmetik işlemleri için işleci.</span><span class="sxs-lookup"><span data-stu-id="69ada-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="69ada-147">Sonucu her zaman aynı veri türüne, kaydırılacak ifade sahiptir.</span><span class="sxs-lookup"><span data-stu-id="69ada-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="69ada-148">Önceki örneği sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="69ada-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="69ada-149">`result1` 192 (0000 0000 1100 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="69ada-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="69ada-150">`result2` 3072 (0000 1100 0000 0000) olan.</span><span class="sxs-lookup"><span data-stu-id="69ada-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="69ada-151">`result3` -32768 (1000 0000 0000 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="69ada-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="69ada-152">`result4` 384 (0000 0001 1000 0000) olur.</span><span class="sxs-lookup"><span data-stu-id="69ada-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="69ada-153">`result5` (sol ötelenen 15 basamak) 0'dır.</span><span class="sxs-lookup"><span data-stu-id="69ada-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="69ada-154">Değiştirme miktarı için `result4` 17 ' hesaplanır ve hangi eşittir 1 15.</span><span class="sxs-lookup"><span data-stu-id="69ada-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69ada-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69ada-155">See also</span></span>

- [<span data-ttu-id="69ada-156">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="69ada-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="69ada-157">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="69ada-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="69ada-158"><<= İşleci</span><span class="sxs-lookup"><span data-stu-id="69ada-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="69ada-159">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="69ada-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="69ada-160">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="69ada-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="69ada-161">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="69ada-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
