---
title: stackalloc (C# Başvurusu)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 905873cf7f576ff35a9bc1c182ce7ebe17920288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269174"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="1c93e-102">stackalloc (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1c93e-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="1c93e-103">`stackalloc` Anahtar sözcüğü bir güvenli olmayan kod bağlamında kullanılan yığında bir bellek bloğu ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="1c93e-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="1c93e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c93e-104">Remarks</span></span>

<span data-ttu-id="1c93e-105">Anahtar sözcüğü yalnızca yerel değişken başlatıcıları içinde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="1c93e-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="1c93e-106">Aşağıdaki kod derleyici hataları neden olur.</span><span class="sxs-lookup"><span data-stu-id="1c93e-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="1c93e-107">C# 7.3 ile başlayarak, dizi Başlatıcısı sözdizimi için kullanabileceğiniz `stackalloc` dizileri.</span><span class="sxs-lookup"><span data-stu-id="1c93e-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="1c93e-108">Değerleri tamsayı olan üç öğeye sahip bir dizi aşağıdaki bildirimlerini bildirme `1`, `2`, ve `3`:</span><span class="sxs-lookup"><span data-stu-id="1c93e-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="1c93e-109">İşaretçi türleri dahil olduğundan `stackalloc` gerektiren bir [güvensiz](unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="1c93e-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="1c93e-110">Daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md)</span><span class="sxs-lookup"><span data-stu-id="1c93e-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="1c93e-111">`stackalloc` benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="1c93e-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="1c93e-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1c93e-112">Examples</span></span>

<span data-ttu-id="1c93e-113">Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırada görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c93e-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="1c93e-114">Her numarası önceki sayılarının toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="1c93e-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="1c93e-115">Kodda, türündeki 20 öğeler içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="1c93e-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="1c93e-116">Blok adresini işaretçinin depolanan `fib`.</span><span class="sxs-lookup"><span data-stu-id="1c93e-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="1c93e-117">Bu bellek çöp toplama tabi değildir ve bu nedenle sabitlenmiş olmak zorunda değildir (kullanarak [sabit](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="1c93e-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="1c93e-118">Bellek bloğu ömrü tanımladığı yöntemi için kullanım ömrü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c93e-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="1c93e-119">Yöntem döndürmeden önce bellek bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1c93e-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="1c93e-120">Aşağıdaki örnek başlatır bir `stackalloc` dizisi bir bit ile bir bit maskesi için her bir öğe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1c93e-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="1c93e-121">C# 7.3 içinde başlayarak kullanılabilir yeni Başlatıcısı sözdizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1c93e-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="1c93e-122">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="1c93e-122">Security</span></span>

<span data-ttu-id="1c93e-123">Güvenli olmayan kod güvenli alternatifler daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="1c93e-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="1c93e-124">Ancak, kullanımını `stackalloc` ortak dil çalışma zamanı (CLR) arabellek taşması algılama özellikleri otomatik olarak etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1c93e-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="1c93e-125">İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1c93e-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c93e-126">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="1c93e-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1c93e-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c93e-127">See Also</span></span>
 [<span data-ttu-id="1c93e-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1c93e-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1c93e-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1c93e-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1c93e-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1c93e-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1c93e-131">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1c93e-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="1c93e-132">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="1c93e-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
