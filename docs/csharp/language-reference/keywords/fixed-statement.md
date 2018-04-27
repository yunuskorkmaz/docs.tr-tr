---
title: fixed Deyimi (C# Başvurusu)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dd117461f792ec7a10b740fbad277de52d05623
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="20230-102">fixed Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="20230-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="20230-103">`fixed` Deyimi taşınabilir bir değişken yerini değiştirme atık toplayıcı engeller.</span><span class="sxs-lookup"><span data-stu-id="20230-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="20230-104">`fixed` Deyimi izin yalnızca bir [güvensiz](unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="20230-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="20230-105">`Fixed` oluşturmak için de kullanılabilir [sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="20230-105">`Fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="20230-106">`fixed` Deyimi ayarlar bir işaretçi bir yönetilen değişken ve "PIN" için değişken deyimin yürütülmesi sırasında.</span><span class="sxs-lookup"><span data-stu-id="20230-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="20230-107">İşaretçileri taşınabilir yönetilen değişkenlere yalnızca yararlı bir `fixed` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="20230-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="20230-108">Olmadan bir `fixed` bağlamı, atık toplama taşımanızı değişkenleri beklenmedik şekilde.</span><span class="sxs-lookup"><span data-stu-id="20230-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="20230-109">C# Derleyici yalnızca bir işaretçi yönetilen bir değişkene atayın olanak sağlayan bir `fixed` deyimi.</span><span class="sxs-lookup"><span data-stu-id="20230-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="20230-110">Bir dizi, bir dize, bir sabit boyutlu arabellek veya değişkenin adresini kullanarak bir işaretçi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20230-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="20230-111">Aşağıdaki örnekte değişken adresleri, dizileri ve dizeleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="20230-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="20230-112">Sabit boyutlu arabellekler hakkında daha fazla bilgi için bkz: [sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="20230-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="20230-113">Aynı türde olmaları durumunda bir deyimde birden çok işaretçileri başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="20230-113">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="20230-114">Farklı türlerdeki işaretçileri başlatmak için yalnızca içe `fixed` aşağıdaki örnekte gösterildiği gibi deyimleri.</span><span class="sxs-lookup"><span data-stu-id="20230-114">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="20230-115">Deyim kodda yürütüldükten sonra tüm sabitlenmiş sabitlenmemiş ve atık toplama değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="20230-115">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="20230-116">Bu nedenle, bu değişkenleri dışında işaret etmiyor `fixed` deyimi.</span><span class="sxs-lookup"><span data-stu-id="20230-116">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="20230-117">Bildirilen değişkenlerin `fixed` deyimi bu kolaylaştıran bu deyim için kapsamlı:</span><span class="sxs-lookup"><span data-stu-id="20230-117">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="20230-118">İşaretçileri başlatılmış `fixed` deyimleri olan salt okunur değişkenler.</span><span class="sxs-lookup"><span data-stu-id="20230-118">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="20230-119">İşaretçi değeri değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirme ve değiştiren gerekir.</span><span class="sxs-lookup"><span data-stu-id="20230-119">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="20230-120">Bildirilen değişken `fixed` deyimi değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="20230-120">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="20230-121">Güvenli modda, burada atık toplama tabi değildir ve bu nedenle sabitlenmelidir gerekmez yığında bellek ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="20230-121">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="20230-122">Daha fazla bilgi için bkz: [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="20230-122">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="20230-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="20230-123">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="20230-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20230-124">See Also</span></span>

 [<span data-ttu-id="20230-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="20230-125">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="20230-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="20230-126">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="20230-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="20230-127">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="20230-128">unsafe</span><span class="sxs-lookup"><span data-stu-id="20230-128">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="20230-129">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="20230-129">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
