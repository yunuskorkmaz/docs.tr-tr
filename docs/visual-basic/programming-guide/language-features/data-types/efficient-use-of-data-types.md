---
title: Veri Türlerinin Etkili Kullanımı (Visual Basic)
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
ms.openlocfilehash: f85acfe7592d7b90423107e0d45bb007fce5f4a8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601149"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="3f8a5-102">Veri Türlerinin Etkili Kullanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f8a5-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="3f8a5-103">Bildirilmemiş değişkenler ve bir veri türü bildirilen değişkenler atanmış `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="3f8a5-104">Bu hızlı yazma kolaylaştırır, ancak bunları daha yavaş çalışmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="3f8a5-105">Yazarak güçlü</span><span class="sxs-lookup"><span data-stu-id="3f8a5-105">Strong Typing</span></span>  
 <span data-ttu-id="3f8a5-106">Tüm değişkenlerin veri türlerini belirtme olarak bilinir *güçlü yazım, yazım*.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="3f8a5-107">Güçlü yazım, yazım kullanarak çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="3f8a5-107">Using strong typing has several advantages:</span></span>  
  
- <span data-ttu-id="3f8a5-108">Bu değişkenleri için IntelliSense desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="3f8a5-109">Bu kod yazarken özelliklerini ve diğer üyeleri görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
- <span data-ttu-id="3f8a5-110">Bu derleyici tür denetimi yararlanır.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="3f8a5-111">Bu, çalışma zamanında taşma gibi hatalar nedeniyle başarısız olabilir deyimleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="3f8a5-112">Ayrıca bunları desteği olmayan nesneler üzerinde yöntemlere yapılan çağrılar yakalar.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
- <span data-ttu-id="3f8a5-113">Bu, kodunuzun daha hızlı bir şekilde yürütülmesini sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="3f8a5-114">En verimli veri türleri</span><span class="sxs-lookup"><span data-stu-id="3f8a5-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="3f8a5-115">Kesir hiçbir zaman içeren değişkenlerini tam sayı veri türleri nonintegral türleri daha büyük/küçük harf etkilidir.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="3f8a5-116">Visual Basic'te `Integer` ve `UInteger` en verimli sayısal türleri.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="3f8a5-117">Kesirli sayılar için `Double` en verimli veri türü, geçerli platformda işlemci çift duyarlıklı kayan nokta işlemleri olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="3f8a5-118">Ancak, işlemleriyle `Double` gibi tam sayı türleri gibi ile kısa sürede olmayan `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="3f8a5-119">Veri türünü belirtme</span><span class="sxs-lookup"><span data-stu-id="3f8a5-119">Specifying Data Type</span></span>  
 <span data-ttu-id="3f8a5-120">Kullanım [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) belirli bir türdeki bir değişken bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="3f8a5-121">Kullanarak aynı anda erişim düzeyini belirtebilirsiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) görüldüğü anahtar sözcüğü Aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="3f8a5-122">Karakter dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3f8a5-122">Character Conversion</span></span>  
 <span data-ttu-id="3f8a5-123">`AscW` Ve `ChrW` işlevler Unicode olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="3f8a5-124">Bunları preference için kullanması gereken `Asc` ve `Chr`, hangi gerekir Çevir içine ve dışına Unicode.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8a5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f8a5-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="3f8a5-126">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="3f8a5-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="3f8a5-127">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="3f8a5-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="3f8a5-128">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="3f8a5-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="3f8a5-129">IntelliSense Kullanma</span><span class="sxs-lookup"><span data-stu-id="3f8a5-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
