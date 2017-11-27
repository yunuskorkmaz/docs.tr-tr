---
title: "Veri Türlerinin Etkili Kullanımı (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e13a1d61aacb06eb336c39aab969847127dfc67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="db598-102">Veri Türlerinin Etkili Kullanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db598-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="db598-103">Bildirilmemiş değişkenleri ve veri türü bildirilen değişkenlerin atanır `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="db598-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="db598-104">Bu, hızlı bir şekilde programları yazmak kolaylaştırır, ancak bunları daha yavaş çalışmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="db598-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="db598-105">Yazarak tanımlayıcı</span><span class="sxs-lookup"><span data-stu-id="db598-105">Strong Typing</span></span>  
 <span data-ttu-id="db598-106">Veri türleri için tüm değişkenleri belirtme olarak bilinir *güçlü yazarak*.</span><span class="sxs-lookup"><span data-stu-id="db598-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="db598-107">Güçlü yazarak kullanarak çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="db598-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="db598-108">Değişkenlerinizi IntelliSense desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="db598-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="db598-109">Bu kodu yazarken özelliklerini ve diğer üyeleri görmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="db598-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="db598-110">Tür derleyici denetlemeyi avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="db598-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="db598-111">Taşma gibi hatalar nedeniyle çalışma zamanında yük devredebilir deyimleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="db598-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="db598-112">Ayrıca bunları desteklemeyen nesnelerde yöntem çağrıları yakalar.</span><span class="sxs-lookup"><span data-stu-id="db598-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="db598-113">Kodunuzu daha hızlı yürütülmesini sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="db598-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="db598-114">En verimli veri türleri</span><span class="sxs-lookup"><span data-stu-id="db598-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="db598-115">Hiçbir zaman kesirler içeren değişkenler için tam sayı veri türleri nonintegral türleri daha büyük/küçük harf verimlidir.</span><span class="sxs-lookup"><span data-stu-id="db598-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="db598-116">İçinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], `Integer` ve `UInteger` en verimli sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="db598-116">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="db598-117">Kesirli sayılar için `Double` en verimli veri türü geçerli platformlarda işlemci çift duyarlıklı kayan nokta işlemleri olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="db598-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="db598-118">Ancak, işlemleriyle `Double` gibi tam sayı türleri gibi ile kadar hızlı değildir `Integer`.</span><span class="sxs-lookup"><span data-stu-id="db598-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="db598-119">Veri türünü belirtme</span><span class="sxs-lookup"><span data-stu-id="db598-119">Specifying Data Type</span></span>  
 <span data-ttu-id="db598-120">Kullanım [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) belirli bir türde bir değişken bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="db598-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="db598-121">Erişim düzeyi kullanarak aynı anda belirtebilirsiniz [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) içinde as anahtar sözcüğü Aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="db598-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="db598-122">Karakter dönüştürme</span><span class="sxs-lookup"><span data-stu-id="db598-122">Character Conversion</span></span>  
 <span data-ttu-id="db598-123">`AscW` Ve `ChrW` işlevleri Unicode olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="db598-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="db598-124">Bunları preference için kullanması gereken `Asc` ve `Chr`, hangi gerekir Çevir içine ve dışına Unicode.</span><span class="sxs-lookup"><span data-stu-id="db598-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db598-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db598-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="db598-126">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="db598-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="db598-127">Sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="db598-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="db598-128">Değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="db598-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="db598-129">IntelliSense kullanma</span><span class="sxs-lookup"><span data-stu-id="db598-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
