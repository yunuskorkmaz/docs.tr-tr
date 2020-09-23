---
title: Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 44736f4db9977d9f69a0571cc80fa327dcf96581
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072515"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="888af-102">Visual Basic'de Dize Temelleri</span><span class="sxs-lookup"><span data-stu-id="888af-102">String Basics in Visual Basic</span></span>

<span data-ttu-id="888af-103">`String`Veri türü bir dizi karakteri temsil eder (her biri, veri türünün bir örneğini sırasıyla temsil eder `Char` ).</span><span class="sxs-lookup"><span data-stu-id="888af-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="888af-104">Bu konuda Visual Basic içindeki dizelerin temel kavramları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="888af-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="888af-105">Dize değişkenleri</span><span class="sxs-lookup"><span data-stu-id="888af-105">String Variables</span></span>  

 <span data-ttu-id="888af-106">Bir dizenin örneğine, bir dizi karakteri temsil eden bir sabit değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="888af-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="888af-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="888af-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="888af-108">Bir `String` değişken bir dize olarak değerlendirilen herhangi bir ifadeyi de kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="888af-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="888af-109">Aşağıda örnekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="888af-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="888af-110">Bir değişkene atanan tüm sabit değer `String` tırnak işaretleri ("") içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="888af-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="888af-111">Bu, bir dize içindeki tırnak işaretinin bir tırnak işaretiyle temsil edimeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="888af-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="888af-112">Örneğin, aşağıdaki kod bir derleyici hatasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="888af-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="888af-113">Derleyici ikinci tırnak işaretinden sonra dizeyi sonlandırdığından ve dizenin geri kalanı kod olarak yorumlandığı için bu kod hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="888af-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="888af-114">Bu sorunu çözmek için, dize sabit değerindeki iki tırnak işaretini dizedeki bir tırnak işareti olarak yorumlar Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="888af-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="888af-115">Aşağıdaki örnek, bir dizeye tırnak işareti eklemenin doğru yolunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="888af-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="888af-116">Yukarıdaki örnekte, sözcükten önceki iki tırnak `Look` işareti dizedeki bir tırnak işaretine dönüşür.</span><span class="sxs-lookup"><span data-stu-id="888af-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="888af-117">Satırın sonundaki üç tırnak işareti, dizedeki bir tırnak işaretini ve dize sonlandırma karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="888af-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="888af-118">Dize sabit değerleri birden çok satır içerebilir:</span><span class="sxs-lookup"><span data-stu-id="888af-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="888af-119">Elde edilen dize, dize sabit değerinde kullandığınız yeni satır dizilerini içerir (vbCr, vbCrLf, vb.).</span><span class="sxs-lookup"><span data-stu-id="888af-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="888af-120">Artık eski geçici çözümü kullanmanız gerekmez:</span><span class="sxs-lookup"><span data-stu-id="888af-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="888af-121">Dizelerdeki karakterler</span><span class="sxs-lookup"><span data-stu-id="888af-121">Characters in Strings</span></span>  

 <span data-ttu-id="888af-122">Bir dize bir dizi değer olarak düşünülebilir `Char` ve `String` tür, diziler tarafından izin verilen düzenlemelere benzer bir dizede birçok oluşturma gerçekleştirmenize olanak tanıyan yerleşik işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="888af-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="888af-123">.NET Framework tüm diziler gibi, bunlar sıfır tabanlı dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="888af-123">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="888af-124">Bir dizedeki belirli bir karaktere `Chars` , dizesinde göründüğü konuma göre erişmek için bir yol sağlayan özelliği aracılığıyla başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="888af-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="888af-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="888af-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="888af-126">Yukarıdaki örnekte, `Chars` dizesinin özelliği dizedeki dördüncü karakteri döndürür `D` ve bunu öğesine atar `myChar` .</span><span class="sxs-lookup"><span data-stu-id="888af-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="888af-127">Ayrıca özelliği aracılığıyla belirli bir dizenin uzunluğunu da alabilirsiniz `Length` .</span><span class="sxs-lookup"><span data-stu-id="888af-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="888af-128">Bir dizede birden çok dizi türü işleyici gerçekleştirmeniz gerekiyorsa, `Char` dizenin işlevini kullanarak bir örnek dizisine dönüştürebilirsiniz `ToCharArray` .</span><span class="sxs-lookup"><span data-stu-id="888af-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="888af-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="888af-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="888af-130">Değişkeni `myArray` artık `Char` , her biri öğesinden bir karakteri temsil eden bir değer dizisi içerir `myString` .</span><span class="sxs-lookup"><span data-stu-id="888af-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="888af-131">Dizelerin Imlebilirlik kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="888af-131">The Immutability of Strings</span></span>  

 <span data-ttu-id="888af-132">Bir dize *sabittir*, yani değeri oluşturulduktan sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="888af-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="888af-133">Ancak, bu, bir dize değişkenine birden fazla değer atanmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="888af-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="888af-134">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="888af-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="888af-135">Burada bir dize değişkeni oluşturulur, bir değer verilir ve sonra değeri değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="888af-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="888af-136">Özellikle, ilk satırda, türünün bir örneği `String` oluşturulur ve değeri verilir `This string is immutable` .</span><span class="sxs-lookup"><span data-stu-id="888af-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="888af-137">Örneğin ikinci satırında yeni bir örnek oluşturulur ve değeri verilir `Or is it?` ve dize değişkeni, ilk örneğe başvurusunu atar ve yeni örneğe bir başvuru depolar.</span><span class="sxs-lookup"><span data-stu-id="888af-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="888af-138">Diğer iç veri türlerinden farklı olarak, `String` bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="888af-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="888af-139">Bir başvuru türü değişkeni bir işleve veya alt yordama bağımsız değişken olarak geçirildiğinde, dizenin gerçek değeri yerine verilerin depolandığı bellek adresine yönelik bir başvuru geçirilir.</span><span class="sxs-lookup"><span data-stu-id="888af-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="888af-140">Bu nedenle, önceki örnekte, değişkenin adı aynı kalır, ancak `String` yeni değeri tutan sınıfının yeni ve farklı bir örneğine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="888af-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888af-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="888af-141">See also</span></span>

- [<span data-ttu-id="888af-142">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="888af-142">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="888af-143">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="888af-143">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="888af-144">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="888af-144">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="888af-145">Temel dize Işlemleri</span><span class="sxs-lookup"><span data-stu-id="888af-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
