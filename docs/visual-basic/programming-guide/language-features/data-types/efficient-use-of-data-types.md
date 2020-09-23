---
title: Veri Türlerinin Etkili Kullanımı
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 7f446b264dcb5c05ed6ddfba34acbbf66be0e447
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084118"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="300b0-102">Veri Türlerinin Etkili Kullanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="300b0-102">Efficient Use of Data Types (Visual Basic)</span></span>

<span data-ttu-id="300b0-103">Bildirilmemiş değişkenlere ve veri türü olmadan belirtilen değişkenlere veri türü atanmamıştır `Object` .</span><span class="sxs-lookup"><span data-stu-id="300b0-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="300b0-104">Bu, programları hızlı bir şekilde yazmayı kolaylaştırır, ancak bunların daha yavaş yürütülmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="300b0-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="300b0-105">Güçlü yazma</span><span class="sxs-lookup"><span data-stu-id="300b0-105">Strong Typing</span></span>

 <span data-ttu-id="300b0-106">Tüm değişkenlerinizin veri türlerini belirtme, *güçlü yazma*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="300b0-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="300b0-107">Güçlü yazma kullanmanın çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="300b0-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="300b0-108">Değişkenleriniz için IntelliSense desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="300b0-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="300b0-109">Bu, kodu yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="300b0-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="300b0-110">Derleyici türü denetlemesinin avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="300b0-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="300b0-111">Bu catch deyimleri, taşma gibi hatalar nedeniyle çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="300b0-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="300b0-112">Ayrıca, bunları desteklemeyen nesneler üzerindeki yöntemlere yapılan çağrıları yakalar.</span><span class="sxs-lookup"><span data-stu-id="300b0-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="300b0-113">Kodunuzun daha hızlı yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="300b0-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="300b0-114">En verimli veri türleri</span><span class="sxs-lookup"><span data-stu-id="300b0-114">Most Efficient Data Types</span></span>

 <span data-ttu-id="300b0-115">Kesirleri olmayan değişkenler için, integral veri türleri İntegral olmayan türlerden daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="300b0-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="300b0-116">Visual Basic, `Integer` ve `UInteger` en verimli sayısal türlerdir.</span><span class="sxs-lookup"><span data-stu-id="300b0-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="300b0-117">Büyük sayılar için `Double` en etkili veri türü, geçerli platformlardaki işlemciler çift duyarlıklı olarak kayan nokta işlemleri gerçekleştirtiğinden.</span><span class="sxs-lookup"><span data-stu-id="300b0-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="300b0-118">Ancak, ile işlemler, gibi `Double` integral türleriyle kadar hızlı değildir `Integer` .</span><span class="sxs-lookup"><span data-stu-id="300b0-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="300b0-119">Veri türünü belirtme</span><span class="sxs-lookup"><span data-stu-id="300b0-119">Specifying Data Type</span></span>

 <span data-ttu-id="300b0-120">Belirli bir türün değişkenini bildirmek için [Dim ifadesini](../../../language-reference/statements/dim-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="300b0-120">Use the [Dim Statement](../../../language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="300b0-121">Aşağıdaki örnekte olduğu gibi [ortak](../../../language-reference/modifiers/public.md), [korumalı](../../../language-reference/modifiers/protected.md), [arkadaş](../../../language-reference/modifiers/friend.md)veya [özel](../../../language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak erişim düzeyini eşzamanlı olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="300b0-121">You can simultaneously specify its access level by using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="300b0-122">Karakter dönüştürme</span><span class="sxs-lookup"><span data-stu-id="300b0-122">Character Conversion</span></span>

 <span data-ttu-id="300b0-123">`AscW`Ve `ChrW` işlevleri Unicode 'da çalışır.</span><span class="sxs-lookup"><span data-stu-id="300b0-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="300b0-124">`Asc`Bu uygulamaları, ve ' ı tercih halinde kullanmanız gerekir ve `Chr` Bu, Unicode 'a ve dışına çevirmelidir.</span><span class="sxs-lookup"><span data-stu-id="300b0-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="300b0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="300b0-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="300b0-126">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="300b0-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="300b0-127">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="300b0-127">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="300b0-128">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="300b0-128">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="300b0-129">IntelliSense kullanma</span><span class="sxs-lookup"><span data-stu-id="300b0-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
