---
title: stackalloc anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 61a27e777a1919a2a6fc5140a311835a8f3daba9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660716"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="b17aa-102">stackalloc (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b17aa-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="b17aa-103">`stackalloc` Anahtar sözcüğü, bir yığında bellek bloğu ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b17aa-103">The `stackalloc` keyword is used to allocate a block of memory on the stack.</span></span>

```csharp
Span<int> block = stackalloc int[100];
```

<span data-ttu-id="b17aa-104">Ayrılmış bir blok için atama bir <xref:System.Span%601?displayName=nameWithType> yerine bir `int*` yığın ayırmaları güvenli bloğunda izin verir.</span><span class="sxs-lookup"><span data-stu-id="b17aa-104">Assigning the allocated block to a <xref:System.Span%601?displayName=nameWithType> instead of an `int*` allows stack allocations in a safe block.</span></span> <span data-ttu-id="b17aa-105">`unsafe` Bağlamı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b17aa-105">The `unsafe` context is not required.</span></span>

## <a name="remarks"></a><span data-ttu-id="b17aa-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b17aa-106">Remarks</span></span>

<span data-ttu-id="b17aa-107">Anahtar sözcüğü, yalnızca yerel değişken başlatıcı içinde geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b17aa-107">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="b17aa-108">Aşağıdaki kod derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b17aa-108">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

<span data-ttu-id="b17aa-109">C# 7.3 ile başlayarak, dizi Başlatıcı sözdizimi kullanabilirsiniz `stackalloc` dizileri.</span><span class="sxs-lookup"><span data-stu-id="b17aa-109">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="b17aa-110">Aşağıdaki bildirimleri tamsayı değerleri olan üç öğe olan bir dizi bildirmek `1`, `2`, ve `3`.</span><span class="sxs-lookup"><span data-stu-id="b17aa-110">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`.</span></span> <span data-ttu-id="b17aa-111">İkinci başlatma bellek atar bir <xref:System.ReadOnlySpan%601>, belirten bellek değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b17aa-111">The second initialization assigns the memory to a <xref:System.ReadOnlySpan%601>, indicating that the memory cannot be modified.</span></span>

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="b17aa-112">İşaretçi türleri söz konusu olduğunda `stackalloc` gerektiren bir [güvenli](unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="b17aa-112">When pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="b17aa-113">Daha fazla bilgi için [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b17aa-113">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="b17aa-114">`stackalloc` benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="b17aa-114">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="b17aa-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b17aa-115">Examples</span></span>

<span data-ttu-id="b17aa-116">Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırayla görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b17aa-116">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="b17aa-117">Her bir sayının, önceki iki sayının toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="b17aa-117">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="b17aa-118">Kodda, 20 öğe türü içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılır.</span><span class="sxs-lookup"><span data-stu-id="b17aa-118">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="b17aa-119">Blok adresini depolanan `Span` `fib`.</span><span class="sxs-lookup"><span data-stu-id="b17aa-119">The address of the block is stored in the `Span` `fib`.</span></span> <span data-ttu-id="b17aa-120">Bu bellek tabi atık koleksiyonu olması gerekmez ve bu nedenle sabitlenmiş gerekmez (kullanarak [sabit](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="b17aa-120">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="b17aa-121">Bellek bloğu ömrünü tanımlayan yöntemin ömrünü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b17aa-121">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="b17aa-122">Yöntem döndürmeden önce belleği serbest bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b17aa-122">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="b17aa-123">Aşağıdaki örnek başlatır bir `stackalloc` her öğe için bir bit maskesi olan bir bit tamsayı dizisi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b17aa-123">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="b17aa-124">Bu yeni Başlatıcı sözdizimi C# 7.3 itibaren kullanıma gösterir:</span><span class="sxs-lookup"><span data-stu-id="b17aa-124">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="b17aa-125">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b17aa-125">Security</span></span>

<span data-ttu-id="b17aa-126">Kullanmanız gereken <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> mümkün olduğunca güvenli olmayan kod güvenli alternatifler daha az güvenlidir çünkü.</span><span class="sxs-lookup"><span data-stu-id="b17aa-126">You should use <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> when possible because unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="b17aa-127">İşaretçiler, kullanımını kullanıldığında bile `stackalloc` otomatik olarak ortak dil çalışma zamanı (CLR) arabellek taşması algılama özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b17aa-127">Even when used with pointers, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="b17aa-128">İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b17aa-128">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b17aa-129">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b17aa-129">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b17aa-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b17aa-130">See also</span></span>

- [<span data-ttu-id="b17aa-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b17aa-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b17aa-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b17aa-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b17aa-133">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b17aa-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b17aa-134">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b17aa-134">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="b17aa-135">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="b17aa-135">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
