---
title: < < Işleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: d6b186ad519bcd7cf82cce12523f2d75e09317cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966894"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="41351-102">\<\<İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41351-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="41351-103">Bit bir düzende aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="41351-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41351-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41351-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="41351-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="41351-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="41351-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="41351-106">Required.</span></span> <span data-ttu-id="41351-107">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="41351-107">Integral numeric value.</span></span> <span data-ttu-id="41351-108">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="41351-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="41351-109">Veri türü, ile `pattern`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="41351-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="41351-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="41351-110">Required.</span></span> <span data-ttu-id="41351-111">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="41351-111">Integral numeric expression.</span></span> <span data-ttu-id="41351-112">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="41351-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="41351-113">`SByte`Veri türü bir integral türü (, `UShort` `Short` `Byte`,,, `Integer` `UInteger`, ,`Long`, veya`ULong`) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41351-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="41351-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="41351-114">Required.</span></span> <span data-ttu-id="41351-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="41351-115">Numeric expression.</span></span> <span data-ttu-id="41351-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="41351-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="41351-117">Veri türü `Integer` veya olarak `Integer`ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41351-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41351-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41351-118">Remarks</span></span>  
 <span data-ttu-id="41351-119">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41351-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="41351-120">Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="41351-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="41351-121">Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, ' ın değerini `amount` , veri `pattern`türüne karşılık gelen bir boyut maskesiyle Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41351-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="41351-122">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41351-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="41351-123">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="41351-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="41351-124">Veri türü`pattern`</span><span class="sxs-lookup"><span data-stu-id="41351-124">Data type of `pattern`</span></span>|<span data-ttu-id="41351-125">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="41351-125">Size mask (decimal)</span></span>|<span data-ttu-id="41351-126">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="41351-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="41351-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="41351-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="41351-128">7</span><span class="sxs-lookup"><span data-stu-id="41351-128">7</span></span>|<span data-ttu-id="41351-129">& H00000007</span><span class="sxs-lookup"><span data-stu-id="41351-129">&H00000007</span></span>|  
|<span data-ttu-id="41351-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="41351-130">`Short`, `UShort`</span></span>|<span data-ttu-id="41351-131">15</span><span class="sxs-lookup"><span data-stu-id="41351-131">15</span></span>|<span data-ttu-id="41351-132">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="41351-132">&H0000000F</span></span>|  
|<span data-ttu-id="41351-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="41351-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="41351-134">31</span><span class="sxs-lookup"><span data-stu-id="41351-134">31</span></span>|<span data-ttu-id="41351-135">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="41351-135">&H0000001F</span></span>|  
|<span data-ttu-id="41351-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="41351-136">`Long`, `ULong`</span></span>|<span data-ttu-id="41351-137">63</span><span class="sxs-lookup"><span data-stu-id="41351-137">63</span></span>|<span data-ttu-id="41351-138">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="41351-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="41351-139">Sıfırsa, değeri değeri ile aynıdır `pattern`. `result` `amount`</span><span class="sxs-lookup"><span data-stu-id="41351-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="41351-140">`amount` Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="41351-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="41351-141">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="41351-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41351-142">İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `<<`</span><span class="sxs-lookup"><span data-stu-id="41351-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="41351-143">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="41351-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="41351-144">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="41351-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41351-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="41351-145">Example</span></span>  
 <span data-ttu-id="41351-146">Aşağıdaki örnek, tam sayı `<<` değerlerinde aritmetik sol vardiyaları gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="41351-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="41351-147">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="41351-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="41351-148">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="41351-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="41351-149">`result1`192 ' dir (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="41351-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="41351-150">`result2`3072 ' dir (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="41351-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="41351-151">`result3`-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="41351-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="41351-152">`result4`384 ' dir (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="41351-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="41351-153">`result5`0 ' dır (sola kaydırılacağı 15 konum).</span><span class="sxs-lookup"><span data-stu-id="41351-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="41351-154">İçin `result4` kaydırma miktarı 17 ve 15 olarak hesaplanır, 1 eşittir.</span><span class="sxs-lookup"><span data-stu-id="41351-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41351-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41351-155">See also</span></span>

- [<span data-ttu-id="41351-156">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="41351-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="41351-157">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="41351-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="41351-158"><<= İşleci</span><span class="sxs-lookup"><span data-stu-id="41351-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="41351-159">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="41351-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="41351-160">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="41351-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="41351-161">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="41351-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
