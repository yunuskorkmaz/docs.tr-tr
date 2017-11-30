---
title: "Windows'da Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c55caaff3fd96b2791e75a392a9522abfceb22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Windows'da Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma
Tüm iş parçacıklarının Yönetimi aracılığıyla yapılır <xref:System.Threading.Thread> sınıfı, ortak dil çalışma zamanı tarafından oluşturulan iş parçacığı ve kod yürütmek için yönetilen ortamı girin çalışma zamanı dışında oluşturulanlar gibi. Çalışma zamanı kodu yönetilen yürütme ortamını içinde hiç yürütülen tüm iş parçacıkları, işlemindeki izler. Başka bir iş parçacığı izlemez. İş parçacığı, COM birlikte çalışma aracılığıyla yönetilen yürütme ortamı girebilirsiniz, (çalışma zamanı yönetilen nesneler olarak yönetilmeyen world COM nesnelerine kullanıma sunar nedeniyle), COM [DllGetClassObject](https://msdn.microsoft.com/en-us/library/ms680760.aspx) işlevi ve platform çağırma.  
  
 Yönetilmeyen bir iş parçacığı aracılığıyla çalışma zamanı girdiğinde, COM aranabilir sarmalayıcısı o iş parçacığı bir iç yönetilen aramak için iş parçacığı yerel deposu sistem örneğin denetler <xref:System.Threading.Thread> nesnesi. Çalışma zamanı, zaten bulunması durumunda, bu iş parçacığı bilmez. Ancak, bir bulamıyorsanız, çalışma zamanı yeni yapılar <xref:System.Threading.Thread> nesne ve o iş parçacığı iş parçacığı yerel depolama alanına yükler.  
  
 Yönetilen iş parçacığı oluşturma, buna <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> kararlı yönetilen iş parçacığı kimliğidir. İş parçacığı ömrü boyunca, bunu herhangi başka bir iş parçacığı, bu değeri elde uygulama etki alanı ne olursa olsun değer birbiriyle çakışır değil.  
  
> [!NOTE]
>  Bir işletim sistemi **ThreadID** yönetilmeyen bir ana bilgisayar yönetilen ve yönetilmeyen iş parçacıkları arasında ilişki denetleyebildiğinden yönetilen iş parçacığı sabit ilişkisi yoktur. Özellikle, Gelişmiş bir konak Fiber API aynı işletim sistemi iş parçacığına yönetilen çok sayıda iş parçacıklarını zamanlama veya yönetilen bir iş parçacığı farklı işletim sistemi iş parçacıkları arasında taşımak için kullanabilirsiniz.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Yönetilen iş parçacığı oluşturma için Win32 Threading eşleme  
 Aşağıdaki tabloda Win32 iş parçacığı öğeleri kendi yaklaşık çalışma zamanı için eşdeğer eşlemeleri. Bu eşlemenin aynı işlevselliği göstermiyor unutmayın. Örneğin, **TerminateThread** değil çalıştırma **son** yan tümceleri veya kaynakları boşaltın ve önlenemeyen. Ancak, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanarak reddedildi tüm geri alma kodu yürütür ve tüm kaynakları kaldırsa <xref:System.Threading.Thread.ResetAbort%2A>. Varsayımlar işlevleri hakkında yapmadan önce yakından belgelerine okuduğunuzdan emin olun.  
  
|Win32'deki|Ortak dil çalışma zamanı|  
|--------------|------------------------------------|  
|**CreateThread**|Birleşimi **iş parçacığı** ve<xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread'i**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Uyku**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** iş parçacığı tutamacı|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Eşdeğeri|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Eşdeğeri|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Eşdeğeri|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Kapatmak için **CoInitializeEx** (OLE32. DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Yönetilen iş parçacığı ve COM grupların  
 Yönetilen iş parçacığı barındıracak olan belirtmek üzere işaretlenmiş bir [tek iş parçacıklı](http://msdn.microsoft.com/library/windows/desktop/ms680112.aspx) veya [birden çok iş parçacıklı](http://msdn.microsoft.com/library/windows/desktop/ms693421.aspx) grup. (Mimarisi, iş parçacığı oluşturma COM hakkında daha fazla bilgi için bkz [işlemler, iş parçacıkları ve grupların](http://msdn.microsoft.com/library/windows/desktop/ms693344.aspx).) <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>, Ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemlerinin <xref:System.Threading.Thread> sınıfının return ve iş parçacığı Grup durumu atayın. Durum ayarlı değil, <xref:System.Threading.Thread.GetApartmentState%2A> döndürür <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Yalnızca iş parçacığı içinde olduğunda özelliği ayarlanabilir <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> durum; bir iş parçacığı için yalnızca bir kez ayarlanabilir.  
  
 İş parçacığı başlatılmadan önce Grup durumu ayarlanmamış ise iş parçacığı birden çok iş parçacıklı bir grup (MTA) başlatılır. Sonlandırıcı iş parçacığı ve tüm iş parçacıkları tarafından denetlenen <xref:System.Threading.ThreadPool> MTA şunlardır.  
  
> [!IMPORTANT]
>  Uygulama başlangıç koduna için Grup durumu denetlemek için tek yolu uygulamaktır <xref:System.MTAThreadAttribute> veya <xref:System.STAThreadAttribute> yordamı için giriş noktası. .NET Framework 1.0 ve 1.1 <xref:System.Threading.Thread.ApartmentState%2A> özelliği kodun ilk satırı ayarlanabilir. Bu, .NET Framework 2. 0 ' izin verilmiyor.  
  
 Ücretsiz iş parçacıklı Sıralayıcı toplanmış gibi com'a yönetilen nesnelere davranır. Diğer bir deyişle, bunlar herhangi bir COM Grup bir ücretsiz iş parçacıklı şekilde çağrılabilir. Bu ücretsiz iş parçacıklı davranışlar değil yalnızca yönetilen nesneleri öğesinden türetilen bu nesneleridir <xref:System.EnterpriseServices.ServicedComponent> veya <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 Yönetilen dünyada için desteği yoktur <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> bağlamı ve bağlama bağlamı yönetilen örnekleri kullanmadığınız sürece. Kurumsal Hizmetler kullandığınız sonra nesnenizin öğesinden türetilmelidir <xref:System.EnterpriseServices.ServicedComponent> (hangi kendisini türetilir <xref:System.ContextBoundObject>).  
  
 Yönetilen kod COM nesnelerine aradığında, her zaman COM kuralları izler. Diğer bir deyişle, COM Grup proxy'leri ve OLE32 tarafından gerektiği şekilde COM + 1.0 bağlam sarmalayıcıları aracılığıyla çağırır.  
  
## <a name="blocking-issues"></a>Engelleme sorunları  
 Bir iş parçacığı yönetilmeyen kod parçacığında engelledi işletim sistemine yönetilmeyen bir çağrı yaparsa, çalışma zamanı için denetimini olmayacak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> veya <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Durumunda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, çalışma zamanı için iş parçacığı işaretler **Abort** ve yönetilen kod yeniden girdiğinde denetimini alır. Yönetilmeyen engelleme yerine yönetilen engelleme kullanabilmeniz için tercih edilir. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>ve benzeri için tüm esnek olan <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. İş parçacığı tek iş parçacıklı bir grupta ise, iş parçacığı engellendi sırasında Ayrıca, tüm yönetilen engelleme işlemlerini doğru iletileri, grupta pompa.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
 <xref:System.Threading.ThreadState>  
 <xref:System.EnterpriseServices.ServicedComponent>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Monitor>
