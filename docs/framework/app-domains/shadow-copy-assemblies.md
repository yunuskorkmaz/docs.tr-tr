---
title: Gölge Kopyalama Derlemeleri
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea7c85e956828e918e3cfe205b980e543e257eb4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743959"
---
# <a name="shadow-copying-assemblies"></a>Gölge Kopyalama Derlemeleri
Uygulama etki alanı kaldırılması olmadan güncelleştirilmesi için bir uygulama etki alanında kullanılan etkinleştirir derlemeleri kopyalama gölge. Bu, özellikle ASP.NET siteleri gibi sürekli olarak kullanılabilir olması gereken uygulamalar için yararlıdır.  
  
> [!IMPORTANT]
>  Gölge kopyalama desteklenmez [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 Ortak dil çalışma zamanı derlemesi bellekten kaldırılana kadar dosya güncelleştirilemiyor için derleme, yüklendiğinde bir derleme dosyası kilitler. Uygulama etki alanı kaldırarak bütünleştirilmiş uygulama etki alanından kaldırmak için tek yolu olduğundan, kullanmakta olduğunuz tüm uygulama etki alanları kadar normal koşullar altında bir derleme diskte güncelleştirilemiyor şekilde onu kaldırıldı.  
  
 Uygulama etki alanı gölge kopyaları için yapılandırıldığında, uygulama yolu derlemelerden başka bir konuma kopyalanır ve o konumdan yüklendi. Kopya kilitli, ancak özgün derleme dosyası kilidinin açık olduğundan ve güncelleştirilebilir.  
  
> [!IMPORTANT]
>  Bu uygulama dizini içinde depolanan veya tarafından belirtilen alt dizinlerinde gölge kopya olabilir yalnızca derlemeleri olan <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> uygulama etki alanı yapılandırıldığında özellikleri. Derlemeleri genel derleme önbelleğinde depolanan gölge kopya değildir.  
  
 Bu makalede aşağıdaki bölümleri içerir:  
  
-   [Etkinleştirme ve kullanma gölge kopyalama](#EnablingAndUsing) temel kullanım ve gölge kopyalama için kullanılabilir seçenekleri açıklar.  
  
-   [Başlangıç performans](#StartupPerformance) içinde kopyalama gölge yapılan değişiklikleri açıklar [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] başlangıç performansı ve önceki sürümleri davranışını dönmek nasıl artırmak için.  
  
-   [Yöntemleri geçersiz](#ObsoleteMethods) özellikleri ve yöntemleri için bu denetim gölge içinde kopyalama yapılan değişiklikleri açıklar [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)].  
  
<a name="EnablingAndUsing"></a>   
## <a name="enabling-and-using-shadow-copying"></a>Gölge Kopyalamayı Etkinleştirme ve Kullanma  
 Özelliklerini kullanabilirsiniz <xref:System.AppDomainSetup> sınıfı şu şekilde gölge kopyalama için uygulama etki alanını yapılandırmak için:  
  
-   Ayarlayarak kopyalama etkinleştir gölge <xref:System.AppDomainSetup.ShadowCopyFiles%2A> dize değeri özelliğine `"true"`.  
  
     Varsayılan olarak, bu ayarı tüm derlemelerde yüklenmeden önce bir yükleme önbelleğine kopyalanacak uygulama yolu neden olur. Bu diğer bilgisayarlardan indirilen dosyaları depolamak için ortak dil çalışma zamanı tarafından tutulan aynı önbellek ve artık gerekmediğinde ortak dil çalışma zamanı dosyaları otomatik olarak siler.  
  
-   İsteğe bağlı olarak kullanarak gölge kopya dosyaları için özel konum ayarlamak <xref:System.AppDomainSetup.CachePath%2A> özelliği ve <xref:System.AppDomainSetup.ApplicationName%2A> özelliği.  
  
     Konumu için temel yolu birleştirerek biçimlendirildiğinden <xref:System.AppDomainSetup.ApplicationName%2A> özelliğine <xref:System.AppDomainSetup.CachePath%2A> özelliği olarak bir alt dizin. Derlemeleri temel yolu için değil bu yolun alt dizinlere Gölge ' dir.  
  
    > [!NOTE]
    >  Varsa <xref:System.AppDomainSetup.ApplicationName%2A> özelliği ayarlı değil, <xref:System.AppDomainSetup.CachePath%2A> özelliği gözardı edilir ve yükleme önbellek kullanılır. Hiçbir özel durum oluşur.  
  
     Özel bir konuma belirtirseniz, dizinler temizleniyor sorumludur ve artık gerekmediğinde dosyalar kopyalanır. Otomatik olarak silinmez.  
  
     Neden gölge kopya dosyaları için özel konum ayarlamak isteyebilirsiniz birkaç nedeni vardır. Uygulamanız çok sayıda kopya oluşturursa gölge kopya dosyaları için özel konum ayarlamak isteyebilirsiniz. Ortak dil çalışma zamanı hala kullanımda olan bir dosyayı silmek dener mümkün olması için yükleme önbellek ömrünü tarafından değil, boyuta göre sınırlıdır. Özel konum ayarlamak için başka bir nedeni, uygulamanızı çalıştıran kullanıcılar ortak dil çalışma zamanı yükleme önbelleğine kullanan dizin konuma yazma erişimi olmadığında olmasıdır.  
  
-   İsteğe bağlı olarak kullanarak gölge kopyası derlemeleri sınırlamak <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliği.  
  
     Uygulama etki alanı için gölge kopyalama etkinleştirdiğinizde, varsayılan tüm derlemelerde uygulama yolu kopyalamaktır — diğer bir deyişle, dizinler belirtilen tarafından <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> özellikleri. Yalnızca gölge kopyaya istediğiniz dizinleri içeren bir dize oluşturma ve dizeye atayarak seçili dizinleri kopyalama sınırlayabilirsiniz <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliği. Dizinleri noktalı virgülle ayırın. Gölge kopyası yalnızca derlemeleri seçili dizinlerde olanlardır.  
  
    > [!NOTE]
    >  Bir dizeyi atamazsanız <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliği veya bu özelliği ayarlamak `null`, tüm derlemelerde tarafından belirtilen dizin <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> özelliklerdir gölge kopya.  
  
    > [!IMPORTANT]
    >  Noktalı virgül sınırlayıcı karakter olduğundan dizin yolu noktalı virgül, içermemelidir. Noktalı virgül hiçbir kaçış karakteri yoktur.  
  
<a name="StartupPerformance"></a>   
## <a name="startup-performance"></a>Başlangıç Performansı  
 Gölge kopyalama kullanan bir uygulama etki alanı başladığında, bir gecikme olur uygulama dizinindeki derlemeler gölge kopya dizinine kopyalanır veya bunların zaten bu konumda olup olmadığını doğrulandı. Önce [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], tüm derlemelerde geçici bir dizine kopyalandı. Her derlemenin derleme adı doğrulamak için açıldı ve güçlü ad doğrulandı. Her derleme, bu daha yakın zamanda gölge kopya dizin kopyalama güncelleştirilmişse olup olmadığını görmek için işaretlenmedi. Bu durumda, gölge kopya dizinine kopyalandı. Son olarak, geçici kopya atıldı.  
  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], varsayılan başlangıç dosya tarihi ve her derleme dosyası tarihi ile uygulama dizinindeki süreleri ve gölge kopya dizininde kopyasının süresi doğrudan Karşılaştırılacak davranıştır. Derleme güncelleştirilmişse, .NET Framework'ün önceki sürümlerinde olduğu gibi yordamın aynısını kullanarak kopyalanır; Aksi takdirde, gölge kopya dizin kopyalama yüklenir.  
  
 Sonuçta elde edilen performans geliştirmesi derlemeleri sık değiştirmeyin ve genellikle derlemeleri küçük bir alt değişikliklerden uygulamalar için en büyük. Bir uygulama değişikliği sık derlemelerde çoğunu, yeni varsayılan davranış performans regresyon neden olabilir. .NET Framework'ün önceki sürümlerini başlangıç davranışını ekleyerek geri [ \<shadowCopyVerifyByTimestamp > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) yapılandırma dosyasına ile `enabled="false"`.  
  
<a name="ObsoleteMethods"></a>   
## <a name="obsolete-methods"></a>Eski Yöntemler  
 <xref:System.AppDomain> Sınıfına sahip çeşitli yöntemler gibi <xref:System.AppDomain.SetShadowCopyFiles%2A> ve <xref:System.AppDomain.ClearShadowCopyPath%2A>uygulama etki alanı üzerinde gölge kopyalama denetlemek için kullanılabilir ancak bunlar .NET Framework sürüm 2.0 geçersiz olarak işaretlendi. Gölge kopyalama özelliklerini kullanmak için uygulama etki alanını yapılandırmak için önerilen yöntem <xref:System.AppDomainSetup> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>  
 [\<shadowCopyVerifyByTimestamp > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
