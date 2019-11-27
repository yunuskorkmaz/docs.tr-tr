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
ms.openlocfilehash: 621dec7537e9c993024e271b96ab8706baf89885
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350103"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="1d64c-102">Veri Türlerinin Etkili Kullanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d64c-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="1d64c-103">Bildirilmemiş değişkenlere ve veri türü olmadan belirtilen değişkenlere `Object` veri türü atanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="1d64c-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="1d64c-104">Bu, programları hızlı bir şekilde yazmayı kolaylaştırır, ancak bunların daha yavaş yürütülmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="1d64c-105">Güçlü yazma</span><span class="sxs-lookup"><span data-stu-id="1d64c-105">Strong Typing</span></span>
 <span data-ttu-id="1d64c-106">Tüm değişkenlerinizin veri türlerini belirtme, *güçlü yazma*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="1d64c-107">Güçlü yazma kullanmanın çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="1d64c-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="1d64c-108">Değişkenleriniz için IntelliSense desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="1d64c-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="1d64c-109">Bu, kodu yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d64c-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="1d64c-110">Derleyici türü denetlemesinin avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="1d64c-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="1d64c-111">Bu catch deyimleri, taşma gibi hatalar nedeniyle çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="1d64c-112">Ayrıca, bunları desteklemeyen nesneler üzerindeki yöntemlere yapılan çağrıları yakalar.</span><span class="sxs-lookup"><span data-stu-id="1d64c-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="1d64c-113">Kodunuzun daha hızlı yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="1d64c-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="1d64c-114">En verimli veri türleri</span><span class="sxs-lookup"><span data-stu-id="1d64c-114">Most Efficient Data Types</span></span>
 <span data-ttu-id="1d64c-115">Kesirleri olmayan değişkenler için, integral veri türleri İntegral olmayan türlerden daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="1d64c-116">Visual Basic, `Integer` ve `UInteger` en verimli sayısal türlerdir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="1d64c-117">Büyük sayılar için `Double` en etkili veri türüdür, çünkü geçerli platformlardaki işlemciler çift duyarlıklı olarak kayan nokta işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="1d64c-118">Ancak, `Double` olan işlemler, `Integer`gibi integral türleri kadar hızlı değildir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="1d64c-119">Veri türünü belirtme</span><span class="sxs-lookup"><span data-stu-id="1d64c-119">Specifying Data Type</span></span>
 <span data-ttu-id="1d64c-120">Belirli bir türün değişkenini bildirmek için [Dim ifadesini](../../../../visual-basic/language-reference/statements/dim-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d64c-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="1d64c-121">Aşağıdaki örnekte olduğu gibi [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md)veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak erişim düzeyini eşzamanlı olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d64c-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="1d64c-122">Karakter dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1d64c-122">Character Conversion</span></span>
 <span data-ttu-id="1d64c-123">`AscW` ve `ChrW` işlevleri Unicode 'da çalışır.</span><span class="sxs-lookup"><span data-stu-id="1d64c-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="1d64c-124">Bunları `Asc` ve `Chr`için tercih ettiğiniz şekilde kullanmanız gerekir; bu, Unicode 'a ve dışına çevrilip çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1d64c-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d64c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d64c-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="1d64c-126">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="1d64c-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="1d64c-127">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="1d64c-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="1d64c-128">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="1d64c-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="1d64c-129">IntelliSense Kullanma</span><span class="sxs-lookup"><span data-stu-id="1d64c-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
