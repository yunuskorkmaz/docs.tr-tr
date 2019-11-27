---
title: << İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 327d0e5cbd1ebcc43bd47fb068f4513940c2165a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350978"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8c2cc-102">\<\< Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c2cc-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="8c2cc-103">Bit bir düzende aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c2cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c2cc-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="8c2cc-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8c2cc-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="8c2cc-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-106">Required.</span></span> <span data-ttu-id="8c2cc-107">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-107">Integral numeric value.</span></span> <span data-ttu-id="8c2cc-108">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="8c2cc-109">Veri türü `pattern`ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="8c2cc-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-110">Required.</span></span> <span data-ttu-id="8c2cc-111">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-111">Integral numeric expression.</span></span> <span data-ttu-id="8c2cc-112">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="8c2cc-113">Veri türü bir tam sayı türü (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`veya `ULong`) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="8c2cc-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-114">Required.</span></span> <span data-ttu-id="8c2cc-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-115">Numeric expression.</span></span> <span data-ttu-id="8c2cc-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="8c2cc-117">Veri türü `Integer` veya `Integer`için genişlemelidir.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c2cc-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c2cc-118">Remarks</span></span>  
 <span data-ttu-id="8c2cc-119">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="8c2cc-120">Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="8c2cc-121">Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, `amount` değerini `pattern`veri türüne karşılık gelen bir boyut maskesiyle Visual Basic maskeleri.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="8c2cc-122">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="8c2cc-123">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8c2cc-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="8c2cc-124">`pattern` veri türü</span><span class="sxs-lookup"><span data-stu-id="8c2cc-124">Data type of `pattern`</span></span>|<span data-ttu-id="8c2cc-125">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="8c2cc-125">Size mask (decimal)</span></span>|<span data-ttu-id="8c2cc-126">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="8c2cc-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="8c2cc-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="8c2cc-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="8c2cc-128">7</span><span class="sxs-lookup"><span data-stu-id="8c2cc-128">7</span></span>|<span data-ttu-id="8c2cc-129">& H00000007</span><span class="sxs-lookup"><span data-stu-id="8c2cc-129">&H00000007</span></span>|  
|<span data-ttu-id="8c2cc-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="8c2cc-130">`Short`, `UShort`</span></span>|<span data-ttu-id="8c2cc-131">15</span><span class="sxs-lookup"><span data-stu-id="8c2cc-131">15</span></span>|<span data-ttu-id="8c2cc-132">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="8c2cc-132">&H0000000F</span></span>|  
|<span data-ttu-id="8c2cc-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="8c2cc-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="8c2cc-134">31</span><span class="sxs-lookup"><span data-stu-id="8c2cc-134">31</span></span>|<span data-ttu-id="8c2cc-135">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="8c2cc-135">&H0000001F</span></span>|  
|<span data-ttu-id="8c2cc-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="8c2cc-136">`Long`, `ULong`</span></span>|<span data-ttu-id="8c2cc-137">63</span><span class="sxs-lookup"><span data-stu-id="8c2cc-137">63</span></span>|<span data-ttu-id="8c2cc-138">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="8c2cc-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="8c2cc-139">`amount` sıfırsa, `result` değeri `pattern`değeriyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="8c2cc-140">`amount` negatifse, imzasız bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="8c2cc-141">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c2cc-142">`<<` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8c2cc-143">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="8c2cc-144">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8c2cc-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c2cc-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c2cc-145">Example</span></span>  
 <span data-ttu-id="8c2cc-146">Aşağıdaki örnek, tamsayı değerlerinde aritmetik sol vardiyaları gerçekleştirmek için `<<` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="8c2cc-147">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="8c2cc-148">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8c2cc-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="8c2cc-149">`result1` 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="8c2cc-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="8c2cc-150">`result2` 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="8c2cc-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="8c2cc-151">`result3`-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="8c2cc-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="8c2cc-152">`result4` 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="8c2cc-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="8c2cc-153">`result5` 0 ' dır (sola kaydırılan 15 konum).</span><span class="sxs-lookup"><span data-stu-id="8c2cc-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="8c2cc-154">`result4` için kaydırma miktarı 17 ve 15 olarak hesaplanır ve 1 eşittir.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c2cc-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c2cc-155">See also</span></span>

- [<span data-ttu-id="8c2cc-156">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8c2cc-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="8c2cc-157">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8c2cc-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8c2cc-158"><<= İşleci</span><span class="sxs-lookup"><span data-stu-id="8c2cc-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="8c2cc-159">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="8c2cc-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8c2cc-160">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="8c2cc-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8c2cc-161">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="8c2cc-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
