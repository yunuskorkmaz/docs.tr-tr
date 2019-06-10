---
title: Çalışma Zamanı Profili Oluşturma
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c56018c61e5566043fb2b9ba8bbee042093f12
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758151"
---
# <a name="runtime-profiling"></a>Çalışma Zamanı Profili Oluşturma
Profil oluşturma tüm geliştirme ve dağıtım senaryosunda performans verilerini toplama yöntemidir. Bu bölüm, geliştiriciler ve uygulama performansı hakkında bilgi toplamak isteyen sistem yöneticilerine yöneliktir.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Performans İzleyicisi'ni (Perfmon.exe) kullanarak performans izleme  
 Performans İzleyicisi'ni, .NET Framework uygulamanızın profilini kullanmak için kolay bir araçtır. Performans İzleyicisi'ni, grafik ile ortak dil çalışma zamanı yüklü olan .NET Framework performans sayaçlarını bulunan verileri temsil eder ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Bu sayaçlar, just-ın-time (JIT) derleyici performans için bellek yönetimi kadar her şeyi izlemek için kullanılabilir. Bunlar, kaynaklar hakkında uygulamanız tarafından kullanılan, uygulamanızın performansını dolaylı bir ölçü olan söyleyin. Uygulamanız dahili olarak nasıl çalıştığını anlamak için bu sayaçlar kullanın.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Windows Vista ve sonraki sürümler Perfmon.exe çalıştırmak için  
  
1. Komut isteminde **perfmon**. **Performans İzleyicisi** Konsolu görünür.  
  
2. İçinde **izleme araçları** klasörünü tıklatın **Performans İzleyicisi**.  
  
3. Performans İzleyicisi araç çubuğunda **Ekle** ise simgesi (artı işareti) sunar. Mevcut değilse İzleyicisi penceresinde sağ tıklayıp **Sayaç Ekle** seçeneği.  
  
     Bu açılır **Sayaç Ekle** iletişim kutusu. **Kullanılabilir sayaçları** liste kutusu kullanılabilir performans nesneleri görüntüler. Önceden tanımlanmış nesneler için bellek yönetimi dahil olmak üzere, .NET Framework uygulamaları için bir dizi vardır ( **.NET CLR bellek**), birlikte çalışabilirlik ( **.NET CLR Interop**), özel durum işleme ( **.NET CLR özel durumları**) ve çoklu iş parçacığı kullanımı ( **.NET CLR LocksAndThreads**). Her performans nesnesi bireysel performans sayaçları içerir. Performans İzleyicisi'nde kullanılabilen performans sayaçlarının listesi için bkz. [performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4. Bunu destekleyen tek performans sayaçları listesini görüntülemek için bir performans nesnesinin adının yanındaki onay kutusunu seçin.  
  
5. Görüntülemek istediğiniz performans sayacı'a tıklayın.  
  
6. İçinde **seçili nesne örneklerini** liste kutusunda, tıklayın  **\<tüm örnekleri >** genel olarak ortak dil çalışma zamanı performans sayacı izlemek istediğinizi belirtmek için (diğer bir deyişle, bir Sistem genelinde bir temele).  
  
     -veya-  
  
     İçinde **seçili nesne örneklerini** liste kutusunda, bu uygulama için performans sayacı izlemek için uygulamanın adına tıklayın.  
  
     Çalışma zamanının birden çok sürümünü ayırt etmek için ya da aynı ada sahip birden çok uygulama ayırt etmek için bir kayıt defteri anahtarı da değiştirmeniz gerekir. Daha fazla bilgi için [performans sayaçları ve işlem içi yan yana uygulamalar](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Performans konsolu çalışırken yeni performans sayaçları yüklendiğinde, durdurun ve yeni sayaçları görünür yapmak için Performans konsolunu yeniden başlatın.  
  
 Bir bölge içinde veya uzak bir paylaşıma var olan bir derleme profil isterseniz, uzak derleme performans sayaçlarını çalıştıran bilgisayarda tam güvene sahip olduğundan emin olun. Derleme yeterli güven yoksa, performans sayaçlarını çalışmaz. Farklı bölgelere güven verme hakkında daha fazla bilgi için bkz: [Caspol.exe (kod erişimi güvenliği ilke aracı)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  .NET Framework 4 yüklü olduğu sistemlerde, Performans İzleyicisi'ni verileri performans sayaçları için bazı kategorilerde gibi görüntülemeyebilir **Data .NET CLR** ve **.NET CLR ağ**, için .NET Framework 1.1 kullanılarak geliştirilen uygulamalar. Bu durumda, Performans İzleyicisi'ni ekleyerek bu verileri görüntülemek için yapılandırabileceğiniz [ \<forcePerformanceCounterUniqueSharedMemoryReads >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) uygulamanın yapılandırma dosyası öğesi.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Okuma ve performans sayaçları program aracılığıyla oluşturma  
 .NET Framework Performans konsolunda kullanılabilir durumda aynı performans bilgileri programlı olarak erişmek için kullanabileceğiniz sınıflar sağlar. Bu sınıflar, özel performans Sayaçlarınızı oluşturma işlemleri de kullanabilirsiniz. Aşağıdaki tabloda bazı performans izleme .NET Framework içinde sağlanan sınıfları açıklar.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Bir Windows NT performans sayacı bileşenini temsil eder. Bu sınıf, önceden tanımlanmış ya da özel sayaçlar okuma ve özel sayaç (yazma) performans verilerini yayınlamak için kullanın.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Sayaçları ve kategoriler bilgisayarda sayaçlarını ile etkileşim kurmak için çeşitli yöntemler sunar.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|İçin bir yükleyici belirtir `PerformanceCounter` bileşeni.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Hesaplama formülü belirtir `NextValue` yöntemi için bir `PerformanceCounter`.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans Sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)
