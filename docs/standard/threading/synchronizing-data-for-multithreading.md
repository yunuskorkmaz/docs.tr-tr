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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159396"
---
# <a name="synchronizing-data-for-multithreading"></a>Çoklu iş parçacığı için verileri eşitleme

Birden çok iş parçacığı tek bir nesnenin özelliklerine ve yöntemlerine çağrı yapabiliyorsa, bu çağrıların eşitlemi çok önemlidir. Aksi takdirde, bir iş parçacığı başka bir iş parçacığının ne yaptığını kesintiye uğratabilir ve nesne geçersiz bir durumda bırakılabilir. Üyeleri bu tür kesintilere karşı korunan bir sınıfa iş parçacığı güvenli denir.  
  
.NET, örnek ve statik üyelere erişimi eşitlemek için çeşitli stratejiler sağlar:  
  
- Eşitlenmiş kod bölgeleri. Performansı artırmak <xref:System.Threading.Monitor> için yalnızca yalnızca ihtiyacı olan kod bloğunu eşitlemek için bu sınıfın sınıf veya derleyici desteğini kullanabilirsiniz.  
  
- Manuel senkronizasyon. .NET sınıf kitaplığı tarafından sağlanan eşitleme nesnelerini kullanabilirsiniz. Bkz. Sınıfın tartışmasını <xref:System.Threading.Monitor> içeren [Eşitleme İlkellerine Genel Bakış.](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
  
- Eşitlenmiş bağlamlar. .NET Framework ve Xamarin uygulamaları için <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> nesneler için basit, otomatik <xref:System.ContextBoundObject> eşitleme etkinleştirmek için kullanabilirsiniz.  
  
- <xref:System.Collections.Concurrent?displayProperty=nameWithType> Ad alanında toplama sınıfları. Bu sınıflar yerleşik senkronize ekleme ve kaldırma işlemleri sağlar. Daha fazla bilgi için [İş Parçacığı Güvenli Koleksiyonları'na](../../../docs/standard/collections/thread-safe/index.md)bakın.  
  
 Ortak dil çalışma süresi, sınıfların gereksinimlere bağlı olarak çeşitli şekillerde eşitlenebilecek bir dizi kategoriye girdiği bir iş parçacığı modeli sağlar. Aşağıdaki tablo, belirli bir eşitleme kategorisine sahip alanlar ve yöntemler için hangi eşitleme desteğinin sağlandığını gösterir.  
  
|Kategori|Genel alanlar|Statik alanlar|Statik yöntemler|Örnek alanlar|Örnek yöntemleri|Belirli kod blokları|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Eşitleme Yok|Hayır|Hayır|Hayır|Hayır|Hayır|Hayır|  
|Senkronize Bağlam|Hayır|Hayır|Hayır|Evet|Evet|Hayır|  
|Senkronize Kod Bölgeleri|Hayır|Hayır|Yalnızca işaretliyse|Hayır|Yalnızca işaretliyse|Yalnızca işaretliyse|  
|Manuel Senkronizasyon|El ile|El ile|El ile|El ile|El ile|El ile|  
  
## <a name="no-synchronization"></a>Eşitleme yok  
 Bu nesneler için varsayılandır. Herhangi bir iş parçacığı herhangi bir yönteme veya alana herhangi bir zamanda erişebilir. Bu nesnelere aynı anda yalnızca bir iş parçacığı erişmelidir.  
  
## <a name="manual-synchronization"></a>Manuel senkronizasyon  
 .NET sınıf kitaplığı iş parçacıklarını eşitlemek için bir dizi sınıf sağlar. Senkronizasyon [İlkellerine Genel Bakış' a](../../../docs/standard/threading/overview-of-synchronization-primitives.md)bakın.  
  
## <a name="synchronized-code-regions"></a>Senkronize kod bölgeleri  
 Kod bloklarını, örnek yöntemlerini <xref:System.Threading.Monitor> ve statik yöntemleri eşitlemek için sınıfı veya derleyici anahtar sözcüğü kullanabilirsiniz. Senkronize statik alanlar için destek yoktur.  
  
 Hem Visual Basic hem de C# kod bloklarının belirli bir `lock` dil anahtar kelimesi, C# ifadesi veya Visual Basic'teki `SyncLock` deyimi destekler. Kod bir iş parçacığı tarafından yürütüldüğünde, kilidi elde etmek için bir girişimde bulunulr. Kilit zaten başka bir iş parçacığı tarafından elde edilmişse, kilit kullanılabilir hale gelene kadar iş parçacığı engeller. İş parçacığı senkronize kod bloğundan çıktığında, iş parçacığı bloktan nasıl çıkarsa çıksın kilit serbest bırakılır.  
  
> [!NOTE]
> Ve `lock` `SyncLock` ifadeler kullanılarak <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> uygulanır <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>ve , böylece <xref:System.Threading.Monitor> diğer yöntemler senkronize bölge içinde onlarla birlikte kullanılabilir.  
  
 Ayrıca, bir yöntemi, yöntemin <xref:System.Runtime.CompilerServices.MethodImplAttribute> <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>tüm gövdesini kilitlemek için <xref:System.Threading.Monitor> kullanmakla aynı etkiye sahip olan veya derleyici anahtar kelimelerinden biri olan bir değere sahip bir yöntemle de dekore edebilirsiniz.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>eşitlenmiş bir kod bölgesine erişimi beklemek gibi engelleme işlemlerinden bir iş parçacığı nı kırmak için kullanılabilir. **Thread.Interrupt** gibi <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>işlemlerden iş parçacığı kırmak için de kullanılır.  
  
> [!IMPORTANT]
> Yöntemleri `typeof(MyType)` (Visual `GetType(MyType)` `MyType::typeid` `static` `Shared` Basic yöntemleri) korumak için c#, Visual Basic veya C++ türüne kilitlenmeyin. Bunun yerine özel statik bir nesne kullanın. Benzer şekilde, örnek `this` yöntemlerini`Me` kilitlemek için C# (Visual Basic'te) kullanmayın. Bunun yerine özel bir nesne kullanın. Bir sınıf veya örnek, sizinki nin dışındaki kodlarla kilitlenebilir ve bu da kilitlenmeveya performans sorunlarına neden olabilir.  
  
### <a name="compiler-support"></a>Derleyici desteği  
 Hem Visual Basic hem de C# <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nesneyi kullanan ve <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> kilitlemeyi kullanan bir dil anahtar sözcüğüdestekler. Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimini destekler; C# [kilit](../../csharp/language-reference/keywords/lock-statement.md) deyimini destekler.  
  
 Her iki durumda da, kod bloğuna bir özel durum atılırsa, **kilit** veya **SyncLock** tarafından edinilen kilit otomatik olarak serbest bırakılır. C# ve Visual Basic derleyicileri, deneyin başında **Monitor.Enter** ve **son** bloğunda **Monitor.Exit** ile bir **deneme**/sonunda**blok** yayır. **Kilit** veya **SyncLock** bloğunun içine bir özel durum atılırsa, **son olarak** işleyici herhangi bir temizleme çalışması yapmanıza olanak sağlamak için çalışır.  
  
## <a name="synchronized-context"></a>Senkronize Bağlam  

.NET Framework ve Xamarin uygulamalarında, tüm <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> örnek <xref:System.ContextBoundObject> yöntemleri ve alanları eşitlemek için herhangi bir üzerinde kullanabilirsiniz. Aynı bağlam etki alanında ki tüm nesneler aynı kilidi paylaşır. Yöntemlere ve alanlara erişmek için birden çok iş parçacığına izin verilir, ancak yalnızca tek bir iş parçacığına herhangi bir anda izin verilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
- [Senkronizasyon İlkellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [SyncLock Deyimi](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock Deyimi](../../csharp/language-reference/keywords/lock-statement.md)
