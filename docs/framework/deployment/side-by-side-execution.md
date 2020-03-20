---
title: .NET Framework'te Yan Yana Yürütme
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
ms.openlocfilehash: e965702943149d3ed34be39bb2923ad52dcf90ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181652"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>.NET Framework'te Yan Yana Yürütme

Yan yana yürütme uygulamanın veya bileşenin birden çok sürümünü aynı bilgisayarda çalıştırma yeteneğidir. Bir bilgisayar üzerinde ortak dil çalışma zamanı sürümünün ve bir uygulamanın ve çalışma zamanının bir sürümünü kullanan bileşenin çeşitli sürümlerine aynı anda sahip olabilirsiniz.  
  
Aynı bilgisayar üzerinde çalışma zamanının farklı iki versiyonunu kullanan çeşitli uygulamaların gösterildiği örnek aşağıdadır. D uygulaması çalışma zamanı sürüm 1.1 kullanırken A, B ve C uygulamaları çalışma zamanı sürüm 1.0 kullanıyor.  
  
![Farklı çalışma zamanı sürümlerinin yan yana yürütülmesi,](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
.NET Framework, ortak dil çalışma zamanı ve API türlerini içeren bir derleme koleksiyonundan oluşur. Çalışma zamanı ve .Net Framework derlemeleri ayrı ayrı uyarlandı. Örneğin, .Net Framework derleme sürümü 4.0 aslında sürüm 1.0.3300.0 iken, çalışma zamanı sürüm 1.0 aslında 4.0.319 sürümüdür.  
  
Aşağıdaki örnek çeşitli uygulamaların aynı bilgisayarda bir bileşenin iki farklı sürümünü kullandığını göstermektedir. Uygulama A ve B bileşenin 1.0 sürümünü kullanırken Uygulama C aynı bileşenin 2.0 sürümünü kullanır.  
  
![Bir bileşenin yan yana yürütülmesini gösteren diyagram.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
Yan yana yürütme size bir bileşenin sürümüne bağlı olan uygulama ve uygulamanın kullandığı çalışma zamanı üzerinde daha fazla denetim, kontrol sağlar.  
  
## <a name="benefits-of-side-by-side-execution"></a>Yan Yana Yürütmenin Yararları  

Windows XP ve .NET Framework' den önce uygulamalar aynı kodun uyumsuz sürümleri arasında kararsız kaldığı için DLL çakışması oluşurdu. DLL içinde yer alan tür bilgileri yalnızca bir dosya adına bağlıydı. Bir uygulamanın bir DLL içinde yer alan tür bilgileriyle uygulamanın oluşturuldu türlerin aynı olduğunu bilmesinin imkanı yoktu. Sonuç olarak, bir bileşenin yeni bir sürümü eski bir sürümü üzerine yazılabilir ve uygulamaları durdurabilir.  
  
Yan yana yürütme ve .NET Framework DLL çakışmalarını gidermek için aşağıdaki özellikleri sağlar:  
  
- Tanımlayıcı adlandırılmış derlemeler.  
  
     Yan yana yürütme bir derlemenin belirli bir sürümüne tür bilgisi bağlamak için tanımlayıcı adlandırılmış derlemeler kullanır. Bu bir uygulama ya da bileşenin bir derlemenin geçersiz bir sürümüne bağlanmasını önler. Tanımlayıcı adlandırılmış derlemeler ayrıca bir bilgisayar üzerinde var olan bir dosyanın çeşitli sürümlerine ve uygulamalar tarafından kullanılmasına izin verir. Daha fazla bilgi için Bkz. [Güçlü Adlandırılmış Derlemeler.](../../standard/assembly/strong-named.md)  
  
- Sürüm uyumlu kod depolama.  
  
     .NET Framework genel derleme önbelleğinde sürüm ile uyumlu kod depolamayı sağlar. Genel birleştirme önbelleği .NET Framework yüklü olan tüm bilgisayarlar üzerinde sunulan mevcut bilgisayar düzeyindeki kod önbelleğidir. Sürüm bazlı derlemeleri, kültür ve yayımcı bilgilerini depolar ve bileşenlerin ve uygulamaların birden çok sürümünü destekler. Daha fazla bilgi için [Genel Montaj Önbelleği'ne](../app-domains/gac.md)bakın.  
  
- Yalıtım.  
  
     .NET Framework kullanarak yalıtım modunda çalışan uygulamalar ve bileşenler oluşturabilirsiniz. Yalıtım, yan yana yürütmenin temel bir bileşenidir. Bir bileşenin ya da uygulamanın kullandığınız çeşitli sürümleri arasında güvenli olan kaynak paylaşmayı ve kaynaklarla uyumlu olmayı sağlar. Yalıtım ayrıca sürüme özgü bir şekilde dosya depolamayı da içerir. Yalıtım hakkında daha fazla bilgi için, [Yan yana Yürütme için Bileşenler Oluşturma Yönergeleri'ne](guidelines-for-creating-components-for-side-by-side-execution.md)bakın.  
  
## <a name="version-compatibility"></a>Sürüm Uyumluluğu  

.Net Framework 1.0 ve 1.1 sürümleri birbiriyle uyumlu olacak şekilde tasarlanmıştır. .NET Framework sürüm 1.0 ile oluşturulmuş bir uygulama sürüm 1.1 ile çalışması gerekir ve .Net Framework sürüm 1.1 ile oluşturulmuş bir uygulamada sürüm 1.0 ile çalışması gerekir. Ancak, unutmayın .Net Framework 1.1 sürümünde eklenen API özellikleri, .Net Framework 1.0 sürümüyle çalışmayacaktır. Sürüm 2.0 ile oluşturulan uygulamalar yalnızca sürüm 2.0 üzerinde çalışır. Sürüm 2.0 uygulamaları sürüm 1.1 veya daha öncesi sürümlerde çalışmayacaktır.  
  
.NET Framework sürümleri çalışma zamanı ve onun ilişkili .Net Framework derlemelerinden (derleme birleştirici olarak başvurulan bir kavram) oluşan tek bir birim olarak kabul edilir. .Net Framework derlemelerinin diğer sürümlerini dahil etmek için derleme bağlamayı yönlendirebilirsiniz, ancak varsayılan derleme bağlamasını geçersiz kılma riskli olabilir ve dağıtım öncesinde ciddi bir şekilde test edilmesi gerekir.  
  
## <a name="locating-runtime-version-information"></a>Çalışma Zamanı Sürüm Bilgilerini Bulma  

Bir uygulamanın veya bileşenin hangi çalışma zamanı sürümüyle derlendiği ve uygulamanın çalıştırılması gereken çalışma zamanı sürümlerinin iki konumda depolandığı bilgiler. Bir uygulama veya bileşen derlendiğinde, derlemek için kullanılan çalışma zamanı sürümündeki bilgiler yönetilen yürütülebilir de depolanır. Uygulamanın veya bileşenin gerektirdiği çalışma zamanı sürümlerindeki bilgiler uygulama yapılandırma dosyasında depolanır.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Yönetilen Yürütülebilir'deki Çalışma Zamanı Sürüm Bilgileri  

Yönetilen her uygulamanın ve bileşenin taşınabilir yürütülebilir (PE) dosya üstbilgisi, birlikte üretildiği çalışma zamanı sürümü hakkında bilgi içerir. Ortak dil çalışma süresi, uygulamanın çalışması gereken çalışma zamanının en olası sürümünü belirlemek için bu bilgileri kullanır.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Uygulama Yapılandırma Dosyasındaki Çalışma Zamanı Sürüm Bilgileri  

PE dosya üstbilgideki bilgilere ek olarak, bir uygulama çalışma zamanı sürüm bilgilerini sağlayan bir uygulama yapılandırma dosyasıyla dağıtılabilir. Uygulama yapılandırma dosyası, uygulama geliştiricisi tarafından oluşturulan ve bir uygulama ile birlikte gönderen XML tabanlı bir dosyadır. Başlangıç [ \<](../configure-apps/file-schema/startup/requiredruntime-element.md) [ \<> bölümünün](../configure-apps/file-schema/startup/startup-element.md)gerekli Runtime> Öğesi , bu dosyada varsa, çalışma zamanının hangi sürümlerini ve uygulamanın hangi bileşeni ni desteklediğini belirtir. Bu dosyayı, bir uygulamanın çalışma zamanının farklı sürümleriyle uyumluluğunu test etmek için de kullanabilirsiniz.  
  
COM ve COM+ uygulamaları da dahil olmak üzere yönetilmeyen kod, çalışma zamanının yönetilen kodla etkileşim kurmak için kullandığı uygulama yapılandırma dosyalarına sahip olabilir. Uygulama yapılandırma dosyası, COM aracılığıyla etkinleştirdiğiniz yönetilen kodları etkiler. Dosya, hangi çalışma zamanı sürümlerini desteklediğini ve derlemenin yeniden yönlendirebileceğini belirtebilir. Varsayılan olarak, yönetilen koda çağrıda bulunan COM interop uygulamaları, bilgisayarda yüklü olan çalışma zamanının en son sürümünü kullanır.  
  
 Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için Uygulamaları [Yapılandırma'ya](../configure-apps/index.md)bakın.  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Çalışma Zamanının Hangi Sürümünün Yükleneceğini Belirleme  

Ortak dil çalışma süresi, bir uygulama için yüklenmesi gereken çalışma zamanının hangi sürümünü belirlemek için aşağıdaki bilgileri kullanır:  
  
- Kullanılabilir çalışma zamanı sürümleri.  
  
- Bir uygulamanın desteklediği çalışma zamanı sürümleri.  
  
### <a name="supported-runtime-versions"></a>Desteklenen Runtime Sürümleri  

Çalışma zamanı, uygulamanın hangi sürümünü desteklediğini belirlemek için uygulama yapılandırma dosyasını ve taşınabilir yürütülebilir (PE) dosya üstbilgisini kullanır. Uygulama yapılandırma dosyası yoksa, çalışma zamanı, uygulamanın PE dosya üstbilgisinde belirtilen çalışma zamanı sürümünü yükler, bu sürüm varsa.  
  
Bir uygulama yapılandırma dosyası varsa, çalışma zamanı aşağıdaki işlemin sonuçlarına göre yüklenmeye uygun çalışma zamanı sürümünü belirler:  
  
1. Çalışma zamanı, uygulama yapılandırma dosyasındaki [ \<desteklenen Runtime> Öğesi](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesini inceler. Desteklenen Runtime>öğesinde belirtilen desteklenen çalışma zamanı sürümlerinden biri veya birkaçı varsa, çalışma zamanı ilk ** \<desteklenen Runtime>** öğesi tarafından belirtilen çalışma zamanı sürümünü yükler. ** \<** Bu sürüm kullanılamıyorsa, çalışma zamanı sonraki ** \<desteklenen Runtime>** öğesini inceler ve belirtilen çalışma zamanı sürümünü yüklemeye çalışır. Bu çalışma zamanı sürümü kullanılamıyorsa, sonraki ** \<desteklenen Runtime>** öğeleri incelenir. Desteklenen çalışma zamanı sürümlerinin hiçbiri yoksa, çalışma zamanı sürümü yüklenmez ve kullanıcıya bir ileti görüntüler (bkz. adım 3).  
  
2. Çalışma süresi, uygulamanın yürütülebilir dosyasının PE dosya üstbilgisini okur. PE dosya üstbilgisi tarafından belirtilen çalışma zamanı sürümü kullanılabilirse, çalışma zamanı bu sürümü yükler. Belirtilen çalışma zamanı sürümü kullanılamıyorsa, çalışma zamanı sürümü Microsoft tarafından PE üstbilgideki çalışma zamanı sürümüyle uyumlu olarak belirlenen çalışma zamanı sürümünü arar. Bu sürüm bulunamazsa, işlem 3 adıma devam eder.  
  
3. Çalışma zamanı, uygulama tarafından desteklenen çalışma zamanı sürümünün kullanılamadığını belirten bir ileti görüntüler. Çalışma süresi yüklenmedi.  
  
    > [!NOTE]
    > Bu iletinin görüntülenmesini, kayıt defteri anahtarı hkLM\Software\Microsoft\\altında NoGuiFromShim değerini kullanarak bastırabilirsiniz. NETFramework veya çevre değişkeni COMPLUS_NoGuiFromShim kullanarak. Örneğin, genellikle kullanıcıyla etkileşimde olmayan,sahipsiz yüklemeler veya Windows hizmetleri gibi uygulamalar için iletiyi bastırabilirsiniz. Bu ileti ekranı bastırıldığında, çalışma zamanı olay günlüğüne bir ileti yazar.  Bilgisayardaki tüm uygulamalar için bu iletiyi bastırmak için kayıt defteri değerini NoGuiFromShim olarak 1 olarak ayarlayın. Alternatif olarak, belirli bir kullanıcı bağlamında çalışan uygulamalar için iletibastırmak için COMPLUS_NoGuiFromShim ortamı değişkenini 1 olarak ayarlayın.  
  
> [!NOTE]
> Çalışma zamanı sürümü yüklendikten sonra, derleme bağlama yönlendirmeleri, tek bir .NET Framework derlemesinin farklı bir sürümünün yüklendiğini belirtebilir. Bu bağlama yönlendirmeleri yalnızca yönlendirilen belirli derlemeyi etkiler.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Kısmen Nitelenmiş Derleme Adları ve Yan Yana Yürütme  

Yan yana sorunların potansiyel bir kaynağı olduğundan, kısmen nitelikli derleme başvuruları yalnızca bir uygulama dizini içindeki derlemelere bağlamak için kullanılabilir. Kodunuzda kısmen nitelikli montaj başvurularından kaçının.  
  
Koddaki kısmen nitelikli derleme başvurularını azaltmak için, kodda oluşan kısmen nitelikli derleme başvurularını tam olarak hak kazanmak için bir uygulama yapılandırma dosyasındaki [ \<uygun Assembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) öğesini kullanabilirsiniz. Yalnızca kısmi başvuruda ayarlanamayan alanları belirtmek için qualifyAssembly>öğesini kullanın. ** \<** **fullName** özniteliğinde listelenen derleme kimliği, derleme adını, genel anahtarı, kültürü ve sürümü tam olarak nitelemek için gereken tüm bilgileri içermelidir.  
  
 Aşağıdaki örnekte, '. adı verilen `myAssembly`bir derlemeyi tam olarak nitelemek için uygulama yapılandırma dosya girişi gösterilmektedir.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
<qualifyAssembly partialName="myAssembly"
fullName="myAssembly,  
      version=1.0.0.0,
publicKeyToken=...,
      culture=neutral"/>
</assemblyBinding>
```  
  
 Bir derleme yük deyimi `myAssembly`başvurulsa, bu yapılandırma dosyası ayarları çalışma `myAssembly` zamanının kısmen nitelikli başvuruyu tam nitelikli bir başvuruya otomatik olarak çevirmesine neden olur. Örneğin, Assembly.Load("myAssembly") Assembly.Load("myAssembly, version=1.0.0.0, publicKeyToken=..., culture=neutral") olur.  
  
> [!NOTE]
> Kısmen başvurulan derlemelerin genel derleme önbelleğinden yüklenmesini yasaklayan ortak dil çalışma zamanı kısıtlamasını atlamak için **LoadWithPartialName** yöntemini kullanabilirsiniz. Bu yöntem, yan yana yürütmede kolayca sorunlara neden olabileceğiiçin yalnızca senaryoları remoting'de kullanılmalıdır.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Bir uygulamanın bir derlemenin belirli bir sürümüne nasıl bağlanacağını açıklar.|  
|[Derleme Bağlama Yönlendirmesini Yapılandırma](configuring-assembly-binding-redirection.md)|Derleme bağlama başvurularının nasıl belirli bir sürümdeki .NET Framework derlemelerine yeniden yönlendirildiğini açıklar.|  
|[Devam Eden Yan Yana Yürütme](in-process-side-by-side-execution.md)|Tek bir işlemde CLR'nin birden çok sürümünü çalıştırılacak işlem içi yan yana çalışma zamanlı ana makine etkinleştirmenin nasıl kullanabileceğini açıklanır.|  
|[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)|Derlemeler üzerine kavramsal bir genel bakış sağlar.|  
|[Uygulama Etki Alanları](../app-domains/application-domains.md)|Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.|  
  
## <a name="reference"></a>Başvuru  

[\<desteklenenRuntime> Öğesi](../configure-apps/file-schema/startup/supportedruntime-element.md)
