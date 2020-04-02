---
title: Görev Paralel Kitaplığı (TPL)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 6785041730a048fb08677dbd054f727e351185d4
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588585"
---
# <a name="task-parallel-library-tpl"></a>Görev Paralel Kitaplığı (TPL)
Görev Paralel Kitaplığı (TPL), ortak türler ve API'ler kümesidir. <xref:System.Threading?displayProperty=nameWithType> <xref:System.Threading.Tasks?displayProperty=nameWithType> TPL'nin amacı, uygulamalara paralellik ve eşzamanlılık ekleme işlemini kolaylaştırarak geliştiricilerin daha üretken olmasını sağlamaktır. TPL, kullanılabilen tüm işlemcilerin en verimli şekilde kullanılması için eşzamanlılık derecesini dinamik olarak ölçeklendirir. Buna ek olarak, TPL işin bölümleme, <xref:System.Threading.ThreadPool>iptal desteği, devlet yönetimi ve diğer alt düzey ayrıntıları işleyerek işlenir. TPL'yi kullanarak, bir yandan programınızın gerçekleştirmek üzere tasarlandığı çalışmaya odaklanırken, diğer yandan kodunuzun performansını en üst düzeye çıkarabilirsiniz.  
  
 .NET Framework 4 ile başlayarak, TPL çok iş parçacığı ve paralel kod yazmak için tercih edilen yoldur. Ancak, bazı kodlar paralelleştirme için uygun değildir; örneğin, bir döngü her yinelemede yalnızca az miktarda iş gerçekleştiriyorsa veya birçok yineleme için çalışmıyorsa, paralelleştirme yükü kodun daha yavaş çalışmasına neden olabilir. Ayrıca, herhangi bir çok iş parçacıklı kod gibi paralelleştirme, program yürütmenize karmaşıklık ekler. TPL, çok iş parçacıklı senaryoları kolaylaştırsa da, TPL'yi etkin şekilde kullanabilmeniz için kilitler, kilitlenmeler ve yarış koşulları gibi iş parçacığı oluşturma kavramlarına ilişkin temel bilgileri öğrenmenizi öneririz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-|-|  
|[Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Paralel `for` ve `foreach` döngülerin nasıl`For` oluşturulup oluşturulabildiğini açıklar (ve `For Each` Visual Basic'te).|  
|[Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|Nesneleri doğrudan kullanarak <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task> veya açıkça kullanarak görevleri dolaylı olarak nasıl oluşturup çalıştırılacak açıklanır.|  
|[Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|TPL Veri Akışı Kitaplığındaki veri akışı bileşenlerinin, birbirleriyle iletişim kurması gereken birden çok işlemi çalıştırmak veya kullanılabilir olduğunda verileri işlemek için nasıl kullanılacağını açıklar.|  
|[Diğer Zaman Uyumsuz Desenlerle TPL Kullanma](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|.NET'te diğer zaman uyumsuz düzenlerle TPL'nin nasıl kullanılacağını açıklar|  
|[Veri ve Görev Paralelliğinde Olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|Bazı yaygın görülen tehlikeleri ve bunların nasıl önleneceğini açıklar.|  
|[Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)|LINQ sorguları ile veri paralelliğinin nasıl elde edileceğini açıklar.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET paralel programlama için üst düzey düğüm.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ile Paralel Programlama Örnekleri](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
