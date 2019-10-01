---
title: '>> İşleç (Visual Basic)'
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
ms.openlocfilehash: 337d651e831dc2ab132056f6e9a1f2b5300bf7f8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701322"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="44266-102">> > Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44266-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="44266-103">Bit bir düzende aritmetik sağa kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44266-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44266-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44266-104">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="44266-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="44266-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="44266-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="44266-106">Required.</span></span> <span data-ttu-id="44266-107">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="44266-107">Integral numeric value.</span></span> <span data-ttu-id="44266-108">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="44266-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="44266-109">Veri türü `pattern` ' dır.</span><span class="sxs-lookup"><span data-stu-id="44266-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="44266-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="44266-110">Required.</span></span> <span data-ttu-id="44266-111">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="44266-111">Integral numeric expression.</span></span> <span data-ttu-id="44266-112">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="44266-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="44266-113">Veri türü bir tam sayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="44266-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="44266-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="44266-114">Required.</span></span> <span data-ttu-id="44266-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="44266-115">Numeric expression.</span></span> <span data-ttu-id="44266-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="44266-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="44266-117">Veri türü `Integer` olmalı veya `Integer` ' e genişlemelidir.</span><span class="sxs-lookup"><span data-stu-id="44266-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44266-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44266-118">Remarks</span></span>  
 <span data-ttu-id="44266-119">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44266-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="44266-120">Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki (oturum açma) biti, sol taraftaki bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="44266-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="44266-121">Bu, `pattern` negatif bir değere sahipse, karıştırılmış konumların tek olarak ayarlandığı anlamına gelir; Aksi takdirde, sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="44266-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="44266-122">@No__t-0, `UShort`, `UInteger` ve `ULong` veri türlerinin işaretsiz olduğunu ve bu nedenle yaymaya yönelik bir oturum açma işlemi olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="44266-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="44266-123">@No__t-0 herhangi bir işaretsiz türde ise, karıştırılmış konumlar her zaman sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="44266-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="44266-124">Sonucun tutabileceğinden daha fazla bite göre kaydırmasını engellemek için, Visual Basic `amount` değeri `pattern` veri türüne karşılık gelen bir boyut maskesiyle.</span><span class="sxs-lookup"><span data-stu-id="44266-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="44266-125">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44266-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="44266-126">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="44266-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="44266-127">@No__t veri türü-0</span><span class="sxs-lookup"><span data-stu-id="44266-127">Data type of `pattern`</span></span>|<span data-ttu-id="44266-128">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="44266-128">Size mask (decimal)</span></span>|<span data-ttu-id="44266-129">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="44266-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="44266-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="44266-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="44266-131">7</span><span class="sxs-lookup"><span data-stu-id="44266-131">7</span></span>|<span data-ttu-id="44266-132">& H00000007</span><span class="sxs-lookup"><span data-stu-id="44266-132">&H00000007</span></span>|  
|<span data-ttu-id="44266-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="44266-133">`Short`, `UShort`</span></span>|<span data-ttu-id="44266-134">15</span><span class="sxs-lookup"><span data-stu-id="44266-134">15</span></span>|<span data-ttu-id="44266-135">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="44266-135">&H0000000F</span></span>|  
|<span data-ttu-id="44266-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="44266-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="44266-137">31</span><span class="sxs-lookup"><span data-stu-id="44266-137">31</span></span>|<span data-ttu-id="44266-138">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="44266-138">&H0000001F</span></span>|  
|<span data-ttu-id="44266-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="44266-139">`Long`, `ULong`</span></span>|<span data-ttu-id="44266-140">63</span><span class="sxs-lookup"><span data-stu-id="44266-140">63</span></span>|<span data-ttu-id="44266-141">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="44266-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="44266-142">@No__t-0 sıfırsa, `result` değeri `pattern` değeri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="44266-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="44266-143">@No__t-0 negatifse, imzasız bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="44266-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="44266-144">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="44266-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="44266-145">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="44266-145">Overloading</span></span>  
 <span data-ttu-id="44266-146">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="44266-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="44266-147">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="44266-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="44266-148">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="44266-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44266-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="44266-149">Example</span></span>  
 <span data-ttu-id="44266-150">Aşağıdaki örnek, tam sayı değerlerinde aritmetik sağa kaymalar gerçekleştirmek için `>>` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44266-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="44266-151">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44266-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="44266-152">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="44266-152">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="44266-153">`result1`, 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="44266-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="44266-154">`result2`, 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="44266-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="44266-155">`result3`, 2 ' dir (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="44266-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="44266-156">`result4`, 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="44266-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="44266-157">`result5` 0 ' dır (sağa kaydırılan 15 konum).</span><span class="sxs-lookup"><span data-stu-id="44266-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="44266-158">@No__t-0 için SHIFT miktarı 18 ve 15 olarak hesaplanır, bu da 2 ' ye eşittir.</span><span class="sxs-lookup"><span data-stu-id="44266-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="44266-159">Aşağıdaki örnek, negatif bir değer üzerinde aritmetik vardiyaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="44266-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="44266-160">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="44266-160">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="44266-161">`negresult1`,-512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="44266-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="44266-162">`negresult2`,-1 ' dir (işaret biti yayılır).</span><span class="sxs-lookup"><span data-stu-id="44266-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44266-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44266-163">See also</span></span>

- [<span data-ttu-id="44266-164">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="44266-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="44266-165">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="44266-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="44266-166">>>= İşleci</span><span class="sxs-lookup"><span data-stu-id="44266-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="44266-167">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="44266-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="44266-168">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="44266-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="44266-169">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="44266-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
