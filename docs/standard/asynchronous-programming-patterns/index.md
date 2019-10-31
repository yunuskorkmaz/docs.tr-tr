---
title: Zaman uyumsuz programlama desenleri
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: dfce69ee18b8346cd802b4934de63bf0a39c72f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124265"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="f8d0f-102">Zaman uyumsuz programlama desenleri</span><span class="sxs-lookup"><span data-stu-id="f8d0f-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="f8d0f-103">.NET, zaman uyumsuz işlemleri gerçekleştirmek için üç model sağlar:</span><span class="sxs-lookup"><span data-stu-id="f8d0f-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="f8d0f-104">Zaman uyumsuz bir işlemin başlatılması ve tamamlanmasını temsil etmek için tek bir yöntem kullanan **görev tabanlı zaman uyumsuz model (TAP)** .</span><span class="sxs-lookup"><span data-stu-id="f8d0f-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="f8d0f-105">.NET Framework 4 ' te dokunma eklendi.</span><span class="sxs-lookup"><span data-stu-id="f8d0f-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="f8d0f-106">**.NET ' te zaman uyumsuz programlama için önerilen yaklaşımdır.**</span><span class="sxs-lookup"><span data-stu-id="f8d0f-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="f8d0f-107">' Deki [Async](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) anahtar C# sözcükleri ve Visual Basic ' deki [Async](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) işleçleri, TAP için dil desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="f8d0f-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="f8d0f-108">Daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz model (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="f8d0f-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="f8d0f-109">Zaman uyumsuz davranış sağlamaya yönelik olay tabanlı eski model olan **olay tabanlı zaman uyumsuz model (EAP)** .</span><span class="sxs-lookup"><span data-stu-id="f8d0f-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="f8d0f-110">`Async` soneki ve bir veya daha fazla olay, olay işleyicisi temsilci türleri ve `EventArg`türetilmiş türler içeren bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8d0f-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="f8d0f-111">EAP .NET Framework 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="f8d0f-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="f8d0f-112">Artık yeni geliştirme için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f8d0f-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="f8d0f-113">Daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="f8d0f-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="f8d0f-114">Zaman uyumsuz davranış sağlamak için <xref:System.IAsyncResult> arabirimini kullanan eski model olan **zaman uyumsuz programlama modeli (APM)** modeli (<xref:System.IAsyncResult> modeli olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="f8d0f-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="f8d0f-115">Bu düzende, zaman uyumlu işlemler `Begin` ve `End` yöntemleri gerektirir (örneğin, `BeginWrite` ve `EndWrite` zaman uyumsuz bir yazma işlemi uygular).</span><span class="sxs-lookup"><span data-stu-id="f8d0f-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="f8d0f-116">Bu model artık yeni geliştirme için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f8d0f-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="f8d0f-117">Daha fazla bilgi için bkz. [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="f8d0f-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="f8d0f-118">Desenlerin karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="f8d0f-118">Comparison of patterns</span></span>

<span data-ttu-id="f8d0f-119">Üç desenin zaman uyumsuz işlemlerin nasıl modellendiği hakkında hızlı bir karşılaştırma için, belirtilen bir uzaklığa göre belirtilen bir veri miktarını belirtilen bir arabellekte okuyan bir `Read` yöntemi düşünün:</span><span class="sxs-lookup"><span data-stu-id="f8d0f-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="f8d0f-120">Bu yöntemin karşılık gelen DOKUNMASı aşağıdaki tek `ReadAsync` yöntemi kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="f8d0f-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="f8d0f-121">EAP karşılığı aşağıdaki tür ve üye kümesini kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="f8d0f-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="f8d0f-122">APM karşılığına `BeginRead` ve `EndRead` yöntemleri kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="f8d0f-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="f8d0f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8d0f-123">See also</span></span>

- [<span data-ttu-id="f8d0f-124">Zaman uyumsuz, derinlemesine</span><span class="sxs-lookup"><span data-stu-id="f8d0f-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="f8d0f-125">İçinde zaman uyumsuz programlamaC#</span><span class="sxs-lookup"><span data-stu-id="f8d0f-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="f8d0f-126">İçinde zaman uyumsuz programlamaF#</span><span class="sxs-lookup"><span data-stu-id="f8d0f-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="f8d0f-127">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8d0f-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
