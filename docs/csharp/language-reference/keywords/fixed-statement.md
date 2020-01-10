---
title: Fixed deyimidir- C# Reference
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713516"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="16866-102">fixed Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="16866-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="16866-103">`fixed` deyimleri, çöp toplayıcısının taşınabilir bir değişkenin yerini değiştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="16866-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="16866-104">Deyime yalnızca güvenli olmayan bir bağlamda izin verilir. [emniyetsiz](unsafe.md) `fixed`</span><span class="sxs-lookup"><span data-stu-id="16866-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="16866-105">[Sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)oluşturmak için `fixed` anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16866-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="16866-106">`fixed` deyimiyle yönetilen bir değişkene yönelik bir işaretçi ve deyimin yürütülmesi sırasında bu değişkenin "PIN" değeri ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="16866-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="16866-107">Taşınabilir yönetilen değişkenlere yönelik işaretçiler yalnızca `fixed` bağlamında faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="16866-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="16866-108">`fixed` bağlamı olmadan çöp toplama, değişkenleri tahmin edilmemiş şekilde yeniden konumlandırmaya yönelik olabilir.</span><span class="sxs-lookup"><span data-stu-id="16866-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="16866-109">C# Derleyici yalnızca bir `fixed` deyimindeki yönetilen değişkene bir işaretçi atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="16866-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="16866-110">Bir diziyi, dizeyi, sabit boyutlu arabelleği veya bir değişkenin adresini kullanarak bir işaretçiyi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16866-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="16866-111">Aşağıdaki örnek, değişken adreslerinin, dizilerin ve dizelerin kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="16866-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="16866-112">7,3 ile C# başlayarak, `fixed` deyimleri diziler, dizeler, sabit boyutlu arabellekler veya yönetilmeyen değişkenlerin ötesinde ek türler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="16866-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="16866-113">`GetPinnableReference` adlı bir yöntemi uygulayan herhangi bir tür sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="16866-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="16866-114">, `GetPinnableReference` [Yönetilmeyen türde](../builtin-types/unmanaged-types.md)bir `ref` değişken döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="16866-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="16866-115">.NET Core 2,0 ' de tanıtılan <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> .NET türleri bu düzenin kullanımını ve sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="16866-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="16866-116">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="16866-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="16866-117">Bu modele katılması gereken türler oluşturuyorsanız, <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> için bir örnek için bkz.</span><span class="sxs-lookup"><span data-stu-id="16866-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="16866-118">Aynı türde olan birden çok işaretçi tek bir bildirimde başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="16866-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="16866-119">Farklı türlerin işaretçilerini başlatmak için, aşağıdaki örnekte gösterildiği gibi `fixed` deyimlerini iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16866-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="16866-120">Deyimdeki kod yürütüldükten sonra, sabitlenmiş değişkenler sabitlenir ve çöp toplamaya tabidir.</span><span class="sxs-lookup"><span data-stu-id="16866-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="16866-121">Bu nedenle, `fixed` deyimin dışında bu değişkenlere işaret vermeyin.</span><span class="sxs-lookup"><span data-stu-id="16866-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="16866-122">`fixed` bildiriminde belirtilen değişkenler bu ifadeye kapsamlıdır ve bu daha kolay hale getirir:</span><span class="sxs-lookup"><span data-stu-id="16866-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="16866-123">`fixed` deyimlerde başlatılan işaretçiler salt okunur değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="16866-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="16866-124">İşaretçi değerini değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirmeniz ve bunu değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16866-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="16866-125">`fixed` ifadesinde belirtilen değişken değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="16866-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="16866-126">Yığın üzerinde bellek ayırabilirsiniz, burada çöp toplamaya tabi değildir ve bu nedenle sabitlenmiş olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="16866-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="16866-127">Bunu yapmak için [`stackalloc` işlecini](../operators/stackalloc.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="16866-127">To do that use the [`stackalloc` operator](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="16866-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="16866-128">C# language specification</span></span>

<span data-ttu-id="16866-129">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [fixed deyimin](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16866-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16866-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16866-130">See also</span></span>

- [<span data-ttu-id="16866-131">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="16866-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16866-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="16866-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16866-133">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="16866-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="16866-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="16866-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="16866-135">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="16866-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="16866-136">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="16866-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
