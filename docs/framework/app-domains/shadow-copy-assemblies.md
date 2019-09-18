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
ms.openlocfilehash: df1c86f2d75b0046af851585e943e13d668d8c55
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053083"
---
# <a name="shadow-copying-assemblies"></a>Gölge Kopyalama Derlemeleri

Gölge kopyalama, uygulama etki alanında kullanılan derlemelerin uygulama etki alanının kaldırılması gerekmeden güncelleştirilmesini sağlar. Bu özellikle, ASP.NET siteleri gibi sürekli kullanılabilir olması gereken uygulamalar için yararlıdır.

> [!IMPORTANT]
> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Uygulamalarda gölge kopyalama desteklenmez.

Ortak dil çalışma zamanı, derleme yüklendiğinde bir derleme dosyasını kilitler, bu nedenle dosya derleme kaldırılana kadar güncelleştirilemez. Bir uygulama etki alanından bir derlemeyi kaldırmak için tek yol, uygulama etki alanını da kaldıracağından, normal koşullarda, kendisini kullanan tüm uygulama etki alanları kaldırılana kadar disk üzerinde bir derleme güncelleştirilemez.

Bir uygulama etki alanı, gölge kopya dosyalarına yapılandırıldığında, uygulama yolundan gelen derlemeler başka bir konuma kopyalanır ve bu konumdan yüklenir. Kopya kilitli, ancak özgün derleme dosyasının kilidi açık ve güncelleştirilmiş olabilir.

> [!IMPORTANT]
> Gölge kopyası olabilecek tek derlemeler, uygulama etki alanı yapılandırıldığında <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> özellikleriyle belirtilen uygulama dizininde veya alt dizinlerinde depolanırlar. Genel derleme önbelleğinde depolanan derlemeler gölge kopyası değildir.

Bu makale aşağıdaki bölümleri içerir:

- [Gölge kopyalamayı etkinleştirmek ve kullanmak](#EnablingAndUsing) , temel kullanımı ve gölge kopyalama için kullanılabilen seçenekleri açıklar.

- [Başlangıç performansı](#StartupPerformance) , başlangıç performansını geliştirmek için .NET Framework 4 ' te gölge kopyalama için yapılan değişiklikleri ve önceki sürümlerin davranışına döndürmeyi açıklar.

- [Kullanılmayan Yöntemler](#ObsoleteMethods) , .NET Framework 2,0 ' de gölge kopyalamayı denetleyen özelliklerde ve yöntemlerde yapılan değişiklikleri açıklar.

<a name="EnablingAndUsing"></a>

## <a name="enabling-and-using-shadow-copying"></a>Gölge Kopyalamayı Etkinleştirme ve Kullanma

Gölge kopyalama için bir uygulama etki alanı <xref:System.AppDomainSetup> yapılandırmak üzere sınıfının özelliklerini aşağıdaki şekilde kullanabilirsiniz:

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A> Özelliği dize değerine `"true"`ayarlayarak gölge kopyalamayı etkinleştirin.

  Varsayılan olarak, bu ayar, uygulama yolundaki tüm derlemelerin yüklenmeden önce bir indirme önbelleğine kopyalanmasını sağlar. Bu, diğer bilgisayarlardan indirilen dosyaları depolamak için ortak dil çalışma zamanı tarafından tutulan önbelleğidir ve artık gerekli olmadığında ortak dil çalışma zamanı dosyaları otomatik olarak siler.

- İsteğe bağlı olarak, <xref:System.AppDomainSetup.CachePath%2A> özelliği <xref:System.AppDomainSetup.ApplicationName%2A> ve özelliğini kullanarak gölge kopyalanmış dosyalar için özel bir konum ayarlayın.

  Konumun temel yolu, özelliği bir alt dizin olarak özelliği ile <xref:System.AppDomainSetup.ApplicationName%2A> birleştirerek <xref:System.AppDomainSetup.CachePath%2A> oluşturulur. Derlemeler, temel yolun kendisi için değil, bu yolun alt dizinlerine kopyalanırlar.

  > [!NOTE]
  > <xref:System.AppDomainSetup.ApplicationName%2A> Özellik ayarlanmamışsa<xref:System.AppDomainSetup.CachePath%2A> , özelliği yok sayılır ve indirme önbelleği kullanılır. Hiçbir özel durum oluşturulmaz.

  Özel bir konum belirtirseniz, artık gerekli olmadığında dizinleri ve kopyalanan dosyaları temizlemek sizin sorumluluğunuzdadır. Bunlar otomatik olarak silinmez.

  Gölge kopyalanmış dosyalar için özel bir konum ayarlamak isteyebileceğiniz birkaç neden vardır. Uygulamanız çok sayıda kopya oluşturursa gölge kopyalanmış dosyalar için özel bir konum ayarlamak isteyebilirsiniz. İndirme önbelleği, kullanım süresine göre değil, boyutla sınırlandırılır, bu nedenle ortak dil çalışma zamanının hala kullanımda olan bir dosyayı silmeye çalışmaları mümkündür. Özel bir konum ayarlamaya yönelik başka bir nedenden dolayı, uygulamanızı çalıştıran kullanıcıların indirme önbelleği için ortak dil çalışma zamanının kullandığı dizin konumuna yazma erişimi olmaz.

- İsteğe bağlı olarak, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliğini kullanarak gölge kopyası olan derlemeleri sınırlayın.

  Bir uygulama etki alanı için gölge kopyalamayı etkinleştirdiğinizde varsayılan değer, uygulama yolundaki tüm derlemeleri (diğer bir deyişle, <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> özellikleri tarafından belirtilen dizinlerde) kopyalamadır. Yalnızca gölge kopyalamak istediğiniz dizinleri içeren bir dize oluşturarak ve dizeyi <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> özelliğine atayarak seçili dizinlere kopyalamayı sınırlayabilirsiniz. Dizinleri noktalı virgülle ayırın. Gölge kopyası olan tek derlemeler seçili dizinlerdeki olanlardır.

  > [!NOTE]
  > <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> Özelliğe bir dize atamadıysanız veya bu özelliği olarak `null`ayarlarsanız, <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> özellikleri tarafından belirtilen dizinlerdeki tüm derlemeler gölge kopyalanır.

  > [!IMPORTANT]
  > Dizin yolları noktalı virgül içermemelidir, çünkü noktalı virgül sınırlayıcı karakterdir. Noktalı virgül için kaçış karakteri yoktur.

<a name="StartupPerformance"></a>

## <a name="startup-performance"></a>Başlangıç Performansı

Gölge kopyalama kullanan bir uygulama etki alanı başladığında, uygulama dizinindeki derlemeler gölge kopya dizinine kopyalanırken veya zaten o konumda olduklarında doğrulanırken bir gecikme olur. .NET Framework 4 ' den önce, tüm derlemeler geçici bir dizine kopyalandı. Her derleme, derleme adını doğrulamak için açıldı ve tanımlayıcı ad doğrulanmıştı. Her derleme, gölge kopya dizinindeki kopyadan daha yakın bir zamanda güncelleştirilip güncelleştirilmediğini görmek için denetlendi. Bu durumda, gölge kopya dizinine kopyalanmıştı. Son olarak, geçici kopyalar atılır.

.NET Framework 4 ' ten itibaren, varsayılan başlangıç davranışı, uygulama dizinindeki her derlemenin dosya tarih ve saatini, gölge kopya dizinindeki kopyanın dosya tarihi ve saati ile doğrudan karşılaştırmaktır. Derleme güncellendiyse, .NET Framework önceki sürümlerinde olduğu gibi aynı yordam kullanılarak kopyalanır; Aksi takdirde, gölge kopya dizinindeki kopya yüklenir.

Elde edilen performans iyileştirmesi, derlemelerin sık olarak değişmediğinden ve değişiklikler genellikle derlemelerin küçük bir alt kümesinde oluştuğu uygulamalar için en iyisidir. Bir uygulama içindeki derlemelerin büyük bir bölümü sıklıkla değiştiğinde yeni varsayılan davranış bir performans gerilemesine neden olabilir. Yapılandırma dosyasına [ \<shadowcopyverifybytimestamp > öğesini](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) ekleyerek .NET Framework önceki sürümlerinin başlangıç davranışını geri yükleyebilirsiniz. `enabled="false"`

<a name="ObsoleteMethods"></a>

## <a name="obsolete-methods"></a>Eski Yöntemler

Sınıfı, <xref:System.AppDomain.SetShadowCopyFiles%2A> ve gibi çeşitli yöntemlere sahiptir ve <xref:System.AppDomain.ClearShadowCopyPath%2A>bu, bir uygulama etki alanında gölge kopyalamayı denetlemek için kullanılabilir, ancak bunlar .NET Framework sürüm 2,0 ' de artık kullanılmıyor olarak işaretlendi. <xref:System.AppDomain> Bir uygulama etki alanını gölge kopyalama için yapılandırmanın önerilen yolu, <xref:System.AppDomainSetup> sınıfının özelliklerini kullanmaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [\<shadowCopyVerifyByTimestamp > öğesi](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
