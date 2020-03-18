---
title: Asenkron programlama desenleri
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: e1efe9c3eb57f317def91e527506c358eb086679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160059"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="db7fd-102">Asenkron programlama desenleri</span><span class="sxs-lookup"><span data-stu-id="db7fd-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="db7fd-103">.NET, eşzamanlı işlemler gerçekleştirmek için üç desen sağlar:</span><span class="sxs-lookup"><span data-stu-id="db7fd-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="db7fd-104">**Görev tabanlı Eşenkron Desen (TAP),** bir eşzamanlı işlemin başlatılmasını ve tamamlanmasını temsil etmek için tek bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="db7fd-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="db7fd-105">TAP ,.NET Framework 4'te tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="db7fd-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="db7fd-106">**.NET'te eşzamanlı programlamaiçin önerilen yaklaşımdır.**</span><span class="sxs-lookup"><span data-stu-id="db7fd-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="db7fd-107">C# [ve](../../csharp/language-reference/keywords/async.md) Visual Basic'teki [Async](../../visual-basic/language-reference/modifiers/async.md) ve [Await](../../visual-basic/language-reference/operators/await-operator.md) işleçleri, [await](../../csharp/language-reference/operators/await.md) TAP için dil desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="db7fd-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="db7fd-108">Daha fazla bilgi için [Görev Tabanlı Eşzamanlı Desen (TAP)](task-based-asynchronous-pattern-tap.md)'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="db7fd-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="db7fd-109">**Olay tabanlı Asynchronous Pattern (EAP)**, asynchronous davranış sağlamak için olay tabanlı eski modeldir.</span><span class="sxs-lookup"><span data-stu-id="db7fd-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="db7fd-110">`Async` Soneki ve bir veya daha fazla olay, olay işleyicisi `EventArg`temsilci türleri ve -türetilmiş türleri olan bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="db7fd-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="db7fd-111">EAP .NET Framework 2.0'da tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="db7fd-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="db7fd-112">Artık yeni bir gelişme için tavsiye edilmez.</span><span class="sxs-lookup"><span data-stu-id="db7fd-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="db7fd-113">Daha fazla bilgi için olay [tabanlı Eşzamanlı Desen (EAP)](event-based-asynchronous-pattern-eap.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="db7fd-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="db7fd-114">**Asynchronous Programming Model (APM)** <xref:System.IAsyncResult> deseni (desen olarak da adlandırılır), asynchronous davranış sağlamak için <xref:System.IAsyncResult> arabirimi kullanan eski modeldir.</span><span class="sxs-lookup"><span data-stu-id="db7fd-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="db7fd-115">Bu desende, senkron `Begin` işlemler `End` gerektirir ve `BeginWrite` yöntemleri `EndWrite` (örneğin, ve bir eşzamanlı yazma işlemi uygulamak için).</span><span class="sxs-lookup"><span data-stu-id="db7fd-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="db7fd-116">Bu desen artık yeni geliştirme için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="db7fd-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="db7fd-117">Daha fazla bilgi için, [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="db7fd-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="db7fd-118">Desenlerin karşılaştırılması</span><span class="sxs-lookup"><span data-stu-id="db7fd-118">Comparison of patterns</span></span>

<span data-ttu-id="db7fd-119">Üç modelin eşzamanlı işlemleri nasıl modellediğinin hızlı `Read` bir karşılaştırması için, belirli bir ofsetten başlayarak sağlanan bir arabellekte belirli miktarda veriyi okuyan bir yöntemi düşünün:</span><span class="sxs-lookup"><span data-stu-id="db7fd-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="db7fd-120">Bu yöntemin TAP karşılığı aşağıdaki `ReadAsync` tek yöntemi ortaya çıkarır:</span><span class="sxs-lookup"><span data-stu-id="db7fd-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="db7fd-121">EAP muadili aşağıdaki tür ve üye kümesini ortaya çıkar:</span><span class="sxs-lookup"><span data-stu-id="db7fd-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="db7fd-122">APM muadili `BeginRead` ve `EndRead` yöntemleri ortaya çıkaracak:</span><span class="sxs-lookup"><span data-stu-id="db7fd-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="db7fd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db7fd-123">See also</span></span>

- [<span data-ttu-id="db7fd-124">Derinlemesine Async</span><span class="sxs-lookup"><span data-stu-id="db7fd-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="db7fd-125">C'de asynchronous programlama #</span><span class="sxs-lookup"><span data-stu-id="db7fd-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="db7fd-126">F'de Async Programlama #</span><span class="sxs-lookup"><span data-stu-id="db7fd-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="db7fd-127">Async ve Await ile Asynchronous Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db7fd-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
