---
title: "Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a><span data-ttu-id="bfcae-102">Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme</span><span class="sxs-lookup"><span data-stu-id="bfcae-102">How to: Iterate File Directories with PLINQ</span></span>
<span data-ttu-id="bfcae-103">Bu örnek, dosya dizinleri işlemleri paralel hale iki basit yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfcae-103">This example shows two simple ways to parallelize operations on file directories.</span></span> <span data-ttu-id="bfcae-104">İlk sorguyu kullanan <xref:System.IO.Directory.GetFiles%2A> bir dizinde ve tüm alt dizinler dosya adlarının dizisini doldurmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="bfcae-104">The first query uses the <xref:System.IO.Directory.GetFiles%2A> method to populate an array of file names in a directory and all subdirectories.</span></span> <span data-ttu-id="bfcae-105">Bu yöntem, tüm diziyi doldurulur ve bu nedenle işlemin başında gecikme getirebilir kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="bfcae-105">This method does not return until the entire array is populated, and therefore it can introduce latency at the beginning of the operation.</span></span> <span data-ttu-id="bfcae-106">Dizi doldurulduktan sonra ancak PLINQ, paralel olarak çok hızlı bir şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bfcae-106">However, after the array is populated, PLINQ can process it in parallel very quickly.</span></span>  
  
 <span data-ttu-id="bfcae-107">İkinci sorguyu statik kullanan <xref:System.IO.Directory.EnumerateDirectories%2A> ve <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> sonuçları hemen döndürülmesini yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bfcae-107">The second query uses the static <xref:System.IO.Directory.EnumerateDirectories%2A> and <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> methods which begin returning results immediately.</span></span> <span data-ttu-id="bfcae-108">Büyük directory ağaçlarında dolaşırken ilk örneği işleme süresinde birçok faktöre bağlıdır rağmen bu yaklaşım daha hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bfcae-108">This approach can be faster when you are iterating over large directory trees, although the processing time compared to the first example can depend on many factors.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bfcae-109">Bu örnekler kullanım göstermek için tasarlanmıştır ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="bfcae-109">These examples are intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="bfcae-110">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="bfcae-110">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfcae-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfcae-111">Example</span></span>  
 <span data-ttu-id="bfcae-112">Aşağıdaki örnek, tüm dizinler ağacında erişimi, dosya boyutları çok büyük olmayan ve erişim zamanları önemli olmadıkları zaman dosya dizinleri basit senaryolarda üzerinden yineleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfcae-112">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="bfcae-113">Dosya adları dizisi oluşturulan sırada bu yaklaşım gecikme başında nokta içerir.</span><span class="sxs-lookup"><span data-stu-id="bfcae-113">This approach involves a period of latency at the beginning while the array of file names is being constructed.</span></span>  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a><span data-ttu-id="bfcae-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfcae-114">Example</span></span>  
 <span data-ttu-id="bfcae-115">Aşağıdaki örnek, tüm dizinler ağacında erişimi, dosya boyutları çok büyük olmayan ve erişim zamanları önemli olmadıkları zaman dosya dizinleri basit senaryolarda üzerinden yineleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfcae-115">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="bfcae-116">Bu yaklaşım, önceki örnekte daha hızlı sonuçlar üretir başlar.</span><span class="sxs-lookup"><span data-stu-id="bfcae-116">This approach begins producing results faster than the previous example.</span></span>  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 <span data-ttu-id="bfcae-117">Kullanırken <xref:System.IO.Directory.GetFiles%2A>, ağacında tüm dizinlerde yeterli izinlere sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bfcae-117">When using <xref:System.IO.Directory.GetFiles%2A>, be sure that you have sufficient permissions on all directories in the tree.</span></span> <span data-ttu-id="bfcae-118">Aksi takdirde bir özel durum ve hiç sonuç döndürmedi.</span><span class="sxs-lookup"><span data-stu-id="bfcae-118">Otherwise an exception will be thrown and no results will be returned.</span></span> <span data-ttu-id="bfcae-119">Kullanırken <xref:System.IO.Directory.EnumerateDirectories%2A> bir PLINQ sorgusunda yineleme devam etmenizi sağlayan normal şekilde g/ç özel durumları işleme sorunlu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bfcae-119">When using the <xref:System.IO.Directory.EnumerateDirectories%2A> in a PLINQ query, it is problematic to handle I/O exceptions in a graceful way that enables you to continue iterating.</span></span> <span data-ttu-id="bfcae-120">Kodunuzu g/ç veya yetkisiz erişim özel durumlarını işlemelidir sonra açıklanan yaklaşımı düşünmelisiniz [nasıl yapılır: paralel sınıfla dosya dizinlerini yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).</span><span class="sxs-lookup"><span data-stu-id="bfcae-120">If your code must handle I/O or unauthorized access exceptions, then you should consider the approach described in [How to: Iterate File Directories with the Parallel Class](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).</span></span>  
  
 <span data-ttu-id="bfcae-121">G/ç gecikmesi bir sorun ise, örneğin bir ağ üzerinden dosya g/ç ile açıklanan zaman uyumsuz g/ç teknikleri birini kullanmayı [TPL ve geleneksel .NET Framework zaman uyumsuz Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) ve bu [blog gönderisi ](http://go.microsoft.com/fwlink/?LinkID=186458).</span><span class="sxs-lookup"><span data-stu-id="bfcae-121">If I/O latency is an issue, for example with file I/O over a network, consider using one of the asynchronous I/O techniques described in [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) and in this [blog post](http://go.microsoft.com/fwlink/?LinkID=186458).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfcae-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfcae-122">See Also</span></span>  
 [<span data-ttu-id="bfcae-123">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="bfcae-123">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
