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
ms.openlocfilehash: 488bccea7d0a8870891859482bece018bf4bda0e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744708"
---
# <a name="mutexes"></a>Zaman Uyumu Sağlayıcılar
Kullanabileceğiniz bir <xref:System.Threading.Mutex> özel bir kaynağa erişim sağlamak için nesne. <xref:System.Threading.Mutex> Sınıfın kullandığı değerinden daha fazla sistem kaynakları <xref:System.Threading.Monitor> sınıfı, ancak uygulama etki alanı sınırları ötesinde sıralanır, birden çok bekler ile kullanılabilir ve farklı işlemlerdeki iş parçacığı eşitleme için kullanılabilir. Yönetilen eşitleme mekanizmaları bir karşılaştırması için bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Kod örnekleri için başvuru belgelerine bakın <xref:System.Threading.Mutex.%23ctor%2A> oluşturucular.  
  
## <a name="using-mutexes"></a>Mutex'leri kullanma  
 Bir iş parçacığı çağrı <xref:System.Threading.WaitHandle.WaitOne%2A> bir mutex isteği sahipliği için yöntemi. Çağrı blokları mutex kullanılabilir hale gelene kadar veya kadar isteğe bağlı zaman aşımı aralığı sona erdiğinde. Bir mutex durumu, iş parçacığının sahip olduğu, sinyal.  
  
 Bir iş parçacığı bir mutex çağırarak serbest kendi <xref:System.Threading.Mutex.ReleaseMutex%2A> yöntemi. İş parçacığı benzeşimini Mutex'leri sahip; diğer bir deyişle, mutex sahibi yalnızca iş parçacığı tarafından serbest bırakılabilir. Bir iş parçacığı sahibi olmadığı, bir mutex yayımlarsa bir <xref:System.ApplicationException> iş parçacığı oluşturulur.  
  
 Çünkü <xref:System.Threading.Mutex> sınıf türetilir <xref:System.Threading.WaitHandle>, statik de çağırabilirsiniz <xref:System.Threading.WaitHandle.WaitAll%2A> veya <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemlerinin <xref:System.Threading.WaitHandle> isteği sahipliğini için bir <xref:System.Threading.Mutex> bekleme tanıtıcıları diğer birlikte.  
  
 Bir iş parçacığı sahipse bir <xref:System.Threading.Mutex>, iş parçacığı aynı belirtebilirsiniz <xref:System.Threading.Mutex> ; yürütme engelleme olmadan yinelenen bekleme isteği çağrılarındaki ancak bunu serbest bırakmalısınız <xref:System.Threading.Mutex> sahipliğini serbest olarak birçok kez.  
  
## <a name="abandoned-mutexes"></a>Terk edilmiş Mutex'leri  
 Bir iş parçacığı bırakmadan sona ererse bir <xref:System.Threading.Mutex>, mutex terk edilir. Mutex koruma kaynak tutarsız bir durumda kalmış olabilir çünkü bu genellikle programlama ve ciddi bir hata gösterir. .NET Framework sürüm 2.0, bir <xref:System.Threading.AbandonedMutexException> mutex'i elde eden sonraki iş parçacığı oluşturulur.  
  
> [!NOTE]
>  .NET Framework sürümleri 1.0 ve 1.1 terk edilmiş bir içinde <xref:System.Threading.Mutex> iş parçacığı alır sahipliği bekliyor sinyal verilmiş duruma dönmesine ve sonraki kümesi. İş parçacığı bekliyorsa <xref:System.Threading.Mutex> bir sinyal durumunda kalır. Hiçbir özel durum oluşturulur.  
  
 Sistem genelinde mutex'i söz konusu olduğunda, Uygulama aniden (örneğin, Windows Görev Yöneticisi'ni kullanarak) sonlandırıldı, bırakılan mutex gösterebilir.  
  
## <a name="local-and-system-mutexes"></a>Yerel ve sistem Mutex'leri  
 Mutex'leri olmak üzere iki tür: yerel mutex'leri ve adlandırılmış sistem mutex'leri. Oluşturursanız, bir <xref:System.Threading.Mutex> bir ad kabul eden oluşturucu kullanılarak nesne bu ada sahip bir işletim sistemi nesne ilişkilidir. Mutex'leri boyunca işletim sistemi tarafından görülebilir ve işlemlerin etkinlikleri eşitlemek için kullanılan sistem adı. Birden çok oluşturabilirsiniz <xref:System.Threading.Mutex> aynı temsil eden nesneleri adlı Sistem mutex ve kullanabileceğiniz <xref:System.Threading.Mutex.OpenExisting%2A> sistem mutex adlı varolan bir açmak için yöntemi.  
  
 Yerel bir mutex yalnızca, işlem içinde bulunur. Yerel bir başvurusu olan işlem herhangi bir iş parçacığı tarafından kullanılabilir <xref:System.Threading.Mutex> nesne. Her <xref:System.Threading.Mutex> ayrı bir yerel mutex nesnedir.  
  
### <a name="access-control-security-for-system-mutexes"></a>Sistem Mutex'leri için erişim denetimi güvenliği  
 .NET Framework sürüm 2.0 sorgulamak ve ayarlamak için adlandırılmış sistem nesneleri Windows erişim denetimi güvenlik olanağı sağlar. Sistem nesneleri geneldir ve bu nedenle kendi dışındaki kod tarafından kilitlenip çünkü sistem mutex'leri oluşturulduğu andan itibaren koruma önerilir.  
  
 Mutex'leri için erişim denetim güvenliği hakkında daha fazla bilgi için bkz. <xref:System.Security.AccessControl.MutexSecurity> ve <xref:System.Security.AccessControl.MutexAccessRule> sınıfları <xref:System.Security.AccessControl.MutexRights> numaralandırma <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, ve <xref:System.Threading.Mutex.OpenExisting%2A> yöntemlerinin <xref:System.Threading.Mutex> sınıfı ve <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> Oluşturucusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [İzleyiciler](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
