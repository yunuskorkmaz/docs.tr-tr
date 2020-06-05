---
title: Tür Karakterleri
ms.date: 01/31/2018
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
ms.openlocfilehash: a48260694c1dfcbbb8f804f220fe89b1663c7319
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393084"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="8d512-102">Tür karakterleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d512-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="8d512-103">Bir bildirim bildiriminde bir veri türü belirtmenin yanı sıra, bazı programlama öğelerinin veri türünü bir *tür karakteriyle*zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d512-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="8d512-104">Tür karakteri, hiçbir türden hiçbir araya girmeden önce öğesini hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="8d512-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="8d512-105">Tür karakteri öğenin adının bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="8d512-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="8d512-106">Tür karakteriyle tanımlanmış bir öğeye, tür karakteri olmadan başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="8d512-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="8d512-107">Tanımlayıcı türü karakterleri</span><span class="sxs-lookup"><span data-stu-id="8d512-107">Identifier type characters</span></span>

<span data-ttu-id="8d512-108">Visual Basic, bir değişkenin veya sabitin veri türünü belirtmek için bir bildirimde kullanabileceğiniz *tanımlayıcı türü karakterlerinin* bir kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d512-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="8d512-109">Aşağıdaki tabloda, kullanılabilir tanımlayıcı türü karakterleri kullanım örnekleri ile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d512-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="8d512-110">Tanımlayıcı türü karakteri</span><span class="sxs-lookup"><span data-stu-id="8d512-110">Identifier type character</span></span>|<span data-ttu-id="8d512-111">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8d512-111">Data type</span></span>|<span data-ttu-id="8d512-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d512-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="8d512-113">,,,,,,,,, `Boolean` `Byte` `Char` `Date` `Object` `SByte` `Short` `UInteger` `ULong` Veya `UShort` veri türleri için ya da diziler ya da yapılar gibi herhangi bir bileşik veri türü için tanımlayıcı türü karakterler yok.</span><span class="sxs-lookup"><span data-stu-id="8d512-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="8d512-114">Bazı durumlarda, `$` `Left$` `Left` türü döndürülen bir değer elde etmek için, örneğin yerine bir Visual Basic işleve bir karakter ekleyebilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="8d512-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="8d512-115">Her durumda, tanımlayıcı türü karakteri tanımlayıcı adını hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="8d512-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="8d512-116">Değişmez değer türü karakterleri</span><span class="sxs-lookup"><span data-stu-id="8d512-116">Literal type characters</span></span>

<span data-ttu-id="8d512-117">*Değişmez* değer, bir veri türünün belirli bir değerinin metinsel gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="8d512-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="8d512-118">Varsayılan değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="8d512-118">Default literal types</span></span>

<span data-ttu-id="8d512-119">Kodunuzda göründüğü gibi bir sabit değerin biçimi normalde veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="8d512-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="8d512-120">Aşağıdaki tabloda bu varsayılan türler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d512-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="8d512-121">Sabit değerin metin biçimi</span><span class="sxs-lookup"><span data-stu-id="8d512-121">Textual form of literal</span></span>|<span data-ttu-id="8d512-122">Varsayılan veri türü</span><span class="sxs-lookup"><span data-stu-id="8d512-122">Default data type</span></span>|<span data-ttu-id="8d512-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d512-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="8d512-124">Sayısal, kesirli bölüm yok</span><span class="sxs-lookup"><span data-stu-id="8d512-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="8d512-125">Sayısal, kesirli bölüm yok, için çok büyük`Integer`</span><span class="sxs-lookup"><span data-stu-id="8d512-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="8d512-126">Sayısal, kesirli bölüm</span><span class="sxs-lookup"><span data-stu-id="8d512-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="8d512-127">Çift tırnak işareti içine alınmış</span><span class="sxs-lookup"><span data-stu-id="8d512-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="8d512-128">Sayı işaretleri içine alınmış</span><span class="sxs-lookup"><span data-stu-id="8d512-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="8d512-129">Zorunlu değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="8d512-129">Forced literal types</span></span>

<span data-ttu-id="8d512-130">Visual Basic değişmez değer *türü karakterleri*sağlar, bu, bir hazır değeri, kendi formu dışında bir veri türünü varsaymaya zorlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d512-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="8d512-131">Bu, karakteri sabit değerin sonuna ekleyerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d512-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="8d512-132">Aşağıdaki tabloda, kullanılabilir değişmez değer türü karakterleri kullanım örnekleri ile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d512-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="8d512-133">Değişmez değer türü karakteri</span><span class="sxs-lookup"><span data-stu-id="8d512-133">Literal type character</span></span>|<span data-ttu-id="8d512-134">Veri türü</span><span class="sxs-lookup"><span data-stu-id="8d512-134">Data type</span></span>|<span data-ttu-id="8d512-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d512-135">Example</span></span>|  
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

<span data-ttu-id="8d512-136">,,,, `Boolean` `Byte` `Date` `Object` `SByte` Veya `String` veri türleri için ya da diziler ya da yapılar gibi herhangi bir bileşik veri türü için değişmez değer türü karakterleri yok.</span><span class="sxs-lookup"><span data-stu-id="8d512-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="8d512-137">Değişmez değerler, `%` `&` `@` `!` `#` `$` değişkenler, sabitler ve ifadeler gibi tanımlayıcı türü karakterlerini de (,,,,,) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d512-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="8d512-138">Ancak, değişmez değer türü karakterleri ( `S` , `I` , `L` , `D` , `F` , `R` , `C` ) yalnızca sabit karakterlerle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d512-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="8d512-139">Her durumda, değişmez değer türü karakteri hemen sabit değeri izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="8d512-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="8d512-140">Onaltılık, ikili ve sekizlik sabit değerler</span><span class="sxs-lookup"><span data-stu-id="8d512-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="8d512-141">Derleyici normalde bir tamsayı değişmez değerini ondalık (10 tabanında) sayı sisteminde olacak şekilde yorumlar.</span><span class="sxs-lookup"><span data-stu-id="8d512-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="8d512-142">Ön eke sahip bir tam sayı (taban 16) numarası, ön eke sahip bir `&H` ikili (taban 2) numarası olarak `&B` ve ön eki olan sekizli (taban 8) numarası olarak bir tamsayı sabit değeri de tanımlayabilirsiniz `&O` .</span><span class="sxs-lookup"><span data-stu-id="8d512-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="8d512-143">Ön eki izleyen basamakların sayı sistemine uygun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d512-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="8d512-144">Aşağıdaki tabloda bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d512-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="8d512-145">Sayı tabanı</span><span class="sxs-lookup"><span data-stu-id="8d512-145">Number base</span></span>|<span data-ttu-id="8d512-146">Ön ek</span><span class="sxs-lookup"><span data-stu-id="8d512-146">Prefix</span></span>|<span data-ttu-id="8d512-147">Geçerli basamak değerleri</span><span class="sxs-lookup"><span data-stu-id="8d512-147">Valid digit values</span></span>|<span data-ttu-id="8d512-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d512-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="8d512-149">Onaltılı (taban 16)</span><span class="sxs-lookup"><span data-stu-id="8d512-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="8d512-150">0-9 ve A-F</span><span class="sxs-lookup"><span data-stu-id="8d512-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="8d512-151">İkili (taban 2)</span><span class="sxs-lookup"><span data-stu-id="8d512-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="8d512-152">0-1</span><span class="sxs-lookup"><span data-stu-id="8d512-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="8d512-153">Sekizlik (taban 8)</span><span class="sxs-lookup"><span data-stu-id="8d512-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="8d512-154">0-7</span><span class="sxs-lookup"><span data-stu-id="8d512-154">0-7</span></span>|`&O77`|

<span data-ttu-id="8d512-155">Visual Basic 2017 ' den başlayarak, bir `_` integral sabit değerinin okunabilirliğini geliştirmek için alt çizgi karakterini () Grup ayırıcısı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d512-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="8d512-156">Aşağıdaki örnek, `_` bir ikili sabit değeri 8 bitlik gruplar halinde gruplandırmak için karakterini kullanır:</span><span class="sxs-lookup"><span data-stu-id="8d512-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="8d512-157">Ön ek değişmez değerini, değişmez değer türü karakteriyle izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d512-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="8d512-158">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d512-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="8d512-159">Önceki örnekte, `counter` -32768 ondalık değerine sahiptir ve `flags` + 32768 ondalık değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8d512-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="8d512-160">Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d512-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="8d512-161">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8d512-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="8d512-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d512-162">See also</span></span>

- [<span data-ttu-id="8d512-163">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="8d512-163">Data Types</span></span>](index.md)
- [<span data-ttu-id="8d512-164">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8d512-164">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="8d512-165">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="8d512-165">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="8d512-166">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="8d512-166">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="8d512-167">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="8d512-167">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="8d512-168">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="8d512-168">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="8d512-169">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="8d512-169">Data Types</span></span>](../../../language-reference/data-types/index.md)
