---
title: volatile (C# Başvurusu)
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 9950bb0e32787306dc34e2c006099332c06bda2b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199974"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="dd5b0-102">volatile (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dd5b0-102">volatile (C# Reference)</span></span>

<span data-ttu-id="dd5b0-103">`volatile` Anahtar sözcüğü gösteren bir alan, aynı anda yürütülen birden çok iş parçacığı tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="dd5b0-104">Derleyici, çalışma zamanı sistemi ve hatta donanım okuma ve bellek konumlara yazma işlemleri performans nedeniyle yeniden.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="dd5b0-105">Bildirilen alanları `volatile` bu iyileştirmeler tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="dd5b0-106">Ekleme `volatile` değiştiricisi, tüm iş parçacıklarının bunlar hedeflenerek gerçekleştirildi sırada başka bir iş parçacığı tarafından gerçekleştirilen geçici yazma dikkate almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="dd5b0-107">Bir tek toplam geçici yazma olarak görülen yürütme tüm iş parçacıklarından sıralama garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>
  
<span data-ttu-id="dd5b0-108">`volatile` Anahtar sözcüğü, bu tür alanlar için uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="dd5b0-108">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
- <span data-ttu-id="dd5b0-109">Başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-109">Reference types.</span></span>  
- <span data-ttu-id="dd5b0-110">İşaretçi türleri (güvenli olmayan bir bağlamda).</span><span class="sxs-lookup"><span data-stu-id="dd5b0-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="dd5b0-111">İşaretçi geçici olabilir, ancak işaret nesnesi dönüştürülemez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="dd5b0-112">Diğer bir deyişle, "işaretçisi geçici." bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-112">In other words, you cannot declare a "pointer to volatile."</span></span>  
- <span data-ttu-id="dd5b0-113">Basit türler gibi `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, ve `bool`.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>  
- <span data-ttu-id="dd5b0-114">Bir `enum` aşağıdaki temel türlerinden birini türüyle: `byte`, `sbyte`, `short`, `ushort`, `int`, veya `uint`.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>  
- <span data-ttu-id="dd5b0-115">Başvuru türleri olarak bilinen genel tür parametreleri.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="dd5b0-116"><xref:System.IntPtr> ve <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  

<span data-ttu-id="dd5b0-117">Diğer türleri dahil olmak üzere, `double` ve `long`, işaretlenemiyor `volatile` çünkü okuma ve yazma işlemleri bu türlerin alanları atomik olmasını garanti edilemez.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="dd5b0-118">Bu tür alanlar çok iş parçacıklı erişimi korumak için kullanmak <xref:System.Threading.Interlocked> sınıf üyeleri veya erişim kullanarak koruma [ `lock` ](lock-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="dd5b0-119">Volatile anahtar sözcüğü yalnızca alanlarına uygulanabilir bir `class` veya `struct`.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-119">The volatile keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="dd5b0-120">Yerel değişkenler bildirilemez `volatile`.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-120">Local variables cannot be declared `volatile`.</span></span>
  
## <a name="example"></a><span data-ttu-id="dd5b0-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd5b0-121">Example</span></span>

<span data-ttu-id="dd5b0-122">Aşağıdaki örnek, bir ortak alan değişken olarak bildirmek gösterilmektedir `volatile`.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-122">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="dd5b0-123">Aşağıdaki örnek nasıl yardımcı veya çalışan iş parçacığı oluşturulabilir ve birincil iş parçacığının ile paralel işleme gerçekleştirmek için kullanılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="dd5b0-124">Arka plan bilgileri için çoklu iş parçacığı hakkında bkz: [yönetilen iş parçacığı](../../../standard/threading/index.md) ve [parçacıkları (C#)](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd5b0-124">For background information about multithreading, see [Managed Threading](../../../standard/threading/index.md) and [Threading (C#)](../../programming-guide/concepts/threading/index.md).</span></span>  
  
[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="dd5b0-125">İle `volatile` bildirimi için eklenen değiştiricisi `_shouldStop` yerde, her zaman aynı sonuçları (yukarıdaki kodda gösterildiği alıntı benzer) elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="dd5b0-126">Ancak, bu değiştirici olmadan `_shouldStop` üyesi, davranıştır tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="dd5b0-127">`DoWork` Yöntemi eski verilerin okunmasını kaynaklanan üye erişimi iyileştirin.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="dd5b0-128">Çok iş parçacıklı programlama yapısı nedeniyle eski okuma sayısını tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="dd5b0-129">Programın farklı çalışmalarında biraz farklı sonuçlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dd5b0-130">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="dd5b0-130">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd5b0-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd5b0-131">See Also</span></span>

- [<span data-ttu-id="dd5b0-132">C#dil belirtimi: volatile anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="dd5b0-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="dd5b0-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="dd5b0-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dd5b0-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dd5b0-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dd5b0-135">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="dd5b0-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dd5b0-136">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="dd5b0-136">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="dd5b0-137">lock deyimi</span><span class="sxs-lookup"><span data-stu-id="dd5b0-137">lock statement</span></span>](lock-statement.md)
- <span data-ttu-id="dd5b0-138"><xref:System.Threading.Interlocked> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="dd5b0-138"><xref:System.Threading.Interlocked> class</span></span>
