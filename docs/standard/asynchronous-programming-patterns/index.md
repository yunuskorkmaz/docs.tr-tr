---
title: Zaman Uyumsuz Programlama Desenleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068410"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="f50c4-102">Zaman Uyumsuz Programlama Desenleri</span><span class="sxs-lookup"><span data-stu-id="f50c4-102">Asynchronous Programming Patterns</span></span>

<span data-ttu-id="f50c4-103">.NET Framework zaman uyumsuz işlemleri gerçekleştirmek için üç desen sağlar:</span><span class="sxs-lookup"><span data-stu-id="f50c4-103">The .NET Framework provides three patterns for performing asynchronous operations:</span></span>  
  
- <span data-ttu-id="f50c4-104">**Zaman uyumsuz programlama modeli (APM)** desen (olarak da adlandırılan <xref:System.IAsyncResult> deseni), burada zaman uyumsuz işlemleri gerektirir `Begin` ve `End` yöntemleri (örneğin, `BeginWrite` ve `EndWrite` için zaman uyumsuz işlemleri yazın).</span><span class="sxs-lookup"><span data-stu-id="f50c4-104">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), where asynchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` for asynchronous write operations).</span></span> <span data-ttu-id="f50c4-105">Bu düzen, artık yeni geliştirme projeleri için tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="f50c4-105">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="f50c4-106">Daha fazla bilgi için [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="f50c4-106">For more information, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span></span>  
  
- <span data-ttu-id="f50c4-107">**Olay tabanlı zaman uyumsuz desen (EAP)**, bir yöntemin gerektiren `Async` sonek ve ayrıca bir veya daha fazla olay, olay işleyicisi temsilci türleri gerektirir ve `EventArg`-türetilmiş türler.</span><span class="sxs-lookup"><span data-stu-id="f50c4-107">**Event-based Asynchronous Pattern (EAP)**, which requires a method that has the `Async` suffix, and also requires one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="f50c4-108">EAP .NET Framework 2.0 sürümünde kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f50c4-108">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="f50c4-109">Artık yeni geliştirme projeleri için tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="f50c4-109">It is no longer recommended for new development.</span></span> <span data-ttu-id="f50c4-110">Daha fazla bilgi için [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="f50c4-110">For more information, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
- <span data-ttu-id="f50c4-111">**Görev tabanlı zaman uyumsuz desen (TAP)**, başlangıcını ve tamamlanmasını zaman uyumsuz bir işlemin temsil etmek için tek bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="f50c4-111">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="f50c4-112">DOKUNUN .NET Framework 4'te kullanıma sunulmuştur ve zaman uyumsuz için önerilen yaklaşım, .NET Framework programlama.</span><span class="sxs-lookup"><span data-stu-id="f50c4-112">TAP was introduced in the .NET Framework 4 and is the recommended approach to asynchronous programming in the .NET Framework.</span></span> <span data-ttu-id="f50c4-113">[Zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) C# anahtar sözcükleri ve [zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic dili işleçleri DOKUNUN için dil desteği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f50c4-113">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic Language add language support for TAP.</span></span> <span data-ttu-id="f50c4-114">Daha fazla bilgi için [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="f50c4-114">For more information, see [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>  
  
## <a name="comparing-patterns"></a><span data-ttu-id="f50c4-115">Desenleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="f50c4-115">Comparing Patterns</span></span>  

<span data-ttu-id="f50c4-116">Nasıl üç model zaman uyumsuz işlemler desenleri hızlı karşılaştırma için göz önünde bir `Read` belirtilen uzaklıkta başlayan sağlanan arabellek içine belirtilen miktarda veri okuyan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f50c4-116">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="f50c4-117">Bu yöntemin APM karşılığı kullanılabilmesini `BeginRead` ve `EndRead` yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="f50c4-117">The APM counterpart of this method would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
<span data-ttu-id="f50c4-118">EAP karşılığı türleri ve üyeleri aşağıdaki kümesini kullanıma:</span><span class="sxs-lookup"><span data-stu-id="f50c4-118">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="f50c4-119">DOKUNUN karşılığı aşağıdaki tek kullanılabilmesini `ReadAsync` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f50c4-119">The TAP counterpart would expose the following single `ReadAsync` method:</span></span>  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="f50c4-120">Sonraki bölümde verilen bağlantıları DOKUNUN, APM ve EAP kapsamlı bir tartışma için bkz.</span><span class="sxs-lookup"><span data-stu-id="f50c4-120">For a comprehensive discussion of TAP, APM, and EAP, see the links provided in the next section.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="f50c4-121">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="f50c4-121">Related topics</span></span>

| <span data-ttu-id="f50c4-122">Başlık</span><span class="sxs-lookup"><span data-stu-id="f50c4-122">Title</span></span> | <span data-ttu-id="f50c4-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f50c4-123">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="f50c4-124">Zaman Uyumsuz Programlama Modeli (APM)</span><span class="sxs-lookup"><span data-stu-id="f50c4-124">Asynchronous Programming Model (APM)</span></span>](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | <span data-ttu-id="f50c4-125">Kullanan eski model açıklar <xref:System.IAsyncResult> zaman uyumsuz davranışı sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="f50c4-125">Describes the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="f50c4-126">Bu model, artık yeni geliştirme projeleri için tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="f50c4-126">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="f50c4-127">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="f50c4-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | <span data-ttu-id="f50c4-128">Zaman uyumsuz davranış sağlamak için olay-tabanlı eski modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f50c4-128">Describes the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="f50c4-129">Bu model, artık yeni geliştirme projeleri için tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="f50c4-129">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="f50c4-130">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="f50c4-130">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | <span data-ttu-id="f50c4-131">Temel yeni zaman uyumsuz deseni açıklar <xref:System.Threading.Tasks> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f50c4-131">Describes the new asynchronous pattern based on the <xref:System.Threading.Tasks> namespace.</span></span> <span data-ttu-id="f50c4-132">Bu model, .NET Framework 4 ve sonraki sürümlerde zaman uyumsuz programlama için önerilen yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="f50c4-132">This model is the recommended approach to asynchronous programming in the .NET Framework 4 and later versions.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f50c4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f50c4-133">See also</span></span>

- [<span data-ttu-id="f50c4-134">C# zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="f50c4-134">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)   
- [<span data-ttu-id="f50c4-135">F # zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="f50c4-135">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [<span data-ttu-id="f50c4-136">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f50c4-136">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
