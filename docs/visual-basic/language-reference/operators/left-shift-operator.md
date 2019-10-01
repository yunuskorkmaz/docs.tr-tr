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
ms.openlocfilehash: 1300ab60e825e7910825be2c65dcab90135ba988
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701124"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="36982-102">\< @ no__t-1 Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36982-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="36982-103">Bit bir düzende aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="36982-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36982-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36982-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="36982-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="36982-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="36982-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="36982-106">Required.</span></span> <span data-ttu-id="36982-107">Integral sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="36982-107">Integral numeric value.</span></span> <span data-ttu-id="36982-108">Bit deseninin kaydırinme sonucu.</span><span class="sxs-lookup"><span data-stu-id="36982-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="36982-109">Veri türü `pattern` ' dır.</span><span class="sxs-lookup"><span data-stu-id="36982-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="36982-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="36982-110">Required.</span></span> <span data-ttu-id="36982-111">Integral sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="36982-111">Integral numeric expression.</span></span> <span data-ttu-id="36982-112">Kaydırılan bit deseninin.</span><span class="sxs-lookup"><span data-stu-id="36982-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="36982-113">Veri türü bir tam sayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="36982-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="36982-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="36982-114">Required.</span></span> <span data-ttu-id="36982-115">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="36982-115">Numeric expression.</span></span> <span data-ttu-id="36982-116">Bit deseninin kaydırılacak bit sayısı.</span><span class="sxs-lookup"><span data-stu-id="36982-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="36982-117">Veri türü `Integer` olmalı veya `Integer` ' e genişlemelidir.</span><span class="sxs-lookup"><span data-stu-id="36982-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36982-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36982-118">Remarks</span></span>  
 <span data-ttu-id="36982-119">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="36982-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="36982-120">Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36982-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="36982-121">Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, `amount` değerini `pattern` veri türüne karşılık gelen bir boyut maskesiyle Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="36982-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="36982-122">Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36982-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="36982-123">Boyut maskeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="36982-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="36982-124">@No__t veri türü-0</span><span class="sxs-lookup"><span data-stu-id="36982-124">Data type of `pattern`</span></span>|<span data-ttu-id="36982-125">Boyut maskesi (ondalık)</span><span class="sxs-lookup"><span data-stu-id="36982-125">Size mask (decimal)</span></span>|<span data-ttu-id="36982-126">Boyut maskesi (onaltılık)</span><span class="sxs-lookup"><span data-stu-id="36982-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="36982-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="36982-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="36982-128">7</span><span class="sxs-lookup"><span data-stu-id="36982-128">7</span></span>|<span data-ttu-id="36982-129">& H00000007</span><span class="sxs-lookup"><span data-stu-id="36982-129">&H00000007</span></span>|  
|<span data-ttu-id="36982-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="36982-130">`Short`, `UShort`</span></span>|<span data-ttu-id="36982-131">15</span><span class="sxs-lookup"><span data-stu-id="36982-131">15</span></span>|<span data-ttu-id="36982-132">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="36982-132">&H0000000F</span></span>|  
|<span data-ttu-id="36982-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="36982-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="36982-134">31</span><span class="sxs-lookup"><span data-stu-id="36982-134">31</span></span>|<span data-ttu-id="36982-135">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="36982-135">&H0000001F</span></span>|  
|<span data-ttu-id="36982-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="36982-136">`Long`, `ULong`</span></span>|<span data-ttu-id="36982-137">63</span><span class="sxs-lookup"><span data-stu-id="36982-137">63</span></span>|<span data-ttu-id="36982-138">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="36982-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="36982-139">@No__t-0 sıfırsa, `result` değeri `pattern` değeri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="36982-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="36982-140">@No__t-0 negatifse, imzasız bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.</span><span class="sxs-lookup"><span data-stu-id="36982-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="36982-141">Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="36982-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36982-142">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="36982-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="36982-143">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="36982-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="36982-144">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="36982-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36982-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="36982-145">Example</span></span>  
 <span data-ttu-id="36982-146">Aşağıdaki örnek, tamsayı değerlerinde aritmetik sol vardiyaları gerçekleştirmek için `<<` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36982-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="36982-147">Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="36982-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="36982-148">Önceki örneğin sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="36982-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="36982-149">`result1`, 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="36982-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="36982-150">`result2`, 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="36982-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="36982-151">`result3`,-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="36982-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="36982-152">`result4`, 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="36982-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="36982-153">`result5`, 0 ' dır (soldaki 15 konum).</span><span class="sxs-lookup"><span data-stu-id="36982-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="36982-154">@No__t-0 için SHIFT miktarı 17 ve 15 olarak hesaplanır; bu değer 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="36982-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36982-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36982-155">See also</span></span>

- [<span data-ttu-id="36982-156">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="36982-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="36982-157">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="36982-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="36982-158"><<= İşleci</span><span class="sxs-lookup"><span data-stu-id="36982-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="36982-159">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="36982-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="36982-160">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="36982-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="36982-161">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="36982-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
