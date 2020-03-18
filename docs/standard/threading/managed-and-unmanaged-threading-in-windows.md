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
ms.openlocfilehash: 6ab0cc7c1ec2f7bbc633ac966dd18ab3ea7a395b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127552"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Windows'da yönetilen ve yönetilmeyen iş parçacığı

Tüm iş parçacıklarının yönetimi, <xref:System.Threading.Thread> ortak dil çalışma zamanı tarafından oluşturulan iş parçacıkları ve kodu yürütmek için yönetilen ortamı giren çalışma zamanı dışında oluşturulanlar da dahil olmak üzere sınıf aracılığıyla yapılır. Çalışma zamanı, işlemdeki tüm iş parçacıklarını, yönetilen yürütme ortamında hiç kod yürütmüş olan tüm iş parçacıklarını izler. Diğer iş parçacıklarını izlemez. İş parçacıkları, yönetilen yürütme ortamına COM interop üzerinden girebilir (çalışma zamanı yönetilen nesneleri COM nesnesi olarak yönetilmeyen dünyaya maruz kaldığı için), COM [DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) işlevini ve platform çağrışımını başlatabilir.  
  
 Yönetilmeyen bir iş parçacığı çalışma süresi ne zaman ,örneğin, com çağrılabilir sarıcı üzerinden girdiğinde, sistem iç <xref:System.Threading.Thread> yönetilen bir nesne aramak için iş parçacığı yerel deposunu denetler. Biri bulunursa, çalışma zamanı bu iş parçacığının zaten farkındadır. Ancak, bir tane bulamazsa, çalışma zamanı <xref:System.Threading.Thread> yeni bir nesne oluşturur ve iş parçacığının yerel deposuna yükler.  
  
 Yönetilen iş parçacığı, <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> kararlı yönetilen iş parçacığı tanımlama. İş parçacığınızın ömrü boyunca, bu değeri elde ettiğiniz uygulama etki alanından bağımsız olarak, başka bir iş parçacığının değeriyle çarpışmaz.  
  
> [!NOTE]
> Yönetilen bir ana bilgisayar yönetilen ve yönetilmeyen iş parçacıkları arasındaki ilişkiyi denetleyebilir, çünkü bir işletim sistemi **ThreadId** yönetilen bir iş parçacığı için sabit bir ilişki vardır. Özellikle, gelişmiş bir ana bilgisayar, aynı işletim sistemi iş parçacığına karşı yönetilen birçok iş parçacığı zamanlamak veya yönetilen bir iş parçacığıfarklı işletim sistemi iş parçacıkları arasında taşımak için Fiber API kullanabilirsiniz.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Win32 iş parçacığından yönetilen iş parçacığına eşleme

 Aşağıdaki tablo, Win32 iş parçacığı öğelerini yaklaşık çalışma süresi eşdeğerleriyle eşler. Bu eşlemenin aynı işlevselliği temsil etmediğini unutmayın. Örneğin, **TerminateThread** **son** yan tümceleri yürütmez veya kaynakları boşaltmaz ve engellenemez. Ancak, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> tüm geri alma kodunuzu yürütür, tüm kaynakları geri <xref:System.Threading.Thread.ResetAbort%2A>alır ve 'yi kullanarak reddedilebilir. İşlevsellik hakkında varsayımlarda bulunmadan önce belgeleri yakından okuduğunuzdan emin olun.  
  
|Yılında Win32|Ortak dilde çalışma süresi|  
|--------------|------------------------------------|  
|**Oluşturma İş Parçacığı**|**İplik** ve<xref:System.Threading.ThreadStart>|  
|**Sonlandırma İş parçacığı**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**Askıya Alma İşi**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Uyku**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|Iş parçacığı kolunda **WaitForSingleObject**|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**Çıkma İş Parçacığı**|Eşdeğeri yok|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Eşdeğeri yok|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Eşdeğeri yok|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|**CoInitializeEx'e** Yakın (OLE32. DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Yönetilen dikiş iplikleri ve COM daireler

Yönetilen iş [parçacığı, tek iş parçacığı](/windows/desktop/com/single-threaded-apartments) veya çok iş [parçacığı bir](/windows/desktop/com/multithreaded-apartments) daire barındıracağını belirtmek için işaretlenebilir. (COM iş parçacığı mimarisi hakkında daha fazla bilgi için, [Bkz. Süreçler, İş Parçacıkları ve Daireler.)](/windows/desktop/com/processes--threads--and-apartments) Sınıf <xref:System.Threading.Thread.GetApartmentState%2A> <xref:System.Threading.Thread.SetApartmentState%2A>dönüş <xref:System.Threading.Thread.TrySetApartmentState%2A> ve bir <xref:System.Threading.Thread> iş parçacığının daire durumunu atama yöntemleri, ve yöntemleri. Durum ayarlanmadıysa, <xref:System.Threading.Thread.GetApartmentState%2A> döndürür. <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>  
  
 Özellik yalnızca iş parçacığı <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> durumdayken ayarlanabilir; bir iş parçacığı için yalnızca bir kez ayarlanabilir.  
  
 İş parçacığı başlatılmadan önce daire durumu ayarlanmazsa, iş parçacığı çok iş parçacığı daire (MTA) olarak başlatılır. Sonlandırıcı iş parçacığı ve kontrol <xref:System.Threading.ThreadPool> edilen tüm iş parçacıkları MTA'dır.  
  
> [!IMPORTANT]
> Uygulama başlangıç kodu için, daire durumunu kontrol etmenin <xref:System.MTAThreadAttribute> tek <xref:System.STAThreadAttribute> yolu giriş noktası yordamını veya .NET Framework 1.0 ve 1.1'de <xref:System.Threading.Thread.ApartmentState%2A> özellik ilk kod satırı olarak ayarlanabilir. Bu,.NET Framework 2.0'da izin verilmez.  
  
 COM'a maruz kalan yönetilen nesneler, serbest dişli mareşalini toplamış gibi düşünür. Başka bir deyişle, herhangi bir COM daireden serbest dişli bir şekilde çağrılabilir. Bu serbest iş parçacığı davranışı sergilemeyen tek yönetilen nesneler, bu <xref:System.EnterpriseServices.ServicedComponent> nesnelerden <xref:System.Runtime.InteropServices.StandardOleMarshalObject>türeyen nesnelerdir veya.  
  
 Yönetilen dünyada, bağlamları ve içeriğe bağlı yönetilen örnekleri <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> kullanmadığınız sürece destek yoktur. Kurumsal Hizmetler kullanıyorsanız, nesnenizin türetilmiş <xref:System.EnterpriseServices.ServicedComponent> olması gerekir <xref:System.ContextBoundObject>(kendisi türetilmiştir).  
  
 Yönetilen kod COM nesnelerine seslendiğinde, her zaman COM kurallarına uyar. Başka bir deyişle, Com daire yakınlık ve COM + 1.0 bağlam sarmalayıcıları aracılığıyla OLE32 tarafından dikte çağırır.  
  
## <a name="blocking-issues"></a>Engelleme sorunları  

Bir iş parçacığı, iş parçacığının yönetilmeyen kodda iş parçacığının denetimini engelleyen işletim sistemine yönetilmeyen bir arama yaparsa, çalışma zamanı iş parçacığının denetimini almaz <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> veya <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Runtime durumunda, çalışma süresi **Abort** için iş parçacığı işaretler ve yönetilen kodu yeniden girdiğinde bunun denetimini alır. Yönetilmeyen engelleme yerine yönetilen engellemeyi kullanmanız tercih edilir. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>, , , ve <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> benzeri <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>tüm duyarlı ve . Ayrıca, iş parçacığınız tek dişli bir dairedeyse, iş parçacığınız engellenirken tüm bu yönetilen engelleme işlemleri dairenizde doğru şekilde iletipompalar.  

## <a name="threads-and-fibers"></a>İplikler ve lifler

.NET iş parçacığı modeli [lifleri](/windows/desktop/procthread/fibers)desteklemez. Lifler kullanılarak uygulanan herhangi bir yönetilmeyen işlevi içine çağırmak gerekir. Bu tür çağrılar .NET çalışma zamanının çökmesine neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>
- <xref:System.Threading.ThreadState>
- <xref:System.EnterpriseServices.ServicedComponent>
- <xref:System.Threading.Thread>
- <xref:System.Threading.Monitor>
