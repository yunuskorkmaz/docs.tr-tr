---
title: İş parçacığı oluşturma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
ms.openlocfilehash: 6f7290b611d8314391d66397bd5f0f43928b8338
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651871"
---
# <a name="threading-visual-basic"></a>İş parçacığı oluşturma (Visual Basic)
İş parçacığı bir defada birden fazla işlem yapabilmesi için eşzamanlı işlem yapmak Visual Basic programınızı sağlar. Örneğin, kullanıcıdan girdi izlemek, arka plan görevleri ve eşzamanlı girdi akışları ile işlemek için iş parçacığı oluşturma kullanabilirsiniz.  
  
 İş parçacığı aşağıdaki özelliklere sahiptir:  
  
-   İş parçacığı eşzamanlı işlem gerçekleştirmek, program etkinleştirin.  
  
-   .NET Framework <xref:System.Threading> iş parçacığı daha kolay kullanarak ad alanı sağlar.  
  
-   İş parçacıkları uygulamanın kaynakları paylaşır. Daha fazla bilgi için bkz: [kullanarak iş parçacıkları ve parçacıkları](../../../../standard/threading/using-threads-and-threading.md).  
  
 Varsayılan olarak, bir Visual Basic programı bir iş parçacığı vardır. Ancak, yardımcı iş parçacığı oluşturulabilir ve birincil iş parçacığı ile paralel kod yürütmek için kullanılır. Bu iş parçacıkları adlandırılırlar *çalışan iş parçacığı*.  
  
 Çalışan iş parçacığı birincil iş parçacığını bağlamadan zaman veya zaman açısından kritik görevleri gerçekleştirmek için kullanılabilir. Örneğin, çalışan iş parçacığı tamamlanacak önceki isteği beklerken olmadan gelen istekleri karşılamak için genellikle sunucu uygulamalarında kullanılır. Çalışan iş parçacığı masaüstü uygulamalarında "arka plan" görevleri gerçekleştirmek için de kullanılır böylece kullanıcı arabirimi öğeleri--kullanıcı eylemlerine yanıt verebilir durumda kalır sürücüleri ana iş parçacığı--.  
  
 İş parçacığı oluşturma sorunları üretilen iş ve yanıt hızını çözer, ancak Kilitlenmeler ve yarış durumları gibi kaynak paylaşma sorunları getirebilir. Birden çok iş parçacığı dosya tanıtıcıları ve ağ bağlantıları gibi farklı kaynaklar gerektiren görevler için en iyisi. Tek kaynak için birden çok iş parçacığı atama eşitleme sorunlara neden olabilir ve sık için başka bir iş parçacığı beklenirken engellenmiş iş parçacıklarının sahip birden çok iş parçacığı kullanma uramayacak.  
  
 Uzun süren gerçekleştirmek için çalışan iş parçacığı veya diğer iş parçacıkları tarafından kullanılan kaynakları çoğunu gerektirmeyen zaman açısından kritik görevleri, ortak bir strateji kullanmaktır. Doğal olarak, bazı kaynaklar programınızdaki birden çok iş parçacığı tarafından erişilmesi gerekir. Bu durumlarda <xref:System.Threading> ad alanı, iş parçacıklarını eşitleme için sınıflar sağlar. Bu sınıfların dahil <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.ManualResetEvent>.  
  
 Birden çok iş parçacığı etkinliklerini eşitlemek için bu sınıfların bazıları veya tümü kullanabilirsiniz, ancak bazı iş parçacığı oluşturma desteği Visual Basic dili tarafından desteklenir. Örneğin, [SyncLock deyimi](../../../../visual-basic/language-reference/statements/synclock-statement.md) örtülü kullanımı aracılığıyla eşitleme özellikleri sağlayan <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], birden çok iş parçacıklı programlama ile Basitleştirilmiş büyük ölçüde <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), yeni eşzamanlı koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramı dayalı yeni bir programlama modeli. Daha fazla bilgi için bkz: [paralel programlama](../../../../standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Birden çok iş parçacıklı uygulamalar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)|Oluşturma ve iş parçacığı kullanma açıklar.|  
|[Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Geçirmek ve birden çok iş parçacıklı uygulamalar parametrelerle dönmek açıklar.|  
|[İzlenecek yol: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Basit bir birden çok iş parçacıklı uygulamasının nasıl oluşturulacağını gösterir.|  
|[İş parçacığı eşitleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)|İş parçacığı etkileşimleri denetlemek açıklar.|  
|[İş parçacığı zamanlayıcılar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)|Ayrı iş parçacıklarına sabit aralıklarda yordamları çalıştırmak açıklar.|  
|[İş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)|Sistem tarafından yönetilen çalışan iş parçacığı havuzu kullanmayı açıklar.|  
|[Nasıl yapılır: iş parçacığı havuzu (Visual Basic) kullanma](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|İş parçacığı havuzu birden çok iş parçacığı eşitlenmiş kullanımını göstermektedir.|  
|[İş parçacığı oluşturma](../../../../standard/threading/index.md)|.NET Framework iş parçacığı oluşturma uygulamak açıklar.|
