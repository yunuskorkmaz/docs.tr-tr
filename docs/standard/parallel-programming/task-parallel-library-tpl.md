---
title: Görev Paralel Kitaplığı (TPL)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
ms.openlocfilehash: 45c9f43e67b66b00758afa0659897971aef317c2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284981"
---
# <a name="task-parallel-library-tpl"></a>Görev Paralel Kitaplığı (TPL)
Görev paralel kitaplığı (TPL), ve ad alanlarındaki genel türler ve API 'Ler kümesidir <xref:System.Threading?displayProperty=nameWithType> <xref:System.Threading.Tasks?displayProperty=nameWithType> . TPL'nin amacı, uygulamalara paralellik ve eşzamanlılık ekleme işlemini kolaylaştırarak geliştiricilerin daha üretken olmasını sağlamaktır. TPL, kullanılabilen tüm işlemcilerin en verimli şekilde kullanılması için eşzamanlılık derecesini dinamik olarak ölçeklendirir. Ayrıca, TPL, işin bölümlenmesini, iş parçacıklarının zamanlamasını, <xref:System.Threading.ThreadPool> iptal desteğini, durum yönetimini ve diğer alt düzey ayrıntıları işler. TPL'yi kullanarak, bir yandan programınızın gerçekleştirmek üzere tasarlandığı çalışmaya odaklanırken, diğer yandan kodunuzun performansını en üst düzeye çıkarabilirsiniz.  
  
 .NET Framework 4 ' te başlayarak, TPL çok iş parçacıklı ve paralel kod yazmak için tercih edilen yoldur. Ancak, bazı kodlar paralelleştirme için uygun değildir; örneğin, bir döngü her yinelemede yalnızca az miktarda iş gerçekleştiriyorsa veya birçok yineleme için çalışmıyorsa, paralelleştirme yükü kodun daha yavaş çalışmasına neden olabilir. Ayrıca, herhangi bir çok iş parçacıklı kod gibi paralelleştirme, program yürütmenize karmaşıklık ekler. TPL, çok iş parçacıklı senaryoları kolaylaştırsa da, TPL'yi etkin şekilde kullanabilmeniz için kilitler, kilitlenmeler ve yarış koşulları gibi iş parçacığı oluşturma kavramlarına ilişkin temel bilgileri öğrenmenizi öneririz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-|-|  
|[Veri paralelliği](data-parallelism-task-parallel-library.md)|Paralel `for` ve `foreach` döngülerin ( `For` ve `For Each` Visual Basic) nasıl oluşturulacağını açıklar.|  
|[Görev tabanlı zaman uyumsuz programlama](task-based-asynchronous-programming.md)|<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>Nesneleri doğrudan kullanarak veya kullanarak açıkça kullanılarak görevlerin nasıl oluşturulduğunu ve çalıştırılacağını açıklar <xref:System.Threading.Tasks.Task> .|  
|[Veri akışı](dataflow-task-parallel-library.md)|TPL Veri Akışı Kitaplığındaki veri akışı bileşenlerinin, birbirleriyle iletişim kurması gereken birden çok işlemi çalıştırmak veya kullanılabilir olduğunda verileri işlemek için nasıl kullanılacağını açıklar.|  
|[Diğer Zaman Uyumsuz Desenlerle TPL Kullanma](using-tpl-with-other-asynchronous-patterns.md)|.NET'te diğer zaman uyumsuz düzenlerle TPL'nin nasıl kullanılacağını açıklar|  
|[Veri ve Görev Paralelliğinde Olası Tuzaklar](potential-pitfalls-in-data-and-task-parallelism.md)|Bazı yaygın görülen tehlikeleri ve bunların nasıl önleneceğini açıklar.|  
|[Paralel LINQ (PLINQ)](introduction-to-plinq.md)|LINQ sorguları ile veri paralelliğinin nasıl elde edileceğini açıklar.|  
|[Paralel programlama](index.md)|.NET paralel programlama için üst düzey düğüm.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core & paralel programlama örnekleri .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
