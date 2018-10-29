---
title: Windows'da Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma
ms.date: 10/24/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- threading [.NET], managed
- threads and fibers [.NET]
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34bd959890717a16df80d3870099757dd7400943
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199740"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Windows yönetilen ve yönetilmeyen iş parçacığı oluşturma

Tüm iş parçacıklarının Yönetim aracılığıyla gerçekleştirilir <xref:System.Threading.Thread> sınıfı, ortak dil çalışma zamanı tarafından oluşturulan iş parçacığı ve kodu yürütmek için yönetilen ortamı girin çalışma zamanı dışında oluşturulanlar gibi. Çalışma zamanı, yönetilen yürütme ortamında kod yürütülen hiç olmadığı kadar tüm iş parçacıkları, işlemindeki izler. Diğer iş parçacıklarını izlemez. İş parçacıkları, COM birlikte çalışma aracılığıyla yönetilen yürütme ortamında girebilirsiniz, (çalışma zamanı yönetilen nesneleri yönetilmeyen dünya çapında COM nesneleri olarak kullanıma sunduğundan), COM [DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) işlevi ve platform çağırma.  
  
 Yönetilmeyen bir iş parçacığı, çalışma zamanı aracılığıyla girdiğinde, COM çağrılabilir sarmalayıcısı bir iç yönetilen için aramak için bu iş parçacığının iş parçacığı yerel deposu sistem gibi denetler <xref:System.Threading.Thread> nesne. Çalışma zamanı, zaten bulunması durumunda bu iş parçacığı farkındadır. Ancak, bir bulamıyorsanız, çalışma zamanı yeni derlemeler <xref:System.Threading.Thread> nesne ve bu iş parçacığının iş parçacığı yerel deposuna yükler.  
  
 Yönetilen iş parçacığı oluşturma, buna <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> kararlı yönetilen iş parçacığı kimliğidir. İş parçacığının ömrü boyunca, bu değeri elde etmek uygulama etki alanı bağımsız olarak diğer tüm iş parçacığından değerle birbiriyle çakışır değil.  
  
> [!NOTE]
>  Bir işletim sistemi **ThreadID** yönetilmeyen bir konak yönetilen ve yönetilmeyen iş parçacıkları arasındaki ilişkiyi kontrol edebildiğiniz yönetilen iş parçacığı sabit ilişkisi yoktur. Özellikle karmaşık bir ana bilgisayar aynı işletim sistemi iş parçacığı birçok yönetilen iş parçacıklarını zamanlama veya yönetilen bir diziyi farklı işletim sistemleri iş parçacıkları arasında Fiber API'yi kullanabilirsiniz.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Yönetilen için iş parçacığı Win32 threading eşleme

 Aşağıdaki tabloda, yaklaşık çalışma zamanı için eşdeğer Win32 iş parçacığı öğeleri eşleştirir. Bu eşleme aynı işlevselliği kapsamadığını unutmayın. Örneğin, **TerminateThread** değil çalıştırma **son** yan tümceleri veya kaynakları boşaltmaya ve önlenemeyen. Ancak, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> tüm geri alma kodu yürütür, tüm kaynaklarını geri kazanır ve kullanarak reddedildi <xref:System.Threading.Thread.ResetAbort%2A>. İşlevler hakkında varsayımlar yapmadan önce yakından belgeleri okuduğunuzdan emin olun.  
  
|Win32'de|Ortak dil çalışma zamanı|  
|--------------|------------------------------------|  
|**CreateThread**|Birleşimi **iş parçacığı** ve <xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Uyku**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** iş parçacığı tutamacı|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Eşdeğeri|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Eşdeğeri|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Eşdeğeri|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Kapatmak için **CoInitializeEx** (OLE32. DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Yönetilen iş parçacıkları ve COM apartmanlar

Onu barındıracağını belirtmek için bir yönetilen iş parçacığı işaretli bir [tek iş parçacıklı](/windows/desktop/com/single-threaded-apartments) veya [birden çok iş parçacıklı](/windows/desktop/com/multithreaded-apartments) grup. (Mimarisi, iş parçacığı COM hakkında daha fazla bilgi için bkz: [işlemler, iş parçacıkları ve apartmanlar](/windows/desktop/com/processes--threads--and-apartments).) <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>, Ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemlerinin <xref:System.Threading.Thread> sınıfı döndürür ve bir iş parçacığı grubu durumunu atayın. Durumu ayarlanmamış ise <xref:System.Threading.Thread.GetApartmentState%2A> döndürür <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Yalnızca iş parçacığı içinde olduğunda özellik ayarlanabilir <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> durum; bir iş parçacığı için yalnızca bir kez ayarlanabilir.  
  
 İş parçacığı başlatılmadan önce Grup durumu ayarlanmazsa, iş parçacığı bir çok iş parçacıklı grubun (MTA) başlatılır. Sonlandırıcı iş parçacığı ve tüm iş parçacıkları tarafından denetlenen <xref:System.Threading.ThreadPool> MTA olan.  
  
> [!IMPORTANT]
>  Uygulama başlangıç koduna için Grup durumu denetlemek için tek yolu uygulamaktır <xref:System.MTAThreadAttribute> veya <xref:System.STAThreadAttribute> yordamı için giriş noktası. .NET Framework 1.0 ve 1.1, <xref:System.Threading.Thread.ApartmentState%2A> özelliği ilk kod satırı ayarlanabilir. Bu, .NET Framework 2.0 sürümünde izin verilmez.  
  
 Ücretsiz iş parçacıklı Sıralayıcı toplanmış com'a yönetilen nesneleri bilgisayarmış gibi. Diğer bir deyişle, bunlar herhangi bir COM Grup serbest iş parçacıklı bir şekilde çağrılabilir. Bu ücretsiz iş parçacıklı eylemi sergilemez yalnızca yönetilen nesneler türetilen bu nesnelerdir <xref:System.EnterpriseServices.ServicedComponent> veya <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 Yönetilen dünyada için desteği yoktur <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> bağlamları ve bağlam bağlı yönetilen örnekleri kullanmadığınız sürece. Kurumsal Hizmetler kullandığınız sonra nesnenizin öğesinden türetilmelidir <xref:System.EnterpriseServices.ServicedComponent> (hangi kendisini türetilir <xref:System.ContextBoundObject>).  
  
 Her zaman yönetilen kod için COM nesneleri çağırdığında, COM kurallara uygun olmalıdır. Diğer bir deyişle, COM grubu proxy'leri ve OLE32 tarafından belirlenen COM + 1.0 bağlam sarmalayıcılar aracılığıyla çağırır.  
  
## <a name="blocking-issues"></a>Engelleme sorunları  

Bir iş parçacığı işletim sisteminin, yönetilmeyen kod parçacığında engelledi yönetilmeyen bir çağrı yaparsa, çalışma zamanı için denetimini olmayacak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> veya <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Durumunda, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, çalışma zamanı iş parçacığı işaretler **iptal** ve yönetilen kod yeniden girdiğinde denetimini alır. Bu, yönetilmeyen engelleme yerine yönetilen engelleme kullanabilmeniz için tercih edilir. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>ve benzeri için tüm hızlı yanıt veriyorlar <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Bir tek iş parçacıklı apartmanda, iş parçacığı ise, iş parçacığı engellenir sırasında Ayrıca, bu yönetilen tüm engelleme işlemleri doğru iletileri, grupta pompa.  

## <a name="threads-and-fibers"></a>İş parçacıkları ve iyileştirmesini

İş parçacığı modeli .NET desteklemediği [iyileştirmesini](/windows/desktop/procthread/fibers). İyileştirmesini kullanılarak uygulanan herhangi bir yönetilmeyen işlevine çağırmalıdır değil. Böyle çağrılar .NET çalışma zamanı bir çökmesine neden neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
- <xref:System.Threading.ThreadState>  
- <xref:System.EnterpriseServices.ServicedComponent>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.Monitor>
