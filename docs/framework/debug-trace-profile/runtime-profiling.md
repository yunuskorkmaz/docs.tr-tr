---
title: "Çalışma Zamanı Profili Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 876635cfe0349c734a61dcc827a6f9594bb2a5d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-profiling"></a>Çalışma Zamanı Profili Oluşturma
Profil oluşturma, tüm geliştirme ve dağıtım senaryosunda performans verilerini toplama bir yöntemdir. Bu bölüm, geliştiriciler ve uygulama performansı hakkında bilgi toplamak istediğiniz sistem yöneticileri için değildir.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Performans İzleyicisi'ni (Perfmon.exe) kullanarak performans izleme  
 Performans İzleyicisi'ni profiline kullanmak için kolay bir araçtır, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uygulama. Performans İzleyicisi'ni grafik ortak dil çalışma zamanı ile yüklü .NET Framework performans sayaçları bulunan verileri temsil eder ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Bu sayaçlar, her şeyi bellek yönetimi tam zamanında (JIT) derleyici performansı izlemek için kullanılabilir. Bunlar, kaynaklar hakkında uygulamanız tarafından kullanılan, uygulamanızın performansını dolaylı bir ölçü olduğu söyleyin. Bu sayaçlar, uygulamanızın dahili olarak nasıl çalıştığını anlamak için kullanın.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Windows Vista ve sonraki sürümlerde Perfmon.exe çalıştırmak için  
  
1.  Komut isteminde **perfmon**. **Performans İzleyicisi** konsolu görüntülenir.  
  
2.  İçinde **izleme araçları** klasörünü tıklatın **Performans İzleyicisi'ni**.  
  
3.  Performans İzleyicisi araç çubuğunda **Ekle** simgesi (artı işareti), yoksa. Mevcut değilse, İzleyicisi penceresinde sağ tıklayın ve seçin **Sayaç Ekle** seçeneği.  
  
     Bu açılır **Sayaç Ekle** iletişim kutusu. **Kullanılabilir sayaçlar** liste kutusu kullanılabilir performans nesneleri görüntüler. Bellek yönetimi dahil olmak üzere, .NET Framework uygulamaları için önceden tanımlanmış nesne sayısı vardır (**.NET CLR bellek**), birlikte çalışabilirlik (**.NET CLR Interop**), özel durum işleme (**.NET CLR özel durumları**) ve çoklu iş parçacığı kullanımı (**.NET CLR LocksAndThreads**). Her performans nesnesi bir dizi bireysel performans sayaçları içerir. Performans İzleyicisi'nde kullanılabilen performans sayaçlarının listesi için bkz: [performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4.  Destekliyorsa bireysel performans sayaçları listesini görüntülemek için bir performans nesne adının yanındaki onay kutusunu seçin.  
  
5.  Görüntülemek istediğiniz performans sayacı'ı tıklatın.  
  
6.  İçinde **seçili nesnenin örnekleri** liste kutusunda, tıklatın  **\<tüm örneklerini >** ortak dil çalışma zamanı performans sayacı genel izlemek istediğiniz belirtmek için (diğer bir deyişle, bir Sistem genelinde).  
  
     veya  
  
     İçinde **seçili nesnenin örnekleri** liste kutusunda, bu uygulama için performans sayacı izlemek için bir uygulama adına tıklayın.  
  
     Çalışma zamanı birden fazla sürümünü ayırt ya da aynı ada sahip birden çok uygulama belirsizliğini ortadan kaldırmak için bir kayıt defteri anahtarını değiştirmeniz gerekir. Daha fazla bilgi için bkz: [performans sayaçları ve işlem içi yan yana uygulamalar](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Performans konsolu çalışırken yeni performans sayaçları yüklendiğinde, durdurmak ve yeni sayaçları görünür hale getirmek için Performans konsolu yeniden başlatın.  
  
 Bir bölgede ya da bir uzak paylaşımda mevcut bir derlemeyi profil istiyorsanız, uzak derleme performans sayaçlarını çalıştıran bilgisayarda tam güven sahip olduğundan emin olun. Derleme yeterli güven yoksa, performans sayaçlarını çalışmaz. Farklı bölgelere güven verme hakkında daha fazla bilgi için bkz: [Caspol.exe (kod erişim güvenliği ilke aracı)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  Üretileceği sistemlerde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] olan yüklü, Performans İzleyicisi'ni verileri performans sayaçları için bazı kategorilerde gibi görüntülemeyebilir **.NET CLR veri** ve **.NET CLR ağ**, için kullanılarak geliştirilen uygulamaları [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]. Bu durumda, ekleyerek bu verileri görüntülemek için Performans İzleyicisi'ni yapılandırabilirsiniz [ \<forcePerformanceCounterUniqueSharedMemoryReads >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) uygulamanın yapılandırma dosyasına öğesi.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Okuma ve performans sayaçları program aracılığıyla oluşturma  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Performans konsolunda kullanılabilir aynı performans bilgileri programlı olarak erişmek için kullanabileceğiniz sınıflar sağlar. Bu sınıfları, özel performans sayaçları oluşturmak için de kullanabilirsiniz. Aşağıdaki tabloda performansı sağlanan sınıfları izleme bazıları açıklanmaktadır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Bir Windows NT performans sayacı bileşenini temsil eder. Bu sınıf, önceden tanımlanmış veya özel sayaçlar okumak ve özel sayaçlar (yazma) performans verilerini yayınlamak için kullanın.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Sayaçları ve bilgisayardaki sayaçları kategorilerinin etkileşimde için çeşitli yöntemler sağlar.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Bir yükleyici için belirtir `PerformanceCounter` bileşeni.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Hesaplama formülü belirtir `NextValue` yöntemi için bir `PerformanceCounter`.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)
