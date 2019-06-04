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
ms.openlocfilehash: 5bbf579540ccb93101dba05c5b2577ae8f24ec09
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486516"
---
# <a name="shadow-copying-assemblies"></a>Gölge Kopyalama Derlemeleri
Gölge kopyalama etki alanını kaldırmadan güncelleştirilmesi için bir uygulama etki alanında kullanılan etkinleştirir derlemeler. Bu, özellikle sürekli olarak ASP.NET siteleri gibi kullanılabilir olması gereken uygulamalar için yararlıdır.  
  
> [!IMPORTANT]
>  Gölge kopyalama desteklenmiyor [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 Ortak dil çalışma zamanı, derlemeyi bellekten kaldırılana kadar dosyası güncelleştirilemiyor şekilde derleme, yüklendiğinde bir derleme dosyası kilitler. Uygulama etki alanındaki bir derlemeyi kaldırmak için tek yolu uygulama etki alanı kaldırılarak, kullanmakta olduğunuz tüm uygulama etki alanları kadar normal koşullar altında bir derleme diskte güncelleştirilemiyor şekilde, kaldırıldı.  
  
 Uygulama etki alanı gölge kopyaları için yapılandırıldığında, uygulama yolu derlemelerden başka bir konuma kopyalanır ve o konumdan yüklenir. Kopya kilitli, ancak orijinal derleme dosyası kilitli değil ve güncelleştirilebilir.  
  
> [!IMPORTANT]
>  Gölge kopya olabilecek yalnızca bu uygulama dizininde depolanan veya belirtilen alt derlemelerdir <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> uygulama etki alanı yapılandırıldığında özellikleri. Gölge kopyalama derlemeleri genel derleme önbelleğinde depolanan değildir.  
  
 Bu makalede, aşağıdaki bölümleri içerir:  
  
- [Etkinleştirme ve kullanma gölge kopyalama](#EnablingAndUsing) temel kullanımı ve gölge kopyalama için kullanılabilir seçenekleri açıklar.  
  
- [Başlangıç performansı](#StartupPerformance) başlangıç performansı ve önceki sürümleri davranışa dönmek nasıl geliştirmek için .NET Framework 4'te kopyalama gölge yapılan değişiklikleri açıklar.  
  
- [Eski yöntemler](#ObsoleteMethods) özellikleri ve yöntemleri için bu denetim gölge içinde kopyalama yapılan değişiklikleri açıklar [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)].  
  
<a name="EnablingAndUsing"></a>   
## <a name="enabling-and-using-shadow-copying"></a>Gölge Kopyalamayı Etkinleştirme ve Kullanma  
 Özelliklerini kullanabilirsiniz <xref:System.AppDomainSetup> sınıfı şu şekilde gölge kopyalama için uygulama etki alanı yapılandırmak için:  
  
- Etkinleştirme gölge kopyalama ayarlayarak <xref:System.AppDomainSetup.ShadowCopyFiles%2A> dize özelliğini `"true"`.  
  
     Varsayılan olarak, bu ayar tüm derlemelerin yüklenmeden önce bir indirme önbelleğini için Kopyalanacak uygulama yolu neden olur. Bu diğer bilgisayarlardan indirilen dosyaları depolamak için ortak dil çalışma zamanı tarafından tutulan aynı önbellek ve artık gerekli olmadığında ortak dil çalışma zamanı dosyaları otomatik olarak siler.  
  
- İsteğe bağlı olarak kullanarak gölge dosyaları için özel konum ayarlamak <xref:System.AppDomainSetup.CachePath%2A> özelliği ve <xref:System.AppDomainSetup.ApplicationName%2A> özelliği.  
  
     Temel yol konumu için birleştirerek biçimlendirilmiş <xref:System.AppDomainSetup.ApplicationName%2A> özelliğini <xref:System.AppDomainSetup.CachePath%2A> özelliği olarak bir alt dizinidir. Temel yol için bu yolu alt dizinleri gölge derlemelerdir.  
  
    > [!NOTE]
    >  Varsa <xref:System.AppDomainSetup.ApplicationName%2A> özelliği ayarlı değil, <xref:System.AppDomainSetup.CachePath%2A> özelliği yok sayılır ve indirme önbelleğini kullanılır. Hiçbir özel durum oluşturulur.  
  
     Özel bir konum belirtirseniz, dizinler temizlemek sizin sorumluluğunuzdadır ve artık gerekli değilse, dosyalar kopyalanır. Otomatik olarak silinmez.  
  
     Gölge kopya dosyaları için özel konum ayarlamak için neden isteyebileceğiniz birkaç neden vardır. Uygulamanız çok sayıda kopya oluşturursa gölge dosyaları için özel konum ayarlamak isteyebilirsiniz. Ortak dil çalışma zamanı hala kullanımda olan bir dosyayı silmek dener mümkün olacak şekilde indirme önbelleğini boyutuna göre yaşam süresi, tarafından değil sınırlıdır. Özel konum ayarlamak için başka bir nedeni, uygulamanızı çalıştıran kullanıcılar, ortak dil çalışma zamanı için indirme önbelleğini kullanır. dizin konumuna yazma erişimi yoktur andır.  
  
- İsteğe bağlı olarak kullanarak gölge kopyası derlemeleri sınırlamak <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliği.  
  
     Bir uygulama etki alanı için gölge kopyalama etkinleştirdiğinizde, tüm derlemeleri uygulama yolu kopyalama için varsayılandır — diğer bir deyişle, tarafından belirtilen dizinlerde <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> özellikleri. Gölge kopya istediğiniz dizinleri içeren bir dize oluşturarak ve dizeye atama için seçilen dizinleri kopyalama sınırlayabilirsiniz <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliği. Dizinlerin noktalı virgülle ayırın. Gölge kopyası yalnızca derlemeler seçilen dizinlerde olanlardır.  
  
    > [!NOTE]
    >  Bir dizeye atamazsanız <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliği veya bu özelliği ayarlamak `null`, tüm derlemelerin tarafından belirtilen dizinlerde <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> gölge özelliklerdir.  
  
    > [!IMPORTANT]
    >  Noktalı virgül sınırlayıcı karakter olduğundan dizin yolları noktalı içermemelidir. Noktalı virgül için hiçbir kaçış karakteri var.  
  
<a name="StartupPerformance"></a>   
## <a name="startup-performance"></a>Başlangıç Performansı  
 Gölge kopyalama kullanan bir uygulama etki alanı başlatıldığında bir gecikme olur derlemeleri uygulama dizininde gölge kopya dizinine kopyalanır veya zaten bu konumda olup olmadıklarını doğrulandı. .NET Framework 4 önce tüm derlemelerin geçici bir dizine kopyalandı. Her derlemenin derleme adını doğrulamak için açıldı ve tanımlayıcı adı doğrulandı. Her derleme, gölge kopya dizinde kopyadan daha yakın zamanda güncelleştirilmişse olup olmadığını görmek için iade. Bu durumda, gölge kopya dizinine kopyalandığı. Son olarak, geçici kopya atıldı.  
  
 .NET Framework 4 ile başlayarak, varsayılan başlangıç dosyası tarih ve saat dosya tarih ile uygulama dizinindeki her derleme ile gölge kopya dizin kopyalama süresi doğrudan Karşılaştırılacak davranışıdır. Derleme güncelleştirildiyse, .NET Framework'ün önceki sürümlerinde olduğu gibi aynı yordamı kullanarak kopyalanır; Aksi takdirde, gölge kopya dizin kopyalama yüklenir.  
  
 Derlemeleri sık değiştirmeyin ve genellikle derlemeleri küçük bir kısmı değişiklikler uygulamaları için en büyük ortaya çıkan performans geliştirmesi. Bir uygulama değişikliği sık derlemelerde çoğunu, yeni varsayılan davranışı bir performans gerileme neden olabilir. .NET Framework'ün önceki sürümlerini başlangıç davranışını ekleyerek geri yükleyebilirsiniz [ \<shadowCopyVerifyByTimestamp > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) yapılandırma dosyasına sahip `enabled="false"`.  
  
<a name="ObsoleteMethods"></a>   
## <a name="obsolete-methods"></a>Eski Yöntemler  
 <xref:System.AppDomain> Sınıfına sahip çeşitli yöntemler gibi <xref:System.AppDomain.SetShadowCopyFiles%2A> ve <xref:System.AppDomain.ClearShadowCopyPath%2A>, bir uygulama etki alanında gölge kopyalama denetlemek için kullanılabilir, ancak bu .NET Framework 2.0 sürümünde geçersiz olarak işaretlendi. Gölge kopyalama özelliklerini kullanmak için bir uygulama etki alanı yapılandırmak için önerilen yöntem <xref:System.AppDomainSetup> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [\<shadowCopyVerifyByTimestamp > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
