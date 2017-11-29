---
title: "stackalloc (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords: stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="fdefd-102">stackalloc (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fdefd-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="fdefd-103">`stackalloc` Anahtar sözcüğü bir güvenli olmayan kod bağlamında kullanılan yığında bir bellek bloğu ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="fdefd-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="fdefd-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdefd-104">Remarks</span></span>  
 <span data-ttu-id="fdefd-105">Anahtar sözcüğü yalnızca yerel değişken başlatıcıları içinde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="fdefd-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="fdefd-106">Aşağıdaki kod derleyici hataları neden olur.</span><span class="sxs-lookup"><span data-stu-id="fdefd-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="fdefd-107">İşaretçi türleri dahil olduğundan `stackalloc` gerektirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="fdefd-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="fdefd-108">Daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="fdefd-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="fdefd-109">`stackalloc`benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="fdefd-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="fdefd-110">Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırada görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fdefd-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="fdefd-111">Her numarası önceki sayılarının toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="fdefd-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="fdefd-112">Kodda, türündeki 20 öğeler içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="fdefd-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="fdefd-113">Blok adresini işaretçinin depolanan `fib`.</span><span class="sxs-lookup"><span data-stu-id="fdefd-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="fdefd-114">Bu bellek çöp toplama tabi değildir ve bu nedenle sabitlenmiş olmak zorunda değildir (kullanarak [sabit](../../../csharp/language-reference/keywords/fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="fdefd-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="fdefd-115">Bellek bloğu ömrü tanımladığı yöntemi için kullanım ömrü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="fdefd-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="fdefd-116">Yöntem döndürmeden önce bellek bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="fdefd-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdefd-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdefd-117">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a><span data-ttu-id="fdefd-118">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="fdefd-118">Security</span></span>  
 <span data-ttu-id="fdefd-119">Güvenli olmayan kod güvenli alternatifler daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="fdefd-119">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="fdefd-120">Ancak, kullanımını `stackalloc` ortak dil çalışma zamanı (CLR) arabellek taşması algılama özellikleri otomatik olarak etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="fdefd-120">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="fdefd-121">İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fdefd-121">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fdefd-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fdefd-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fdefd-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdefd-123">See Also</span></span>  
 [<span data-ttu-id="fdefd-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fdefd-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fdefd-125">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fdefd-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fdefd-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fdefd-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fdefd-127">İşleç anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fdefd-127">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="fdefd-128">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="fdefd-128">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
