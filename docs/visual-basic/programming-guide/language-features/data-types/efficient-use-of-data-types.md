---
description: 'Hakkında daha fazla bilgi edinin: veri türlerinin etkili kullanımı (Visual Basic)'
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
ms.openlocfilehash: e7660bbdec530ef18d663975e314d90b64e4b055
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476442"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="efb7c-103">Veri Türlerinin Etkili Kullanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efb7c-103">Efficient Use of Data Types (Visual Basic)</span></span>

<span data-ttu-id="efb7c-104">Bildirilmemiş değişkenlere ve veri türü olmadan belirtilen değişkenlere veri türü atanmamıştır `Object` .</span><span class="sxs-lookup"><span data-stu-id="efb7c-104">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="efb7c-105">Bu, programları hızlı bir şekilde yazmayı kolaylaştırır, ancak bunların daha yavaş yürütülmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="efb7c-105">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="efb7c-106">Güçlü yazma</span><span class="sxs-lookup"><span data-stu-id="efb7c-106">Strong Typing</span></span>

 <span data-ttu-id="efb7c-107">Tüm değişkenlerinizin veri türlerini belirtme, *güçlü yazma* olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="efb7c-107">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="efb7c-108">Güçlü yazma kullanmanın çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="efb7c-108">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="efb7c-109">Değişkenleriniz için IntelliSense desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="efb7c-109">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="efb7c-110">Bu, kodu yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="efb7c-110">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="efb7c-111">Derleyici türü denetlemesinin avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="efb7c-111">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="efb7c-112">Bu catch deyimleri, taşma gibi hatalar nedeniyle çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="efb7c-112">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="efb7c-113">Ayrıca, bunları desteklemeyen nesneler üzerindeki yöntemlere yapılan çağrıları yakalar.</span><span class="sxs-lookup"><span data-stu-id="efb7c-113">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="efb7c-114">Kodunuzun daha hızlı yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="efb7c-114">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="efb7c-115">En verimli veri türleri</span><span class="sxs-lookup"><span data-stu-id="efb7c-115">Most Efficient Data Types</span></span>

 <span data-ttu-id="efb7c-116">Kesirleri olmayan değişkenler için, integral veri türleri İntegral olmayan türlerden daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="efb7c-116">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="efb7c-117">Visual Basic, `Integer` ve `UInteger` en verimli sayısal türlerdir.</span><span class="sxs-lookup"><span data-stu-id="efb7c-117">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="efb7c-118">Büyük sayılar için `Double` en etkili veri türü, geçerli platformlardaki işlemciler çift duyarlıklı olarak kayan nokta işlemleri gerçekleştirtiğinden.</span><span class="sxs-lookup"><span data-stu-id="efb7c-118">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="efb7c-119">Ancak, ile işlemler, gibi `Double` integral türleriyle kadar hızlı değildir `Integer` .</span><span class="sxs-lookup"><span data-stu-id="efb7c-119">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="efb7c-120">Veri türünü belirtme</span><span class="sxs-lookup"><span data-stu-id="efb7c-120">Specifying Data Type</span></span>

 <span data-ttu-id="efb7c-121">Belirli bir türün değişkenini bildirmek için [Dim ifadesini](../../../language-reference/statements/dim-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="efb7c-121">Use the [Dim Statement](../../../language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="efb7c-122">Aşağıdaki örnekte olduğu gibi [ortak](../../../language-reference/modifiers/public.md), [korumalı](../../../language-reference/modifiers/protected.md), [arkadaş](../../../language-reference/modifiers/friend.md)veya [özel](../../../language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak erişim düzeyini eşzamanlı olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efb7c-122">You can simultaneously specify its access level by using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="efb7c-123">Karakter dönüştürme</span><span class="sxs-lookup"><span data-stu-id="efb7c-123">Character Conversion</span></span>

 <span data-ttu-id="efb7c-124">`AscW`Ve `ChrW` işlevleri Unicode 'da çalışır.</span><span class="sxs-lookup"><span data-stu-id="efb7c-124">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="efb7c-125">`Asc`Bu uygulamaları, ve ' ı tercih halinde kullanmanız gerekir ve `Chr` Bu, Unicode 'a ve dışına çevirmelidir.</span><span class="sxs-lookup"><span data-stu-id="efb7c-125">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="efb7c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efb7c-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="efb7c-127">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="efb7c-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="efb7c-128">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="efb7c-128">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="efb7c-129">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="efb7c-129">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="efb7c-130">IntelliSense kullanma</span><span class="sxs-lookup"><span data-stu-id="efb7c-130">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
