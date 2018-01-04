---
title: "Görev Paralel Kitaplığı (TPL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
caps.latest.revision: "37"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2a124d355b4480aebff3c40e2ccece618e1979f6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="task-parallel-library-tpl"></a>Görev Paralel Kitaplığı (TPL)
Görev paralel kitaplığı (TPL) genel türler ve API'leri kümesidir <xref:System.Threading?displayProperty=nameWithType> ve <xref:System.Threading.Tasks?displayProperty=nameWithType> ad alanları. TPL'nin amacı, uygulamalara paralellik ve eşzamanlılık ekleme işlemini kolaylaştırarak geliştiricilerin daha üretken olmasını sağlamaktır. TPL, kullanılabilen tüm işlemcilerin en verimli şekilde kullanılması için eşzamanlılık derecesini dinamik olarak ölçeklendirir. Ayrıca, TPL üzerinde iş parçacıklarının zamanlama çalışmanın Bölümlendirmeyi işleyen <xref:System.Threading.ThreadPool>, iptal desteği, durum yönetimi ve diğer alt düzey ayrıntıları. TPL'yi kullanarak, bir yandan programınızın gerçekleştirmek üzere tasarlandığı çalışmaya odaklanırken, diğer yandan kodunuzun performansını en üst düzeye çıkarabilirsiniz.  
  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], TPL birden çok iş parçacıklı ve paralel kod yazmayı tercih edilen yöntemdir. Ancak, bazı kodlar paralelleştirme için uygun değildir; örneğin, bir döngü her yinelemede yalnızca az miktarda iş gerçekleştiriyorsa veya birçok yineleme için çalışmıyorsa, paralelleştirme yükü kodun daha yavaş çalışmasına neden olabilir. Ayrıca, herhangi bir çok iş parçacıklı kod gibi paralelleştirme, program yürütmenize karmaşıklık ekler. TPL, çok iş parçacıklı senaryoları kolaylaştırsa da, TPL'yi etkin şekilde kullanabilmeniz için kilitler, kilitlenmeler ve yarış koşulları gibi iş parçacığı oluşturma kavramlarına ilişkin temel bilgileri öğrenmenizi öneririz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-|-|  
|[Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Paralel oluşturmayı açıklar `for` ve `foreach` döngüleri (`For` ve `For Each` Visual Basic'te).|  
|[Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Oluşturma ve örtük olarak kullanarak çalışan görevler açıklar <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> veya kullanarak açıkça <xref:System.Threading.Tasks.Task> nesnelerini doğrudan.|  
|[Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|TPL Veri Akışı Kitaplığındaki veri akışı bileşenlerinin, birbirleriyle iletişim kurması gereken birden çok işlemi çalıştırmak veya kullanılabilir olduğunda verileri işlemek için nasıl kullanılacağını açıklar.|  
|[Diğer Zaman Uyumsuz Desenlerle TPL Kullanma](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|.NET'te diğer zaman uyumsuz düzenlerle TPL'nin nasıl kullanılacağını açıklar|  
|[Veri ve Görev Paralelliğinde Olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Bazı yaygın görülen tehlikeleri ve bunların nasıl önleneceğini açıklar.|  
|[Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|LINQ sorguları ile veri paralelliğinin nasıl elde edileceğini açıklar.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET paralel programlama için üst düzey düğüm.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework ile paralel programlama için örnek](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
