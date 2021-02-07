---
description: " << Işleci hakkında daha fazla bilgi edinin (Visual Basic)"
title: << İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 079af61e5c4ce3834db0877feace724c74c8169c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665633"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="af43f-103">\<\< İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af43f-103">\<\< Operator (Visual Basic)</span></span>

<span data-ttu-id="af43f-104">Bit bir düzende aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="af43f-104">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af43f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="af43f-105">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="af43f-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="af43f-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="af43f-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af43f-107">Required.</span></span> <span data-ttu-id="af43f-108">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="af43f-108">Integral numeric value.</span></span> <span data-ttu-id="af43f-109">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="af43f-109">The result of shifting the bit pattern.</span></span> <span data-ttu-id="af43f-110">Veri türü, ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="af43f-110">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="af43f-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af43f-111">Required.</span></span> <span data-ttu-id="af43f-112">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="af43f-112">Integral numeric expression.</span></span> <span data-ttu-id="af43f-113">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="af43f-113">The bit pattern to be shifted.</span></span> <span data-ttu-id="af43f-114">Veri türü bir integral türü ( `SByte` , `Byte` ,,,, `Short` `UShort` `Integer` `UInteger` , `Long` , veya `ULong` ) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af43f-114">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="af43f-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af43f-115">Required.</span></span> <span data-ttu-id="af43f-116">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="af43f-116">Numeric expression.</span></span> <span data-ttu-id="af43f-117">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="af43f-117">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="af43f-118">Veri türü `Integer` veya olarak ayarlanmalıdır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="af43f-118">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af43f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af43f-119">Remarks</span></span>  

 <span data-ttu-id="af43f-120">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af43f-120">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="af43f-121">Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="af43f-121">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="af43f-122">Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, ' ın değerini, `amount` veri türüne karşılık gelen bir boyut maskesiyle Visual Basic `pattern` .</span><span class="sxs-lookup"><span data-stu-id="af43f-122">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="af43f-123">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af43f-123">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="af43f-124">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="af43f-124">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="af43f-125">Veri türü `pattern`</span><span class="sxs-lookup"><span data-stu-id="af43f-125">Data type of `pattern`</span></span>|<span data-ttu-id="af43f-126">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="af43f-126">Size mask (decimal)</span></span>|<span data-ttu-id="af43f-127">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="af43f-127">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="af43f-128">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="af43f-128">`SByte`, `Byte`</span></span>|<span data-ttu-id="af43f-129">7</span><span class="sxs-lookup"><span data-stu-id="af43f-129">7</span></span>|<span data-ttu-id="af43f-130">&H00000007</span><span class="sxs-lookup"><span data-stu-id="af43f-130">&H00000007</span></span>|  
|<span data-ttu-id="af43f-131">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="af43f-131">`Short`, `UShort`</span></span>|<span data-ttu-id="af43f-132">15</span><span class="sxs-lookup"><span data-stu-id="af43f-132">15</span></span>|<span data-ttu-id="af43f-133">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="af43f-133">&H0000000F</span></span>|  
|<span data-ttu-id="af43f-134">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="af43f-134">`Integer`, `UInteger`</span></span>|<span data-ttu-id="af43f-135">31</span><span class="sxs-lookup"><span data-stu-id="af43f-135">31</span></span>|<span data-ttu-id="af43f-136">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="af43f-136">&H0000001F</span></span>|  
|<span data-ttu-id="af43f-137">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="af43f-137">`Long`, `ULong`</span></span>|<span data-ttu-id="af43f-138">63</span><span class="sxs-lookup"><span data-stu-id="af43f-138">63</span></span>|<span data-ttu-id="af43f-139">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="af43f-139">&H0000003F</span></span>|  
  
 <span data-ttu-id="af43f-140">`amount`Sıfırsa, değeri `result` değeri ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="af43f-140">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="af43f-141">`amount`Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="af43f-141">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="af43f-142">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="af43f-142">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af43f-143">`<<`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="af43f-143">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="af43f-144">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="af43f-144">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="af43f-145">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="af43f-145">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af43f-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="af43f-146">Example</span></span>  

 <span data-ttu-id="af43f-147">Aşağıdaki örnek, `<<` tam sayı değerlerinde aritmetik sol vardiyaları gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="af43f-147">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="af43f-148">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="af43f-148">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="af43f-149">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="af43f-149">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="af43f-150">`result1` 192 ' dir (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="af43f-150">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="af43f-151">`result2` 3072 ' dir (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="af43f-151">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="af43f-152">`result3` -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="af43f-152">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="af43f-153">`result4` 384 ' dir (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="af43f-153">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="af43f-154">`result5` 0 ' dır (sola kaydırılacağı 15 konum).</span><span class="sxs-lookup"><span data-stu-id="af43f-154">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="af43f-155">İçin kaydırma miktarı `result4` 17 ve 15 olarak hesaplanır, 1 eşittir.</span><span class="sxs-lookup"><span data-stu-id="af43f-155">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af43f-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af43f-156">See also</span></span>

- [<span data-ttu-id="af43f-157">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="af43f-157">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="af43f-158">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="af43f-158">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="af43f-159"><<= Işleci</span><span class="sxs-lookup"><span data-stu-id="af43f-159"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="af43f-160">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="af43f-160">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="af43f-161">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="af43f-161">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="af43f-162">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="af43f-162">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
