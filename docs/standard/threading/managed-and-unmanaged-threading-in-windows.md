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
ms.openlocfilehash: da32d514b19424487cebc1d113388cfa9a2dbdf0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913236"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Windows 'da yönetilen ve yönetilmeyen iş parçacığı

Tüm iş parçacıklarının yönetimi, ortak dil çalışma <xref:System.Threading.Thread> zamanı tarafından oluşturulan iş parçacıkları ve kodu yürütmek için yönetilen ortama girerken çalışma zamanının dışında oluşturulanlar dahil olmak üzere sınıfı aracılığıyla yapılır. Çalışma zamanı, işlem sırasında yönetilen yürütme ortamında kod yürüten tüm iş parçacıklarını izler. Diğer iş parçacıklarını izlemez. İş parçacıkları, yönetilen yürütme ortamını COM birlikte çalışma aracılığıyla girebilir (çalışma zamanı yönetilen nesneleri yönetilmeyen dünyayı COM nesneleri olarak kullanıma sunduğundan), COM [DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) işlevini ve platform çağrılmasını sağlar.  
  
 Yönetilmeyen bir iş parçacığı, örneğin, com çağrılabilir bir sarmalayıcı aracılığıyla çalışma zamanına girdiğinde, sistem, iç yönetilen <xref:System.Threading.Thread> bir nesneyi aramak için iş parçacığının yerel depo parçacığını denetler. Bir tane bulunursa, çalışma zamanı bu iş parçacığının zaten farkında olur. Ancak, bir tane bulamazsa, çalışma zamanı yeni <xref:System.Threading.Thread> bir nesne oluşturur ve bu iş parçacığının iş parçacığı yerel deposuna yüklenir.  
  
 Yönetilen iş parçacığında, <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> kararlı yönetilen iş parçacığı kimliğidir. İş parçacığınız kullanım ömrü boyunca, bu değeri aldığınız uygulama etki alanından bağımsız olarak diğer herhangi bir iş parçacığından elde etmeyecektir.  
  
> [!NOTE]
> Yönetilmeyen bir konak yönetilen ve yönetilmeyen iş parçacıkları arasındaki ilişkiyi denetleyebildiğinden, bir işletim sistemi **tehdit** , yönetilen bir iş parçacığı ile sabit ilişkiye sahip değildir. Özellikle, gelişmiş bir ana bilgisayar aynı işletim sistemi iş parçacığında birçok yönetilen iş parçacığını zamanlamak veya yönetilen bir iş parçacığını farklı işletim sistemi iş parçacıkları arasında taşımak için fiber API 'YI kullanabilir.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Win32 iş parçacığından yönetilen iş parçacığına eşleme

 Aşağıdaki tablo, Win32 iş parçacığı öğelerini yaklaşık çalışma zamanına eşit olarak eşler. Bu eşlemenin aynı işlevselliği temsil etmediği unutulmamalıdır. Örneğin, **TerminateThread** **finally** yan tümceleri çalıştırmaz veya kaynakları serbest bırakırsanız ve engellenemez. Ancak tüm geri alma kodunuzu <xref:System.Threading.Thread.ResetAbort%2A> yürütür,tümkaynaklarıgerikazanırvekullanılarakreddedilebilir.<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> İşlevlerle ilgili varsayımlar yapmadan önce belgeleri okuduğunuzdan emin olun.  
  
|Win32 'te|Ortak dil çalışma zamanında|  
|--------------|------------------------------------|  
|**CreateThread**|**Iş parçacığının** birleşimi ve<xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread Iş parçacığı**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Kullanılmadığında**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|İş parçacığı tanıtıcısından **WaitForSingleObject**|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Eşdeğer değil|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Eşdeğer değil|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Eşdeğer değil|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|**CoInitializeEx** 'a kapat (Ole32. DOSYASıNı|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Yönetilen iş parçacıkları ve com apartmanlar

Yönetilen bir iş parçacığı, [tek iş parçacıklı](/windows/desktop/com/single-threaded-apartments) veya çok [iş parçacıklı](/windows/desktop/com/multithreaded-apartments) bir grubu barındıracak olduğunu göstermek için işaretlenebilir. (COM iş parçacığı mimarisi hakkında daha fazla bilgi için bkz. [süreçler, Iş parçacıkları ve apartmanlar](/windows/desktop/com/processes--threads--and-apartments).) Sınıfının, <xref:System.Threading.Thread.SetApartmentState%2A> ve<xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemleri, bir iş parçacığının Grup durumunu döndürür ve atar. <xref:System.Threading.Thread.GetApartmentState%2A> <xref:System.Threading.Thread> Durum ayarlanmamışsa, <xref:System.Threading.Thread.GetApartmentState%2A> döndürür <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Özelliği yalnızca iş parçacığı <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> durumundayken ayarlanabilir; bir iş parçacığı için yalnızca bir kez ayarlanabilir.  
  
 Grup durumu, iş parçacığı başlatılmadan önce ayarlanmamışsa, iş parçacığı, çok iş parçacıklı apartman (MTA) olarak başlatılır. Sonlandırıcı iş parçacığı ve tarafından <xref:System.Threading.ThreadPool> denetlenen tüm iş parçacıkları MTA.  
  
> [!IMPORTANT]
> Uygulama başlangıç kodu için, grup durumunu denetlemek için tek yol, <xref:System.MTAThreadAttribute> <xref:System.STAThreadAttribute> veya öğesini giriş noktası yordamına uygulamaktır. .NET Framework 1,0 ve 1,1 ' de, <xref:System.Threading.Thread.ApartmentState%2A> özellik ilk kod satırı olarak ayarlanabilir. .NET Framework 2,0 ' de buna izin verilmez.  
  
 COM 'a sunulan yönetilen nesneler, serbest iş parçacıklı Sıralayıcı 'nın toplanmamış gibi davranır. Diğer bir deyişle, ücretsiz iş parçacıklı bir şekilde herhangi bir COM grubundan çağrılabilir. Bu serbest iş parçacıklı davranışı sergilemeyen tek yönetilen nesneler, veya <xref:System.EnterpriseServices.ServicedComponent> <xref:System.Runtime.InteropServices.StandardOleMarshalObject>' den türetilen nesnelerdir.  
  
 Yönetilen dünyada, bağlamlar ve bağlam bağlantılı yönetilen örnekler kullanmadığınız <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> durumlar için destek yoktur. Kurumsal Hizmetler kullanıyorsanız, nesnenizin ' den <xref:System.EnterpriseServices.ServicedComponent> türetmeniz gerekir (Bu, öğesinden <xref:System.ContextBoundObject>türetilir).  
  
 Yönetilen kod COM nesnelerine aradığında, her zaman COM kurallarını izler. Diğer bir deyişle, OLE32 tarafından dikte edildiği gibi COM apartman proxy 'leri ve COM+ 1,0 bağlam sarmalayıcıları aracılığıyla çağrı yapılır.  
  
## <a name="blocking-issues"></a>Sorunları engelleme  

Bir iş parçacığı, yönetilmeyen koddaki iş parçacığını engelleyen işletim sistemine yönetilmeyen bir çağrı yapıyorsa, çalışma zamanı veya <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>için denetimi almaz. Durumunda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, çalışma zamanı, iş parçacığını **iptal** için işaretler ve yönetilen kodu yeniden girdiğinde bunun denetimini alır. Yönetilmeyen engelleme yerine yönetilen engellemeyi kullanmanız tercih edilir. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType><xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> ,,<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> , ,<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>,, vb.<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>tüm ve için tamamen yanıt veriyor. <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> Ayrıca, iş parçacığın tek iş parçacıklı bir apartman halinde olması halinde, iş parçacığı engellenirken tüm bu yönetilen engelleyici işlemler, ağınızdaki iletileri doğru bir şekilde kaklacaktır.  

## <a name="threads-and-fibers"></a>İş parçacıkları ve fiberler

.NET iş parçacığı modeli [lifleri görmeyin](/windows/desktop/procthread/fibers)'yi desteklemez. Fibers kullanılarak uygulanan hiçbir yönetilmeyen işlevi çağırmamalıdır. Bu tür çağrılar, .NET çalışma zamanının kilitlenmesine neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>
- <xref:System.Threading.ThreadState>
- <xref:System.EnterpriseServices.ServicedComponent>
- <xref:System.Threading.Thread>
- <xref:System.Threading.Monitor>
