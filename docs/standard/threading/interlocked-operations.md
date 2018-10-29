---
title: Birbirine Kenetlenmiş İşlemler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f96286da84e41e79fb0b6253d6f20eea89da21a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201364"
---
# <a name="interlocked-operations"></a><span data-ttu-id="0660c-102">Birbirine kenetlenmiş işlemler</span><span class="sxs-lookup"><span data-stu-id="0660c-102">Interlocked operations</span></span>

<span data-ttu-id="0660c-103"><xref:System.Threading.Interlocked?displayProperty=nameWithType> Sınıfı, birden çok iş parçacığı tarafından paylaşılan bir değişkene erişimi eşitleme yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0660c-103">The <xref:System.Threading.Interlocked?displayProperty=nameWithType> class provides methods that synchronize access to a variable that is shared by multiple threads.</span></span> <span data-ttu-id="0660c-104">Değişken paylaşılan bellekte ise, iş parçacıkları farklı işlemler, bu mekanizma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0660c-104">The threads of different processes can use this mechanism if the variable is in shared memory.</span></span> <span data-ttu-id="0660c-105">Birbirine kenetlenmiş işlemler atomik — diğer bir deyişle, tüm işlemi aynı değişken üzerinde başka bir işlem tarafından kesintiye birimidir.</span><span class="sxs-lookup"><span data-stu-id="0660c-105">Interlocked operations are atomic — that is, the entire operation is a unit that cannot be interrupted by another operation on the same variable.</span></span> <span data-ttu-id="0660c-106">Burada bir iş parçacığı bir bellek adresi, ancak önce onu değiştirmenize ve depolamak için bir fırsat sahip bir değer yüklendikten sonra askıya alınmadan bu işletim sistemlerinde preemptive ile çoklu iş parçacığı önem taşır.</span><span class="sxs-lookup"><span data-stu-id="0660c-106">This is important in operating systems with preemptive multithreading, where a thread can be suspended after loading a value from a memory address, but before having the chance to alter it and store it.</span></span>  
  
 <span data-ttu-id="0660c-107"><xref:System.Threading.Interlocked> Sınıfı aşağıdaki işlemleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="0660c-107">The <xref:System.Threading.Interlocked> class provides the following operations:</span></span>  
  
-   <span data-ttu-id="0660c-108"><xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> Yöntemi bir tamsayı değeri bir değişkene ekler ve yeni bir değişkenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0660c-108">The <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> method adds an integer value to a variable and returns the new value of the variable.</span></span>  
  
-   <span data-ttu-id="0660c-109"><xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> Yöntemi, bir 64-bit tamsayı değeri atomik işlem olarak okur.</span><span class="sxs-lookup"><span data-stu-id="0660c-109">The <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> method reads a 64-bit integer value as an atomic operation.</span></span> <span data-ttu-id="0660c-110">Bu bir 64-bit tamsayı okuma normalde atomik bir işlem olduğu 32-bit işletim sistemlerinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="0660c-110">This is useful on 32-bit operating systems, where reading a 64-bit integer is not ordinarily an atomic operation.</span></span>  
  
-   <span data-ttu-id="0660c-111"><xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Interlocked.Decrement%2A?displayProperty=nameWithType> yöntemleri artırın veya bir değişkeni azaltır ve sonuç değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0660c-111">The <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> and <xref:System.Threading.Interlocked.Decrement%2A?displayProperty=nameWithType> methods increment or decrement a variable and return the resulting value.</span></span>  
  
-   <span data-ttu-id="0660c-112"><xref:System.Threading.Interlocked.Exchange%2A?displayProperty=nameWithType> Yöntemi, o değer ve yeni bir değerle değiştirmeyi belirtilen bir değişkende değeri atomik bir değişim gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0660c-112">The <xref:System.Threading.Interlocked.Exchange%2A?displayProperty=nameWithType> method performs an atomic exchange of the value in a specified variable, returning that value and replacing it with a new value.</span></span> <span data-ttu-id="0660c-113">Genel bir <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29> exchange herhangi bir başvuru türünde bir değişken üzerinde gerçekleştirmek için bu yöntem aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="0660c-113">Use a generic <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29> overload of this method to perform the exchange on a variable of any reference type.</span></span>  
  
-   <span data-ttu-id="0660c-114"><xref:System.Threading.Interlocked.CompareExchange%2A?displayProperty=nameWithType> Yöntemi de birbiriyle değiştirir iki değerler, ancak bir karşılaştırma sonucu topolojideki.</span><span class="sxs-lookup"><span data-stu-id="0660c-114">The <xref:System.Threading.Interlocked.CompareExchange%2A?displayProperty=nameWithType> method also exchanges two values, but contingent on the result of a comparison.</span></span> <span data-ttu-id="0660c-115">Genel bir <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> exchange herhangi bir başvuru türünde bir değişken üzerinde gerçekleştirmek için bu yöntem aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="0660c-115">Use a generic <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> overload of this method to perform the exchange on a variable of any reference type.</span></span>  
  
 <span data-ttu-id="0660c-116">Modern işlemcilerde yöntemlerinin <xref:System.Threading.Interlocked> sınıfı tek bir yönerge genellikle uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="0660c-116">On modern processors, the methods of the <xref:System.Threading.Interlocked> class can often be implemented by a single instruction.</span></span> <span data-ttu-id="0660c-117">Bu nedenle, bunlar çok yüksek performanslı eşitlemeyi sağlaması ve daha üst düzey eşitleme mekanizmaları oluşturmak için kullanılan dönüş kilitleri ister.</span><span class="sxs-lookup"><span data-stu-id="0660c-117">Thus, they provide very high-performance synchronization and can be used to build higher-level synchronization mechanisms, like spin locks.</span></span>  
  
 <span data-ttu-id="0660c-118">Kullanan bir örnek için <xref:System.Threading.Monitor> ve <xref:System.Threading.Interlocked> birleşimi, sınıflara bakın <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="0660c-118">For an example that uses the <xref:System.Threading.Monitor> and <xref:System.Threading.Interlocked> classes in combination, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="compareexchange-example"></a><span data-ttu-id="0660c-119">CompareExchange örneği</span><span class="sxs-lookup"><span data-stu-id="0660c-119">CompareExchange example</span></span>

 <span data-ttu-id="0660c-120"><xref:System.Threading.Interlocked.CompareExchange%2A> Yöntemi, daha basit artırma ve azaltma daha karmaşık hesaplamaları korumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0660c-120">The <xref:System.Threading.Interlocked.CompareExchange%2A> method can be used to protect computations that are more complicated than simple increment and decrement.</span></span> <span data-ttu-id="0660c-121">Aşağıdaki örnek, bir değişken olarak depolanan toplam ekleyen bir iş parçacığı açısından güvenli yöntemi gösterir. nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="0660c-121">The following example demonstrates a thread-safe method that adds to a running total stored as a floating point number.</span></span> <span data-ttu-id="0660c-122">(Tamsayılar için <xref:System.Threading.Interlocked.Add%2A> yöntemi daha basit bir çözümdür.) Tam kod örnekleri için bkz. aşırı yüklemeleri <xref:System.Threading.Interlocked.CompareExchange%2A> tek duyarlık hem çift duyarlıklı kayan nokta bağımsız değişkenleri alır (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> ve <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span><span class="sxs-lookup"><span data-stu-id="0660c-122">(For integers, the <xref:System.Threading.Interlocked.Add%2A> method is a simpler solution.) For complete code examples, see the overloads of <xref:System.Threading.Interlocked.CompareExchange%2A> that take single-precision and double-precision floating-point arguments (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> and <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a><span data-ttu-id="0660c-123">Exchange ve CompareExchange yazılmamış aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="0660c-123">Untyped overloads of Exchange and CompareExchange</span></span>

 <span data-ttu-id="0660c-124"><xref:System.Threading.Interlocked.Exchange%2A> Ve <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemlerine sahip türü bağımsız değişkenleri, aşırı yüklemeler <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="0660c-124">The <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods have overloads that take arguments of type <xref:System.Object>.</span></span> <span data-ttu-id="0660c-125">İlk bağımsız değişken her birinin bu aşırı yüklemeler `ref Object` (`ByRef … As Object` Visual Basic'te), ve tür güvenliği gerektirir, bu bağımsız değişken olarak kesin olarak belirlenmiş için geçirilen değişkeni <xref:System.Object>; yalnızca ilk bağımsız değişkenin türü atanamaz <xref:System.Object> Bu yöntemleri çağrılırken.</span><span class="sxs-lookup"><span data-stu-id="0660c-125">The first argument of each of these overloads is `ref Object` (`ByRef … As Object` in Visual Basic), and type safety requires the variable passed to this argument to be typed strictly as <xref:System.Object>; you cannot simply cast the first argument to type <xref:System.Object> when calling these methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0660c-126">.NET Framework sürüm 2.0 ve üzeri, genel aşırı yüklemelerini kullanın <xref:System.Threading.Interlocked.Exchange%2A> ve <xref:System.Threading.Interlocked.CompareExchange%2A> kesin alışverişi yöntemleri türdeki değişkenler.</span><span class="sxs-lookup"><span data-stu-id="0660c-126">In the .NET Framework version 2.0 and later, use the generic overloads of the <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods to exchange strongly typed variables.</span></span>  
  
 <span data-ttu-id="0660c-127">Aşağıdaki kod örneği vlastnost typu gösterir `ClassA` ayarlanabilecek yalnızca bir kez gibi .NET Framework sürüm 1.0 veya 1.1 uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="0660c-127">The following code example shows a property of type `ClassA` that can be set only once, as it might be implemented in the .NET Framework version 1.0 or 1.1.</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0660c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0660c-128">See also</span></span>

- <xref:System.Threading.Interlocked?displayProperty=nameWithType>  
- <xref:System.Threading.Monitor?displayProperty=nameWithType>  
- [<span data-ttu-id="0660c-129">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0660c-129">Threading</span></span>](index.md)  
- [<span data-ttu-id="0660c-130">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="0660c-130">Threading objects and features</span></span>](threading-objects-and-features.md)
