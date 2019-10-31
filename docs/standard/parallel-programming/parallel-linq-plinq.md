---
title: Paralel LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140044"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="f25a5-102">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f25a5-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="f25a5-103">Paralel LINQ (PLıNQ) LINQ to Objects paralel uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f25a5-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="f25a5-104">PLıNQ, <xref:System.Linq> ad alanı için uzantı yöntemleri olarak LINQ standart sorgu işleçlerinin tam kümesini uygular ve paralel işlemler için ek işleçlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f25a5-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="f25a5-105">PLıNQ, LINQ sözdiziminin basitliğini ve okunabilirliğini paralel programlama gücüyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f25a5-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="f25a5-106">Görev paralel kitaplığını hedefleyen kod gibi, PLıNQ sorguları, ana bilgisayarın özelliklerine göre eşzamanlılık derecesindeki ölçeği de ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="f25a5-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="f25a5-107">Birçok senaryoda PLıNQ, ana bilgisayardaki tüm kullanılabilir çekirdekleri daha verimli bir şekilde kullanarak LINQ to Objects sorgularının hızını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="f25a5-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="f25a5-108">Bu artış performansı, masaüstü üzerinde yüksek performanslı bilgi işlem gücü sağlar.</span><span class="sxs-lookup"><span data-stu-id="f25a5-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f25a5-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f25a5-109">In This Section</span></span>  
 [<span data-ttu-id="f25a5-110">PLINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="f25a5-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="f25a5-111">PLINQ'te Hızlandırmayı Anlama</span><span class="sxs-lookup"><span data-stu-id="f25a5-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="f25a5-112">PLINQ'te Sıra Koruma</span><span class="sxs-lookup"><span data-stu-id="f25a5-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="f25a5-113">PLINQ'te Birleştirme Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f25a5-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="f25a5-114">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="f25a5-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="f25a5-115">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="f25a5-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="f25a5-116">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="f25a5-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="f25a5-117">Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="f25a5-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="f25a5-118">Nasıl yapılır: PLINQ Sorgusunu İptal Etme</span><span class="sxs-lookup"><span data-stu-id="f25a5-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="f25a5-119">Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma</span><span class="sxs-lookup"><span data-stu-id="f25a5-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="f25a5-120">Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="f25a5-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="f25a5-121">Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="f25a5-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="f25a5-122">Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme</span><span class="sxs-lookup"><span data-stu-id="f25a5-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="f25a5-123">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="f25a5-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="f25a5-124">PLINQ Veri Örneği</span><span class="sxs-lookup"><span data-stu-id="f25a5-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="f25a5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f25a5-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="f25a5-126">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="f25a5-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="f25a5-127">Dil ile tümleşik sorgu (LINQ)-C#</span><span class="sxs-lookup"><span data-stu-id="f25a5-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="f25a5-128">Dil ile tümleşik sorgu (LINQ)-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f25a5-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
