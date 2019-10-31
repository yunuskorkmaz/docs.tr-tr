---
title: 'Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: 6efc89e5c22f53d9b2c48e535c783d488df16462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130334"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="55ab8-102">Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="55ab8-102">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="55ab8-103"><xref:System.Lazy%601?displayProperty=nameWithType> sınıfı, nesnelerin yavaş başlatılmasını ve örneklenmesini gerçekleştirme işini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="55ab8-103">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="55ab8-104">Nesneleri yavaş bir şekilde başlatarak, hiçbir zaman gerekli olmadıklarında bunları her türlü oluşturmak zorunda kalmaktan kaçınabilirsiniz veya ilk erişilene kadar başlatma işleminin ertelenebilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ab8-104">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="55ab8-105">Daha fazla bilgi için bkz. [yavaş başlatma](lazy-initialization.md).</span><span class="sxs-lookup"><span data-stu-id="55ab8-105">For more information, see [Lazy Initialization](lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ab8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="55ab8-106">Example</span></span>  
 <span data-ttu-id="55ab8-107">Aşağıdaki örnek, <xref:System.Lazy%601>bir değerin nasıl başlatılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ab8-107">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="55ab8-108">`someCondition` değişkenini true veya false olarak ayarlayan başka bir koda bağlı olarak, yavaş değişkenin gerekli olabileceğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="55ab8-108">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
  {  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
  }  
```  
  
## <a name="example"></a><span data-ttu-id="55ab8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="55ab8-109">Example</span></span>  
 <span data-ttu-id="55ab8-110">Aşağıdaki örnek, yalnızca geçerli iş parçacığındaki geçerli nesne örneği için görünür olan bir türü başlatmak üzere <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> sınıfının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ab8-110">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="55ab8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55ab8-111">See also</span></span>

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [<span data-ttu-id="55ab8-112">Geç Başlatma</span><span class="sxs-lookup"><span data-stu-id="55ab8-112">Lazy Initialization</span></span>](lazy-initialization.md)
