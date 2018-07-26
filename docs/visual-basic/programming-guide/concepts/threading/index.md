---
title: İş parçacığı (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
ms.openlocfilehash: fd1530a2b03c01b0a1cba0ce3ed4e18f2bf29046
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874839"
---
# <a name="threading-visual-basic"></a>İş parçacığı (Visual Basic)
İş parçacığı aynı anda birden fazla işlemi yapabilir, böylece eş zamanlı işlem yapmak, Visual Basic programını sağlar. Örneğin, kullanıcıdan girdi izleme, arka plan görevlerini gerçekleştirmek ve eşzamanlı giriş akışları işlemek için iş parçacığı kullanabilirsiniz.  
  
 İş parçacıkları, aşağıdaki özelliklere sahiptir:  
  
-   İş parçacıklarının eş zamanlı işlem gerçekleştirmek programınızı etkinleştirin.  
  
-   .NET Framework <xref:System.Threading> iş parçacığı daha kolay kullanarak ad alanı sağlar.  
  
-   İş parçacığı, uygulamanın kaynakları paylaşır. Daha fazla bilgi için [kullanarak iş parçacıkları ve parçacıkları](../../../../standard/threading/using-threads-and-threading.md).  
  
 Varsayılan olarak, bir Visual Basic programını tek bir iş parçacığı vardır. Ancak, ikincil iş parçacığı oluşturulabilir ve birincil iş parçacığı ile paralel kod yürütmek için kullanılır. Bu iş parçacıkları genellikle adlı *çalışan iş parçacıkları*.  
  
 Çalışan iş parçacıkları, birincil iş parçacığını bağlamadan zaman açısından kritik ya da zaman alıcı görevleri gerçekleştirmek için kullanılabilir. Örneğin, çalışan iş parçacığı önceki isteğin tamamlanması beklemenize gerek kalmadan, gelen istekleri karşılamak için genellikle sunucu uygulamalarında kullanılır. Çalışan iş parçacıkları aynı zamanda masaüstü uygulamalarında "arka plan" görevleri gerçekleştirmek için kullanılır, böylece kullanıcı arabirimi öğeleri--kalan kullanıcı eylemlerine duyarlı sürücüleri ana iş parçacığı--.  
  
 İş parçacığı oluşturma sorunları aktarım hızı ve yanıt hızını çözer, ancak Kilitlenmeler ve yarış koşulları gibi kaynak paylaşımını sorunlar çıkarabilir. Birden çok iş parçacığı, dosya tanıtıcıları ve ağ bağlantıları gibi farklı kaynakları gerektiren görevler için idealdir. Birden çok iş parçacığı için tek bir kaynak atama eşitleme sorunlarına neden olabilir ve diğer iş parçacıkları için beklenirken zaman sık engellenen iş parçacıkları sahip birden çok iş parçacığı kullanım amacını boşa çıkarır.  
  
 Ortak bir strateji, zaman alıcı gerçekleştirmek için çalışan iş parçacıkları veya diğer iş parçacıkları tarafından kullanılan kaynakları birçoğu gerektirmeyen zaman açısından kritik görevleri kullanmaktır. Doğal olarak, bazı kaynaklar programınızdaki birden çok iş parçacığı tarafından erişilmelidir. Bu gibi durumlarda için <xref:System.Threading> ad alanı, iş parçacıklarını eşitleme için sınıflar sağlar. Bu sınıfları <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.ManualResetEvent>.  
  
 Birden çok iş parçacığı etkinliklerini eşitlemek için bu sınıfların bazılarını veya tümünü kullanabilirsiniz, ancak bazı iş parçacığı oluşturma desteği Visual Basic dili tarafından desteklenir. Örneğin, [SyncLock deyimi](../../../../visual-basic/language-reference/statements/synclock-statement.md) eşitleme özellikleri aracılığıyla örtük sağlar <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], çok iş parçacıklı programlama ile Basitleştirilmiş büyük ölçüde <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), yeni eşzamanlı koleksiyon sınıflarını içinde <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramını temel alarak yeni bir programlama modeli. Daha fazla bilgi için [paralel programlama](../../../../standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Çok iş parçacıklı uygulamalar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)|İş parçacıkları oluşturup kullanacağınızı açıklar.|  
|[Parametreler ve dönüş değerleri için birden çok iş parçacıklı yordamlar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Başarılı ve çok iş parçacıklı uygulamalar parametrelerle döndürmek açıklar.|  
|[İzlenecek yol: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Basit bir çok iş parçacıklı uygulamanın nasıl oluşturulacağını gösterir.|  
|[İş parçacığı eşitleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)|İş parçacığı etkileşimler denetlemek nasıl açıklar.|  
|[İş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)|Sistem tarafından yönetilen çalışan iş parçacığı havuzu kullanmayı açıklar.|  
|[Nasıl yapılır: iş parçacığı havuzu (Visual Basic) kullanma](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Eşzamanlı iş parçacığı havuzundaki birden çok iş parçacığı kullanımını gösterir.|  
|[İş parçacığı oluşturma](../../../../standard/threading/index.md)|.NET Framework'teki iş parçacığı uygulanacağını açıklar.|
