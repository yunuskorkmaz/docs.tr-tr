---
title: Visual Basic'de Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: f1f6b98d7db510373f2729fab2a6e0ad993ea086
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591387"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="357a5-102">Visual Basic'de Dize Temelleri</span><span class="sxs-lookup"><span data-stu-id="357a5-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="357a5-103">`String` Veri türünü temsil eden bir karakter dizisi (her sırayla örneğini temsil eden `Char` veri türü).</span><span class="sxs-lookup"><span data-stu-id="357a5-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="357a5-104">Bu konu Visual Basic'de dizeleri temel kavramları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="357a5-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="357a5-105">Dize değişkenleri</span><span class="sxs-lookup"><span data-stu-id="357a5-105">String Variables</span></span>  
 <span data-ttu-id="357a5-106">Bir dizenin bir örneğini temsil eden bir karakter dizisi değişmez değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="357a5-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="357a5-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="357a5-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="357a5-108">A `String` değişkeni de bir dizeye değerlendirilen bir ifade kabul edin.</span><span class="sxs-lookup"><span data-stu-id="357a5-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="357a5-109">Aşağıda örnekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="357a5-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="357a5-110">Atanan tüm sabit bir `String` değişkeni tırnak içine alınmalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="357a5-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="357a5-111">Bu, bir dize içindeki bir tırnak işareti bir tırnak işareti temsil edilemeyen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="357a5-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="357a5-112">Örneğin, aşağıdaki kod bir derleyici hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="357a5-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="357a5-113">Bu kod, çünkü derleyici dize ikinci bir tırnak işaretinden sonra sona erer ve dizenin geri kalanı, kod olarak yorumlanır, bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="357a5-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="357a5-114">Bu sorunu çözmek için Visual Basic, iki tırnak işaretleri dize değişmez değeri tek tırnak işareti içinde dize olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="357a5-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="357a5-115">Aşağıdaki örnek, bir dizedeki bir tırnak işareti eklemek için doğru şekilde gösterir:</span><span class="sxs-lookup"><span data-stu-id="357a5-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="357a5-116">Yukarıdaki örnekte, iki tırnak işaretleri Word'ün önceki `Look` dizesinde tek tırnak işareti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="357a5-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="357a5-117">Satır sonundaki üç tırnak işaretleri dize ve dize sonlandırma karakter bir tırnak işareti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="357a5-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="357a5-118">Çok satırlı dize değişmez değerleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="357a5-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="357a5-119">Ortaya çıkan dize, dize sabit değerinde (vbcr, vbcrlf, vb.) kullanılan yeni satır dizilerinin içerir.</span><span class="sxs-lookup"><span data-stu-id="357a5-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="357a5-120">Artık eski geçici çözümü kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="357a5-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="357a5-121">Dizelerdeki karakterleri</span><span class="sxs-lookup"><span data-stu-id="357a5-121">Characters in Strings</span></span>  
 <span data-ttu-id="357a5-122">Bir dize, bir dizi olarak düşünülebilir `Char` değerleri ve `String` türü diziler tarafından izin verilen işlemeleri benzer bir dizesine birçok işlemeleri gerçekleştirme olanak tanıyan yerleşik işlevleri vardır.</span><span class="sxs-lookup"><span data-stu-id="357a5-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="357a5-123">.NET Framework'teki tüm dizi gibi sıfır tabanlı diziler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="357a5-123">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="357a5-124">Bir dize içinde belirli bir karakter bakabilirsiniz `Chars` özelliği bir karakter dizesi içinde göründüğü konumu erişmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="357a5-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="357a5-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="357a5-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="357a5-126">Yukarıdaki örnekte, `Chars` dize özelliğini döndürür dördüncü karakter olan dizesinde `D`ve buna atayan `myChar`.</span><span class="sxs-lookup"><span data-stu-id="357a5-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="357a5-127">Belirli bir dizenin uzunluğunu da edinebilirsiniz `Length` özelliği.</span><span class="sxs-lookup"><span data-stu-id="357a5-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="357a5-128">Bir dize üzerinde birden fazla dizi türü değişikliklerini gerçekleştirmeniz gerekiyorsa, bunu bir dizisi olarak dönüştürebilirsiniz `Char` kullanarak örnekler `ToCharArray` dize işlevi.</span><span class="sxs-lookup"><span data-stu-id="357a5-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="357a5-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="357a5-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="357a5-130">Değişken `myArray` artık bir dizi içeren `Char` değerleri, her bir karakteri temsil eden `myString`.</span><span class="sxs-lookup"><span data-stu-id="357a5-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="357a5-131">Değiştirilemezlik dizeler</span><span class="sxs-lookup"><span data-stu-id="357a5-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="357a5-132">Bir dizedir *değişmez*, değeri bir kez değiştirilemez anlamına oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="357a5-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="357a5-133">Ancak, bu, birden fazla değer bir dize değişkenine atamanızı engellemez.</span><span class="sxs-lookup"><span data-stu-id="357a5-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="357a5-134">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="357a5-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="357a5-135">Burada verilen bir değer bir dize değişkeni oluşturulur ve ardından değeri değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="357a5-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="357a5-136">Özellikle, ilk satırda, türün bir örneğini `String` oluşturulur ve değerin `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="357a5-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="357a5-137">Örneğin ikinci satırda yeni bir örneği oluşturulur ve değerin `Or is it?`, string değişkeni, ilk örneğine başvuru atar ve yeni örneğe bir başvuru depolar.</span><span class="sxs-lookup"><span data-stu-id="357a5-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="357a5-138">Diğer iç veri türleri farklı `String` bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="357a5-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="357a5-139">Verilerin depolandığı bellek adresi başvurusu, başvuru türünde bir değişken bağımsız değişken olarak bir işlev veya alt yordamı geçirildiğinde, gerçek dize değerini yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="357a5-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="357a5-140">Önceki örnekte, değişken adı aynı kalır, ancak bir yeni ve farklı örneğine işaret `String` yeni değeri tutan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="357a5-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357a5-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="357a5-141">See also</span></span>

- [<span data-ttu-id="357a5-142">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="357a5-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="357a5-143">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="357a5-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="357a5-144">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="357a5-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="357a5-145">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="357a5-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
