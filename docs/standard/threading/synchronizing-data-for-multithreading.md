---
title: "Çoklu İş Parçacığı Kullanımı için Veri Eşitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17eba2f930fda06d643d78c73c117e89ae86928
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="synchronizing-data-for-multithreading"></a>Çoklu İş Parçacığı Kullanımı için Veri Eşitleme
Birden çok iş parçacığı özellikleri ve yöntemleri tek bir nesnenin çağrıları yaptığınızda bu çağrıları eşitlenmiş önemlidir. Aksi halde bir iş parçacığı başka bir iş parçacığı yaptıklarını yarıda kesebilecek ve Nesne geçersiz bir durumda kalabilir. Üyeleri böyle kesintilerden korunan bir sınıf, iş parçacığı denir.  
  
 Ortak dil altyapısı örneği ve statik üyeler erişimi eşitlemek için birkaç stratejileri sağlar:  
  
-   Eşitlenen kod bölgeleri. Kullanabileceğiniz <xref:System.Threading.Monitor> sınıfı veya derleyici desteği kodu engelleyecek yalnızca eşitlemek Bu sınıf için gereken, performansı artırma.  
  
-   El ile eşitleme. .NET Framework sınıf kitaplığı tarafından sağlanan eşitleme nesneleri kullanabilirsiniz. Bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md), tartışması içeren <xref:System.Threading.Monitor> sınıfı.  
  
-   Eşitleme bağlamı. Kullanabileceğiniz <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> için basit, Otomatik eşitlemeyi etkinleştirmek için <xref:System.ContextBoundObject> nesneleri.  
  
-   Koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı. Bu sınıfların sağlamak eşitlenen yerleşik ekleme ve kaldırma işlemleri. Daha fazla bilgi için bkz: [iş parçacığı koleksiyonları](../../../docs/standard/collections/thread-safe/index.md).  
  
 Ortak dil çalışma zamanı sınıfları çeşitli gereksinimlerine bağlı olarak farklı şekillerde eşitlenen kategori sayısı içine düşen bir iş parçacığı modeli sağlar. Aşağıdaki tabloda, hangi eşitleme destek alanları ve verilen eşitleme kategorisiyle yöntemleri için sağlanan gösterir.  
  
|Kategori|Genel alanlar|Statik alanları|Statik yöntemler|Örnek alanı|Örnek yöntemleri|Özel kod blokları|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Hiçbir eşitleme|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|  
|Eşitlenen bağlamı|Hayır|Hayır|Hayır|Evet|Evet|Hayır|  
|Eşitlenen kod bölgeleri|Hayır|Hayır|Sadece işaretliyse|Hayır|Sadece işaretliyse|Sadece işaretliyse|  
|El ile eşitleme|El ile|El ile|El ile|El ile|El ile|El ile|  
  
## <a name="no-synchronization"></a>Hiçbir eşitleme  
 Bu nesneler için varsayılan değerdir. Hiçbir iş parçacığı herhangi bir yöntemi veya alan herhangi bir zamanda erişebilir. Bir seferde yalnızca bir iş parçacığı bu nesnelere erişen.  
  
## <a name="manual-synchronization"></a>El ile eşitleme  
 .NET Framework sınıf kitaplığı iş parçacıklarını eşitleme için bir dizi sınıfları sağlar. Bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Eşitlenen kod bölgeleri  
 Kullanabileceğiniz <xref:System.Threading.Monitor> sınıfı ya da kod, örnek yöntemleri ve statik yöntemler bloklarını eşitlemek için bir derleyici anahtar sözcük. Eşitlenen statik alanları için desteği yoktur.  
  
 Hem Visual Basic ve C# dil anahtar sözcüğü ile kod bloklarını işaretleme desteği `lock` deyimi C# veya `SyncLock` Visual Basic'de deyimini. Kod bir iş parçacığı tarafından çalıştırıldığında girişiminde kilidi için yapılır. Kilidi başka bir iş parçacığı tarafından kilit kullanılabilir oluncaya kadar iş parçacığı blokları edinilen durumunda. İş parçacığı eşitlenmiş kod bloğunu çıktığında, iş parçacığı blok çıkar ne olursa olsun kilidi yayımlanır.  
  
> [!NOTE]
>  `lock` Ve `SyncLock` deyimleri kullanarak uygulanır <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, bu nedenle diğer yöntemlerini <xref:System.Threading.Monitor> eşitlenmiş bölgedeki bunları ile birlikte kullanılabilir.  
  
 Bir yöntemle tasarlamanız bir **MethodImplAttribute** ve **MethodImplOptions.Synchronized**, kullanarak aynı etkiye sahip **İzleyici** veya derleyici yöntemin tüm gövdesi kilitlemek için anahtar sözcükler.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>Eşitlenen bölge kodu erişimi için beklenirken gibi engelleme işlemleri dışında bir iş parçacığı ayırmak için kullanılabilir. **Thread.Interrupt** ayrıca iş parçacıkları gibi işlemleri dışında ayırmak için kullanılan <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Türü kilitlemeyin — diğer bir deyişle, `typeof(MyType)` C# ' ta, `GetType(MyType)` Visual Basic'te veya `MyType::typeid` c++ — korumak için `static` yöntemleri (`Shared` yöntemleri Visual Basic'te). Bunun yerine özel bir statik nesnesi kullanın. Benzer şekilde, kullanmayın `this` C# (`Me` Visual Basic'te) kilit örneği yöntemleri. Bunun yerine özel bir nesne kullanın. Bir sınıf veya örnek kod, kendi olası neden kilitlenmeleri veya performans sorunları dışındaki tarafından kilitlenmiş.  
  
### <a name="compiler-support"></a>Derleyici desteği  
 Hem Visual Basic ve C# desteği kullanan bir dil anahtar sözcüğü <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> nesnesi kilitlenemiyor. Visual Basic destekler [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) deyimi; C# destekler [kilit](~/docs/csharp/language-reference/keywords/lock-statement.md) deyimi.  
  
 Her iki durumda da kodda bir özel durum oluşursa bloğu tarafından alınan kilidi **kilit** veya **SyncLock** otomatik olarak yayımlanır. C# ve Visual Basic derleyicileri yayma bir **deneyin**/**son** ile engelleme **Monitor.Enter** deneyin başındaki ve **Monitor.Exit**  içinde **son** bloğu. İçinde bir özel durum oluşursa **kilit** veya **SyncLock** bloğu **son** işleyicisi çalışır herhangi bir temizleme iş yapmanıza olanak sağlar.  
  
## <a name="synchronized-context"></a>Eşitlenen bağlamı  
 Kullanabileceğiniz **SynchronizationAttribute** herhangi **ContextBoundObject** tüm örnek yöntemleri ve alanları eşitlenecek. Aynı bağlam etki alanındaki tüm nesnelerin aynı kilit paylaşır. Birden çok iş parçacığı yöntemleri ve alanları erişmesine izin verilir, ancak herhangi bir anda yalnızca tek bir iş parçacığı izin verilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
 [İş parçacıkları ve iş parçacığı oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 [Eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 [SyncLock deyimi](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
 [lock deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md)
