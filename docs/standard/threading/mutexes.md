---
title: Zaman Uyumu Sağlayıcılar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
ms.openlocfilehash: 874f879697db0b47c73626350eeb05a01b38e1bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127564"
---
# <a name="mutexes"></a>Zaman Uyumu Sağlayıcılar
Bir kaynağa özel erişim sağlamak için bir <xref:System.Threading.Mutex> nesnesi kullanabilirsiniz. <xref:System.Threading.Mutex> sınıfı, <xref:System.Threading.Monitor> sınıfından daha fazla sistem kaynağı kullanır, ancak uygulama etki alanı sınırları arasında sıralanabilir, birden fazla bekleme ile birlikte kullanılabilir ve farklı işlemlerdeki iş parçacıklarını eşzamanlı hale getirmek için kullanılabilir. Yönetilen eşitleme mekanizmalarının karşılaştırması için bkz. [eşitleme temelleri 'Ne genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Kod örnekleri için bkz. <xref:System.Threading.Mutex.%23ctor%2A> oluşturucuları için başvuru belgeleri.  
  
## <a name="using-mutexes"></a>Birbirini kapsamayan kullanma  
 Bir iş parçacığı sahiplik istemek için bir mutex 'in <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemini çağırır. Çağrı, mutex kullanılabilir olana kadar ya da isteğe bağlı zaman aşımı aralığı aşana kadar engeller. Bir mutex 'in durumu, kendisine ait bir iş parçacığı yoksa sinyal edilir.  
  
 Bir iş parçacığı, <xref:System.Threading.Mutex.ReleaseMutex%2A> yöntemini çağırarak bir mutex yayınlar. Zaman uyumu sağlayıcılar iş parçacığı benzeşimine sahiptir; diğer bir deyişle, mutex yalnızca sahibi olan iş parçacığı tarafından kullanılabilir. Bir iş parçacığı sahip olmadığı bir mutex yayınlarsa, iş parçacığında bir <xref:System.ApplicationException> oluşturulur.  
  
 <xref:System.Threading.Mutex> sınıfı <xref:System.Threading.WaitHandle>türetildiği için, diğer bekleme tutamaçlarla birlikte bir <xref:System.Threading.WaitHandle> sahipliğini istemek üzere <xref:System.Threading.Mutex> statik <xref:System.Threading.WaitHandle.WaitAll%2A> veya <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemlerini de çağırabilirsiniz.  
  
 Bir iş parçacığı bir <xref:System.Threading.Mutex>sahip ise, bu iş parçacığı, yürütmeyi engellemeden yinelenen bekleme isteği çağrılarında aynı <xref:System.Threading.Mutex> belirtebilir; Ancak, sahipliği serbest bırakmak için <xref:System.Threading.Mutex> çok kez serbest bırakmalıdır.  
  
## <a name="abandoned-mutexes"></a>Bırakılan mutex 'ler  
 Bir iş parçacığı bir <xref:System.Threading.Mutex>serbest bırakılmadan sonlandığında, mutex terk edilir. Bu genellikle, mutex 'in koruduğu kaynak tutarsız bir durumda bırakılmış olduğundan ciddi bir programlama hatası gösterir. .NET Framework sürüm 2,0 ' de, mutex 'i alan bir sonraki iş parçacığında bir <xref:System.Threading.AbandonedMutexException> oluşturulur.  
  
> [!NOTE]
> 1,0 ve 1,1 .NET Framework sürümlerinde, bırakılmış bir <xref:System.Threading.Mutex> sinyal edildi durumuna ayarlanır ve bir sonraki bekleme iş parçacığı sahiplik alır. Bekleyen bir iş parçacığı yoksa <xref:System.Threading.Mutex> sinyal sinyali içinde kalır. Hiçbir özel durum oluşturulmaz.  
  
 Sistem genelinde bir mutex söz konusu olduğunda, bırakılan bir mutex, bir uygulamanın aniden sonlandırıldığı (örneğin, Windows Görev Yöneticisi kullanılarak) anlamına gelebilir.  
  
## <a name="local-and-system-mutexes"></a>Yerel ve sistem zaman uyumu sağlayıcılar  
 Birbirini kapsamayan iki tür vardır: yerel zaman uyumu sağlayıcılar ve adlandırılmış sistem zaman uyumu. Adı kabul eden bir Oluşturucu kullanarak bir <xref:System.Threading.Mutex> nesnesi oluşturursanız, bu ad bir işletim sistemi nesnesi ile ilişkilendirilir. Adlandırılmış sistem zaman uyumu sağlayıcılar, işletim sistemi genelinde görünür ve işlem etkinliklerini eşzamanlı hale getirmek için kullanılabilir. Aynı adlı sistem mutex 'i temsil eden birden çok <xref:System.Threading.Mutex> nesnesi oluşturabilir ve <xref:System.Threading.Mutex.OpenExisting%2A> metodunu kullanarak var olan bir adlandırılmış sistem mutex 'i açabilirsiniz.  
  
 Yerel bir mutex yalnızca işlem içinde bulunur. Bu, işleminizde yerel <xref:System.Threading.Mutex> nesnesine bir başvurusu olan herhangi bir iş parçacığı tarafından kullanılabilir. Her <xref:System.Threading.Mutex> nesnesi ayrı bir yerel mutex 'dir.  
  
### <a name="access-control-security-for-system-mutexes"></a>Sistem zaman uyumu sağlayıcılar için Access Control güvenliği  
 .NET Framework sürüm 2,0, adlandırılmış sistem nesneleri için Windows erişim denetimi güvenliğini sorgulama ve ayarlama yeteneği sağlar. Sistem nesneleri genel olduğundan ve bu nedenle kendi dışında bir kodla kilitlenebildiğinden, oluşturma aşamasından sistem zaman uyumu koruması önerilir.  
  
 Zaman uyumu sağlayıcılar için erişim denetimi güvenliği hakkında daha fazla bilgi için, <xref:System.Threading.Mutex.SetAccessControl%2A>sınıfının ve <xref:System.Threading.Mutex.OpenExisting%2A> oluşturucusunun <xref:System.Security.AccessControl.MutexSecurity> ve <xref:System.Security.AccessControl.MutexAccessRule> sınıflarına, <xref:System.Security.AccessControl.MutexRights> sabit listesine, <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex> ve <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> yöntemlerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [İş parçacıkları ve iş parçacığı](threads-and-threading.md)
- [İş parçacığı oluşturma](index.md)
