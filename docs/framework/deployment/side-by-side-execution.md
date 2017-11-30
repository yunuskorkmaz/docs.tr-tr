---
title: ".NET Framework'te Yan Yana Yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25a5092da1526bc266c5cc483cc3cd81d2ac3385
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="side-by-side-execution-in-the-net-framework"></a>.NET Framework'te Yan Yana Yürütme
Yan yana yürütme uygulamanın veya bileşenin birden çok sürümünü aynı bilgisayarda çalıştırma yeteneğidir. Bir bilgisayar üzerinde ortak dil çalışma zamanı sürümünün ve bir uygulamanın ve çalışma zamanının bir sürümünü kullanan bileşenin çeşitli sürümlerine aynı anda sahip olabilirsiniz.  
  
 Aynı bilgisayar üzerinde çalışma zamanının farklı iki versiyonunu kullanan çeşitli uygulamaların gösterildiği örnek aşağıdadır. D uygulaması çalışma zamanı sürüm 1.1 kullanırken A, B ve C uygulamaları çalışma zamanı sürüm 1.0 kullanıyor.  
  
 ![Yan &#45; tarafından &#45; yan yürütme](../../../docs/framework/deployment/media/simplesbs.gif "simplesbs")  
Çalışma zamanının iki sürümünü yan yana yürütme  
  
 .NET Framework, ortak dil çalışma zamanı ve API türlerini içeren bir derleme koleksiyonundan oluşur. Çalışma zamanı ve .Net Framework derlemeleri ayrı ayrı uyarlandı. Örneğin, .Net Framework derleme sürümü 4.0 aslında sürüm 1.0.3300.0 iken, çalışma zamanı sürüm 1.0 aslında 4.0.319 sürümüdür.  
  
 Aşağıdaki örnek çeşitli uygulamaların aynı bilgisayarda bir bileşenin iki farklı sürümünü kullandığını göstermektedir. Uygulama A ve B bileşenin 1.0 sürümünü kullanırken Uygulama C aynı bileşenin 2.0 sürümünü kullanır.  
  
 ![Yan &#45; tarafından &#45; yan yürütme](../../../docs/framework/deployment/media/compsbs.gif "compsbs")  
Bir bileşenin iki sürümünün yan yana yürütülmesi  
  
 Yan yana yürütme size bir bileşenin sürümüne bağlı olan uygulama ve uygulamanın kullandığı çalışma zamanı üzerinde daha fazla denetim, kontrol sağlar.  
  
## <a name="benefits-of-side-by-side-execution"></a>Yan Yana Yürütmenin Yararları  
 Windows XP ve .NET Framework' den önce uygulamalar aynı kodun uyumsuz sürümleri arasında kararsız kaldığı için DLL çakışması oluşurdu. DLL içinde yer alan tür bilgileri yalnızca bir dosya adına bağlıydı. Bir uygulamanın bir DLL içinde yer alan tür bilgileriyle uygulamanın oluşturuldu türlerin aynı olduğunu bilmesinin imkanı yoktu. Sonuç olarak, bir bileşenin yeni bir sürümü eski bir sürümü üzerine yazılabilir ve uygulamaları durdurabilir.  
  
 Yan yana yürütme ve .NET Framework DLL çakışmalarını gidermek için aşağıdaki özellikleri sağlar:  
  
-   Tanımlayıcı adlandırılmış derlemeler.  
  
     Yan yana yürütme bir derlemenin belirli bir sürümüne tür bilgisi bağlamak için tanımlayıcı adlandırılmış derlemeler kullanır. Bu bir uygulama ya da bileşenin bir derlemenin geçersiz bir sürümüne bağlanmasını önler. Tanımlayıcı adlandırılmış derlemeler ayrıca bir bilgisayar üzerinde var olan bir dosyanın çeşitli sürümlerine ve uygulamalar tarafından kullanılmasına izin verir. Daha fazla bilgi için bkz: [Strong-Named derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Sürüm uyumlu kod depolama.  
  
     .NET Framework genel derleme önbelleğinde sürüm ile uyumlu kod depolamayı sağlar. Genel birleştirme önbelleği .NET Framework yüklü olan tüm bilgisayarlar üzerinde sunulan mevcut bilgisayar düzeyindeki kod önbelleğidir. Sürüm bazlı derlemeleri, kültür ve yayımcı bilgilerini depolar ve bileşenlerin ve uygulamaların birden çok sürümünü destekler. Daha fazla bilgi için bkz: [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md).  
  
-   Yalıtım.  
  
     .NET Framework kullanarak yalıtım modunda çalışan uygulamalar ve bileşenler oluşturabilirsiniz. Yalıtım, yan yana yürütmenin temel bir bileşenidir. Bir bileşenin ya da uygulamanın kullandığınız çeşitli sürümleri arasında güvenli olan kaynak paylaşmayı ve kaynaklarla uyumlu olmayı sağlar. Yalıtım ayrıca sürüme özgü bir şekilde dosya depolamayı da içerir. Yalıtımı hakkında daha fazla bilgi için bkz: [oluşturma bileşenler yan yana yürütme için yönergeleri](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Sürüm Uyumluluğu  
 .Net Framework 1.0 ve 1.1 sürümleri birbiriyle uyumlu olacak şekilde tasarlanmıştır. .NET Framework sürüm 1.0 ile oluşturulmuş bir uygulama sürüm 1.1 ile çalışması gerekir ve .Net Framework sürüm 1.1 ile oluşturulmuş bir uygulamada sürüm 1.0 ile çalışması gerekir. Ancak, unutmayın .Net Framework 1.1 sürümünde eklenen API özellikleri, .Net Framework 1.0 sürümüyle çalışmayacaktır. Sürüm 2.0 ile oluşturulan uygulamalar yalnızca sürüm 2.0 üzerinde çalışır. Sürüm 2.0 uygulamaları sürüm 1.1 veya daha öncesi sürümlerde çalışmayacaktır.  
  
 .NET Framework sürümleri çalışma zamanı ve onun ilişkili .Net Framework derlemelerinden (derleme birleştirici olarak başvurulan bir kavram) oluşan tek bir birim olarak kabul edilir. .Net Framework derlemelerinin diğer sürümlerini dahil etmek için derleme bağlamayı yönlendirebilirsiniz, ancak varsayılan derleme bağlamasını geçersiz kılma riskli olabilir ve dağıtım öncesinde ciddi bir şekilde test edilmesi gerekir.  
  
## <a name="locating-runtime-version-information"></a>Çalışma Zamanı Sürüm Bilgilerini Bulma  
 Hangi çalışma zamanı sürümü bir uygulama veya bileşenin ile derlenen ve çalıştırılması için uygulama çalışma zamanı'nın hangi sürümleri gerekli bilgileri iki konumda depolanır. Bir uygulama veya bileşenin derlendiğinde onu derlemek için kullanılan çalışma zamanı sürümü hakkında bilgi Yönetilen yürütülebilir dosya içinde depolanır. Uygulamanın veya bileşenin gerektirir çalışma zamanı sürümleri hakkında bilgi uygulama yapılandırma dosyasında depolanır.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Yönetilen yürütülebilir çalışma zamanı sürüm bilgisi  
 Taşınabilir yürütülebilir (PE) dosya üstbilgisi her yönetilen bir uygulamanın ve bileşeni ile oluşturulmuş çalışma zamanı sürümü hakkında bilgiler içerir. Ortak dil çalışma zamanı bu bilgi büyük olasılıkla uygulamayı çalıştırmak için gereken çalışma zamanı sürümü belirlemek için kullanır.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Uygulama yapılandırma dosyasında çalışma zamanı sürüm bilgileri  
 PE dosya üstbilgisi bilgilerin yanı sıra, bir uygulama çalışma zamanı sürüm bilgileri sağlayan uygulama yapılandırma dosyası ile dağıtılabilir. Uygulama yapılandırma dosyası uygulama geliştiricisi tarafından oluşturulur ve bir uygulama ile birlikte bir XML tabanlı dosyasıdır. [ \<RequiredRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) , [ \<başlangıç > bölümünde](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), bu dosyada, varsa, hangi çalışma zamanı ve hangi sürümleri belirtir bir Uygulama bileşeni destekler. Sınama sırasında bu dosya, uygulamanın uyumluluk çalışma zamanı farklı sürümleri ile test için de kullanabilirsiniz.  
  
 Yönetilmeyen kod COM ve COM + uygulamaları dahil olmak üzere, yönetilen kod ile etkileşmek için çalışma zamanı kullanır uygulama yapılandırma dosyaları olabilir. Uygulama yapılandırma dosyası com etkinleştirme herhangi bir yönetilen kod etkiler Dosyayı hangi çalışma zamanı sürümlerini destekliyorsa, aynı zamanda derleme yönlendiren belirtebilirsiniz. Varsayılan olarak, COM birlikte çalışma uygulamaları için arayan kod bilgisayarda yüklü çalışma zamanı en son sürümünü yönetilen kullan.  
  
 Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Çalışma Zamanının Hangi Sürümünün Yükleneceğini Belirleme  
 Ortak dil çalışma zamanı için bir uygulama yüklemek için çalışma zamanı'nın hangi sürümünü belirlemek için aşağıdaki bilgileri kullanır:  
  
-   Kullanılabilen çalışma zamanı sürümleri.  
  
-   Bir uygulama destekleyen çalışma zamanı sürümleri.  
  
### <a name="supported-runtime-versions"></a>Desteklenen çalışma zamanı sürümleri  
 Çalışma zamanı, bir uygulama çalışma zamanı hangi sürümünü destekleyen belirlemek için uygulama yapılandırma dosyasını ve taşınabilir yürütülebilir (PE) dosya üstbilgisi kullanır. Herhangi bir uygulama yapılandırma dosyası varsa, bu sürüm kullanılabilir durumdaysa çalışma zamanı uygulamanın PE dosya üstbilgisinde belirtilen çalışma zamanı sürümü yükler.  
  
 Uygulama yapılandırma dosyası varsa, çalışma zamanı şu işlem sonuçlarına göre yüklemek için uygun çalışma zamanı sürümü belirler:  
  
1.  Çalışma zamanı inceler [ \<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) uygulama yapılandırma dosyasında öğesi. Bir veya daha fazla belirtilen desteklenen çalışma zamanı sürümlerinin  **\<supportedRuntime >** öğesi, çalışma zamanı ilk tarafından belirtilen çalışma zamanı sürümü yükler  **\< supportedRuntime >** öğesi. Bu sürümü kullanılabilir durumda değilse, çalışma zamanı sonraki inceler  **\<supportedRuntime >** öğesi ve çalışma zamanı sürümü belirtilmiş yüklemeye çalışır. Bu çalışma zamanı sürümü değilse kullanılabilir, sonraki  **\<supportedRuntime >** öğeleri incelenmesini. Çalışma zamanı desteklenen çalışma zamanı sürümlerini hiçbiri varsa, bir çalışma zamanı sürümü yüklemek başarısız olur ve kullanıcı için bir ileti görüntülenir (3. adıma bakın).  
  
2.  Çalışma zamanı uygulamanın yürütülebilir dosyasının PE dosya üstbilgisi okur. PE dosya üstbilgisi tarafından belirtilen çalışma zamanı sürümü kullanılabilir durumda, çalışma zamanı bu sürümü yükler. Çalışma zamanı sürümü belirtilmiş kullanılabilir durumda değilse, çalışma zamanı PE üstbilgisinde çalışma zamanı sürümü ile uyumlu olacak şekilde Microsoft tarafından belirlenen bir çalışma zamanı sürümü arar. Bu sürüm bulunmazsa, işlem 3. adıma devam eder.  
  
3.  Çalışma zamanı uygulama tarafından desteklenen çalışma zamanı sürümü kullanılamaz olduğunu belirten bir ileti görüntüler. Çalışma zamanı yüklenmedi.  
  
    > [!NOTE]
    >  Kayıt defteri anahtarı HKLM\Software\Microsoft altında NoGuiFromShim değerini kullanarak bu iletinin görünümünü gizleyebilirsiniz\\. NETFramework veya ortam değişkeni COMPLUS_NoGuiFromShim kullanıyor. Örneğin, ileti değil genellikle etkileşim katılımsız yüklemeleri veya Windows Hizmetleri gibi kullanıcı uygulamalarla için gizleyebilirsiniz. Bu ileti görüntü atlandığında, çalışma zamanı olay günlüğüne bir ileti yazar.  Bir bilgisayardaki tüm uygulamalar için bu iletinin gösterilmemesi için 1 NoGuiFromShim kayıt defteri değerini ayarlayın. Alternatif olarak, belirli bir kullanıcı bağlamında çalışan uygulamalar için iletinin gösterilmemesi için 1 COMPLUS_NoGuiFromShim ortam değişkeni ayarlayın.  
  
> [!NOTE]
>  Çalışma zamanı sürümü yüklendikten sonra bağımsız bir .NET Framework derleme farklı bir sürümünü yüklenmesi derleme bağlama yeniden yönlendirmeleri belirtebilirsiniz. Bu bağlama yeniden yönlendirmeleri yönlendirilen belirli derleme etkiler.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Kısmen Nitelenmiş Derleme Adları ve Yan Yana Yürütme  
 Yan yana sorunlarının olası bir kaynak olduğundan, kısmen nitelikli derleme başvuruları yalnızca bir uygulama dizini içinde derlemeleri bağlamak için kullanılabilir. Kısmen koşullu derleme başvurularını kodunuzda kaçının.  
  
 Kısmen koşullu derleme başvurularını kod azaltmak için kullanabileceğiniz [ \<qualifyAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) kısmen tam olarak nitelemek için bir uygulama yapılandırma dosyasında öğenin nitelenmiş ortaya derleme başvuruları kodu. Kullanım  **\<qualifyAssembly >** öğesi yalnızca kısmi başvurusunda ayarlanmadı alanları belirtin. Listelenen derleme kimliği **fullName** özniteliği, derleme adı tam olarak nitelemek için gerekli tüm bilgileri içermelidir: derleme adı, ortak anahtar, kültür ve sürüm.  
  
 Uygulama yapılandırma dosyası Girişi'adlı bir derleme tam olarak nitelemek için aşağıdaki örnekte `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Her bir derleme yükleme deyimi başvuruları `myAssembly`, bu yapılandırma dosyası ayarları otomatik olarak kısmen tam çevirmek çalışma zamanı neden `myAssembly` tam başvuru referansı. Örneğin, Assembly.Load("myAssembly") Assembly.Load olur ("myAssembly, sürüm 1.0.0.0, publicKeyToken =..., culture = neutral =").  
  
> [!NOTE]
>  Kullanabileceğiniz **LoadWithPartialName** kısmen yasaklar ortak dil çalışma zamanı kısıtlama atlamak için yöntemi başvurulan derlemeleri genel derleme önbelleğinden yüklendi. Kolayca yan yana yürütme sorunlara yol açabilir gibi bu yöntemi yalnızca uzaktan iletişim senaryolarında kullanılmalıdır.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: etkinleştirme ve otomatik bağlama yönlendirmesini devre dışı](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Bir uygulamanın bir derlemenin belirli bir sürümüne nasıl bağlanacağını açıklar.|  
|[Derleme bağlama yönlendirmesini yapılandırma](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Derleme bağlama başvurularının nasıl belirli bir sürümdeki .NET Framework derlemelerine yeniden yönlendirildiğini açıklar.|  
|[İşlem içi yan yana yürütme](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Tek bir işlemde CLR'nin birden çok sürümünü çalıştırılacak işlem içi yan yana çalışma zamanlı ana makine etkinleştirmenin nasıl kullanabileceğini açıklanır.|  
|[Ortak dil çalışma zamanı derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Derlemeler üzerine kavramsal bir genel bakış sağlar.|  
|[Uygulama etki alanları](../../../docs/framework/app-domains/application-domains.md)|Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.|  
  
## <a name="reference"></a>Başvuru  
 [\<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
