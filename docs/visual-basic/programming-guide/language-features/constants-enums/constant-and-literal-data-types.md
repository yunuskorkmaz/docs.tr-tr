---
title: Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 1d030f8058cd497212c20bca8f064f2bedc99fce
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999933"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="f645b-102">Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f645b-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="f645b-103">Bir sabit değer kendisi yerine bir değişkenin değerini veya 3 sayı veya dize "Hello" gibi bir ifadenin sonucu olarak ifade bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="f645b-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="f645b-104">Bir değişmez değerin yerini alır ve bu değer bir değişken değerini değiştirebilir, programın boyunca saklar anlamlı bir ad bir sabittir.</span><span class="sxs-lookup"><span data-stu-id="f645b-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="f645b-105">Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olduğu `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olduğu `On`, tüm sabit bir türle açıkça bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="f645b-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="f645b-106">Aşağıdaki örnekte, veri türü `MyByte` açıkça veri türü olarak bildirilmiş `Byte`:</span><span class="sxs-lookup"><span data-stu-id="f645b-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 <span data-ttu-id="f645b-107">Zaman `Option Infer` olduğu `On` veya `Option Strict` olduğu `Off`, bir veri türüyle belirtmeden bir sabit bildirebilirsiniz bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f645b-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="f645b-108">Derleyici sabiti ifadesinin türünden türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="f645b-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="f645b-109">Varsayılan olarak sayısal tamsayı sabit değeri saçıldığı `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="f645b-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="f645b-110">Kayan noktalı sayılar için varsayılan veri türü `Double`ve anahtar sözcükler `True` ve `False` belirtin bir `Boolean` sabit.</span><span class="sxs-lookup"><span data-stu-id="f645b-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="f645b-111">Değişmez değerler ve tür zorlama</span><span class="sxs-lookup"><span data-stu-id="f645b-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="f645b-112">Bazı durumlarda, belirli bir tür için bir sabit değer zorlamak isteyebilirsiniz; Örneğin, özellikle büyük tamsayı değişmez değer türünde bir değişkene atarken `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f645b-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="f645b-113">Aşağıdaki örnek, bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f645b-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="f645b-114">Değişmez değerin gösterimi hata sonuçları.</span><span class="sxs-lookup"><span data-stu-id="f645b-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="f645b-115">`Decimal` Veri türü tutabilir değeri bu büyük ancak değişmez değer olarak örtük olarak temsil edilen bir `Long`, hangi olamaz.</span><span class="sxs-lookup"><span data-stu-id="f645b-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="f645b-116">İki yolla belirli veri türü için bir sabit değer coerce: bir tür kendisine karakterinin ya da karakterini içinde yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="f645b-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="f645b-117">Türü bir karakteri veya karakterleri kapsayan gerekir hemen önünde ve/veya boşluk olmaması veya herhangi bir türde karakter değişmez değeri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f645b-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="f645b-118">Önceki örnekte iş yapmak için ekleyebilir `D` karakter olarak temsil edilen neden değişmez değer türü bir `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="f645b-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 <span data-ttu-id="f645b-119">Aşağıdaki örnek, türü, kapsayan karakter doğru kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f645b-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 <span data-ttu-id="f645b-120">Aşağıdaki tabloda gösterilen kapsayan karakterleri ve karakter türü Visual Basic'te kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f645b-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="f645b-121">Veri türü</span><span class="sxs-lookup"><span data-stu-id="f645b-121">Data type</span></span>|<span data-ttu-id="f645b-122">Kapsayan karakter</span><span class="sxs-lookup"><span data-stu-id="f645b-122">Enclosing character</span></span>|<span data-ttu-id="f645b-123">Eklenen türü karakteri</span><span class="sxs-lookup"><span data-stu-id="f645b-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="f645b-124">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-124">(none)</span></span>|<span data-ttu-id="f645b-125">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="f645b-126">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-126">(none)</span></span>|<span data-ttu-id="f645b-127">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="f645b-128">"</span><span class="sxs-lookup"><span data-stu-id="f645b-128">"</span></span>|<span data-ttu-id="f645b-129">C</span><span class="sxs-lookup"><span data-stu-id="f645b-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="f645b-130">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="f645b-131">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-131">(none)</span></span>|<span data-ttu-id="f645b-132">D veya @</span><span class="sxs-lookup"><span data-stu-id="f645b-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="f645b-133">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-133">(none)</span></span>|<span data-ttu-id="f645b-134">R veya #</span><span class="sxs-lookup"><span data-stu-id="f645b-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="f645b-135">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-135">(none)</span></span>|<span data-ttu-id="f645b-136">%</span><span class="sxs-lookup"><span data-stu-id="f645b-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="f645b-137">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-137">(none)</span></span>|<span data-ttu-id="f645b-138">M veya &</span><span class="sxs-lookup"><span data-stu-id="f645b-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="f645b-139">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-139">(none)</span></span>|<span data-ttu-id="f645b-140">S</span><span class="sxs-lookup"><span data-stu-id="f645b-140">S</span></span>|  
|`Single`|<span data-ttu-id="f645b-141">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-141">(none)</span></span>|<span data-ttu-id="f645b-142">F veya!</span><span class="sxs-lookup"><span data-stu-id="f645b-142">F or !</span></span>|  
|`String`|<span data-ttu-id="f645b-143">"</span><span class="sxs-lookup"><span data-stu-id="f645b-143">"</span></span>|<span data-ttu-id="f645b-144">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="f645b-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f645b-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f645b-145">See Also</span></span>  
 [<span data-ttu-id="f645b-146">Kullanıcı Tanımlı Sabitler</span><span class="sxs-lookup"><span data-stu-id="f645b-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="f645b-147">Nasıl yapılır: Bir Sabit Bildirme</span><span class="sxs-lookup"><span data-stu-id="f645b-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="f645b-148">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f645b-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="f645b-149">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="f645b-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="f645b-150">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="f645b-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="f645b-151">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f645b-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="f645b-152">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="f645b-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="f645b-153">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="f645b-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="f645b-154">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f645b-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="f645b-155">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f645b-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
