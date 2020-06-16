---
title: Çoklu İş Parçacığı Kullanımı için Veri Eşitleme
description: .NET ' te çoklu iş parçacıklı verileri eşitlemeyi öğrenin. Eşitlenmiş kod bölgeleri, el ile eşitleme veya eşitlenmiş bağlamlar gibi stratejileri seçin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
ms.openlocfilehash: 4d528c54816961caa251ce054abf2c6cf07e9d01
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769112"
---
# <a name="synchronizing-data-for-multithreading"></a>Çoklu iş parçacıklı verileri eşitleme

Birden çok iş parçacığı tek bir nesnenin özelliklerine ve yöntemlerine çağrı yapabileceği zaman, bu çağrıların eşitlenmesi kritik öneme sahiptir. Aksi takdirde bir iş parçacığı başka bir iş parçacığının ne yaptığını kesintiye uğratabilir ve nesne geçersiz bir durumda kalabilir. Üyelerine bu kesintileri korunan bir sınıfa iş parçacığı güvenli denir.  
  
.NET, örnek ve statik üyelere erişimi eşzamanlı hale getirmek için çeşitli stratejiler sağlar:  
  
- Eşitlenmiş kod bölgeleri. <xref:System.Threading.Monitor>Yalnızca ihtiyaç duyduğunuz kod bloğunu eşleştirmek için bu sınıf için sınıfı veya derleyici desteğini kullanabilirsiniz, performansı geliştirir.  
  
- El ile eşitleme. .NET sınıf kitaplığı tarafından sunulan eşitleme nesnelerini kullanabilirsiniz. Sınıf hakkındaki tartışmayı içeren, bkz. [eşitleme temel elemanlarına genel bakış](overview-of-synchronization-primitives.md) <xref:System.Threading.Monitor> .  
  
- Eşitlenmiş bağlamlar. .NET Framework ve Xamarin uygulamalarında, <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> nesneleri için basit ve otomatik eşitlemeyi etkinleştirmek için kullanabilirsiniz <xref:System.ContextBoundObject> .  
  
- Ad alanındaki koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> . Bu sınıflar yerleşik eşitlenmiş ekleme ve kaldırma işlemleri sağlar. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../collections/thread-safe/index.md).  
  
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
 .NET sınıf kitaplığı, iş parçacıklarını eşitlemeye yönelik bir dizi sınıf sağlar. Bkz. [eşitleme temel elemanlarına genel bakış](overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Eşitlenmiş kod bölgeleri  
 <xref:System.Threading.Monitor>Kod bloklarını, örnek yöntemleri ve statik yöntemleri senkronize etmek için sınıfını veya bir derleyici anahtar sözcüğünü kullanabilirsiniz. Eşitlenmiş statik alanlar için destek yoktur.  
  
 Hem Visual Basic hem de C#, belirli bir dil anahtar sözcüğü, `lock` C# ' deki Ifade veya `SyncLock` Visual Basic içindeki deyimle birlikte kod blokları işaretlemesini destekler. Kod bir iş parçacığı tarafından yürütüldüğünde, kilidi almak için bir girişimde bulunuldu. Kilit zaten başka bir iş parçacığı tarafından edindiyseniz, kilit kullanılabilir hale gelene kadar iş parçacığı engeller. İş parçacığı eşitlenmiş kod bloğundan çıktığında, iş parçacığının bloğundan nasıl çıkmadığına bakılmaksızın kilit serbest bırakılır.  
  
> [!NOTE]
> `lock`Ve `SyncLock` deyimleri, ve kullanılarak uygulanır <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> . bu nedenle, <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> diğer yöntemleri <xref:System.Threading.Monitor> eşitlenmiş bölge içinde kendileriyle birlikte kullanılabilir.  
  
 Ayrıca, yöntemi ile aynı etkiye sahip olan ile bir yöntemi <xref:System.Runtime.CompilerServices.MethodImplAttribute> <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType> <xref:System.Threading.Monitor> süsleyip, yöntemin tamamının tamamını kilitlemek için derleyici anahtar sözcükleriyle birini kullanabilirsiniz.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>, eşitlenen bir kod bölgesine erişimi bekleyen bir iş parçacığını bölmek için kullanılabilir. **Thread. Interrupt** Ayrıca, gibi işlemlerden oluşan iş parçacıklarını bölmek için de kullanılır <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
> Yöntemleri korumak için (örneğin, C# ' ta, Visual Basic veya C++ ' da) türü kilitlemeyin `typeof(MyType)` `GetType(MyType)` `MyType::typeid` `static` ( `Shared` Visual Basic içindeki Yöntemler). Bunun yerine özel bir statik nesne kullanın. Benzer şekilde, `this` `Me` örnek yöntemleri kilitlemek için C# ' de (Visual Basic) kullanmayın. Bunun yerine özel bir nesne kullanın. Bir sınıf veya örnek, kendi dışında bir kodla kilitlenebilir, bu da kilitlenmelere veya performans sorunlarına yol açabilir.  
  
### <a name="compiler-support"></a>Derleyici desteği  
 Hem Visual Basic hem de C# <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> , nesneyi kilitlemek için ve kullanan bir Language anahtar sözcüğünü destekler. Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ifadesini destekler; C#, [Lock](../../csharp/language-reference/keywords/lock-statement.md) ifadesini destekler.  
  
 Her iki durumda da, kod bloğunda bir özel durum oluşturulursa, **kilit** veya **SyncLock** tarafından alınan kilit otomatik olarak serbest bırakılır. C# ve Visual Basic derleyicileri, Monitor ile **TRY** / **finally** bloğunu yayar. TRY 'ın başlangıcında **ENTER** , **finally** bloğunda **Monitor. Exit** yazın. **Kilit** veya **SyncLock** bloğunun içinde bir özel durum oluşturulursa, **finally** işleyicisi herhangi bir temizleme işi yapmanıza olanak tanımak için çalışır.  
  
## <a name="synchronized-context"></a>Eşitlenmiş bağlam  

Yalnızca .NET Framework ve Xamarin uygulamalarında, <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> <xref:System.ContextBoundObject> tüm örnek yöntemlerini ve alanlarını eşleştirmek için üzerinde öğesini kullanabilirsiniz. Aynı bağlam etki alanındaki tüm nesneler aynı kilidi paylaşır. Birden çok iş parçacığının yöntemlere ve alanlara erişmesine izin verilir, ancak herhangi bir zamanda yalnızca tek bir iş parçacığına izin verilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)
- [Eşitleme temelleri 'ne genel bakış](overview-of-synchronization-primitives.md)
- [SyncLock Deyimi](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock Deyimi](../../csharp/language-reference/keywords/lock-statement.md)
