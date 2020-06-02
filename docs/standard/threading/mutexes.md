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
ms.openlocfilehash: f9267bdd19a14995851f2689651c001815812912
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291181"
---
# <a name="mutexes"></a>Zaman Uyumu Sağlayıcılar
<xref:System.Threading.Mutex>Bir kaynağa özel erişim sağlamak için bir nesnesi kullanabilirsiniz. <xref:System.Threading.Mutex>Sınıfı sınıfından daha fazla sistem kaynağı kullanır <xref:System.Threading.Monitor> , ancak uygulama etki alanı sınırları arasında sıralanabilir, birden fazla bekleme ile birlikte kullanılabilir ve farklı işlemlerdeki iş parçacıklarını eşzamanlı hale getirmek için kullanılabilir. Yönetilen eşitleme mekanizmalarının karşılaştırması için bkz. [eşitleme temelleri 'Ne genel bakış](overview-of-synchronization-primitives.md).  
  
 Kod örnekleri için, oluşturucuların başvuru belgelerine bakın <xref:System.Threading.Mutex.%23ctor%2A> .  
  
## <a name="using-mutexes"></a>Birbirini kapsamayan kullanma  
 Bir iş parçacığı <xref:System.Threading.WaitHandle.WaitOne%2A> sahiplik istemek için bir mutex yöntemini çağırır. Çağrı, mutex kullanılabilir olana kadar ya da isteğe bağlı zaman aşımı aralığı aşana kadar engeller. Bir mutex 'in durumu, kendisine ait bir iş parçacığı yoksa sinyal edilir.  
  
 Bir iş parçacığı yöntemini çağırarak bir mutex yayınlar <xref:System.Threading.Mutex.ReleaseMutex%2A> . Zaman uyumu sağlayıcılar iş parçacığı benzeşimine sahiptir; diğer bir deyişle, mutex yalnızca sahibi olan iş parçacığı tarafından kullanılabilir. Bir iş parçacığı sahip olmadığı bir mutex yayınlarsa, iş parçacığında bir bir zaman <xref:System.ApplicationException> atılır.  
  
 <xref:System.Threading.Mutex>Sınıfı öğesinden türetildiğinden <xref:System.Threading.WaitHandle> , <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle.WaitAny%2A> <xref:System.Threading.WaitHandle> <xref:System.Threading.Mutex> diğer bekleme tutamaçlarına sahip bir birleşiminin sahipliğini istemek için statik veya yöntemlerini de çağırabilirsiniz.  
  
 Bir iş parçacığı bir sürümüne sahipse <xref:System.Threading.Mutex> , bu iş parçacığı <xref:System.Threading.Mutex> yürütmeyi engellemeden yinelenen bekleme istek çağrılarında aynısını belirtebilir; ancak, <xref:System.Threading.Mutex> sahipliği serbest bırakmak için kaç kez serbest bırakmalıdır.  
  
## <a name="abandoned-mutexes"></a>Bırakılan mutex 'ler  
 Bir iş parçacığı bir serbest bırakılmadan sonlandığında <xref:System.Threading.Mutex> , mutex terk edilir. Bu genellikle, mutex 'in koruduğu kaynak tutarsız bir durumda bırakılmış olduğundan ciddi bir programlama hatası gösterir. .NET Framework sürüm 2,0 ' de, mutex 'i alan bir <xref:System.Threading.AbandonedMutexException> sonraki iş parçacığında bir oluşturulur.  
  
> [!NOTE]
> 1,0 ve 1,1 .NET Framework sürümlerinde, bırakılan <xref:System.Threading.Mutex> durum sinyal durumuna ayarlanır ve bir sonraki bekleme iş parçacığı sahiplik alır. Bekleyen bir iş parçacığı yoksa, <xref:System.Threading.Mutex> sinyal sinyali verilmiş durumda kalır. Özel durum oluşturulmaz.  
  
 Sistem genelinde bir mutex söz konusu olduğunda, bırakılan bir mutex, bir uygulamanın aniden sonlandırıldığı (örneğin, Windows Görev Yöneticisi kullanılarak) anlamına gelebilir.  
  
## <a name="local-and-system-mutexes"></a>Yerel ve sistem zaman uyumu sağlayıcılar  
 Birbirini kapsamayan iki tür vardır: yerel zaman uyumu sağlayıcılar ve adlandırılmış sistem zaman uyumu. Bir <xref:System.Threading.Mutex> adı kabul eden bir Oluşturucu kullanarak bir nesne oluşturursanız, bu ad bir işletim sistemi nesnesi ile ilişkilendirilir. Adlandırılmış sistem zaman uyumu sağlayıcılar, işletim sistemi genelinde görünür ve işlem etkinliklerini eşzamanlı hale getirmek için kullanılabilir. <xref:System.Threading.Mutex>Aynı adlı sistem mutex 'i temsil eden birden çok nesne oluşturabilirsiniz ve bu <xref:System.Threading.Mutex.OpenExisting%2A> yöntemi kullanarak var olan bir adlandırılmış sistem mutex 'i açabilirsiniz.  
  
 Yerel bir mutex yalnızca işlem içinde bulunur. Bu, işleinizdeki yerel nesneye yönelik bir başvuruya sahip herhangi bir iş parçacığı tarafından kullanılabilir <xref:System.Threading.Mutex> . Her <xref:System.Threading.Mutex> nesne ayrı bir yerel mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Sistem zaman uyumu sağlayıcılar için Access Control güvenliği  
 .NET Framework sürüm 2,0, adlandırılmış sistem nesneleri için Windows erişim denetimi güvenliğini sorgulama ve ayarlama yeteneği sağlar. Sistem nesneleri genel olduğundan ve bu nedenle kendi dışında bir kodla kilitlenebildiğinden, oluşturma aşamasından sistem zaman uyumu koruması önerilir.  
  
 Zaman uyumu sağlayıcılar için erişim denetimi güvenliği hakkında daha fazla bilgi için, bkz <xref:System.Security.AccessControl.MutexSecurity> <xref:System.Security.AccessControl.MutexAccessRule> . ve <xref:System.Security.AccessControl.MutexRights> sınıfı, sabit listesi,,, <xref:System.Threading.Mutex.GetAccessControl%2A> <xref:System.Threading.Mutex.SetAccessControl%2A> ve <xref:System.Threading.Mutex.OpenExisting%2A> yöntemi <xref:System.Threading.Mutex> ve <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> Oluşturucu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [İş parçacıkları ve iş parçacığı](threads-and-threading.md)
- [İş Parçacığı Oluşturma](index.md)
