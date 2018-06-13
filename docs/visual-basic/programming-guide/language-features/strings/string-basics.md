---
title: Visual Basic'de Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7d2477070dce558aa932c822852ac8ac9c6721e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654066"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="27d32-102">Visual Basic'de Dize Temelleri</span><span class="sxs-lookup"><span data-stu-id="27d32-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="27d32-103">`String` Veri türünü temsil eden bir karakter dizisi (her sırayla örneğini temsil eden `Char` veri türü).</span><span class="sxs-lookup"><span data-stu-id="27d32-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="27d32-104">Bu konu, Visual Basic'de dizeleri temel kavramları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="27d32-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="27d32-105">Dize değişkenleri</span><span class="sxs-lookup"><span data-stu-id="27d32-105">String Variables</span></span>  
 <span data-ttu-id="27d32-106">Bir dize örneği bir karakter dizisi temsil eden sabit bir değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="27d32-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="27d32-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27d32-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 <span data-ttu-id="27d32-108">A `String` değişkeni hesaplandığında bir dize sonucu herhangi bir ifade de kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="27d32-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="27d32-109">Aşağıda örnekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="27d32-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 <span data-ttu-id="27d32-110">Atanan tüm sabit bir `String` değişkeni tırnak işaretleri içine alınmalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="27d32-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="27d32-111">Bu, tırnak işareti dize içinde bir tırnak işaretiyle gösterilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="27d32-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="27d32-112">Örneğin, aşağıdaki kod derleyici hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="27d32-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 <span data-ttu-id="27d32-113">Bu kod, çünkü derleyici dize ikinci tırnağından sonra sonlandırır ve dizenin geri kalanı kodu olarak yorumlanır bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="27d32-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="27d32-114">Bu sorunu çözmek için Visual Basic iki tırnak işaretleri içine bir dize sabit değeri dize tek tırnak işareti olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="27d32-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="27d32-115">Aşağıdaki örnek, bir tırnak işareti içindeki bir dizeye dahil etmek için doğru bir şekilde gösterir:</span><span class="sxs-lookup"><span data-stu-id="27d32-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 <span data-ttu-id="27d32-116">Önceki örnekte, iki Word'ün önceki tırnak `Look` dizesindeki tek tırnak işareti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="27d32-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="27d32-117">Satırın sonundaki üç tırnak işaretleri dize ve dize sonlandırma karakter tek tırnak işareti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27d32-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="27d32-118">Dize değişmez değerleri birden fazla satır içerebilir:</span><span class="sxs-lookup"><span data-stu-id="27d32-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="27d32-119">Sonuç dizesini dizenizi içinde değişmez değer (vbcr, vbcrlf, vb.) kullanılan yeni satır sıraları içerir.</span><span class="sxs-lookup"><span data-stu-id="27d32-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="27d32-120">Artık eski geçici çözüm kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="27d32-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="27d32-121">Dizelerdeki karakterleri</span><span class="sxs-lookup"><span data-stu-id="27d32-121">Characters in Strings</span></span>  
 <span data-ttu-id="27d32-122">Bir dize, bir dizi olarak düşünülebilir `Char` değerleri ve `String` türü diziler tarafından izin verilen işlemeleri benzer bir dizesine birçok işlemeleri gerçekleştirme olanak tanıyan yerleşik işlevler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="27d32-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="27d32-123">Tüm içinde dizi gibi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bu sıfır tabanlı dizidir.</span><span class="sxs-lookup"><span data-stu-id="27d32-123">Like all array in [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="27d32-124">Belirli bir karakterin bir dizedeki bakabilirsiniz `Chars` özelliği bir karakter dizesini göründüğü konuma göre erişmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="27d32-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="27d32-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27d32-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 <span data-ttu-id="27d32-126">Yukarıdaki örnekte, `Chars` dize özelliği olan dizesinde dördüncü karakter döndürür `D`ve atar `myChar`.</span><span class="sxs-lookup"><span data-stu-id="27d32-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="27d32-127">Belirli bir dizenin uzunluğunu elde edebilirsiniz `Length` özelliği.</span><span class="sxs-lookup"><span data-stu-id="27d32-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="27d32-128">Bir dize üzerinde birden fazla dizi türü işlemeleri gerçekleştirme ihtiyacınız varsa, bir dizi için dönüştürebilirsiniz `Char` kullanarak örnekleri `ToCharArray` dize işlevi.</span><span class="sxs-lookup"><span data-stu-id="27d32-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="27d32-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="27d32-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 <span data-ttu-id="27d32-130">Değişkeni `myArray` artık bir dizi içeren `Char` değerleri, her bir karakteri temsil eden `myString`.</span><span class="sxs-lookup"><span data-stu-id="27d32-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="27d32-131">Dizeleri girişi</span><span class="sxs-lookup"><span data-stu-id="27d32-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="27d32-132">Bir dize *değişmez*, değeri bir kez değiştirilemez anlamına oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="27d32-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="27d32-133">Ancak, bu, dize değişkenine birden fazla değer atama engellemez.</span><span class="sxs-lookup"><span data-stu-id="27d32-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="27d32-134">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="27d32-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 <span data-ttu-id="27d32-135">Burada, bir değeri verildiğinde bir dize değişkeni oluşturulur ve ardından değeri değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="27d32-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="27d32-136">Daha açık belirtmek gerekirse, ilk satırda, türünün bir örneği `String` oluşturulur ve değeri verildiğinde `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="27d32-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="27d32-137">İkinci satırında Örneğin, yeni bir örneği oluşturulur ve değeri verildiğinde `Or is it?`, ve dize değişkeni, ilk örneğine başvuru atar ve yeni örneğine başvuru depolar.</span><span class="sxs-lookup"><span data-stu-id="27d32-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="27d32-138">Diğer iç veri türleri farklı `String` bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="27d32-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="27d32-139">Başvuru türünde bir değişken bağımsız değişken olarak bir işlev veya alt yordama geçirildiğinde, verilerinin depolandığı bellek adresi için bir başvuru dize gerçek değer yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="27d32-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="27d32-140">Önceki örnekte, değişkenin adını aynı kalır ancak bir yeni ve farklı örneğine işaret ediyor `String` yeni değeri tutan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="27d32-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d32-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27d32-141">See Also</span></span>  
 [<span data-ttu-id="27d32-142">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="27d32-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="27d32-143">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="27d32-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="27d32-144">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="27d32-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="27d32-145">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="27d32-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
