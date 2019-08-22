---
title: Çoklu İş Parçacığı Kullanımı için Veri Eşitleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e558d86fd4e012a6b88e0bcd05d58ecddc6cc20
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666264"
---
# <a name="synchronizing-data-for-multithreading"></a>Çoklu iş parçacıklı verileri eşitleme

Birden çok iş parçacığı tek bir nesnenin özelliklerine ve yöntemlerine çağrı yapabileceği zaman, bu çağrıların eşitlenmesi kritik öneme sahiptir. Aksi takdirde bir iş parçacığı başka bir iş parçacığının ne yaptığını kesintiye uğratabilir ve nesne geçersiz bir durumda kalabilir. Üyelerine bu kesintileri korunan bir sınıfa iş parçacığı güvenli denir.  
  
.NET, örnek ve statik üyelere erişimi eşzamanlı hale getirmek için çeşitli stratejiler sağlar:  
  
- Eşitlenmiş kod bölgeleri. Yalnızca ihtiyaç duyduğunuz kod <xref:System.Threading.Monitor> bloğunu eşleştirmek için bu sınıf için sınıfı veya derleyici desteğini kullanabilirsiniz, performansı geliştirir.  
  
- El ile eşitleme. .NET sınıf kitaplığı tarafından sunulan eşitleme nesnelerini kullanabilirsiniz. <xref:System.Threading.Monitor> Sınıf hakkındaki tartışmayı içeren, bkz. [eşitleme temel elemanlarına genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
- Eşitlenmiş bağlamlar. .NET Framework ve Xamarin uygulamalarında, <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> nesneleri için <xref:System.ContextBoundObject> basit ve otomatik eşitlemeyi etkinleştirmek için kullanabilirsiniz.  
  
- <xref:System.Collections.Concurrent?displayProperty=nameWithType> Ad alanındaki koleksiyon sınıfları. Bu sınıflar yerleşik eşitlenmiş ekleme ve kaldırma işlemleri sağlar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../../../docs/standard/collections/thread-safe/index.md).  
  
 Ortak dil çalışma zamanı, sınıfların gereksinimlere bağlı olarak çeşitli farklı yollarla eşitlenebilecek bir dizi kategoride yer aldığı bir iş parçacığı modeli sağlar. Aşağıdaki tabloda, belirli bir eşitleme kategorisine sahip alanlar ve yöntemler için hangi eşitleme desteğinin sağlandığı gösterilmektedir.  
  
|Kategori|Genel alanlar|Statik alanlar|Statik yöntemler|Örnek alanları|Örnek yöntemleri|Belirli kod blokları|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Eşitleme yok|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|  
|Eşitlenmiş bağlam|Hayır|Hayır|Hayır|Evet|Evet|Hayır|  
|Eşitlenmiş kod bölgeleri|Hayır|Hayır|Yalnızca işaretlenmişse|Hayır|Yalnızca işaretlenmişse|Yalnızca işaretlenmişse|  
|El ile eşitleme|El ile|El ile|El ile|El ile|El ile|El ile|  
  
## <a name="no-synchronization"></a>Eşitleme yok  
 Bu, nesneler için varsayılandır. Herhangi bir iş parçacığı herhangi bir zamanda herhangi bir yönteme veya alana erişebilir. Tek seferde yalnızca bir iş parçacığının bu nesnelere erişmesi gerekir.  
  
## <a name="manual-synchronization"></a>El ile eşitleme  
 .NET sınıf kitaplığı, iş parçacıklarını eşitlemeye yönelik bir dizi sınıf sağlar. Bkz. [eşitleme temel elemanlarına genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Eşitlenmiş kod bölgeleri  
 Kod bloklarını, örnek <xref:System.Threading.Monitor> yöntemleri ve statik yöntemleri senkronize etmek için sınıfını veya bir derleyici anahtar sözcüğünü kullanabilirsiniz. Eşitlenmiş statik alanlar için destek yoktur.  
  
 Her ikisi de C# Visual Basic ve belirli bir dil anahtar sözcüğü, `lock` içindeki C# `SyncLock` ifadesini veya Visual Basic ifadesini içeren kod blokları işaretlemesini destekler. Kod bir iş parçacığı tarafından yürütüldüğünde, kilidi almak için bir girişimde bulunuldu. Kilit zaten başka bir iş parçacığı tarafından edindiyseniz, kilit kullanılabilir hale gelene kadar iş parçacığı engeller. İş parçacığı eşitlenmiş kod bloğundan çıktığında, iş parçacığının bloğundan nasıl çıkmadığına bakılmaksızın kilit serbest bırakılır.  
  
> [!NOTE]
>  <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor> Ve deyimleri, ve<xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>kullanılarak uygulanır. bu nedenle, diğer yöntemleri eşitlenmiş bölge içinde kendileriyle birlikte kullanılabilir. `SyncLock` `lock`  
  
 Ayrıca <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>, yöntemi ile aynı etkiye <xref:System.Threading.Monitor> sahip olan <xref:System.Runtime.CompilerServices.MethodImplAttribute> ile bir yöntemi süsleyip, yöntemin tamamının tamamını kilitlemek için derleyici anahtar sözcükleriyle birini kullanabilirsiniz.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>, eşitlenen bir kod bölgesine erişimi bekleyen bir iş parçacığını bölmek için kullanılabilir. **Thread. Interrupt** Ayrıca, gibi <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>işlemlerden oluşan iş parçacıklarını bölmek için de kullanılır.  
  
> [!IMPORTANT]
>  Yöntemi `typeof(MyType)` ( `GetType(MyType)` `MyType::typeid`VisualBasiciçindeki yöntemleri) C# C++ korumak için`static` , bu türü (' de, içinde, Visual Basic veya içinde — kilitleme.`Shared` Bunun yerine özel bir statik nesne kullanın. Benzer şekilde, örnek yöntemleri `this` kilitlemek C# için`Me` içinde (Visual Basic olarak) kullanmayın. Bunun yerine özel bir nesne kullanın. Bir sınıf veya örnek, kendi dışında bir kodla kilitlenebilir, bu da kilitlenmelere veya performans sorunlarına yol açabilir.  
  
### <a name="compiler-support"></a>Derleyici desteği  
 Hem Visual Basic hem C# de nesneyi kilitlemek için ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> kullanan <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> bir dil anahtar sözcüğünü destekler. Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ifadesini destekler; C# [Lock](../../csharp/language-reference/keywords/lock-statement.md) ifadesini destekler.  
  
 Her iki durumda da, kod bloğunda bir özel durum oluşturulursa, **kilit** veya **SyncLock** tarafından alınan kilit otomatik olarak serbest bırakılır. Ve C# Visual Basic derleyicileri, Monitor ile **TRY**/**finally** bloğunu yayar. TRY 'ın başlangıcında ENTER, **finally** bloğunda **Monitor. Exit** **yazın** . **Kilit** veya **SyncLock** bloğunun içinde bir özel durum oluşturulursa, **finally** işleyicisi herhangi bir temizleme işi yapmanıza olanak tanımak için çalışır.  
  
## <a name="synchronized-context"></a>Eşitlenmiş bağlam  
 
Yalnızca .NET Framework ve Xamarin uygulamalarında, <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> tüm örnek yöntemlerini ve alanlarını eşleştirmek <xref:System.ContextBoundObject> için üzerinde öğesini kullanabilirsiniz. Aynı bağlam etki alanındaki tüm nesneler aynı kilidi paylaşır. Birden çok iş parçacığının yöntemlere ve alanlara erişmesine izin verilir, ancak herhangi bir zamanda yalnızca tek bir iş parçacığına izin verilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
- [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [SyncLock Deyimi](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock Deyimi](../../csharp/language-reference/keywords/lock-statement.md)
