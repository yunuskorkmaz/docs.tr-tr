---
title: Paralel LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c438170ec48f40e59f8710d4e3820d6e915bed5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666280"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="52b01-102">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="52b01-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="52b01-103">Paralel LINQ (PLINQ) bir paralel LINQ to Objects'in uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="52b01-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="52b01-104">PLINQ için genişletme yöntemleri olarak LINQ standart sorgu işleçlerinin tam kümesini uygular <xref:System.Linq> ad alanı ve paralel işlemler için ek işleçler.</span><span class="sxs-lookup"><span data-stu-id="52b01-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="52b01-105">PLINQ'nun paralel programlama gücüyle basitliği ve LINQ söz dizimi okunabilirliğini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="52b01-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="52b01-106">Kod gibi ana bilgisayar becerilerine dayalı eşzamanlılık derecesini, PLINQ sorguları hedefleyen görev paralel kitaplığı ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="52b01-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="52b01-107">Birçok senaryoda PLINQ önemli ölçüde LINQ hızına Plınq sorgularının tüm mevcut çekirdekler ana bilgisayarda daha verimli bir şekilde kullanarak artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52b01-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="52b01-108">Bu performans artışı masaüstüne yüksek performanslı bilgi işlem gücü getirir.</span><span class="sxs-lookup"><span data-stu-id="52b01-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52b01-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="52b01-109">In This Section</span></span>  
 [<span data-ttu-id="52b01-110">PLINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="52b01-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="52b01-111">PLINQ'te Hızlandırmayı Anlama</span><span class="sxs-lookup"><span data-stu-id="52b01-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="52b01-112">PLINQ'te Sıra Koruma</span><span class="sxs-lookup"><span data-stu-id="52b01-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="52b01-113">PLINQ'te Birleştirme Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="52b01-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="52b01-114">Nasıl yapılır: Basit bir PLINQ sorgusu oluşturma ve yürütme</span><span class="sxs-lookup"><span data-stu-id="52b01-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="52b01-115">Nasıl yapılır: PLINQ sorgusunda sıralama denetimi</span><span class="sxs-lookup"><span data-stu-id="52b01-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="52b01-116">Nasıl yapılır: Paralel ve sıralı LINQ sorgularını birleştirme</span><span class="sxs-lookup"><span data-stu-id="52b01-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="52b01-117">Nasıl yapılır: PLINQ sorgusunda özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="52b01-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="52b01-118">Nasıl yapılır: PLINQ sorgusunu iptal etme</span><span class="sxs-lookup"><span data-stu-id="52b01-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="52b01-119">Nasıl yapılır: Özel bir PLINQ toplama işlevi yazma</span><span class="sxs-lookup"><span data-stu-id="52b01-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="52b01-120">Nasıl yapılır: PLINQ'te yürütme modunu belirtme</span><span class="sxs-lookup"><span data-stu-id="52b01-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="52b01-121">Nasıl yapılır: PLINQ'te birleştirme seçeneklerini belirtme</span><span class="sxs-lookup"><span data-stu-id="52b01-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="52b01-122">Nasıl yapılır: PLINQ ile dosya dizinlerini yineleme</span><span class="sxs-lookup"><span data-stu-id="52b01-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="52b01-123">Nasıl yapılır: Ölçü PLINQ sorgu performansını</span><span class="sxs-lookup"><span data-stu-id="52b01-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="52b01-124">PLINQ Veri Örneği</span><span class="sxs-lookup"><span data-stu-id="52b01-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="52b01-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52b01-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="52b01-126">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="52b01-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="52b01-127">Dil ile tümleşik sorgu (LINQ)-C#</span><span class="sxs-lookup"><span data-stu-id="52b01-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="52b01-128">Dil ile tümleşik sorgu (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52b01-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
