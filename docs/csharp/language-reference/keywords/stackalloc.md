---
title: stackalloc anahtar sözcüğü (C# Başvurusu)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 16b2933423599e985ce57257595d67026dba93ca
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184536"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="b66c4-102">stackalloc (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b66c4-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="b66c4-103">`stackalloc` Anahtar sözcüğü bir güvenli olmayan kod bağlamında bir yığında bellek bloğu ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b66c4-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="b66c4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b66c4-104">Remarks</span></span>

<span data-ttu-id="b66c4-105">Anahtar sözcüğü, yalnızca yerel değişken başlatıcı içinde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b66c4-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="b66c4-106">Aşağıdaki kod derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b66c4-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="b66c4-107">C# 7.3 ile başlayarak, dizi Başlatıcı sözdizimi kullanabilirsiniz `stackalloc` dizileri.</span><span class="sxs-lookup"><span data-stu-id="b66c4-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="b66c4-108">Aşağıdaki bildirimleri tamsayı değerleri olan üç öğe olan bir dizi bildirmek `1`, `2`, ve `3`:</span><span class="sxs-lookup"><span data-stu-id="b66c4-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="b66c4-109">İşaretçi türleri dahil olduğundan `stackalloc` gerektiren bir [güvenli](unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="b66c4-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="b66c4-110">Daha fazla bilgi için [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b66c4-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="b66c4-111">`stackalloc` benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="b66c4-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="b66c4-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b66c4-112">Examples</span></span>

<span data-ttu-id="b66c4-113">Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırayla görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b66c4-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="b66c4-114">Her bir sayının, önceki iki sayının toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="b66c4-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="b66c4-115">Kodda, 20 öğe türü içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılır.</span><span class="sxs-lookup"><span data-stu-id="b66c4-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="b66c4-116">Blok adresini işaretçide depolanan `fib`.</span><span class="sxs-lookup"><span data-stu-id="b66c4-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="b66c4-117">Bu bellek tabi atık koleksiyonu olması gerekmez ve bu nedenle sabitlenmiş gerekmez (kullanarak [sabit](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="b66c4-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="b66c4-118">Bellek bloğu ömrünü tanımlayan yöntemin ömrünü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b66c4-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="b66c4-119">Yöntem döndürmeden önce belleği serbest bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b66c4-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="b66c4-120">Aşağıdaki örnek başlatır bir `stackalloc` her öğe için bir bit maskesi olan bir bit tamsayı dizisi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b66c4-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="b66c4-121">Bu yeni Başlatıcı sözdizimi C# 7.3 itibaren kullanıma gösterir:</span><span class="sxs-lookup"><span data-stu-id="b66c4-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="b66c4-122">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b66c4-122">Security</span></span>

<span data-ttu-id="b66c4-123">Güvenli olmayan kod güvenli alternatifler daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="b66c4-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="b66c4-124">Ancak, kullanımını `stackalloc` otomatik olarak ortak dil çalışma zamanı (CLR) arabellek taşması algılama özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b66c4-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="b66c4-125">İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b66c4-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b66c4-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b66c4-126">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b66c4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b66c4-127">See also</span></span>

- [<span data-ttu-id="b66c4-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b66c4-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="b66c4-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b66c4-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b66c4-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b66c4-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="b66c4-131">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b66c4-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
- [<span data-ttu-id="b66c4-132">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="b66c4-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)