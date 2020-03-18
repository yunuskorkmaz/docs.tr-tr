---
title: sabit Ekstre - C# Referans
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713516"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="021bd-102">fixed Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="021bd-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="021bd-103">İfade, `fixed` çöp toplayıcısının taşınır değişkeninyerini değiştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="021bd-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="021bd-104">Bildirime `fixed` yalnızca [güvenli olmayan](unsafe.md) bir bağlamda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="021bd-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="021bd-105">Sabit boyutlu `fixed` [arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)oluşturmak için anahtar kelimeyi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="021bd-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="021bd-106">İfade, `fixed` yönetilen bir değişkene işaretçi ayarlar ve deyimin yürütülmesi sırasında bu değişkeni "sabitler".</span><span class="sxs-lookup"><span data-stu-id="021bd-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="021bd-107">Hareketli yönetilen değişkenlere işaretçiler yalnızca bir `fixed` bağlamda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="021bd-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="021bd-108">`fixed` Bağlam olmadan, çöp toplama değişkenleri öngörülemeyen bir şekilde başka bir yere taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="021bd-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="021bd-109">C# derleyicisi yalnızca bir `fixed` deyimde yönetilen bir değişkene işaretçi atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="021bd-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="021bd-110">Bir dizi, dize, sabit boyutlu arabellek veya bir değişkenin adresini kullanarak bir işaretçiyi başlatmayapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="021bd-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="021bd-111">Aşağıdaki örnekte değişken adresleri, diziler ve dizeleri kullanımı gösteriş verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="021bd-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="021bd-112">`fixed` C# 7.3 ile başlayarak, deyim diziler, dizeleri, sabit boyut arabellekleri veya yönetilmeyen değişkenler ötesinde ek türler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="021bd-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="021bd-113">Adlandırılmış `GetPinnableReference` bir yöntem uygulayan herhangi bir tür sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="021bd-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="021bd-114">Yönetilmeyen `GetPinnableReference` bir `ref` [türün](../builtin-types/unmanaged-types.md)değişkenini döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="021bd-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="021bd-115">.NET Core <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 2.0'da tanıtılan ve .NET türleri bu deseni kullanır ve sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="021bd-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="021bd-116">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="021bd-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="021bd-117">Bu desene katılması gereken türler oluşturuyorsanız, deseni uygulama örneğine bakın. <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="021bd-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="021bd-118">Birden çok işaretçi, hepsi aynı türdeyse, tek bir deyimde baş harflere para bürünebilir:</span><span class="sxs-lookup"><span data-stu-id="021bd-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="021bd-119">Farklı türdeki işaretçileri başlatmak `fixed` için, aşağıdaki örnekte gösterildiği gibi deyimleri yerleştirmenin yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="021bd-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="021bd-120">İfadedeki kod yürütüldükten sonra, sabitlenmiş değişkenler sabitlenmez ve çöp toplamaya tabi tutulur.</span><span class="sxs-lookup"><span data-stu-id="021bd-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="021bd-121">Bu nedenle, ifade dışında `fixed` bu değişkenleri işaret etmeyin.</span><span class="sxs-lookup"><span data-stu-id="021bd-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="021bd-122">`fixed` İfadede bildirilen değişkenler bu ifadeye göre kapsama getirilir ve bu da durumu kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="021bd-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="021bd-123">İfadelerde `fixed` başlattırılan işaretçiler yalnızca okunur değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="021bd-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="021bd-124">İşaretçi değerini değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirmeniz ve bunu değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="021bd-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="021bd-125">`fixed` İfadede bildirilen değişken değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="021bd-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="021bd-126">Bellekleri yığına ayırabilirsiniz, çöp toplamaya tabi olmadığı ve bu nedenle sabitlenmesi gerekmediği durumlarda.</span><span class="sxs-lookup"><span data-stu-id="021bd-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="021bd-127">Bunu yapmak için [ `stackalloc` operatörü](../operators/stackalloc.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="021bd-127">To do that use the [`stackalloc` operator](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="021bd-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="021bd-128">C# language specification</span></span>

<span data-ttu-id="021bd-129">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sabit ifade](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="021bd-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="021bd-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="021bd-130">See also</span></span>

- [<span data-ttu-id="021bd-131">C# Referans</span><span class="sxs-lookup"><span data-stu-id="021bd-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="021bd-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="021bd-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="021bd-133">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="021bd-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="021bd-134">Güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="021bd-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="021bd-135">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="021bd-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="021bd-136">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="021bd-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
