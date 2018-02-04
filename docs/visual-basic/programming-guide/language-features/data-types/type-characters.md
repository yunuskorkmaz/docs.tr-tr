---
title: "Tür Karakterleri (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: bdb675b9605d03829c95897382daa6d03cf1b041
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="eca12-102">Karakterlerini (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eca12-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="eca12-103">Bir veri türü bildirimi deyiminde belirtmeye ek olarak, bazı programlama öğeleri ile veri türünü zorlayabilirsiniz bir *türü karakteri*.</span><span class="sxs-lookup"><span data-stu-id="eca12-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="eca12-104">Tür karakteri hemen öğe, herhangi bir türde müdahalede bulunan hiçbir karakter izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eca12-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="eca12-105">Tür karakteri öğesinin adı bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="eca12-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="eca12-106">Tür karakteri ile tanımlanmış bir öğe türü karakteri başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="eca12-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="eca12-107">Tanımlayıcı türü karakterleri</span><span class="sxs-lookup"><span data-stu-id="eca12-107">Identifier type characters</span></span>

<span data-ttu-id="eca12-108">Visual Basic sağlayan bir dizi *tanımlayıcı türü karakterleri* değişkeni ya da sabit veri türünü belirtmek için bir bildiriminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eca12-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="eca12-109">Aşağıdaki tabloda kullanılabilir tanımlayıcı türü karakterleri kullanım örnekleri ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eca12-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="eca12-110">Tanımlayıcı türü karakteri</span><span class="sxs-lookup"><span data-stu-id="eca12-110">Identifier type character</span></span>|<span data-ttu-id="eca12-111">Veri türü</span><span class="sxs-lookup"><span data-stu-id="eca12-111">Data type</span></span>|<span data-ttu-id="eca12-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="eca12-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="eca12-113">Hiçbir tanımlayıcı türü karakterleri mevcut `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, veya `UShort` veri türleri veya herhangi bileşik veri türleri dizileri veya yapıları gibi.</span><span class="sxs-lookup"><span data-stu-id="eca12-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="eca12-114">Bazı durumlarda, ekleyebilirsiniz `$` için Visual Basic işlevi, örneğin karakter `Left$` yerine `Left`, döndürülen değer türü elde etmek için `String`.</span><span class="sxs-lookup"><span data-stu-id="eca12-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="eca12-115">Tüm durumlarda tanımlayıcı türü karakteri hemen tanımlayıcı adı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eca12-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="eca12-116">Değişmez değer türü karakterleri</span><span class="sxs-lookup"><span data-stu-id="eca12-116">Literal type characters</span></span>

<span data-ttu-id="eca12-117">A *değişmez değer* bir veri türünün belirli bir değerinin metinsel gösterimini değil.</span><span class="sxs-lookup"><span data-stu-id="eca12-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="eca12-118">Varsayılan değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="eca12-118">Default literal types</span></span>

<span data-ttu-id="eca12-119">Kodunuzda normalde göründüğü gibi bir hazır değer form veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="eca12-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="eca12-120">Aşağıdaki tabloda, bu varsayılan türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eca12-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="eca12-121">Metin biçiminde değişmez değeri</span><span class="sxs-lookup"><span data-stu-id="eca12-121">Textual form of literal</span></span>|<span data-ttu-id="eca12-122">Varsayılan veri türü</span><span class="sxs-lookup"><span data-stu-id="eca12-122">Default data type</span></span>|<span data-ttu-id="eca12-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="eca12-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="eca12-124">Sayısal, Hayır kesirli bölümü</span><span class="sxs-lookup"><span data-stu-id="eca12-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="eca12-125">Sayısal, Hayır kesirli bölümü, için çok büyük`Integer`</span><span class="sxs-lookup"><span data-stu-id="eca12-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="eca12-126">Sayısal, kesirli bölümü</span><span class="sxs-lookup"><span data-stu-id="eca12-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="eca12-127">Çift tırnak işaretleri içine</span><span class="sxs-lookup"><span data-stu-id="eca12-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="eca12-128">İçinde sayı işaretleri arasına</span><span class="sxs-lookup"><span data-stu-id="eca12-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="eca12-129">Zorlanmış değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="eca12-129">Forced literal types</span></span>

<span data-ttu-id="eca12-130">Visual Basic sağlayan bir dizi *değişmez değer türü karakterleri*, farklı bir veri türü, form varsaymak bir hazır değer zorlamak için kullanabileceğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="eca12-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="eca12-131">Karakter sabit değeri sonuna ekleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eca12-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="eca12-132">Aşağıdaki tabloda kullanılabilir değişmez değer türü karakterleri kullanım örnekleri ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eca12-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="eca12-133">Değişmez değer türü karakteri</span><span class="sxs-lookup"><span data-stu-id="eca12-133">Literal type character</span></span>|<span data-ttu-id="eca12-134">Veri türü</span><span class="sxs-lookup"><span data-stu-id="eca12-134">Data type</span></span>|<span data-ttu-id="eca12-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="eca12-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="eca12-136">Değişmez değer türü karakterleri mevcut `Boolean`, `Byte`, `Date`, `Object`, `SByte`, veya `String` veri türleri veya dizileri veya yapıları gibi tüm bileşik veri türleri için.</span><span class="sxs-lookup"><span data-stu-id="eca12-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="eca12-137">Değişmez değerler tanımlayıcı türü karakterleri da kullanabilirsiniz (`%`, `&`, `@`, `!`, `#`, `$`) değişkenlerinin, sabitleri ve ifadeler gibi.</span><span class="sxs-lookup"><span data-stu-id="eca12-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="eca12-138">Ancak, sabit karakterleri yazın (`S`, `I`, `L`, `D`, `F`, `R`, `C`) yalnızca değişmez değerler ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eca12-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="eca12-139">Tüm durumlarda değişmez değer türü karakteri hemen hazır değeri izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eca12-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="eca12-140">Onaltılık, ikili ve sekizlik değişmez değerler</span><span class="sxs-lookup"><span data-stu-id="eca12-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="eca12-141">Derleyici ondalık (10 tabanı) sayı sisteminde olacak şekilde bir tamsayı değişmez değer normal olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="eca12-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="eca12-142">Değişmez değer bir tamsayı olan bir onaltılı (16 tabanı) sayı olarak tanımlayabilirsiniz `&H` öneki ile ikili (2 tabanı) sayı olarak `&B` öneki ve bir sekizli (8 tabanı) olarak numara ile `&O` öneki.</span><span class="sxs-lookup"><span data-stu-id="eca12-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="eca12-143">Önek izleyin basamaklı sayı sistemi için uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eca12-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="eca12-144">Aşağıdaki tabloda bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eca12-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="eca12-145">Temel numarası</span><span class="sxs-lookup"><span data-stu-id="eca12-145">Number base</span></span>|<span data-ttu-id="eca12-146">önek</span><span class="sxs-lookup"><span data-stu-id="eca12-146">Prefix</span></span>|<span data-ttu-id="eca12-147">Geçerli basamaklı değerler</span><span class="sxs-lookup"><span data-stu-id="eca12-147">Valid digit values</span></span>|<span data-ttu-id="eca12-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="eca12-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="eca12-149">Onaltılı (16 tabanı)</span><span class="sxs-lookup"><span data-stu-id="eca12-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="eca12-150">0-9 ve A-F</span><span class="sxs-lookup"><span data-stu-id="eca12-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="eca12-151">İkili (2 tabanı)</span><span class="sxs-lookup"><span data-stu-id="eca12-151">Binary (base 2)</span></span>|`0B`|<span data-ttu-id="eca12-152">0-1</span><span class="sxs-lookup"><span data-stu-id="eca12-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="eca12-153">Octal (8 tabanı)</span><span class="sxs-lookup"><span data-stu-id="eca12-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="eca12-154">0-7</span><span class="sxs-lookup"><span data-stu-id="eca12-154">0-7</span></span>|`&O77`|

<span data-ttu-id="eca12-155">Visual Basic 2017'dan başlayarak, alt çizgi karakterini kullanabilirsiniz (`_`) bir tam sayı sabit değeri okunabilirliğini artırmak için Grup ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="eca12-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="eca12-156">Aşağıdaki örnek kullanır `_` karakter sabit değeri bir ikili 8 bit gruplar halinde gruplandırmak için:</span><span class="sxs-lookup"><span data-stu-id="eca12-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="eca12-157">Değişmez değer türü karakteri ile önekli bir hazır değer izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eca12-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="eca12-158">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="eca12-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="eca12-159">Önceki örnekte, `counter` -32768, ondalık değeri vardır ve `flags` +32768 ondalık değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="eca12-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="eca12-160">Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="eca12-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="eca12-161">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="eca12-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="eca12-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eca12-162">See Also</span></span>

 [<span data-ttu-id="eca12-163">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="eca12-163">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="eca12-164">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="eca12-164">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="eca12-165">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="eca12-165">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="eca12-166">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="eca12-166">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="eca12-167">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="eca12-167">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="eca12-168">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="eca12-168">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="eca12-169">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="eca12-169">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
