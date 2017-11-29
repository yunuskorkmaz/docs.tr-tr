---
title: "İşleç Anahtar Sözcükleri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- keywords [C#], operators
- operators [C#], keywords
ms.assetid: f745c81f-f8d8-4673-86a1-0f3a85cc63c3
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d30e85dd76f37c797ec212b9e0700ab93a21a67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-keywords-c-reference"></a><span data-ttu-id="e7a96-102">İşleç Anahtar Sözcükleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e7a96-102">Operator Keywords (C# Reference)</span></span>
<span data-ttu-id="e7a96-103">Bir nesnenin bir yazı tipi boyutu alma, çalışma zamanı tür denetlemesi nesneleri oluşturma gibi çeşitli eylemleri ve diğer eylemleri gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7a96-103">Used to perform miscellaneous actions such as creating objects, checking the run-time type of an object, obtaining the size of a type, and other actions.</span></span> <span data-ttu-id="e7a96-104">Bu bölüm, aşağıdaki anahtar sözcükler sunar:</span><span class="sxs-lookup"><span data-stu-id="e7a96-104">This section introduces the following keywords:</span></span>  
  
-   <span data-ttu-id="e7a96-105">[olarak](../../../csharp/language-reference/keywords/as.md) bir nesne için uyumlu bir türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e7a96-105">[as](../../../csharp/language-reference/keywords/as.md) Converts an object to a compatible type.</span></span>  
  
-   <span data-ttu-id="e7a96-106">[await](../../../csharp/language-reference/keywords/await.md) awaited bir görevi tamamlanana kadar bir zaman uyumsuz yöntem askıya alır.</span><span class="sxs-lookup"><span data-stu-id="e7a96-106">[await](../../../csharp/language-reference/keywords/await.md) Suspends an async method until an awaited task is completed.</span></span>  
  
-   <span data-ttu-id="e7a96-107">[olan](../../../csharp/language-reference/keywords/is.md) bir nesnenin çalışma zamanı türü denetler.</span><span class="sxs-lookup"><span data-stu-id="e7a96-107">[is](../../../csharp/language-reference/keywords/is.md) Checks the run-time type of an object.</span></span>  
  
-   [<span data-ttu-id="e7a96-108">Yeni</span><span class="sxs-lookup"><span data-stu-id="e7a96-108">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
  
    -   <span data-ttu-id="e7a96-109">[New işleci](../../../csharp/language-reference/keywords/new-operator.md) nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e7a96-109">[new Operator](../../../csharp/language-reference/keywords/new-operator.md) Creates objects.</span></span>  
  
    -   <span data-ttu-id="e7a96-110">[New değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md) devralınmış bir üyeyi gizler.</span><span class="sxs-lookup"><span data-stu-id="e7a96-110">[new Modifier](../../../csharp/language-reference/keywords/new-modifier.md) Hides an inherited member.</span></span>  
  
    -   <span data-ttu-id="e7a96-111">[New kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md) bir tür parametresi niteliği taşır.</span><span class="sxs-lookup"><span data-stu-id="e7a96-111">[new Constraint](../../../csharp/language-reference/keywords/new-constraint.md) Qualifies a type parameter.</span></span>  
  
-   <span data-ttu-id="e7a96-112">[nameof](nameof.md) değişkeni, tür veya üye basit (nitelenmemiş) dize adını alır.</span><span class="sxs-lookup"><span data-stu-id="e7a96-112">[nameof](nameof.md) Obtains the simple (unqualified) string name of a variable, type, or member.</span></span>
 
-   <span data-ttu-id="e7a96-113">[sizeof](../../../csharp/language-reference/keywords/sizeof.md) bir yazı tipi boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="e7a96-113">[sizeof](../../../csharp/language-reference/keywords/sizeof.md) Obtains the size of a type.</span></span>  
  
-   <span data-ttu-id="e7a96-114">[typeof](../../../csharp/language-reference/keywords/typeof.md) elde ediyor **System.Type** nesne türü için.</span><span class="sxs-lookup"><span data-stu-id="e7a96-114">[typeof](../../../csharp/language-reference/keywords/typeof.md) Obtains the **System.Type** object for a type.</span></span>  
  
-   [<span data-ttu-id="e7a96-115">TRUE</span><span class="sxs-lookup"><span data-stu-id="e7a96-115">true</span></span>](../../../csharp/language-reference/keywords/true.md)  
  
    -   <span data-ttu-id="e7a96-116">[true işleci](../../../csharp/language-reference/keywords/true-operator.md) true belirtmek için boolean değeri true değerini döndürür ve aksi takdirde false döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7a96-116">[true Operator](../../../csharp/language-reference/keywords/true-operator.md) Returns the boolean value true to indicate true and returns false otherwise.</span></span>  
  
    -   <span data-ttu-id="e7a96-117">[TRUE değişmez değeri](../../../csharp/language-reference/keywords/true-literal.md) true boolean değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e7a96-117">[true Literal](../../../csharp/language-reference/keywords/true-literal.md) Represents the boolean value true.</span></span>  
  
-   [<span data-ttu-id="e7a96-118">false</span><span class="sxs-lookup"><span data-stu-id="e7a96-118">false</span></span>](../../../csharp/language-reference/keywords/false.md)  
  
    -   <span data-ttu-id="e7a96-119">[false işleci](../../../csharp/language-reference/keywords/false-operator.md) false değerini gösteren bir Boole değeri true değerini döndürür ve aksi takdirde false döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7a96-119">[false Operator](../../../csharp/language-reference/keywords/false-operator.md) Returns the Boolean value true to indicate false and returns false otherwise.</span></span>  
  
    -   <span data-ttu-id="e7a96-120">[false değişmez değeri](../../../csharp/language-reference/keywords/false-literal.md) Boole değeri false temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e7a96-120">[false Literal](../../../csharp/language-reference/keywords/false-literal.md) Represents the boolean value false.</span></span>  
  
-   <span data-ttu-id="e7a96-121">[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) yığında bir bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="e7a96-121">[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) Allocates a block of memory on the stack.</span></span>  
  
 <span data-ttu-id="e7a96-122">İşleçler ve ifadeler olarak kullanılabilir, aşağıdaki anahtar ele alınmaktadır [deyimleri](../../../csharp/language-reference/keywords/statement-keywords.md) bölümü:</span><span class="sxs-lookup"><span data-stu-id="e7a96-122">The following keywords, which can be used as operators and as statements, are covered in the [Statements](../../../csharp/language-reference/keywords/statement-keywords.md) section:</span></span>  
  
-   <span data-ttu-id="e7a96-123">[işaretli](../../../csharp/language-reference/keywords/checked.md) işaretli belirtir bağlamı.</span><span class="sxs-lookup"><span data-stu-id="e7a96-123">[checked](../../../csharp/language-reference/keywords/checked.md) Specifies checked context.</span></span>  
  
-   <span data-ttu-id="e7a96-124">[Unchecked](../../../csharp/language-reference/keywords/unchecked.md) denetlenmeyen bağlam belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7a96-124">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specifies unchecked context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a96-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7a96-125">See Also</span></span>  
 [<span data-ttu-id="e7a96-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e7a96-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e7a96-127">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e7a96-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e7a96-128">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e7a96-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e7a96-129">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e7a96-129">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
