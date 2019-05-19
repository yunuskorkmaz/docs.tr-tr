---
title: fixed Statement - C# başvurusu
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: a852f36c05075365ced8ec39457b15601ca3c3fb
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877078"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="5000c-102">fixed Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5000c-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="5000c-103">`fixed` Deyimi, taşınabilir bir değişken yerini değiştirme alanından çöp toplayıcı engeller.</span><span class="sxs-lookup"><span data-stu-id="5000c-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="5000c-104">`fixed` Deyimi izin yalnızca bir [güvenli](unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="5000c-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="5000c-105">Ayrıca `fixed` oluşturmak için anahtar sözcüğü [sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="5000c-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="5000c-106">`fixed` Deyimi ayarlar bir işaretçi yönetilen bir değişken ve "Sabitlemeleri" değişken deyimin yürütülmesi sırasında.</span><span class="sxs-lookup"><span data-stu-id="5000c-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="5000c-107">Yalnızca taşınabilir yönetilen değişkenleri işaretçileri kullanışlıdır bir `fixed` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="5000c-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="5000c-108">Olmadan bir `fixed` bağlamı, çöp toplama dışında yeniden konumlandırmakta değişkenleri ilgilenmeye.</span><span class="sxs-lookup"><span data-stu-id="5000c-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="5000c-109">C# derleyicisi yalnızca, bir işaretçi yönetilen bir değişkene atamanıza olanak tanır bir `fixed` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5000c-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="5000c-110">Bir işaretçi, bir dizi, bir dize, bir sabit boyutlu arabellek veya değişkenin adresini kullanarak başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5000c-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="5000c-111">Aşağıdaki örnekte, değişken adresleri, diziler ve dizeleri kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5000c-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="5000c-112">C# 7.3 ile başlangıç `fixed` deyimi yerler diziler, dizeler, sabit boyutlu arabellekler veya yönetilmeyen değişkenleri ötesinde ek türleri üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="5000c-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed-size buffers, or unmanaged variables.</span></span> <span data-ttu-id="5000c-113">Adlı bir yöntem uygulayan herhangi bir tür `GetPinnableReference` sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5000c-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="5000c-114">`GetPinnableReference` Döndürmelidir bir `ref` değişken için bir yönetilmeyen türe.</span><span class="sxs-lookup"><span data-stu-id="5000c-114">The `GetPinnableReference` must return a `ref` variable to an unmanaged type.</span></span> <span data-ttu-id="5000c-115">Üzerinde konusuna [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="5000c-115">See the topic on [pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md) for more information.</span></span> <span data-ttu-id="5000c-116">.NET türleri <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> sunulan .NET Core 2.0 olun bu düzeni kullanın ve sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5000c-116">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="5000c-117">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5000c-117">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="5000c-118">Bu düzende alması gereken türleri oluşturuyorsanız, bkz. <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> desenini uygulama örneği.</span><span class="sxs-lookup"><span data-stu-id="5000c-118">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="5000c-119">Aynı türde ise tek bir deyimde birden çok işaretçi başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="5000c-119">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="5000c-120">Farklı türlerde işaretçileri başlatmak için yalnızca içe `fixed` ifadeleri, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5000c-120">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="5000c-121">Deyim kodda yürütüldükten sonra sabitlenmiş olan tüm değişkenler sabitlenmemiş ve çöp toplama var.</span><span class="sxs-lookup"><span data-stu-id="5000c-121">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="5000c-122">Bu nedenle, bu değişkenlere dışında işaret etmeyen `fixed` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5000c-122">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="5000c-123">İçinde bildirilmiş değişkenlerin `fixed` deyimi bu kolaylaştıracak ifade, kapsamı:</span><span class="sxs-lookup"><span data-stu-id="5000c-123">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="5000c-124">İşaretçileri başlatılamadı `fixed` deyimleri olan salt okunur değişkenler.</span><span class="sxs-lookup"><span data-stu-id="5000c-124">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="5000c-125">İşaretçi değeri değiştirmek istiyorsanız, ikinci işaretçi değişkeninin bildirimini ve değiştiren gerekir.</span><span class="sxs-lookup"><span data-stu-id="5000c-125">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="5000c-126">İçinde bildirilen değişken `fixed` deyimi değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="5000c-126">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="5000c-127">Burada tabi atık koleksiyonu olması gerekmez ve bu nedenle sabitlenmiş gerekmez yığında bellek ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5000c-127">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="5000c-128">Daha fazla bilgi için [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="5000c-128">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="5000c-129">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5000c-129">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5000c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5000c-130">See also</span></span>

- [<span data-ttu-id="5000c-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5000c-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5000c-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5000c-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5000c-133">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5000c-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5000c-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="5000c-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="5000c-135">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="5000c-135">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
