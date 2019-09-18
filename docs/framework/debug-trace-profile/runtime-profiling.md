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
ms.openlocfilehash: 163022256dfbeb303a500d9c1d574054c5b550d7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052292"
---
# <a name="runtime-profiling"></a>Çalışma Zamanı Profili Oluşturma
Profil oluşturma, herhangi bir geliştirme veya dağıtım senaryosunda performans verileri toplama yöntemidir. Bu bölüm, uygulama performansı hakkında bilgi toplamak isteyen geliştiricilere ve sistem yöneticilerine yöneliktir.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Performans Izleyicisi (Perfmon. exe) kullanarak performansı izleme  
 Performans Izleyicisi, .NET Framework uygulamanızı profil için kullanabileceğiniz en kolay araçtır. Performans Izleyicisi, ortak dil çalışma zamanı ve Windows SDK birlikte yüklenen .NET Framework performans sayaçlarında bulunan verileri grafiksel olarak temsil eder. Bu sayaçlar, bellek yönetiminden tam zamanında (JıT) derleyici performansına kadar her şeyi izlemek için kullanılabilir. Uygulama performansının dolaylı bir ölçüsü olan, uygulamanızın kullandığı kaynakları size bildirir. Uygulamanızın dahili olarak nasıl çalıştığını anlamak için bu sayaçları kullanın.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Windows Vista ve sonraki sürümlerde Perfmon. exe ' yi çalıştırmak için  
  
1. Komut isteminde **Perfmon**yazın. **Performans İzleyicisi** konsolu görüntülenir.  
  
2. **Izleme Araçları** klasöründe **Performans İzleyicisi**' ne tıklayın.  
  
3. Performans Izleyicisi araç çubuğunda, varsa **Ekle** simgesine (artı işareti) tıklayın. Mevcut değilse, izleyici penceresinde sağ tıklayın ve **Sayaç Ekle** seçeneğini belirleyin.  
  
     Bu, **Sayaç Ekle** iletişim kutusunu açar. **Kullanılabilir sayaçlar** liste kutusu kullanılabilir performans nesnelerini görüntüler. Bellek yönetimi ( **.NET CLR belleği**), birlikte çalışabilirlik ( **.net clr birlikte çalışma**), özel durum Işleme ( **.net clr özel durumları**) gibi .NET Framework uygulamalar için önceden tanımlanmış birçok nesne vardır Çoklu iş parçacığı oluşturma ( **.NET CLR LocksAndThreads**). Her performans nesnesi, bazı ayrı performans sayaçlarını içerir. Performans Izleyicisinde bulunan performans sayaçlarının listesi için bkz. [performans sayaçları](performance-counters.md).  
  
4. Desteklediği tek performans sayaçlarının listesini görüntülemek için bir performans nesnesi adının yanındaki onay kutusunu işaretleyin.  
  
5. Görüntülemek istediğiniz performans sayacını tıklayın.  
  
6. **Seçilen nesne örnekleri** liste kutusunda, ortak dil çalışma zamanının genel olarak performans sayacını izlemek istediğinizi belirtmek için  **\<> tüm örnekler** ' e tıklayın (yani, sistem genelinde).  
  
     -veya-  
  
     **Seçilen nesne örnekleri** liste kutusunda, uygulamanın performans sayacını izlemek için bir uygulama adına tıklayın.  
  
     Çalışma zamanının birden çok sürümünü ayırt etmek veya aynı ada sahip birden çok uygulamayı kesinleştirmeniz için bir kayıt defteri anahtarını da değiştirmelisiniz. Daha fazla bilgi için bkz. [performans sayaçları ve Işlem Içi yan yana uygulamalar](performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
> Performans konsolu çalışırken yeni performans sayaçları yüklendiğinde, yeni sayaçların görünür olması için Performans konsolunu durdurup yeniden başlatın.  
  
 Bir bölgede veya uzak paylaşımda bulunan bir derlemenin profilini oluşturmak istiyorsanız, uzak derlemenin performans sayaçlarını çalıştıran bilgisayarda tam güvene sahip olduğundan emin olun. Derlemenin yeterli güveni yoksa, performans sayaçları çalışmaz. Farklı bölgelere güven verme hakkında daha fazla bilgi için bkz. [Caspol. exe (kod erişimi güvenlik Ilkesi aracı)](../tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
> .NET Framework 4 ' ün yüklendiği sistemlerde, performans Izleyicisi .net **clr verileri** ve **.NET CLR ağı**gibi bazı kategorilerdeki performans sayaçlarındaki verileri .NET kullanılarak geliştirilmiş uygulamalar için görüntülemeyebilir Framework 1,1. Bu durumda, [ \<forcePerformanceCounterUniqueSharedMemoryReads >](../configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) öğesini uygulamanın yapılandırma dosyasına ekleyerek performans izleyicisini bu verileri görüntüleyecek şekilde yapılandırabilirsiniz.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Programlı olarak performans sayaçlarını okuma ve oluşturma  
 .NET Framework, Performans konsolunda bulunan performans bilgilerine programlı bir şekilde erişmek için kullanabileceğiniz sınıflar sağlar. Özel performans sayaçları oluşturmak için bu sınıfları da kullanabilirsiniz. Aşağıdaki tabloda .NET Framework belirtilen bazı performans izleme sınıfları açıklanmaktadır.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Bir Windows NT performans sayacı bileşenini temsil eder. Bu sınıfı, önceden tanımlanmış mevcut veya özel sayaçları okumak ve performans verilerini Özel sayaçlara yayımlamak (yazmak) için kullanın.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|, Bilgisayardaki sayaçların ve sayaçların kategorileriyle etkileşim kurmak için çeşitli yöntemler sağlar.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|`PerformanceCounter` Bileşen için bir yükleyici belirtir.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|İçin yönteminin`NextValue` hesaplanacağı formülü belirtir. `PerformanceCounter`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans Sayaçları](performance-counters.md)
