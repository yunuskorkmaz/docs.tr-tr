---
title: Paralel LINQ (PLINQ)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 94eeeda4666a4e6c1cb8729d6563ffcc4aa479c4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="b1874-102">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b1874-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="b1874-103">Paralel LINQ (PLINQ) nesnelere LINQ paralel bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="b1874-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="b1874-104">PLINQ için genişletme yöntemleri olarak LINQ standart sorgu işleçleri tam kümesi uygulayan <xref:System.Linq> ad alanı ve paralel işlemleri için ek işleçler sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b1874-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="b1874-105">PLINQ Basitlik ve LINQ sözdizimi okunabilirliğini paralel programlama güç ile birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b1874-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="b1874-106">Yalnızca kod gibi ana bilgisayar özelliklerine göre eşzamanlılık ölçüde PLINQ sorguları hedefleyen görev paralel kitaplığı ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="b1874-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="b1874-107">Birçok senaryoda PLINQ önemli ölçüde LINQ hızı nesneleri sorgular için tüm kullanılabilir çekirdekler ana bilgisayarda daha verimli bir şekilde kullanarak artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1874-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="b1874-108">Bu performans, yüksek performanslı bilgi işlem gücü Masaüstü üzerine getirir.</span><span class="sxs-lookup"><span data-stu-id="b1874-108">This increased performance brings high performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1874-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b1874-109">In This Section</span></span>  
 [<span data-ttu-id="b1874-110">PLINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="b1874-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="b1874-111">PLINQ'te Hızlandırmayı Anlama</span><span class="sxs-lookup"><span data-stu-id="b1874-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="b1874-112">PLINQ'te Sıra Koruma</span><span class="sxs-lookup"><span data-stu-id="b1874-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="b1874-113">PLINQ'te Birleştirme Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b1874-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="b1874-114">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="b1874-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="b1874-115">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="b1874-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="b1874-116">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="b1874-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="b1874-117">Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="b1874-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="b1874-118">Nasıl yapılır: PLINQ Sorgusunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="b1874-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="b1874-119">Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma</span><span class="sxs-lookup"><span data-stu-id="b1874-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="b1874-120">Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="b1874-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="b1874-121">Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="b1874-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="b1874-122">Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme</span><span class="sxs-lookup"><span data-stu-id="b1874-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="b1874-123">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="b1874-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="b1874-124">PLINQ Veri Örneği</span><span class="sxs-lookup"><span data-stu-id="b1874-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="b1874-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1874-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="b1874-126">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="b1874-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="b1874-127">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="b1874-127">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
