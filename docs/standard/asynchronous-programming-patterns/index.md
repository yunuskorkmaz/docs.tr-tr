---
title: Asenkron programlama desenleri
description: Görev tabanlı zaman uyumsuz model (TAP), olay tabanlı zaman uyumsuz model (EAP), .NET 'te & zaman uyumsuz programlama modeli (APM) hakkında bilgi edinin.
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: bd4d44d8de8a64be82e9ce6af593a86719b59fcf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583511"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="b11d2-103">Asenkron programlama desenleri</span><span class="sxs-lookup"><span data-stu-id="b11d2-103">Asynchronous programming patterns</span></span>

<span data-ttu-id="b11d2-104">.NET, zaman uyumsuz işlemleri gerçekleştirmek için üç model sağlar:</span><span class="sxs-lookup"><span data-stu-id="b11d2-104">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="b11d2-105">Zaman uyumsuz bir işlemin başlatılması ve tamamlanmasını temsil etmek için tek bir yöntem kullanan **görev tabanlı zaman uyumsuz model (TAP)**.</span><span class="sxs-lookup"><span data-stu-id="b11d2-105">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="b11d2-106">.NET Framework 4 ' te dokunma eklendi.</span><span class="sxs-lookup"><span data-stu-id="b11d2-106">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="b11d2-107">**.NET ' te zaman uyumsuz programlama için önerilen yaklaşımdır.**</span><span class="sxs-lookup"><span data-stu-id="b11d2-107">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="b11d2-108">C# ' deki [Async](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) anahtar sözcükleri ve Visual Basic ' deki [Async](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) işleçleri, TAP için dil desteği Ekle ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b11d2-108">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="b11d2-109">Daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz model (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="b11d2-109">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="b11d2-110">Zaman uyumsuz davranış sağlamaya yönelik olay tabanlı eski model olan **olay tabanlı zaman uyumsuz model (EAP)**.</span><span class="sxs-lookup"><span data-stu-id="b11d2-110">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="b11d2-111">`Async`Son ek ve bir veya daha fazla olay, olay işleyicisi temsilci türleri ve-türetilmiş türler içeren bir yöntem gerektirir `EventArg` .</span><span class="sxs-lookup"><span data-stu-id="b11d2-111">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="b11d2-112">EAP .NET Framework 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="b11d2-112">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="b11d2-113">Artık yeni geliştirme için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b11d2-113">It's no longer recommended for new development.</span></span> <span data-ttu-id="b11d2-114">Daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="b11d2-114">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="b11d2-115">Zaman uyumsuz davranış sağlamak için arabirimi kullanan eski model olan **zaman uyumsuz programlama modeli (APM)** modeli (Ayrıca, model olarak da bilinir <xref:System.IAsyncResult> ) <xref:System.IAsyncResult> .</span><span class="sxs-lookup"><span data-stu-id="b11d2-115">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="b11d2-116">Bu düzende, zaman uyumlu işlemler `Begin` ve `End` yöntemleri gerektirir (örneğin, `BeginWrite` ve `EndWrite` bir zaman uyumsuz yazma işlemi uygulamak için).</span><span class="sxs-lookup"><span data-stu-id="b11d2-116">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="b11d2-117">Bu model artık yeni geliştirme için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b11d2-117">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="b11d2-118">Daha fazla bilgi için bkz. [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="b11d2-118">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="b11d2-119">Desenlerin karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="b11d2-119">Comparison of patterns</span></span>

<span data-ttu-id="b11d2-120">Üç desenin zaman uyumsuz işlemlerin nasıl modellendiği hakkında hızlı bir karşılaştırma için, `Read` belirtilen bir uzaklığa göre belirtilen bir veri miktarını belirtilen bir arabellekte okuyan bir yöntemi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b11d2-120">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="b11d2-121">Bu yöntemin karşılık gelen DOKUNMASı, aşağıdaki tek yöntemi kullanıma sunar `ReadAsync` :</span><span class="sxs-lookup"><span data-stu-id="b11d2-121">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="b11d2-122">EAP karşılığı aşağıdaki tür ve üye kümesini kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="b11d2-122">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="b11d2-123">APM karşılığı, `BeginRead` ve yöntemlerini kullanıma sunar `EndRead` :</span><span class="sxs-lookup"><span data-stu-id="b11d2-123">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="b11d2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b11d2-124">See also</span></span>

- [<span data-ttu-id="b11d2-125">Zaman uyumsuz, derinlemesine</span><span class="sxs-lookup"><span data-stu-id="b11d2-125">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="b11d2-126">C 'de zaman uyumsuz programlama #</span><span class="sxs-lookup"><span data-stu-id="b11d2-126">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="b11d2-127">F 'de zaman uyumsuz programlama #</span><span class="sxs-lookup"><span data-stu-id="b11d2-127">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="b11d2-128">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b11d2-128">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
