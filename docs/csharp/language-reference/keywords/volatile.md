---
description: volatile-C# başvurusu
title: volatile-C# başvurusu
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: bb89e99e8e28ff1e263817f498619dbfae700a50
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141705"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="78c99-103">volatile (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="78c99-103">volatile (C# Reference)</span></span>

<span data-ttu-id="78c99-104">`volatile`Anahtar sözcüğü, bir alanın aynı anda yürütülen birden çok iş parçacığı tarafından değiştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="78c99-104">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="78c99-105">Derleyici, çalışma zamanı sistemi ve hatta donanım, performans nedeniyle bellek konumlarına okuma ve yazma işlemlerini yeniden düzenleyebilir.</span><span class="sxs-lookup"><span data-stu-id="78c99-105">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="78c99-106">Belirtilen alanlar `volatile` bu iyileştirmelere tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="78c99-106">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="78c99-107">Değiştirici eklendiğinde, `volatile` tüm iş parçacıklarının diğer bir iş parçacığı tarafından gerçekleştirilen geçici yazmaları gerçekleştirdikleri sırayla gözlemleyecek olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="78c99-107">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="78c99-108">Yürütmenin tüm iş parçacıklarından görüldüğü şekilde, tek bir toplam geçici yazma sıralaması garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="78c99-108">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="78c99-109">`volatile`Anahtar sözcüğü bu türlerin alanlarına uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="78c99-109">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="78c99-110">Başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="78c99-110">Reference types.</span></span>
- <span data-ttu-id="78c99-111">İşaretçi türleri (güvenli olmayan bir bağlamda).</span><span class="sxs-lookup"><span data-stu-id="78c99-111">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="78c99-112">İşaretçinin kendisi geçici olsa da, işaret ettiği nesnenin bu şekilde olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="78c99-112">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="78c99-113">Diğer bir deyişle, "geçici işaretçi işaretçisi" bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="78c99-113">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="78c99-114">,,, `sbyte` `byte` `short` `ushort` , `int` , `uint` , `char` , `float` Ve `bool` gibi basit türler.</span><span class="sxs-lookup"><span data-stu-id="78c99-114">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="78c99-115">`enum`Aşağıdaki temel türlerden birine sahip bir tür: `byte` ,,, `sbyte` `short` `ushort` , `int` , veya `uint` .</span><span class="sxs-lookup"><span data-stu-id="78c99-115">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="78c99-116">Başvuru türleri olarak bilinen genel tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="78c99-116">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="78c99-117"><xref:System.IntPtr> ve <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="78c99-117"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="78c99-118">Ve dahil diğer türler `double` , `long` `volatile` Bu türlerin alanlarına okuma ve yazma işlemleri atomik olarak garanti edilmediği için işaretlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="78c99-118">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="78c99-119">Bu tür alanlara çok iş parçacıklı erişimi korumak için, <xref:System.Threading.Interlocked> sınıf üyelerini kullanın veya ifadesini kullanarak erişimi koruyun [`lock`](lock-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="78c99-119">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="78c99-120">`volatile`Anahtar sözcüğü yalnızca bir veya alanlarına uygulanabilir `class` `struct` .</span><span class="sxs-lookup"><span data-stu-id="78c99-120">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="78c99-121">Yerel değişkenler bildirilemez `volatile` .</span><span class="sxs-lookup"><span data-stu-id="78c99-121">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="78c99-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="78c99-122">Example</span></span>

<span data-ttu-id="78c99-123">Aşağıdaki örnek, olarak bir ortak alan değişkeninin nasıl bildirilemeyeceğini gösterir `volatile` .</span><span class="sxs-lookup"><span data-stu-id="78c99-123">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="78c99-124">Aşağıdaki örnek, birincil iş parçacığından paralel olarak işleme gerçekleştirmek için bir yardımcı veya çalışan iş parçacığının nasıl oluşturulup kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="78c99-124">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="78c99-125">Çoklu iş parçacığı hakkında daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="78c99-125">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="78c99-126">`volatile`Yerine gelen bildirimine eklenen değiştiriciyle `_shouldStop` , her zaman aynı sonuçları elde edersiniz (Yukarıdaki kodda gösterilen alıntıya benzer).</span><span class="sxs-lookup"><span data-stu-id="78c99-126">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="78c99-127">Ancak, üye üzerinde bu değiştirici olmadan `_shouldStop` davranış tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="78c99-127">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="78c99-128">`DoWork`Yöntemi, üye erişimini iyileştirebilmenizi sağlayabilir ve bu da eski verilerin okunmasına yol açar.</span><span class="sxs-lookup"><span data-stu-id="78c99-128">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="78c99-129">Çok iş parçacıklı programlama doğası nedeniyle, eski okuma sayısı tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="78c99-129">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="78c99-130">Programın farklı çalıştırmaları biraz farklı sonuçlar üretecektir.</span><span class="sxs-lookup"><span data-stu-id="78c99-130">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="78c99-131">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="78c99-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="78c99-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78c99-132">See also</span></span>

- [<span data-ttu-id="78c99-133">C# dil belirtimi: volatile anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="78c99-133">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="78c99-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="78c99-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="78c99-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="78c99-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="78c99-136">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="78c99-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="78c99-137">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="78c99-137">Modifiers</span></span>](index.md)
- [<span data-ttu-id="78c99-138">Lock deyimleri</span><span class="sxs-lookup"><span data-stu-id="78c99-138">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
