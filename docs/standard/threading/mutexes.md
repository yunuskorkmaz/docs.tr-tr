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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127564"
---
# <a name="mutexes"></a>Zaman Uyumu Sağlayıcılar
Bir kaynağa <xref:System.Threading.Mutex> özel erişim sağlamak için bir nesne kullanabilirsiniz. Sınıf <xref:System.Threading.Mutex> sınıftan <xref:System.Threading.Monitor> daha fazla sistem kaynakları kullanır, ancak uygulama etki alanı sınırları arasında marshaled olabilir, birden çok bekleme ile kullanılabilir ve farklı işlemlerde iş parçacıkları eşitlemek için kullanılabilir. Yönetilen eşitleme mekanizmalarının karşılaştırılması için, [Eşitleme İlkellerine Genel Bakış'a](../../../docs/standard/threading/overview-of-synchronization-primitives.md)bakın.  
  
 Kod örnekleri için, oluşturucular <xref:System.Threading.Mutex.%23ctor%2A> için başvuru belgelerine bakın.  
  
## <a name="using-mutexes"></a>Mutexes kullanma  
 Bir iş <xref:System.Threading.WaitHandle.WaitOne%2A> parçacığı sahiplik istemek için bir mutex yöntemi çağırır. Mutex kullanılabilir olana veya isteğe bağlı zaman aşımı aralığı bitene kadar arama blokları. Bir mutex durumu hiçbir iş parçacığı sahibi ise sinyal verilir.  
  
 Bir iş parçacığı yöntemini <xref:System.Threading.Mutex.ReleaseMutex%2A> çağırarak bir mutex bültenleri. Mutexes iplik afinite var; diğer bir şey, mutex yalnızca ona sahip olan iş parçacığı tarafından serbest bırakılabilir. Bir iş parçacığı sahibi olmayan bir mutex salgılarsa, iş parçacığına bir mitex <xref:System.ApplicationException> atılır.  
  
 <xref:System.Threading.Mutex> <xref:System.Threading.WaitHandle>Sınıf türetilmiştir çünkü, statik <xref:System.Threading.WaitHandle.WaitAll%2A> veya <xref:System.Threading.WaitHandle.WaitAny%2A> diğer bekleme <xref:System.Threading.WaitHandle> tutamaçları ile <xref:System.Threading.Mutex> birlikte bir sahipliğini istemek için yöntemler de arayabilirsiniz.  
  
 Bir iş parçacığı, <xref:System.Threading.Mutex>bu iş parçacığı, yürütme engellemeden yinelenen bekleme isteği aramalarında aynı <xref:System.Threading.Mutex> belirtebilirsiniz sahibi; ancak, sahiplik <xref:System.Threading.Mutex> serbest bırakmak için birçok kez serbest bırakmak gerekir.  
  
## <a name="abandoned-mutexes"></a>Terk Edilmiş Mutexes  
 Bir iş parçacığı bir <xref:System.Threading.Mutex>serbest bırakmadan sona ererse, mutex terk olduğu söyleniyor. Bu genellikle ciddi bir programlama hatası gösterir, çünkü mutex'in koruduğu kaynak tutarsız bir durumda bırakılabilir. .NET Framework sürüm 2.0'da, mutex'i alan bir sonraki iş parçacığına bir <xref:System.Threading.AbandonedMutexException> atılmıştır.  
  
> [!NOTE]
> .NET Framework sürümleri1.0 ve 1.1'de <xref:System.Threading.Mutex> terk edilmiş bir durum sinyal durumuna ayarlanır ve bir sonraki bekleme iş parçacığı sahiplik alır. İş parçacığı beklemiyorsa, <xref:System.Threading.Mutex> sinyalli durumda kalır. Özel durum oluşturulmaz.  
  
 Sistem çapında bir mutex durumunda, terk edilmiş bir mutex bir uygulama aniden (örneğin, Windows Görev Yöneticisi kullanılarak) sonlandırıldığını gösterebilir.  
  
## <a name="local-and-system-mutexes"></a>Yerel ve Sistem Mutexes  
 Mutexes iki tür vardır: yerel mutexes ve adlı sistem mutexes. Bir <xref:System.Threading.Mutex> ad kabul eden bir oluşturucu kullanarak bir nesne oluşturursanız, bu addaki bir işletim sistemi nesnesi ile ilişkilidir. Adlandırılmış sistem mutexes işletim sistemi boyunca görülebilir ve süreçlerin faaliyetlerini senkronize etmek için kullanılabilir. Aynı adlı <xref:System.Threading.Mutex> sistem mutex temsil eden birden çok nesne oluşturabilir <xref:System.Threading.Mutex.OpenExisting%2A> ve varolan bir adlandırılmış sistem mutex açmak için yöntemi kullanabilirsiniz.  
  
 Yerel bir mutex yalnızca işlem içinde var. İşleminizdeki yerel <xref:System.Threading.Mutex> nesneye başvuru olan herhangi bir iş parçacığı tarafından kullanılabilir. Her <xref:System.Threading.Mutex> nesne ayrı bir yerel mutex olduğunu.  
  
### <a name="access-control-security-for-system-mutexes"></a>Sistem Mutexes için Erişim Kontrol Güvenliği  
 .NET Framework sürüm 2.0, adlandırılmış sistem nesneleri için Windows erişim denetimi güvenliğini sorgulama ve ayarlama olanağı sağlar. Sistem nesneleri genel olduğundan ve bu nedenle kendi kodla kilitlenebilir, çünkü oluşturma andan itibaren sistem mutexes korunması önerilir.  
  
 Mutexes için erişim denetimi güvenliği hakkında <xref:System.Security.AccessControl.MutexSecurity> <xref:System.Security.AccessControl.MutexAccessRule> bilgi <xref:System.Security.AccessControl.MutexRights> için, sınıfları, <xref:System.Threading.Mutex.GetAccessControl%2A>numaralandırma, , <xref:System.Threading.Mutex.SetAccessControl%2A>ve <xref:System.Threading.Mutex.OpenExisting%2A> <xref:System.Threading.Mutex> sınıfın <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> yöntemleri ve oluşturucu bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [İş parçacıkları ve iş parçacığı](threads-and-threading.md)
- [İş Parçacığı Oluşturma](index.md)
