---
title: İş parçacığı (C#)
ms.date: 07/20/2015
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
ms.openlocfilehash: 35f0ee3bfd67104d9eaab7c4dde7e35a28a374c5
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934707"
---
# <a name="threading-c"></a>İş parçacığı (C#)
İş parçacığı aynı anda birden fazla işlemi yapabilir, böylece eş zamanlı işlem yapmak C# programınızı sağlar. Örneğin, kullanıcıdan girdi izleme, arka plan görevlerini gerçekleştirmek ve eşzamanlı giriş akışları işlemek için iş parçacığı kullanabilirsiniz.  
  
 İş parçacıkları, aşağıdaki özelliklere sahiptir:  
  
-   İş parçacıklarının eş zamanlı işlem gerçekleştirmek programınızı etkinleştirin.  
  
-   .NET Framework <xref:System.Threading> iş parçacığı daha kolay kullanarak ad alanı sağlar.  
  
-   İş parçacığı, uygulamanın kaynakları paylaşır. Daha fazla bilgi için [kullanarak iş parçacıkları ve parçacıkları](../../../../../docs/standard/threading/using-threads-and-threading.md).  
  
 Varsayılan olarak, bir iş parçacığı bir C# programı vardır. Ancak, ikincil iş parçacığı oluşturulabilir ve birincil iş parçacığı ile paralel kod yürütmek için kullanılır. Bu iş parçacıkları genellikle adlı *çalışan iş parçacıkları*.  
  
 Çalışan iş parçacıkları, birincil iş parçacığını bağlamadan zaman açısından kritik ya da zaman alıcı görevleri gerçekleştirmek için kullanılabilir. Örneğin, çalışan iş parçacığı önceki isteğin tamamlanması beklemenize gerek kalmadan, gelen istekleri karşılamak için genellikle sunucu uygulamalarında kullanılır. Çalışan iş parçacıkları aynı zamanda masaüstü uygulamalarında "arka plan" görevleri gerçekleştirmek için kullanılır, böylece kullanıcı arabirimi öğeleri--kalan kullanıcı eylemlerine duyarlı sürücüleri ana iş parçacığı--.  
  
 İş parçacığı oluşturma sorunları aktarım hızı ve yanıt hızını çözer, ancak Kilitlenmeler ve yarış koşulları gibi kaynak paylaşımını sorunlar çıkarabilir. Birden çok iş parçacığı, dosya tanıtıcıları ve ağ bağlantıları gibi farklı kaynakları gerektiren görevler için idealdir. Birden çok iş parçacığı için tek bir kaynak atama eşitleme sorunlarına neden olabilir ve diğer iş parçacıkları için beklenirken zaman sık engellenen iş parçacıkları sahip birden çok iş parçacığı kullanım amacını boşa çıkarır.  
  
 Ortak bir strateji, zaman alıcı gerçekleştirmek için çalışan iş parçacıkları veya diğer iş parçacıkları tarafından kullanılan kaynakları birçoğu gerektirmeyen zaman açısından kritik görevleri kullanmaktır. Doğal olarak, bazı kaynaklar programınızdaki birden çok iş parçacığı tarafından erişilmelidir. Bu gibi durumlarda için <xref:System.Threading> ad alanı, iş parçacıklarını eşitleme için sınıflar sağlar. Bu sınıfları <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.ManualResetEvent>.  
  
 Birden çok iş parçacığı etkinliklerini eşitlemek için bu sınıfların bazılarını veya tümünü kullanabilirsiniz, ancak bazı iş parçacığı oluşturma desteği C# dili tarafından desteklenir. Örneğin, [Lock deyiminin](../../../../csharp/language-reference/keywords/lock-statement.md) eşitleme özellikleri aracılığıyla örtük sağlar <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], çok iş parçacıklı programlama ile Basitleştirilmiş büyük ölçüde <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), yeni eşzamanlı koleksiyon sınıflarını içinde <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramını temel alarak yeni bir programlama modeli. Daha fazla bilgi için [paralel programlama](../../../../../docs/standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İş parçacığı eşitleme (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|İş parçacığı etkileşimler denetlemek nasıl açıklar.|  
|[İş parçacığı oluşturma](../../../../../docs/standard/threading/index.md)|.NET Framework'teki iş parçacığı uygulanacağını açıklar.|
