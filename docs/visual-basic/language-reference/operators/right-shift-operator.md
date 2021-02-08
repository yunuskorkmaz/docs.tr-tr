---
description: " >> Işleci hakkında daha fazla bilgi edinin (Visual Basic)"
title: '>> Operatör'
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
ms.openlocfilehash: 125b93f129734d196bd1f7f9c4fde86ab5d66319
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795306"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="29fcd-103">>> Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29fcd-103">>> Operator (Visual Basic)</span></span>

<span data-ttu-id="29fcd-104">Bit bir düzende aritmetik sağa kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-104">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29fcd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="29fcd-105">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="29fcd-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="29fcd-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="29fcd-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-107">Required.</span></span> <span data-ttu-id="29fcd-108">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="29fcd-108">Integral numeric value.</span></span> <span data-ttu-id="29fcd-109">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="29fcd-109">The result of shifting the bit pattern.</span></span> <span data-ttu-id="29fcd-110">Veri türü, ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="29fcd-110">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="29fcd-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-111">Required.</span></span> <span data-ttu-id="29fcd-112">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="29fcd-112">Integral numeric expression.</span></span> <span data-ttu-id="29fcd-113">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="29fcd-113">The bit pattern to be shifted.</span></span> <span data-ttu-id="29fcd-114">Veri türü bir integral türü ( `SByte` , `Byte` ,,,, `Short` `UShort` `Integer` `UInteger` , `Long` , veya `ULong` ) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29fcd-114">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="29fcd-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-115">Required.</span></span> <span data-ttu-id="29fcd-116">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="29fcd-116">Numeric expression.</span></span> <span data-ttu-id="29fcd-117">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="29fcd-117">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="29fcd-118">Veri türü `Integer` veya olarak ayarlanmalıdır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="29fcd-118">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29fcd-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29fcd-119">Remarks</span></span>  

 <span data-ttu-id="29fcd-120">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-120">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="29fcd-121">Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki (oturum açma) biti, sol taraftaki bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="29fcd-121">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="29fcd-122">Yani `pattern` negatif bir değer varsa, karıştırılmış konumlar bir olarak ayarlanır; Aksi takdirde sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="29fcd-122">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="29fcd-123">,, Ve veri türlerinin `Byte` `UShort` imzasız olduğunu `UInteger` ve bu `ULong` nedenle, yaymaya yönelik bir işaret biti olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="29fcd-123">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="29fcd-124">`pattern`Herhangi bir işaretsiz türde ise, karıştırılmış konumlar her zaman sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="29fcd-124">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="29fcd-125">Sonucun tutabileceğinden daha fazla bite göre kaydırmasını engellemek için, ' ın ' ın `amount` veri türüne karşılık gelen bir boyut maskesiyle değerini Visual Basic `pattern` .</span><span class="sxs-lookup"><span data-stu-id="29fcd-125">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="29fcd-126">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29fcd-126">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="29fcd-127">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29fcd-127">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="29fcd-128">Veri türü `pattern`</span><span class="sxs-lookup"><span data-stu-id="29fcd-128">Data type of `pattern`</span></span>|<span data-ttu-id="29fcd-129">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="29fcd-129">Size mask (decimal)</span></span>|<span data-ttu-id="29fcd-130">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="29fcd-130">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="29fcd-131">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="29fcd-131">`SByte`, `Byte`</span></span>|<span data-ttu-id="29fcd-132">7</span><span class="sxs-lookup"><span data-stu-id="29fcd-132">7</span></span>|<span data-ttu-id="29fcd-133">&H00000007</span><span class="sxs-lookup"><span data-stu-id="29fcd-133">&H00000007</span></span>|  
|<span data-ttu-id="29fcd-134">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="29fcd-134">`Short`, `UShort`</span></span>|<span data-ttu-id="29fcd-135">15</span><span class="sxs-lookup"><span data-stu-id="29fcd-135">15</span></span>|<span data-ttu-id="29fcd-136">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="29fcd-136">&H0000000F</span></span>|  
|<span data-ttu-id="29fcd-137">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="29fcd-137">`Integer`, `UInteger`</span></span>|<span data-ttu-id="29fcd-138">31</span><span class="sxs-lookup"><span data-stu-id="29fcd-138">31</span></span>|<span data-ttu-id="29fcd-139">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="29fcd-139">&H0000001F</span></span>|  
|<span data-ttu-id="29fcd-140">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="29fcd-140">`Long`, `ULong`</span></span>|<span data-ttu-id="29fcd-141">63</span><span class="sxs-lookup"><span data-stu-id="29fcd-141">63</span></span>|<span data-ttu-id="29fcd-142">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="29fcd-142">&H0000003F</span></span>|  
  
 <span data-ttu-id="29fcd-143">`amount`Sıfırsa, değeri `result` değeri ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="29fcd-143">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="29fcd-144">`amount`Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-144">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="29fcd-145">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="29fcd-145">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="29fcd-146">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="29fcd-146">Overloading</span></span>  

 <span data-ttu-id="29fcd-147">`>>`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-147">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="29fcd-148">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="29fcd-148">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="29fcd-149">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="29fcd-149">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29fcd-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="29fcd-150">Example</span></span>  

 <span data-ttu-id="29fcd-151">Aşağıdaki örnek, `>>` tam sayı değerlerinde aritmetik sağa kaymalar gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="29fcd-151">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="29fcd-152">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-152">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="29fcd-153">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29fcd-153">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="29fcd-154">`result1` 2560 ' dir (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="29fcd-154">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="29fcd-155">`result2` 160 ' dir (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="29fcd-155">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="29fcd-156">`result3` 2 ' dir (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="29fcd-156">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="29fcd-157">`result4` 640 ' dir (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="29fcd-157">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="29fcd-158">`result5` 0 ' dır (sağa kaydırılan 15 konum).</span><span class="sxs-lookup"><span data-stu-id="29fcd-158">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="29fcd-159">İçin kaydırma miktarı `result4` 18 ve 15 olarak hesaplanır, bu da 2 ' ye eşittir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-159">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="29fcd-160">Aşağıdaki örnek, negatif bir değer üzerinde aritmetik vardiyaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="29fcd-160">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="29fcd-161">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29fcd-161">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="29fcd-162">`negresult1` -512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="29fcd-162">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="29fcd-163">`negresult2` -1 ' dir (işaret biti yayılır).</span><span class="sxs-lookup"><span data-stu-id="29fcd-163">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29fcd-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29fcd-164">See also</span></span>

- [<span data-ttu-id="29fcd-165">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="29fcd-165">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="29fcd-166">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="29fcd-166">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="29fcd-167">>>= Işleci</span><span class="sxs-lookup"><span data-stu-id="29fcd-167">>>= Operator</span></span>](right-shift-assignment-operator.md)
- [<span data-ttu-id="29fcd-168">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="29fcd-168">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="29fcd-169">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="29fcd-169">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="29fcd-170">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="29fcd-170">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
