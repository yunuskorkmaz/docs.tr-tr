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
ms.openlocfilehash: 1128b32a739e7dbf3893dcd19b37247cd4643c85
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370641"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="59aa0-102">\<\<İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59aa0-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="59aa0-103">Bit bir düzende aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59aa0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59aa0-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="59aa0-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="59aa0-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="59aa0-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-106">Required.</span></span> <span data-ttu-id="59aa0-107">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="59aa0-107">Integral numeric value.</span></span> <span data-ttu-id="59aa0-108">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="59aa0-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="59aa0-109">Veri türü, ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="59aa0-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="59aa0-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-110">Required.</span></span> <span data-ttu-id="59aa0-111">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="59aa0-111">Integral numeric expression.</span></span> <span data-ttu-id="59aa0-112">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="59aa0-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="59aa0-113">Veri türü bir integral türü ( `SByte` , `Byte` ,,,, `Short` `UShort` `Integer` `UInteger` , `Long` , veya `ULong` ) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59aa0-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="59aa0-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-114">Required.</span></span> <span data-ttu-id="59aa0-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="59aa0-115">Numeric expression.</span></span> <span data-ttu-id="59aa0-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="59aa0-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="59aa0-117">Veri türü `Integer` veya olarak ayarlanmalıdır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="59aa0-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59aa0-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59aa0-118">Remarks</span></span>  
 <span data-ttu-id="59aa0-119">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="59aa0-120">Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="59aa0-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="59aa0-121">Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, ' ın değerini, `amount` veri türüne karşılık gelen bir boyut maskesiyle Visual Basic `pattern` .</span><span class="sxs-lookup"><span data-stu-id="59aa0-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="59aa0-122">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59aa0-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="59aa0-123">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="59aa0-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="59aa0-124">Veri türü`pattern`</span><span class="sxs-lookup"><span data-stu-id="59aa0-124">Data type of `pattern`</span></span>|<span data-ttu-id="59aa0-125">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="59aa0-125">Size mask (decimal)</span></span>|<span data-ttu-id="59aa0-126">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="59aa0-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="59aa0-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="59aa0-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="59aa0-128">7</span><span class="sxs-lookup"><span data-stu-id="59aa0-128">7</span></span>|<span data-ttu-id="59aa0-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="59aa0-129">&H00000007</span></span>|  
|<span data-ttu-id="59aa0-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="59aa0-130">`Short`, `UShort`</span></span>|<span data-ttu-id="59aa0-131">15</span><span class="sxs-lookup"><span data-stu-id="59aa0-131">15</span></span>|<span data-ttu-id="59aa0-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="59aa0-132">&H0000000F</span></span>|  
|<span data-ttu-id="59aa0-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="59aa0-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="59aa0-134">31</span><span class="sxs-lookup"><span data-stu-id="59aa0-134">31</span></span>|<span data-ttu-id="59aa0-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="59aa0-135">&H0000001F</span></span>|  
|<span data-ttu-id="59aa0-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="59aa0-136">`Long`, `ULong`</span></span>|<span data-ttu-id="59aa0-137">63</span><span class="sxs-lookup"><span data-stu-id="59aa0-137">63</span></span>|<span data-ttu-id="59aa0-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="59aa0-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="59aa0-139">`amount`Sıfırsa, değeri `result` değeri ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="59aa0-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="59aa0-140">`amount`Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="59aa0-141">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="59aa0-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59aa0-142">`<<`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="59aa0-143">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="59aa0-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="59aa0-144">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="59aa0-144">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59aa0-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="59aa0-145">Example</span></span>  
 <span data-ttu-id="59aa0-146">Aşağıdaki örnek, `<<` tam sayı değerlerinde aritmetik sol vardiyaları gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="59aa0-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="59aa0-147">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="59aa0-148">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="59aa0-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="59aa0-149">`result1`192 ' dir (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="59aa0-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="59aa0-150">`result2`3072 ' dir (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="59aa0-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="59aa0-151">`result3`-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="59aa0-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="59aa0-152">`result4`384 ' dir (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="59aa0-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="59aa0-153">`result5`0 ' dır (sola kaydırılacağı 15 konum).</span><span class="sxs-lookup"><span data-stu-id="59aa0-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="59aa0-154">İçin kaydırma miktarı `result4` 17 ve 15 olarak hesaplanır, 1 eşittir.</span><span class="sxs-lookup"><span data-stu-id="59aa0-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59aa0-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59aa0-155">See also</span></span>

- [<span data-ttu-id="59aa0-156">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="59aa0-156">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="59aa0-157">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="59aa0-157">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="59aa0-158"><<= Işleci</span><span class="sxs-lookup"><span data-stu-id="59aa0-158"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="59aa0-159">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="59aa0-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="59aa0-160">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="59aa0-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="59aa0-161">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="59aa0-161">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
