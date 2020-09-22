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
ms.openlocfilehash: 77bf26d4e6bb068f9130deed5eb1ecbaee62afce
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866791"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="eb433-102">\<\< İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb433-102">\<\< Operator (Visual Basic)</span></span>

<span data-ttu-id="eb433-103">Bit bir düzende aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="eb433-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb433-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb433-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="eb433-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="eb433-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="eb433-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb433-106">Required.</span></span> <span data-ttu-id="eb433-107">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="eb433-107">Integral numeric value.</span></span> <span data-ttu-id="eb433-108">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="eb433-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="eb433-109">Veri türü, ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="eb433-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="eb433-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb433-110">Required.</span></span> <span data-ttu-id="eb433-111">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="eb433-111">Integral numeric expression.</span></span> <span data-ttu-id="eb433-112">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="eb433-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="eb433-113">Veri türü bir integral türü ( `SByte` , `Byte` ,,,, `Short` `UShort` `Integer` `UInteger` , `Long` , veya `ULong` ) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb433-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="eb433-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb433-114">Required.</span></span> <span data-ttu-id="eb433-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="eb433-115">Numeric expression.</span></span> <span data-ttu-id="eb433-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="eb433-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="eb433-117">Veri türü `Integer` veya olarak ayarlanmalıdır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="eb433-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb433-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb433-118">Remarks</span></span>  

 <span data-ttu-id="eb433-119">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb433-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="eb433-120">Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="eb433-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="eb433-121">Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, ' ın değerini, `amount` veri türüne karşılık gelen bir boyut maskesiyle Visual Basic `pattern` .</span><span class="sxs-lookup"><span data-stu-id="eb433-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="eb433-122">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb433-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="eb433-123">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="eb433-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="eb433-124">Veri türü `pattern`</span><span class="sxs-lookup"><span data-stu-id="eb433-124">Data type of `pattern`</span></span>|<span data-ttu-id="eb433-125">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="eb433-125">Size mask (decimal)</span></span>|<span data-ttu-id="eb433-126">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="eb433-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="eb433-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="eb433-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="eb433-128">7</span><span class="sxs-lookup"><span data-stu-id="eb433-128">7</span></span>|<span data-ttu-id="eb433-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="eb433-129">&H00000007</span></span>|  
|<span data-ttu-id="eb433-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="eb433-130">`Short`, `UShort`</span></span>|<span data-ttu-id="eb433-131">15</span><span class="sxs-lookup"><span data-stu-id="eb433-131">15</span></span>|<span data-ttu-id="eb433-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="eb433-132">&H0000000F</span></span>|  
|<span data-ttu-id="eb433-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="eb433-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="eb433-134">31</span><span class="sxs-lookup"><span data-stu-id="eb433-134">31</span></span>|<span data-ttu-id="eb433-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="eb433-135">&H0000001F</span></span>|  
|<span data-ttu-id="eb433-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="eb433-136">`Long`, `ULong`</span></span>|<span data-ttu-id="eb433-137">63</span><span class="sxs-lookup"><span data-stu-id="eb433-137">63</span></span>|<span data-ttu-id="eb433-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="eb433-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="eb433-139">`amount`Sıfırsa, değeri `result` değeri ile aynıdır `pattern` .</span><span class="sxs-lookup"><span data-stu-id="eb433-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="eb433-140">`amount`Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="eb433-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="eb433-141">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="eb433-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb433-142">`<<`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="eb433-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="eb433-143">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="eb433-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="eb433-144">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="eb433-144">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb433-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb433-145">Example</span></span>  

 <span data-ttu-id="eb433-146">Aşağıdaki örnek, `<<` tam sayı değerlerinde aritmetik sol vardiyaları gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb433-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="eb433-147">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eb433-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="eb433-148">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="eb433-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="eb433-149">`result1` 192 ' dir (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="eb433-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="eb433-150">`result2` 3072 ' dir (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="eb433-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="eb433-151">`result3` -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="eb433-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="eb433-152">`result4` 384 ' dir (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="eb433-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="eb433-153">`result5` 0 ' dır (sola kaydırılacağı 15 konum).</span><span class="sxs-lookup"><span data-stu-id="eb433-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="eb433-154">İçin kaydırma miktarı `result4` 17 ve 15 olarak hesaplanır, 1 eşittir.</span><span class="sxs-lookup"><span data-stu-id="eb433-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb433-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb433-155">See also</span></span>

- [<span data-ttu-id="eb433-156">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="eb433-156">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="eb433-157">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="eb433-157">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="eb433-158"><<= Işleci</span><span class="sxs-lookup"><span data-stu-id="eb433-158"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="eb433-159">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="eb433-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="eb433-160">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="eb433-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="eb433-161">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="eb433-161">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
