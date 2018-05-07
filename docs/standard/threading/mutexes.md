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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1f3df40a468c7c0f7da0b559ea9b01703cd200a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mutexes"></a>Zaman Uyumu Sağlayıcılar
Kullanabileceğiniz bir <xref:System.Threading.Mutex> özel bir kaynağa erişim sağlamak için nesne. <xref:System.Threading.Mutex> Sınıfını kullanır daha fazla sistem kaynağı <xref:System.Threading.Monitor> sınıfı, ancak uygulama etki alanı sınırlarında sıralanmış, birden çok bekler ile kullanılabilir ve farklı işlemler iş parçacığı eşitleme için kullanılabilir. Yönetilen eşitleme mekanizmaları karşılaştırması için bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Kod örnekleri için başvuru belgelerine bakın <xref:System.Threading.Mutex.%23ctor%2A> oluşturucular.  
  
## <a name="using-mutexes"></a>Zaman uyumu sağlayıcılar kullanma  
 Bir iş parçacığı çağırır <xref:System.Threading.WaitHandle.WaitOne%2A> isteği sahipliği için mutex yöntemi. Çağrı blokları mutex kullanılabilir hale gelene kadar veya kadar isteğe bağlı zaman aşımı aralığı sona erdiğinde. Bir mutex durumunu hiçbir iş parçacığı, sahip değilse verdi.  
  
 Bir iş parçacığı bir mutex çağırarak serbest kendi <xref:System.Threading.Mutex.ReleaseMutex%2A> yöntemi. Zaman uyumu sağlayıcılar iş parçacığı benzeşimini; yine de sahip istiyor musunuz? diğer bir deyişle, mutex sahibi yalnızca iş parçacığı tarafından serbest bırakılabilir. Bir iş parçacığı sahibi olmadığı, mutex yayımlarsa bir <xref:System.ApplicationException> iş parçacığında oluşturuldu.  
  
 Çünkü <xref:System.Threading.Mutex> sınıfı türetilir <xref:System.Threading.WaitHandle>, ayrıca, statik çağırabilirsiniz <xref:System.Threading.WaitHandle.WaitAll%2A> veya <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemlerini <xref:System.Threading.WaitHandle> isteği sahipliğini için bir <xref:System.Threading.Mutex> bekleme tanıtıcıları diğer ile birlikte.  
  
 Bir iş parçacığı sahipse bir <xref:System.Threading.Mutex>, iş parçacığı aynı belirtebilirsiniz <xref:System.Threading.Mutex> ; yürütülmesinin engelleme olmadan yinelenen bekleme istek çağrılarının ancak bunu serbest bırakmak gerekir <xref:System.Threading.Mutex> sahipliği yayımlamayı gibi birçok kez.  
  
## <a name="abandoned-mutexes"></a>Terk edilmiş zaman uyumu sağlayıcılar  
 Bir iş parçacığı bırakmadan ererse bir <xref:System.Threading.Mutex>, mutex terk söylenir. Mutex koruma kaynak tutarsız bir durumda kalmış olabilir çünkü bu, genellikle ciddi bir programlama hatası gösterir. .NET Framework sürüm 2.0, bir <xref:System.Threading.AbandonedMutexException> mutex edinir sonraki iş parçacığı içinde oluşturulur.  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 ve 1.1, terk edilmiş bir <xref:System.Threading.Mutex> iş durumu ve sonraki kümesine bekliyor iş parçacığı alır sahipliği. Hiçbir iş parçacığı bekliyorsa <xref:System.Threading.Mutex> sinyal verilmiş bir durumda kalır. Hiçbir özel durum oluşur.  
  
 Sistem genelinde mutex söz konusu olduğunda, bırakılan mutex Uygulama aniden (örneğin, Windows Görev Yöneticisi'ni kullanarak) sonlandırıldı olduğunu gösteriyor olabilir.  
  
## <a name="local-and-system-mutexes"></a>Yerel ve sistem zaman uyumu sağlayıcılar  
 Zaman uyumu sağlayıcılar olan iki tür: yerel zaman uyumu sağlayıcılar ve adlandırılmış sistem zaman uyumu sağlayıcılar. Oluşturursanız, bir <xref:System.Threading.Mutex> bir ad kabul eden bir oluşturucu kullanılarak nesne bu ada sahip bir işletim sistemi nesne ilişkilidir. Zaman uyumu sağlayıcılar işletim sistemi tarafından görülebilir ve işlemler etkinliklerini eşitlemek için kullanılan sistem adı. Birden çok oluşturabilirsiniz <xref:System.Threading.Mutex> aynı temsil eden nesneler adlı Sistem mutex ve kullanabileceğiniz <xref:System.Threading.Mutex.OpenExisting%2A> varolan açmak için yöntemini adlı Sistem mutex.  
  
 Yerel mutex yalnızca işleminizin içinde bulunmaktadır. Yerel bir başvuru içeriyor, işlemdeki tüm iş parçacığı tarafından kullanılabilir <xref:System.Threading.Mutex> nesnesi. Her <xref:System.Threading.Mutex> ayrı bir yerel mutex nesnesidir.  
  
### <a name="access-control-security-for-system-mutexes"></a>Sistem zaman uyumu sağlayıcılar için erişim denetimi güvenliği  
 .NET Framework sürüm 2.0 sorgulamak ve adlandırılmış sistem nesneleri için Windows erişim denetimi güvenlik olanağı sağlar. Sistem nesneleri genel olduğundan ve bu nedenle, kendi dışında bir kod tarafından kilitlenip sistem zaman uyumu sağlayıcılar oluşturma andan itibaren koruma önerilir.  
  
 Zaman uyumu sağlayıcılar için erişim denetimi güvenliği hakkında daha fazla bilgi için bkz: <xref:System.Security.AccessControl.MutexSecurity> ve <xref:System.Security.AccessControl.MutexAccessRule> sınıfları <xref:System.Security.AccessControl.MutexRights> numaralandırma, <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, ve <xref:System.Threading.Mutex.OpenExisting%2A> yöntemlerinin <xref:System.Threading.Mutex> sınıfı ve <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> Oluşturucusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [İzleyicileri](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
