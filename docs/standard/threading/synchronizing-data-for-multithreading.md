---
title: Çoklu İş Parçacığı Kullanımı için Veri Eşitleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
ms.openlocfilehash: a70bd3070d8b1dcd06e55d330a01d29071293f6c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159396"
---
# <a name="synchronizing-data-for-multithreading"></a>Çoklu iş parçacıklı verileri eşitleme

Birden çok iş parçacığı tek bir nesnenin özelliklerine ve yöntemlerine çağrı yapabileceği zaman, bu çağrıların eşitlenmesi kritik öneme sahiptir. Aksi takdirde bir iş parçacığı başka bir iş parçacığının ne yaptığını kesintiye uğratabilir ve nesne geçersiz bir durumda kalabilir. Üyelerine bu kesintileri korunan bir sınıfa iş parçacığı güvenli denir.  
  
.NET, örnek ve statik üyelere erişimi eşzamanlı hale getirmek için çeşitli stratejiler sağlar:  
  
- Eşitlenmiş kod bölgeleri. Yalnızca ihtiyaç duyduğunuz kod bloğunu eşleştirmek için bu sınıf için <xref:System.Threading.Monitor> sınıfını veya derleyici desteğini kullanabilirsiniz, performansı geliştirir.  
  
- El ile eşitleme. .NET sınıf kitaplığı tarafından sunulan eşitleme nesnelerini kullanabilirsiniz. <xref:System.Threading.Monitor> sınıfının bir tartışmasını içeren [eşitleme temel larına genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)konusuna bakın.  
  
- Eşitlenmiş bağlamlar. .NET Framework ve Xamarin uygulamalarında, <xref:System.ContextBoundObject> nesneleri için basit ve otomatik eşitlemeyi etkinleştirmek üzere <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> kullanabilirsiniz.  
  
- <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanındaki koleksiyon sınıfları. Bu sınıflar yerleşik eşitlenmiş ekleme ve kaldırma işlemleri sağlar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../../../docs/standard/collections/thread-safe/index.md).  
  
 Ortak dil çalışma zamanı, sınıfların gereksinimlere bağlı olarak çeşitli farklı yollarla eşitlenebilecek bir dizi kategoride yer aldığı bir iş parçacığı modeli sağlar. Aşağıdaki tabloda, belirli bir eşitleme kategorisine sahip alanlar ve yöntemler için hangi eşitleme desteğinin sağlandığı gösterilmektedir.  
  
|Kategori|Genel alanlar|Statik alanlar|Statik yöntemler|Örnek alanları|Örnek yöntemleri|Belirli kod blokları|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Eşitleme yok|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|  
|Eşitlenmiş bağlam|Hayır|Hayır|Hayır|Yes|Yes|Hayır|  
|Eşitlenmiş kod bölgeleri|Hayır|Hayır|Yalnızca işaretlenmişse|Hayır|Yalnızca işaretlenmişse|Yalnızca işaretlenmişse|  
|El ile eşitleme|El ile|El ile|El ile|El ile|El ile|El ile|  
  
## <a name="no-synchronization"></a>Eşitleme yok  
 Bu, nesneler için varsayılandır. Herhangi bir iş parçacığı herhangi bir zamanda herhangi bir yönteme veya alana erişebilir. Tek seferde yalnızca bir iş parçacığının bu nesnelere erişmesi gerekir.  
  
## <a name="manual-synchronization"></a>El ile eşitleme  
 .NET sınıf kitaplığı, iş parçacıklarını eşitlemeye yönelik bir dizi sınıf sağlar. Bkz. [eşitleme temel elemanlarına genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Eşitlenmiş kod bölgeleri  
 Kod bloklarını, örnek yöntemleri ve statik yöntemleri senkronize etmek için <xref:System.Threading.Monitor> sınıfını veya bir derleyici anahtar sözcüğünü kullanabilirsiniz. Eşitlenmiş statik alanlar için destek yoktur.  
  
 Hem Visual Basic C# hem de belirli bir dil anahtar sözcüğüyle kod blokları, içindeki C# `lock` ifadesiyle veya `SyncLock` deyimindeki Visual Basic. Kod bir iş parçacığı tarafından yürütüldüğünde, kilidi almak için bir girişimde bulunuldu. Kilit zaten başka bir iş parçacığı tarafından edindiyseniz, kilit kullanılabilir hale gelene kadar iş parçacığı engeller. İş parçacığı eşitlenmiş kod bloğundan çıktığında, iş parçacığının bloğundan nasıl çıkmadığına bakılmaksızın kilit serbest bırakılır.  
  
> [!NOTE]
> `lock` ve `SyncLock` deyimleri <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>kullanılarak uygulanır. bu nedenle, diğer <xref:System.Threading.Monitor> yöntemleri eşitlenmiş bölge içinde kendileriyle birlikte kullanılabilir.  
  
 Ayrıca, bir <xref:System.Runtime.CompilerServices.MethodImplAttribute> bir yöntemi, <xref:System.Threading.Monitor> kullanma ile aynı etkiye sahip olan bir <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>, yöntemin tüm gövdesini kilitlemek için derleyici anahtar kelimeleriyle de kullanabilirsiniz.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>, eşitlenen bir kod bölgesine erişimi bekleyen bir iş parçacığını bölmek için kullanılabilir. **Thread. Interrupt** Ayrıca <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>gibi işlemlerden dışarı iş parçacıklarını bölmek için de kullanılır.  
  
> [!IMPORTANT]
> `static` yöntemlerini (`Shared` yöntemleri Visual Basic) korumak için, türü C#(yani, içindeki `typeof(MyType)` `GetType(MyType)`, Visual Basic C++ veya `MyType::typeid` içindeki kilitlemeyin. Bunun yerine özel bir statik nesne kullanın. Benzer şekilde, örnek yöntemleri kilitlemek için C# içinde `this` (Visual Basic`Me`) kullanmayın. Bunun yerine özel bir nesne kullanın. Bir sınıf veya örnek, kendi dışında bir kodla kilitlenebilir, bu da kilitlenmelere veya performans sorunlarına yol açabilir.  
  
### <a name="compiler-support"></a>Derleyici desteği  
 Hem Visual Basic hem C# de nesneyi kilitlemek için <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> kullanan bir dil anahtar sözcüğünü destekler. Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ifadesini destekler; C# [Lock](../../csharp/language-reference/keywords/lock-statement.md) ifadesini destekler.  
  
 Her iki durumda da, kod bloğunda bir özel durum oluşturulursa, **kilit** veya **SyncLock** tarafından alınan kilit otomatik olarak serbest bırakılır. Ve C# Visual Basic derleyicileri, Monitor ile **TRY**/**finally** bloğunu yayar. TRY 'ın başlangıcında ENTER, **finally** bloğunda **Monitor. Exit** **yazın** . **Kilit** veya **SyncLock** bloğunun içinde bir özel durum oluşturulursa, **finally** işleyicisi herhangi bir temizleme işi yapmanıza olanak tanımak için çalışır.  
  
## <a name="synchronized-context"></a>Eşitlenmiş bağlam  

Yalnızca .NET Framework ve Xamarin uygulamalarında, tüm örnek yöntemlerini ve alanlarını eşleştirmek için <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> herhangi bir <xref:System.ContextBoundObject> kullanabilirsiniz. Aynı bağlam etki alanındaki tüm nesneler aynı kilidi paylaşır. Birden çok iş parçacığının yöntemlere ve alanlara erişmesine izin verilir, ancak herhangi bir zamanda yalnızca tek bir iş parçacığına izin verilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
- [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [SyncLock Deyimi](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock Deyimi](../../csharp/language-reference/keywords/lock-statement.md)
