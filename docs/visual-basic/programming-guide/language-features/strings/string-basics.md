---
title: Visual Basic'de Dize Temelleri
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8881ad6ab7f28689019463abdab3b867e010d51e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="b8c73-102">Visual Basic'de Dize Temelleri</span><span class="sxs-lookup"><span data-stu-id="b8c73-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="b8c73-103">`String` Veri türünü temsil eden bir karakter dizisi (her sırayla örneğini temsil eden `Char` veri türü).</span><span class="sxs-lookup"><span data-stu-id="b8c73-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="b8c73-104">Bu konu dizeleri temel kavramları tanıtır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8c73-104">This topic introduces the basic concepts of strings in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="b8c73-105">Dize değişkenleri</span><span class="sxs-lookup"><span data-stu-id="b8c73-105">String Variables</span></span>  
 <span data-ttu-id="b8c73-106">Bir dize örneği bir karakter dizisi temsil eden sabit bir değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="b8c73-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="b8c73-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b8c73-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 <span data-ttu-id="b8c73-108">A `String` değişkeni hesaplandığında bir dize sonucu herhangi bir ifade de kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="b8c73-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="b8c73-109">Aşağıda örnekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b8c73-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 <span data-ttu-id="b8c73-110">Atanan tüm sabit bir `String` değişkeni tırnak işaretleri içine alınmalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="b8c73-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="b8c73-111">Bu, tırnak işareti dize içinde bir tırnak işaretiyle gösterilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b8c73-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="b8c73-112">Örneğin, aşağıdaki kod derleyici hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="b8c73-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 <span data-ttu-id="b8c73-113">Bu kod, çünkü derleyici dize ikinci tırnağından sonra sonlandırır ve dizenin geri kalanı kodu olarak yorumlanır bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b8c73-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="b8c73-114">Bu sorunu çözmek için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] iki tırnak işaretleri içine bir dize sabit değeri dize tek tırnak işareti olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="b8c73-114">To solve this problem, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="b8c73-115">Aşağıdaki örnek, bir tırnak işareti içindeki bir dizeye dahil etmek için doğru bir şekilde gösterir:</span><span class="sxs-lookup"><span data-stu-id="b8c73-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 <span data-ttu-id="b8c73-116">Önceki örnekte, iki Word'ün önceki tırnak `Look` dizesindeki tek tırnak işareti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="b8c73-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="b8c73-117">Satırın sonundaki üç tırnak işaretleri dize ve dize sonlandırma karakter tek tırnak işareti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8c73-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="b8c73-118">Dize değişmez değerleri birden fazla satır içerebilir:</span><span class="sxs-lookup"><span data-stu-id="b8c73-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="b8c73-119">Sonuç dizesini dizenizi içinde değişmez değer (vbcr, vbcrlf, vb.) kullanılan yeni satır sıraları içerir.</span><span class="sxs-lookup"><span data-stu-id="b8c73-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="b8c73-120">Artık eski geçici çözüm kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b8c73-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="b8c73-121">Dizelerdeki karakterleri</span><span class="sxs-lookup"><span data-stu-id="b8c73-121">Characters in Strings</span></span>  
 <span data-ttu-id="b8c73-122">Bir dize, bir dizi olarak düşünülebilir `Char` değerleri ve `String` türü diziler tarafından izin verilen işlemeleri benzer bir dizesine birçok işlemeleri gerçekleştirme olanak tanıyan yerleşik işlevler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b8c73-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="b8c73-123">Tüm içinde dizi gibi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bu sıfır tabanlı dizidir.</span><span class="sxs-lookup"><span data-stu-id="b8c73-123">Like all array in [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="b8c73-124">Belirli bir karakterin bir dizedeki bakabilirsiniz `Chars` özelliği bir karakter dizesini göründüğü konuma göre erişmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8c73-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="b8c73-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b8c73-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 <span data-ttu-id="b8c73-126">Yukarıdaki örnekte, `Chars` dize özelliği olan dizesinde dördüncü karakter döndürür `D`ve atar `myChar`.</span><span class="sxs-lookup"><span data-stu-id="b8c73-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="b8c73-127">Belirli bir dizenin uzunluğunu elde edebilirsiniz `Length` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b8c73-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="b8c73-128">Bir dize üzerinde birden fazla dizi türü işlemeleri gerçekleştirme ihtiyacınız varsa, bir dizi için dönüştürebilirsiniz `Char` kullanarak örnekleri `ToCharArray` dize işlevi.</span><span class="sxs-lookup"><span data-stu-id="b8c73-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="b8c73-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b8c73-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 <span data-ttu-id="b8c73-130">Değişkeni `myArray` artık bir dizi içeren `Char` değerleri, her bir karakteri temsil eden `myString`.</span><span class="sxs-lookup"><span data-stu-id="b8c73-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="b8c73-131">Dizeleri girişi</span><span class="sxs-lookup"><span data-stu-id="b8c73-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="b8c73-132">Bir dize *değişmez*, değeri bir kez değiştirilemez anlamına oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="b8c73-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="b8c73-133">Ancak, bu, dize değişkenine birden fazla değer atama engellemez.</span><span class="sxs-lookup"><span data-stu-id="b8c73-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="b8c73-134">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b8c73-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 <span data-ttu-id="b8c73-135">Burada, bir değeri verildiğinde bir dize değişkeni oluşturulur ve ardından değeri değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="b8c73-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="b8c73-136">Daha açık belirtmek gerekirse, ilk satırda, türünün bir örneği `String` oluşturulur ve değeri verildiğinde `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="b8c73-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="b8c73-137">İkinci satırında Örneğin, yeni bir örneği oluşturulur ve değeri verildiğinde `Or is it?`, ve dize değişkeni, ilk örneğine başvuru atar ve yeni örneğine başvuru depolar.</span><span class="sxs-lookup"><span data-stu-id="b8c73-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="b8c73-138">Diğer iç veri türleri farklı `String` bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="b8c73-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="b8c73-139">Başvuru türünde bir değişken bağımsız değişken olarak bir işlev veya alt yordama geçirildiğinde, verilerinin depolandığı bellek adresi için bir başvuru dize gerçek değer yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b8c73-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="b8c73-140">Önceki örnekte, değişkenin adını aynı kalır ancak bir yeni ve farklı örneğine işaret ediyor `String` yeni değeri tutan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8c73-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c73-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8c73-141">See Also</span></span>  
 [<span data-ttu-id="b8c73-142">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="b8c73-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="b8c73-143">Dize veri türü</span><span class="sxs-lookup"><span data-stu-id="b8c73-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="b8c73-144">Char veri türü</span><span class="sxs-lookup"><span data-stu-id="b8c73-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="b8c73-145">Temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="b8c73-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
