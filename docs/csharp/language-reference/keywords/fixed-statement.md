---
title: "fixed Deyimi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="72897-102">fixed Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="72897-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="72897-103">`fixed` Deyimi taşınabilir bir değişken yerini değiştirme atık toplayıcı engeller.</span><span class="sxs-lookup"><span data-stu-id="72897-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="72897-104">`fixed` Deyimi izin yalnızca bir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="72897-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="72897-105">`Fixed`oluşturmak için de kullanılabilir [sabit boyutlu arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="72897-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="72897-106">`fixed` Deyimi ayarlar bir işaretçi bir yönetilen değişken ve "PIN" için değişken deyimin yürütülmesi sırasında.</span><span class="sxs-lookup"><span data-stu-id="72897-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="72897-107">Olmadan `fixed`, atık toplama değişkenleri beklenmedik şekilde taşımanızı beri taşınabilir yönetilen değişkenleri işaretçiler az kullanımını olacaktır.</span><span class="sxs-lookup"><span data-stu-id="72897-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="72897-108">C# Derleyici yalnızca bir işaretçi yönetilen bir değişkene atayın olanak sağlayan bir `fixed` deyimi.</span><span class="sxs-lookup"><span data-stu-id="72897-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 <span data-ttu-id="72897-109">Bir dizi, bir dize, bir sabit boyutlu arabellek veya değişkenin adresini kullanarak bir işaretçi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72897-109">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="72897-110">Aşağıdaki örnekte değişken adresleri, dizileri ve dizeleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="72897-110">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="72897-111">Sabit boyutlu arabellekler hakkında daha fazla bilgi için bkz: [sabit boyutlu arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="72897-111">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 <span data-ttu-id="72897-112">Bunların tümü aynı türde sürece birden çok işaretçileri başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72897-112">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="72897-113">Farklı türlerdeki işaretçileri başlatmak için yalnızca içe `fixed` aşağıdaki örnekte gösterildiği gibi deyimleri.</span><span class="sxs-lookup"><span data-stu-id="72897-113">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 <span data-ttu-id="72897-114">Deyim kodda yürütüldükten sonra tüm sabitlenmiş sabitlenmemiş ve atık toplama değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="72897-114">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="72897-115">Bu nedenle, bu değişkenleri dışında işaret etmiyor `fixed` deyimi.</span><span class="sxs-lookup"><span data-stu-id="72897-115">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72897-116">Sabit deyimlerinde başlatılmış işaretçileri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="72897-116">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="72897-117">Güvenli modda, burada atık toplama tabi değildir ve bu nedenle sabitlenmelidir gerekmez yığında bellek ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="72897-117">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="72897-118">Daha fazla bilgi için bkz: [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="72897-118">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72897-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="72897-119">Example</span></span>  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="72897-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="72897-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72897-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72897-121">See Also</span></span>  
 [<span data-ttu-id="72897-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="72897-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="72897-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="72897-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="72897-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="72897-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="72897-125">güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="72897-125">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="72897-126">Sabit boyutlu arabellekler</span><span class="sxs-lookup"><span data-stu-id="72897-126">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
