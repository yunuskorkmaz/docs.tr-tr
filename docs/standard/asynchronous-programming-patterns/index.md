---
title: Zaman uyumsuz programlama desenleri
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d76aef201fead37923a65cfeead16638b09842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031180"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="3ede8-102">Zaman uyumsuz programlama desenleri</span><span class="sxs-lookup"><span data-stu-id="3ede8-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="3ede8-103">.NET, zaman uyumsuz işlemleri gerçekleştirmek için üç desen sağlar:</span><span class="sxs-lookup"><span data-stu-id="3ede8-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="3ede8-104">**Görev tabanlı zaman uyumsuz desen (TAP)**, başlangıcını ve tamamlanmasını zaman uyumsuz bir işlemin temsil etmek için tek bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ede8-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="3ede8-105">DOKUNUN, .NET Framework 4'te tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="3ede8-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="3ede8-106">**. NET'te zaman uyumsuz programlama için önerilen yaklaşımdır.**</span><span class="sxs-lookup"><span data-stu-id="3ede8-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="3ede8-107">[Zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) anahtar sözcükleri C# ve [zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic'de işleçler DOKUNUN için dil desteği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ede8-107">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="3ede8-108">Daha fazla bilgi için [görev tabanlı zaman uyumsuz desen (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="3ede8-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="3ede8-109">**Olay tabanlı zaman uyumsuz desen (EAP)**, zaman uyumsuz davranış sağlamak için olay-tabanlı eski model olduğu.</span><span class="sxs-lookup"><span data-stu-id="3ede8-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="3ede8-110">Bir yöntemin gerektirir `Async` soneki ve bir veya daha fazla olaylar, olay işleyicisi temsilci türleri ve `EventArg`-türetilmiş türler.</span><span class="sxs-lookup"><span data-stu-id="3ede8-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="3ede8-111">EAP .NET Framework 2.0 sürümünde kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="3ede8-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="3ede8-112">Artık yeni geliştirme projeleri için tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="3ede8-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="3ede8-113">Daha fazla bilgi için [olay tabanlı zaman uyumsuz desen (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="3ede8-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="3ede8-114">**Zaman uyumsuz programlama modeli (APM)** desen (olarak da adlandırılan <xref:System.IAsyncResult> deseni), kullanan eski model olduğu <xref:System.IAsyncResult> zaman uyumsuz davranışı sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="3ede8-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="3ede8-115">Bu düzende, zaman uyumlu işlemler gerektiren `Begin` ve `End` yöntemleri (örneğin, `BeginWrite` ve `EndWrite` bir zaman uyumsuz yazma işlemini uygulamak için).</span><span class="sxs-lookup"><span data-stu-id="3ede8-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="3ede8-116">Bu düzen, artık yeni geliştirme projeleri için tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="3ede8-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="3ede8-117">Daha fazla bilgi için [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="3ede8-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="3ede8-118">Desenler karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="3ede8-118">Comparison of patterns</span></span>

<span data-ttu-id="3ede8-119">Nasıl üç model zaman uyumsuz işlemler desenleri hızlı karşılaştırma için göz önünde bir `Read` belirtilen uzaklıkta başlayan sağlanan arabellek içine belirtilen miktarda veri okuyan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3ede8-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="3ede8-120">Bu yöntemin DOKUNUN karşılığı aşağıdaki tek kullanılabilmesini `ReadAsync` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3ede8-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="3ede8-121">EAP karşılığı türleri ve üyeleri aşağıdaki kümesini kullanıma:</span><span class="sxs-lookup"><span data-stu-id="3ede8-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="3ede8-122">APM karşılığı kullanılabilmesini `BeginRead` ve `EndRead` yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="3ede8-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="3ede8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ede8-123">See also</span></span>

- [<span data-ttu-id="3ede8-124">Zaman uyumsuz derinlemesine</span><span class="sxs-lookup"><span data-stu-id="3ede8-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="3ede8-125">C# zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="3ede8-125">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)
- [<span data-ttu-id="3ede8-126">Zaman uyumsuz programlamaF#</span><span class="sxs-lookup"><span data-stu-id="3ede8-126">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="3ede8-127">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ede8-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
