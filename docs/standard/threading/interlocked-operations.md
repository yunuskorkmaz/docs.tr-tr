---
title: "Birbirine Kenetlenmiş İşlemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 122058b7e826e27fe6c60c5b07610f7c63e64f78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interlocked-operations"></a><span data-ttu-id="777ae-102">Birbirine Kenetlenmiş İşlemler</span><span class="sxs-lookup"><span data-stu-id="777ae-102">Interlocked Operations</span></span>
<span data-ttu-id="777ae-103"><xref:System.Threading.Interlocked> Sınıfı birden çok iş parçacığı tarafından paylaşılan bir değişken erişimi eşitlemek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="777ae-103">The <xref:System.Threading.Interlocked> class provides methods that synchronize access to a variable that is shared by multiple threads.</span></span> <span data-ttu-id="777ae-104">Değişken paylaşılan bellekte ise iş parçacıkları farklı işlemler, bu mekanizma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="777ae-104">The threads of different processes can use this mechanism if the variable is in shared memory.</span></span> <span data-ttu-id="777ae-105">Birbirine kenetlenmiş işlemler atomik — diğer bir deyişle, tüm işlem aynı değişkeni ınterlocked başka bir işlem tarafından kesilemez bir birimdir.</span><span class="sxs-lookup"><span data-stu-id="777ae-105">Interlocked operations are atomic — that is, the entire operation is a unit that cannot be interrupted by another interlocked operation on the same variable.</span></span> <span data-ttu-id="777ae-106">Bu, bir iş parçacığı bir bellek adresi, ancak önce alter ve depolamak için Fırsat sahip bir değer yüklendikten sonra askıya alınabilir işletim sistemlerinde PreEmptive tarafından ile çoklu iş parçacığı kullanımı, önemlidir.</span><span class="sxs-lookup"><span data-stu-id="777ae-106">This is important in operating systems with preemptive multithreading, where a thread can be suspended after loading a value from a memory address, but before having the chance to alter it and store it.</span></span>  
  
 <span data-ttu-id="777ae-107"><xref:System.Threading.Interlocked> Sınıfı, aşağıdaki işlemleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="777ae-107">The <xref:System.Threading.Interlocked> class provides the following operations:</span></span>  
  
-   <span data-ttu-id="777ae-108">.NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.Add%2A> yöntemi bir tamsayı değeri bir değişkene ekler ve yeni değişkenin değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="777ae-108">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method adds an integer value to a variable and returns the new value of the variable.</span></span>  
  
-   <span data-ttu-id="777ae-109">.NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.Read%2A> yöntemi bir 64-bit tamsayı değeri atomik bir işlem olarak okur.</span><span class="sxs-lookup"><span data-stu-id="777ae-109">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Read%2A> method reads a 64-bit integer value as an atomic operation.</span></span> <span data-ttu-id="777ae-110">Bu bir 64-bit tamsayı okuma normalde atomik bir işlem olduğu 32-bit işletim sistemlerinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="777ae-110">This is useful on 32-bit operating systems, where reading a 64-bit integer is not ordinarily an atomic operation.</span></span>  
  
-   <span data-ttu-id="777ae-111"><xref:System.Threading.Interlocked.Increment%2A> Ve <xref:System.Threading.Interlocked.Decrement%2A> yöntemleri artırın veya bir değişken azaltma ve çıkan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="777ae-111">The <xref:System.Threading.Interlocked.Increment%2A> and <xref:System.Threading.Interlocked.Decrement%2A> methods increment or decrement a variable and return the resulting value.</span></span>  
  
-   <span data-ttu-id="777ae-112"><xref:System.Threading.Interlocked.Exchange%2A> Yöntemi, o değer ve yeni değerle yerine belirtilen bir değişkende değerinin atomik bir exchange gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="777ae-112">The <xref:System.Threading.Interlocked.Exchange%2A> method performs an atomic exchange of the value in a specified variable, returning that value and replacing it with a new value.</span></span> <span data-ttu-id="777ae-113">Bu yöntemin bir genel aşırı .NET Framework sürüm 2. 0'da, bu exchange herhangi başvuru türünde bir değişken gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="777ae-113">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="777ae-114">Bkz: <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span><span class="sxs-lookup"><span data-stu-id="777ae-114">See <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span></span>  
  
-   <span data-ttu-id="777ae-115"><xref:System.Threading.Interlocked.CompareExchange%2A> Yöntemi de alış verişleri iki değerleri, ancak bir karşılaştırma sonucu üzerinde contingent.</span><span class="sxs-lookup"><span data-stu-id="777ae-115">The <xref:System.Threading.Interlocked.CompareExchange%2A> method also exchanges two values, but contingent on the result of a comparison.</span></span> <span data-ttu-id="777ae-116">Bu yöntemin bir genel aşırı .NET Framework sürüm 2. 0'da, bu exchange herhangi başvuru türünde bir değişken gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="777ae-116">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="777ae-117">Bkz: <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span><span class="sxs-lookup"><span data-stu-id="777ae-117">See <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span></span>  
  
 <span data-ttu-id="777ae-118">Modern işlemcilerde yöntemlerinin <xref:System.Threading.Interlocked> sınıfı tarafından tek bir yönerge genellikle uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="777ae-118">On modern processors, the methods of the <xref:System.Threading.Interlocked> class can often be implemented by a single instruction.</span></span> <span data-ttu-id="777ae-119">Bu nedenle, bunlar çok yüksek performanslı eşitleme sağlamak ve üst düzey eşitleme mekanizmaları oluşturmak için kullanılan ister döndürme kilitler.</span><span class="sxs-lookup"><span data-stu-id="777ae-119">Thus, they provide very high-performance synchronization and can be used to build higher-level synchronization mechanisms, like spin locks.</span></span>  
  
 <span data-ttu-id="777ae-120">Kullanan bir örnek <xref:System.Threading.Monitor> ve <xref:System.Threading.Interlocked> bileşimi sınıflara bakın [izleyicileri](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="777ae-120">For an example that uses the <xref:System.Threading.Monitor> and <xref:System.Threading.Interlocked> classes in combination, see [Monitors](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="compareexchange-example"></a><span data-ttu-id="777ae-121">CompareExchange örneği</span><span class="sxs-lookup"><span data-stu-id="777ae-121">CompareExchange Example</span></span>  
 <span data-ttu-id="777ae-122"><xref:System.Threading.Interlocked.CompareExchange%2A> Yöntemi, basit artırma ve azaltma daha karmaşık hesaplamalar korumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="777ae-122">The <xref:System.Threading.Interlocked.CompareExchange%2A> method can be used to protect computations that are more complicated than simple increment and decrement.</span></span> <span data-ttu-id="777ae-123">Aşağıdaki örnek, bir kayan olarak depolanan toplam ekleyen bir iş parçacığı yöntemi gösterir nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="777ae-123">The following example demonstrates a thread-safe method that adds to a running total stored as a floating point number.</span></span> <span data-ttu-id="777ae-124">(Tamsayılar, <xref:System.Threading.Interlocked.Add%2A> daha basit bir çözüm yöntemidir.) Tam kod örnekleri için bkz: aşırı <xref:System.Threading.Interlocked.CompareExchange%2A> tek duyarlıklı ve çift duyarlıklı kayan nokta değişkenleri alın (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> ve <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span><span class="sxs-lookup"><span data-stu-id="777ae-124">(For integers, the <xref:System.Threading.Interlocked.Add%2A> method is a simpler solution.) For complete code examples, see the overloads of <xref:System.Threading.Interlocked.CompareExchange%2A> that take single-precision and double-precision floating-point arguments (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> and <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a><span data-ttu-id="777ae-125">Exchange ve CompareExchange türsüz aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="777ae-125">Untyped Overloads of Exchange and CompareExchange</span></span>  
 <span data-ttu-id="777ae-126"><xref:System.Threading.Interlocked.Exchange%2A> Ve <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemlerine sahip türünde bağımsız değişkenler almayan aşırı <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="777ae-126">The <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods have overloads that take arguments of type <xref:System.Object>.</span></span> <span data-ttu-id="777ae-127">İlk bağımsız değişken her birinin bu aşırı `ref Object` (`ByRef … As Object` Visual Basic'te), ve tür güvenliği gerektiren bu bağımsız değişken olarak kesinlikle yazılması için geçirilen değişken <xref:System.Object>; yazmak için ilk bağımsız değişken yalnızca atanamaz <xref:System.Object> Bu yöntemleri çağrılırken.</span><span class="sxs-lookup"><span data-stu-id="777ae-127">The first argument of each of these overloads is `ref Object` (`ByRef … As Object` in Visual Basic), and type safety requires the variable passed to this argument to be typed strictly as <xref:System.Object>; you cannot simply cast the first argument to type <xref:System.Object> when calling these methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="777ae-128">.NET Framework sürüm 2. 0'da, genel aşırı kullanmak <xref:System.Threading.Interlocked.Exchange%2A> ve <xref:System.Threading.Interlocked.CompareExchange%2A> kesinlikle gönderip almak için yöntemleri yazılan değişkenler.</span><span class="sxs-lookup"><span data-stu-id="777ae-128">In the .NET Framework version 2.0, use the generic overloads of the <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods to exchange strongly typed variables.</span></span>  
  
 <span data-ttu-id="777ae-129">Aşağıdaki kod örneğinde türünde bir özellik gösterir `ClassA` ayarlanabilecek yalnızca bir kez, .NET Framework sürüm 1.0 veya 1.1 uygulanan.</span><span class="sxs-lookup"><span data-stu-id="777ae-129">The following code example shows a property of type `ClassA` that can be set only once, as it might be implemented in the .NET Framework version 1.0 or 1.1.</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="777ae-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="777ae-130">See Also</span></span>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="777ae-131">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="777ae-131">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="777ae-132">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="777ae-132">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
