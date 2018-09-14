---
title: Çoklu İş Parçacığı Kullanımı için Veri Eşitleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a7561a09b1b47827b3476b5525863503765064f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45526947"
---
# <a name="synchronizing-data-for-multithreading"></a>Çoklu İş Parçacığı Kullanımı için Veri Eşitleme
Birden çok iş parçacığı özellikleri ve yöntemleri tek bir nesnenin çağrı yaptığınızda bu çağrıları eşitlenmiş önemlidir. Aksi takdirde bir iş parçacığı başka bir iş parçacığı yaptığı yarıda kesebilecek ve Nesne geçersiz bir durumda kalabilir. Böyle kesintilerden korunan üyeleri bir sınıf, iş parçacığı güvenli olarak adlandırılır.  
  
 Ortak dil altyapısı örneği ve statik üyeler erişimi eşitlemek için çeşitli stratejileri sağlar:  
  
-   Eşitlenmiş kod bölgeleri. Kullanabileceğiniz <xref:System.Threading.Monitor> kodunu engeller yalnızca eşitlemek için bu sınıfın sınıf ya da derleyici desteği gerekir, performansı artırma.  
  
-   El ile eşitleme. .NET Framework sınıf kitaplığı tarafından sağlanan eşitleme nesneleri kullanabilirsiniz. Bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md), hakkında ayrıntılı bilgi içeren <xref:System.Threading.Monitor> sınıfı.  
  
-   Eşitleme bağlamı. Kullanabileceğiniz <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> için basit, Otomatik eşitlemeyi etkinleştirmek için <xref:System.ContextBoundObject> nesneleri.  
  
-   Koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı. Bu sınıfların sağlayan yerleşik eşitlenmiş ekleme ve kaldırma işlemleri. Daha fazla bilgi için [iş parçacığı güvenli koleksiyonları](../../../docs/standard/collections/thread-safe/index.md).  
  
 Ortak dil çalışma zamanı, sınıfları birkaç farklı şekilde gereksinimlerine bağlı olarak çeşitli eşitlenebilir kategorileri kalan bir iş parçacığı modeli sağlar. Aşağıdaki tabloda, hangi eşitleme desteği alanlar ve yöntemler ile belirtilen eşitleme kategori için sağlanan gösterilmektedir.  
  
|Kategori|Genel alanlar|Statik alanlar|Statik yöntemler|Örnek alanları|Örnek yöntemleri|Belirli kod blokları|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Eşitleme|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|  
|Eşitleme bağlamı|Hayır|Hayır|Hayır|Evet|Evet|Hayır|  
|Eşitlenmiş kod bölgeleri|Hayır|Hayır|Yalnızca işaretli|Hayır|Yalnızca işaretli|Yalnızca işaretli|  
|El ile eşitleme|El ile|El ile|El ile|El ile|El ile|El ile|  
  
## <a name="no-synchronization"></a>Eşitleme  
 Bu nesneler için varsayılandır. Herhangi bir iş parçacığı herhangi bir zamanda herhangi bir yöntemi veya alana erişebilirsiniz. Aynı anda yalnızca tek bir iş parçacığı bu nesnelere erişebilirsiniz.  
  
## <a name="manual-synchronization"></a>El ile eşitleme  
 .NET Framework sınıf kitaplığı, iş parçacıklarını eşitleme için bir dizi sınıfları sağlar. Bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Eşitlenmiş kod bölgeleri  
 Kullanabileceğiniz <xref:System.Threading.Monitor> sınıfı veya kod, örnek yöntemler ve statik yöntemler blokları eşitlemek üzere derleyici anahtar sözcüğü. Eşitlenmiş statik alanlar için desteği yoktur.  
  
 Visual Basic ve C# dil anahtar sözcüğü ile kod bloklarından birini işaretleme desteği `lock` C# deyimi veya `SyncLock` Visual Basic'te deyimi. Bir iş parçacığının kod yürütüldüğünde, bir kilidi almak için girişimde. Kilit başka bir iş parçacığı tarafından alınan, kilit kadar iş parçacığı blokları kullanılabilir olur. İş parçacığı eşitlenmiş kod bloğunu çıktığında kilidi nasıl blok iş parçacığından çıkar ne olursa olsun yayımlanır.  
  
> [!NOTE]
>  `lock` Ve `SyncLock` deyimleri kullanarak uygulanır <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, bu nedenle diğer yöntemleri <xref:System.Threading.Monitor> eşitlenmiş bölge içinde bunları ile birlikte kullanılabilir.  
  
 Ayrıca bir yöntemle donatmak bir **MethodImplAttribute** ve **Methodımploptions.Synchronized**, kullanmakla aynı etkiye sahiptir **İzleyici** veya derleyici yöntemin tüm gövdesinin kilitlemek için anahtar sözcükler.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> bir iş parçacığı dışında eşitlenmiş bir bölge kodu erişimi için beklenirken gibi engelleme işlemleri ayırmak için kullanılabilir. **Thread.Interrupt** ayrıca iş parçacığı gibi işlemler dışında ayırmak için kullanılan <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Türü kilitlemez — diğer bir deyişle, `typeof(MyType)` C# ' ta, `GetType(MyType)` Visual Basic'te veya `MyType::typeid` c++ — korumak için `static` yöntemleri (`Shared` yöntem Visual Basic'te). Bunun yerine özel bir statik nesnesi kullanın. Benzer şekilde, kullanmayın `this` C# (`Me` Visual Basic'te) kilit örnek yöntemleri için. Bunun yerine bir özel nesneye kullanın. Bir sınıf veya örnek, kendi olası neden kilitlenmeleri veya performans sorunlarını dışındaki kod tarafından kilitlenmiş.  
  
### <a name="compiler-support"></a>Derleyici desteği  
 Visual Basic ve C# desteği kullanan bir dil anahtar kelimesi <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> nesnesi kilitlenemiyor. Visual Basic destekler [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) deyimi; C# destekler [kilit](~/docs/csharp/language-reference/keywords/lock-statement.md) deyimi.  
  
 Her iki durumda da, kodda bir özel durum oluşturulursa bloğu tarafından alınan kilidi **kilit** veya **SyncLock** otomatik olarak yayımlanır. C# ve Visual Basic derleyicileri yayma bir **deneyin**/**son** ile block **Monitor.Enter** dene, başında ve **Monitor.Exit**  içinde **son** blok. İçinde bir özel durum oluşturulursa **kilit** veya **SyncLock** bloğu **son** herhangi bir temizleme iş yapmanıza izin verdiği için işleyici çalıştırır.  
  
## <a name="synchronized-context"></a>Eşitleme bağlamı  
 Kullanabileceğiniz **SynchronizationAttribute** herhangi **ContextBoundObject** tüm örnek yöntemleri ve alanları eşitlenecek. Aynı bağlam etki alanındaki tüm nesnelerin aynı kilit paylaşın. Birden çok iş parçacığı yöntemlerin ve alanların erişmesine izin verilir, ancak herhangi bir anda yalnızca tek bir iş parçacığı izin verilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
- [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
- [SyncLock Deyimi](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
- [lock Deyimi](~/docs/csharp/language-reference/keywords/lock-statement.md)
