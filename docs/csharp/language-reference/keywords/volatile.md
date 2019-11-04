---
title: Geçici C# başvuru
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: e72173ba1b91f03ccb1c15ca6451ac997666bc7f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422121"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="f7cb1-102">volatile (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f7cb1-102">volatile (C# Reference)</span></span>

<span data-ttu-id="f7cb1-103">`volatile` anahtar sözcüğü, bir alanın aynı anda yürütülen birden çok iş parçacığı tarafından değiştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="f7cb1-104">Derleyici, çalışma zamanı sistemi ve hatta donanım, performans nedeniyle bellek konumlarına okuma ve yazma işlemlerini yeniden düzenleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="f7cb1-105">`volatile` olarak belirtilen alanlar bu iyileştirmelere tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="f7cb1-106">`volatile` değiştiricisini eklemek, tüm iş parçacıklarının gerçekleştirilen diğer bir iş parçacığı tarafından gerçekleştirilen geçici yazmaları gözlemleyecek olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="f7cb1-107">Yürütmenin tüm iş parçacıklarından görüldüğü şekilde, tek bir toplam geçici yazma sıralaması garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="f7cb1-108">`volatile` anahtar sözcüğü bu türlerin alanlarına uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="f7cb1-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="f7cb1-109">Başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-109">Reference types.</span></span>
- <span data-ttu-id="f7cb1-110">İşaretçi türleri (güvenli olmayan bir bağlamda).</span><span class="sxs-lookup"><span data-stu-id="f7cb1-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="f7cb1-111">İşaretçinin kendisi geçici olsa da, işaret ettiği nesnenin bu şekilde olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="f7cb1-112">Diğer bir deyişle, "geçici işaretçi işaretçisi" bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="f7cb1-113">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`ve `bool`gibi basit türler.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="f7cb1-114">Aşağıdaki temel türlerden birine sahip `enum` türü: `byte`, `sbyte`, `short`, `ushort`, `int`veya `uint`.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="f7cb1-115">Başvuru türleri olarak bilinen genel tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="f7cb1-116"><xref:System.IntPtr> ve <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="f7cb1-117">`double` ve `long`dahil diğer türler `volatile` olarak işaretlenemez, çünkü bu türlerin alanlarına okuma ve yazma işlemleri atomik olarak garanti edilemez.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="f7cb1-118">Bu tür alanlara çok iş parçacıklı erişimi korumak için, <xref:System.Threading.Interlocked> sınıf üyelerini kullanın veya [`lock`](lock-statement.md) ifadesini kullanarak erişimi koruyun.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="f7cb1-119">`volatile` anahtar sözcüğü yalnızca bir `class` veya `struct`alanlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="f7cb1-120">Yerel değişkenler `volatile`olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="f7cb1-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7cb1-121">Example</span></span>

<span data-ttu-id="f7cb1-122">Aşağıdaki örnek, `volatile`olarak bir ortak alan değişkeninin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="f7cb1-123">Aşağıdaki örnek, birincil iş parçacığından paralel olarak işleme gerçekleştirmek için bir yardımcı veya çalışan iş parçacığının nasıl oluşturulup kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="f7cb1-124">Çoklu iş parçacığı hakkında daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7cb1-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="f7cb1-125">`_shouldStop` bildirimine eklenen `volatile` değiştiricisi ile, her zaman aynı sonuçları elde edersiniz (Yukarıdaki kodda gösterilen alıntıya benzer).</span><span class="sxs-lookup"><span data-stu-id="f7cb1-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="f7cb1-126">Ancak, `_shouldStop` üyesinde Bu değiştirici olmadan davranış tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="f7cb1-127">`DoWork` yöntemi üye erişimini iyileştirebilmenizi sağlayabilir ve bu da eski verilerin okunmasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="f7cb1-128">Çok iş parçacıklı programlama doğası nedeniyle, eski okuma sayısı tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="f7cb1-129">Programın farklı çalıştırmaları biraz farklı sonuçlar üretecektir.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f7cb1-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f7cb1-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f7cb1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7cb1-131">See also</span></span>

- [<span data-ttu-id="f7cb1-132">C#dil belirtimi: volatile anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f7cb1-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="f7cb1-133">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="f7cb1-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f7cb1-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f7cb1-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f7cb1-135">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f7cb1-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f7cb1-136">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="f7cb1-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f7cb1-137">Lock deyimleri</span><span class="sxs-lookup"><span data-stu-id="f7cb1-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
