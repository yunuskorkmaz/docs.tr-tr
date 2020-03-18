---
title: uçucu - C# Referans
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712851"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="6ce6d-102">volatile (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6ce6d-102">volatile (C# Reference)</span></span>

<span data-ttu-id="6ce6d-103">Anahtar `volatile` kelime, bir alanın aynı anda yürütülen birden çok iş parçacığı tarafından değiştirilebileceğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="6ce6d-104">Derleyici, çalışma zamanı sistemi ve hatta donanım, performans nedenleriyle okumaları ve yazmaları bellek konumlarına yeniden düzenleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="6ce6d-105">Beyan edilen `volatile` alanlar bu optimizasyonlara tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="6ce6d-106">Değiştiricinin eklenmesi, tüm iş parçacıklarının, `volatile` gerçekleştirildikleri sırada başka bir iş parçacığı tarafından gerçekleştirilen geçici yazıları gözlemlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="6ce6d-107">Yürütmenin tüm iş parçacıklarından görüldüğü gibi, geçici yazmaların tek bir toplam siparişinin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="6ce6d-108">`volatile` Anahtar kelime bu tür alanlara uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="6ce6d-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="6ce6d-109">Başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-109">Reference types.</span></span>
- <span data-ttu-id="6ce6d-110">İşaretçi türleri (güvenli olmayan bir bağlamda).</span><span class="sxs-lookup"><span data-stu-id="6ce6d-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="6ce6d-111">İşaretçinin kendisi geçici olsa da, işaret ettiği nesnenin geçici olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="6ce6d-112">Başka bir deyişle, "uçucu işaretçi" olarak bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="6ce6d-113">`sbyte` `byte`,, `short` `ushort`, `int`, `uint`, `char`, `float`, `bool`, ve .</span><span class="sxs-lookup"><span data-stu-id="6ce6d-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="6ce6d-114">Aşağıdaki `enum` temel türlerden birine sahip `byte` `sbyte`bir `short` `ushort`tür: , , , `int`, veya `uint`.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="6ce6d-115">Başvuru türleri olduğu bilinen genel tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="6ce6d-116"><xref:System.IntPtr> ve <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="6ce6d-117">Bu tür `double` `long` `volatile` alanlara okunup yazdığı ndan, atomik olduğu garanti edilemez.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="6ce6d-118">Bu tür alanlara çok iş parçacığı erişimini <xref:System.Threading.Interlocked> korumak için sınıf üyelerini [`lock`](lock-statement.md) kullanın veya deyimi kullanarak erişimi koruyun.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="6ce6d-119">Anahtar `volatile` kelime yalnızca a `class` veya `struct`. alanlarına uygulanabilir</span><span class="sxs-lookup"><span data-stu-id="6ce6d-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="6ce6d-120">Yerel değişkenler bildirilemez. `volatile`</span><span class="sxs-lookup"><span data-stu-id="6ce6d-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="6ce6d-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ce6d-121">Example</span></span>

<span data-ttu-id="6ce6d-122">Aşağıdaki örnek, ortak alan değişkenini `volatile`nasıl .</span><span class="sxs-lookup"><span data-stu-id="6ce6d-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="6ce6d-123">Aşağıdaki örnek, yardımcı veya alt iş parçacığının birincil iş parçacığınınkine paralel olarak nasıl oluşturulabileceğini ve işleme gerçekleştirmek için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="6ce6d-124">Çok iş parçacığı hakkında daha fazla bilgi için [Yönetilen İş Parçacığı'na](../../../standard/threading/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="6ce6d-125">`volatile` Değiştirici yerinde bildirimine `_shouldStop` eklendikten sonra, her zaman aynı sonuçları alırsınız (önceki kodda gösterilen alıntıya benzer).</span><span class="sxs-lookup"><span data-stu-id="6ce6d-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="6ce6d-126">Ancak, `_shouldStop` üye üzerinde bu değiştirici olmadan, davranış öngörülemez.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="6ce6d-127">Yöntem, `DoWork` üye erişimini optimize ederek eski verilerin okunmasıyla sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="6ce6d-128">Çok iş parçacığı programlama doğası nedeniyle, bayat okuma sayısı öngörülemez.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="6ce6d-129">Programın farklı çalışır biraz farklı sonuçlar üretecektir.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6ce6d-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6ce6d-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6ce6d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ce6d-131">See also</span></span>

- [<span data-ttu-id="6ce6d-132">C# dil belirtimi: geçici anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="6ce6d-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="6ce6d-133">C# Referans</span><span class="sxs-lookup"><span data-stu-id="6ce6d-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ce6d-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6ce6d-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6ce6d-135">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="6ce6d-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6ce6d-136">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="6ce6d-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="6ce6d-137">kilit deyimi</span><span class="sxs-lookup"><span data-stu-id="6ce6d-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
