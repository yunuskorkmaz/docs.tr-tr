---
title: "İş parçacığı (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 661208662c022b2a3b9c5daae6b0425e46ea6501
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="threading-c"></a>İş parçacığı (C#)
İş parçacığı bir defada birden fazla işlem yapabilmesi için eşzamanlı işlem yapmak, C# programı sağlar. Örneğin, kullanıcıdan girdi izlemek, arka plan görevleri ve eşzamanlı girdi akışları ile işlemek için iş parçacığı oluşturma kullanabilirsiniz.  
  
 İş parçacığı aşağıdaki özelliklere sahiptir:  
  
-   İş parçacığı eşzamanlı işlem gerçekleştirmek, program etkinleştirin.  
  
-   .NET Framework <xref:System.Threading> iş parçacığı daha kolay kullanarak ad alanı sağlar.  
  
-   İş parçacıkları uygulamanın kaynakları paylaşır. Daha fazla bilgi için bkz: [kullanarak iş parçacıkları ve parçacıkları](../../../../../docs/standard/threading/using-threads-and-threading.md).  
  
 Varsayılan olarak, bir C# programı bir iş parçacığı vardır. Ancak, yardımcı iş parçacığı oluşturulabilir ve birincil iş parçacığı ile paralel kod yürütmek için kullanılır. Bu iş parçacıkları adlandırılırlar *çalışan iş parçacığı*.  
  
 Çalışan iş parçacığı birincil iş parçacığını bağlamadan zaman veya zaman açısından kritik görevleri gerçekleştirmek için kullanılabilir. Örneğin, çalışan iş parçacığı tamamlanacak önceki isteği beklerken olmadan gelen istekleri karşılamak için genellikle sunucu uygulamalarında kullanılır. Çalışan iş parçacığı masaüstü uygulamalarında "arka plan" görevleri gerçekleştirmek için de kullanılır böylece kullanıcı arabirimi öğeleri--kullanıcı eylemlerine yanıt verebilir durumda kalır sürücüleri ana iş parçacığı--.  
  
 İş parçacığı oluşturma sorunları üretilen iş ve yanıt hızını çözer, ancak Kilitlenmeler ve yarış durumları gibi kaynak paylaşma sorunları getirebilir. Birden çok iş parçacığı dosya tanıtıcıları ve ağ bağlantıları gibi farklı kaynaklar gerektiren görevler için en iyisi. Tek kaynak için birden çok iş parçacığı atama eşitleme sorunlara neden olabilir ve sık için başka bir iş parçacığı beklenirken engellenmiş iş parçacıklarının sahip birden çok iş parçacığı kullanma uramayacak.  
  
 Uzun süren gerçekleştirmek için çalışan iş parçacığı veya diğer iş parçacıkları tarafından kullanılan kaynakları çoğunu gerektirmeyen zaman açısından kritik görevleri, ortak bir strateji kullanmaktır. Doğal olarak, bazı kaynaklar programınızdaki birden çok iş parçacığı tarafından erişilmesi gerekir. Bu durumlarda <xref:System.Threading> ad alanı, iş parçacıklarını eşitleme için sınıflar sağlar. Bu sınıfların dahil <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.ManualResetEvent>.  
  
 Birden çok iş parçacığı etkinliklerini eşitlemek için bu sınıfların bazıları veya tümü kullanabilirsiniz, ancak bazı iş parçacığı oluşturma desteği C# dili tarafından desteklenir. Örneğin, [Lock deyimi](../../../../csharp/language-reference/keywords/lock-statement.md) örtülü kullanımı aracılığıyla eşitleme özellikleri sağlayan <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], birden çok iş parçacıklı programlama ile Basitleştirilmiş büyük ölçüde <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), yeni eşzamanlı koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramı dayalı yeni bir programlama modeli. Daha fazla bilgi için bkz: [paralel programlama](../../../../../docs/standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Birden çok iş parçacıklı uygulamalar (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|Oluşturma ve iş parçacığı kullanma açıklar.|  
|[Parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Geçirmek ve birden çok iş parçacıklı uygulamalar parametrelerle dönmek açıklar.|  
|[İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Basit bir birden çok iş parçacıklı uygulamasının nasıl oluşturulacağını gösterir.|  
|[İş parçacığı eşitleme (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|İş parçacığı etkileşimleri denetlemek açıklar.|  
|[İş parçacığı zamanlayıcılar (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|Ayrı iş parçacıklarına sabit aralıklarda yordamları çalıştırmak açıklar.|  
|[İş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|Sistem tarafından yönetilen çalışan iş parçacığı havuzu kullanmayı açıklar.|  
|[Nasıl yapılır: iş parçacığı havuzu (C#) kullanma](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|İş parçacığı havuzu birden çok iş parçacığı eşitlenmiş kullanımını göstermektedir.|  
|[İş parçacığı oluşturma](../../../../../docs/standard/threading/index.md)|.NET Framework iş parçacığı oluşturma uygulamak açıklar.|
