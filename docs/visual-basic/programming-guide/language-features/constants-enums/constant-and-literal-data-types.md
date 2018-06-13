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
ms.openlocfilehash: 8d110ec17bcdb03f339d779b2950ba56d77957cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649854"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="31389-102">Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31389-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="31389-103">Bir sabit değer olarak kendisi yerine bir değişkenin değeri veya 3 sayı veya dize "Hello" gibi bir ifadenin sonucu olarak ifade bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="31389-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="31389-104">Bir sabit bir hazır değer yerini alır ve bu aynı değer değerini değiştirebilir, bir değişken aksine program boyunca korur anlamlı bir addır.</span><span class="sxs-lookup"><span data-stu-id="31389-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="31389-105">Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olan `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olan `On`, tüm sabit veri türüne sahip açıkça bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="31389-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="31389-106">Aşağıdaki örnekte, veri türü `MyByte` açıkça veri türü olarak bildirilmiş `Byte`:</span><span class="sxs-lookup"><span data-stu-id="31389-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 <span data-ttu-id="31389-107">Zaman `Option Infer` olan `On` veya `Option Strict` olan `Off`, bir veri türüyle belirtmeden bir sabit bildirebilir bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="31389-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="31389-108">Derleyici ifade türünden sabiti türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="31389-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="31389-109">Varsayılan olarak sabit bir sayısal tamsayı cast `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="31389-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="31389-110">Kayan nokta sayıları için varsayılan veri türü `Double`ve anahtar sözcükler `True` ve `False` belirtin bir `Boolean` sabit.</span><span class="sxs-lookup"><span data-stu-id="31389-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="31389-111">Değişmez değerler ve tür zorlama</span><span class="sxs-lookup"><span data-stu-id="31389-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="31389-112">Bazı durumlarda, belirli veri türü için bir hazır değer zorlamak isteyebilirsiniz; Örneğin, özellikle büyük tam sayı değişmez değer türü bir değişkene atarken `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="31389-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="31389-113">Aşağıdaki örnek, bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="31389-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="31389-114">Sabit gösteriminden hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="31389-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="31389-115">`Decimal` Veri türü tutun değeri bu büyük ancak sabit örtük olarak temsil edilen bir `Long`, hangi olamaz.</span><span class="sxs-lookup"><span data-stu-id="31389-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="31389-116">İki yolla belirli veri türü için bir hazır değer coerce: ona bir tür karakteri ekleyerek veya karakterini içinde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31389-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="31389-117">Tür karakteri veya karakterini gerekir hemen önünde ve/veya boşluk olmaması veya herhangi bir türde karakter olmayan sabit izleyin.</span><span class="sxs-lookup"><span data-stu-id="31389-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="31389-118">Önceki örnekte iş yapmak için ekleyebilirsiniz `D` türü karakteri olarak gösterilemeyecek kadar neden değişmez değeri için bir `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="31389-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 <span data-ttu-id="31389-119">Aşağıdaki örnek, türü ve kapsayan karakterleri doğru kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="31389-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 <span data-ttu-id="31389-120">Aşağıdaki tabloda gösterildiği kapsayan karakterler ve Visual Basic'te kullanılabilir karakterleri yazın.</span><span class="sxs-lookup"><span data-stu-id="31389-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="31389-121">Veri türü</span><span class="sxs-lookup"><span data-stu-id="31389-121">Data type</span></span>|<span data-ttu-id="31389-122">Kapsayan karakter</span><span class="sxs-lookup"><span data-stu-id="31389-122">Enclosing character</span></span>|<span data-ttu-id="31389-123">Eklenen türü karakteri</span><span class="sxs-lookup"><span data-stu-id="31389-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="31389-124">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-124">(none)</span></span>|<span data-ttu-id="31389-125">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="31389-126">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-126">(none)</span></span>|<span data-ttu-id="31389-127">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="31389-128">"</span><span class="sxs-lookup"><span data-stu-id="31389-128">"</span></span>|<span data-ttu-id="31389-129">C</span><span class="sxs-lookup"><span data-stu-id="31389-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="31389-130">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="31389-131">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-131">(none)</span></span>|<span data-ttu-id="31389-132">D @</span><span class="sxs-lookup"><span data-stu-id="31389-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="31389-133">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-133">(none)</span></span>|<span data-ttu-id="31389-134">R veya #</span><span class="sxs-lookup"><span data-stu-id="31389-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="31389-135">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-135">(none)</span></span>|<span data-ttu-id="31389-136">Veya %</span><span class="sxs-lookup"><span data-stu-id="31389-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="31389-137">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-137">(none)</span></span>|<span data-ttu-id="31389-138">M veya &</span><span class="sxs-lookup"><span data-stu-id="31389-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="31389-139">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-139">(none)</span></span>|<span data-ttu-id="31389-140">S</span><span class="sxs-lookup"><span data-stu-id="31389-140">S</span></span>|  
|`Single`|<span data-ttu-id="31389-141">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-141">(none)</span></span>|<span data-ttu-id="31389-142">F veya!</span><span class="sxs-lookup"><span data-stu-id="31389-142">F or !</span></span>|  
|`String`|<span data-ttu-id="31389-143">"</span><span class="sxs-lookup"><span data-stu-id="31389-143">"</span></span>|<span data-ttu-id="31389-144">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="31389-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31389-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31389-145">See Also</span></span>  
 [<span data-ttu-id="31389-146">Kullanıcı Tanımlı Sabitler</span><span class="sxs-lookup"><span data-stu-id="31389-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="31389-147">Nasıl yapılır: Bir Sabit Bildirme</span><span class="sxs-lookup"><span data-stu-id="31389-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="31389-148">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="31389-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="31389-149">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="31389-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="31389-150">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="31389-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="31389-151">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="31389-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="31389-152">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="31389-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="31389-153">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="31389-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="31389-154">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="31389-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="31389-155">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="31389-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
