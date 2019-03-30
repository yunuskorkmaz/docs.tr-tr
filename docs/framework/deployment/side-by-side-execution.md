---
title: .NET Framework'te Yan Yana Yürütme
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03600a7c7fbff30acab46f875fb8cd2516207457
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654607"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>.NET Framework'te Yan Yana Yürütme
Yan yana yürütme uygulamanın veya bileşenin birden çok sürümünü aynı bilgisayarda çalıştırma yeteneğidir. Bir bilgisayar üzerinde ortak dil çalışma zamanı sürümünün ve bir uygulamanın ve çalışma zamanının bir sürümünü kullanan bileşenin çeşitli sürümlerine aynı anda sahip olabilirsiniz.  
  
 Aynı bilgisayar üzerinde çalışma zamanının farklı iki versiyonunu kullanan çeşitli uygulamaların gösterildiği örnek aşağıdadır. D uygulaması çalışma zamanı sürüm 1.1 kullanırken A, B ve C uygulamaları çalışma zamanı sürüm 1.0 kullanıyor.  
  
 ![Farklı çalışma zamanı sürümlerinin yan yana yürütme](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
 .NET Framework, ortak dil çalışma zamanı ve API türlerini içeren bir derleme koleksiyonundan oluşur. Çalışma zamanı ve .Net Framework derlemeleri ayrı ayrı uyarlandı. Örneğin, .Net Framework derleme sürümü 4.0 aslında sürüm 1.0.3300.0 iken, çalışma zamanı sürüm 1.0 aslında 4.0.319 sürümüdür.  
  
 Aşağıdaki örnek çeşitli uygulamaların aynı bilgisayarda bir bileşenin iki farklı sürümünü kullandığını göstermektedir. Uygulama A ve B bileşenin 1.0 sürümünü kullanırken Uygulama C aynı bileşenin 2.0 sürümünü kullanır.  
  
 ![Yan yana yürütme bir bileşenin gösteren diyagram.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
 Yan yana yürütme size bir bileşenin sürümüne bağlı olan uygulama ve uygulamanın kullandığı çalışma zamanı üzerinde daha fazla denetim, kontrol sağlar.  
  
## <a name="benefits-of-side-by-side-execution"></a>Yan Yana Yürütmenin Yararları  
 Windows XP ve .NET Framework' den önce uygulamalar aynı kodun uyumsuz sürümleri arasında kararsız kaldığı için DLL çakışması oluşurdu. DLL içinde yer alan tür bilgileri yalnızca bir dosya adına bağlıydı. Bir uygulamanın bir DLL içinde yer alan tür bilgileriyle uygulamanın oluşturuldu türlerin aynı olduğunu bilmesinin imkanı yoktu. Sonuç olarak, bir bileşenin yeni bir sürümü eski bir sürümü üzerine yazılabilir ve uygulamaları durdurabilir.  
  
 Yan yana yürütme ve .NET Framework DLL çakışmalarını gidermek için aşağıdaki özellikleri sağlar:  
  
-   Tanımlayıcı adlandırılmış derlemeler.  
  
     Yan yana yürütme bir derlemenin belirli bir sürümüne tür bilgisi bağlamak için tanımlayıcı adlandırılmış derlemeler kullanır. Bu bir uygulama ya da bileşenin bir derlemenin geçersiz bir sürümüne bağlanmasını önler. Tanımlayıcı adlandırılmış derlemeler ayrıca bir bilgisayar üzerinde var olan bir dosyanın çeşitli sürümlerine ve uygulamalar tarafından kullanılmasına izin verir. Daha fazla bilgi için [Strong-Named derlemeleri](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Sürüm uyumlu kod depolama.  
  
     .NET Framework genel derleme önbelleğinde sürüm ile uyumlu kod depolamayı sağlar. Genel birleştirme önbelleği .NET Framework yüklü olan tüm bilgisayarlar üzerinde sunulan mevcut bilgisayar düzeyindeki kod önbelleğidir. Sürüm bazlı derlemeleri, kültür ve yayımcı bilgilerini depolar ve bileşenlerin ve uygulamaların birden çok sürümünü destekler. Daha fazla bilgi için [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md).  
  
-   Yalıtım.  
  
     .NET Framework kullanarak yalıtım modunda çalışan uygulamalar ve bileşenler oluşturabilirsiniz. Yalıtım, yan yana yürütmenin temel bir bileşenidir. Bir bileşenin ya da uygulamanın kullandığınız çeşitli sürümleri arasında güvenli olan kaynak paylaşmayı ve kaynaklarla uyumlu olmayı sağlar. Yalıtım ayrıca sürüme özgü bir şekilde dosya depolamayı da içerir. Yalıtım hakkında daha fazla bilgi için bkz: [yan yana yürütme için bileşenleri oluşturma için yönergeler](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Sürüm Uyumluluğu  
 .Net Framework 1.0 ve 1.1 sürümleri birbiriyle uyumlu olacak şekilde tasarlanmıştır. .NET Framework sürüm 1.0 ile oluşturulmuş bir uygulama sürüm 1.1 ile çalışması gerekir ve .Net Framework sürüm 1.1 ile oluşturulmuş bir uygulamada sürüm 1.0 ile çalışması gerekir. Ancak, unutmayın .Net Framework 1.1 sürümünde eklenen API özellikleri, .Net Framework 1.0 sürümüyle çalışmayacaktır. Sürüm 2.0 ile oluşturulan uygulamalar yalnızca sürüm 2.0 üzerinde çalışır. Sürüm 2.0 uygulamaları sürüm 1.1 veya daha öncesi sürümlerde çalışmayacaktır.  
  
 .NET Framework sürümleri çalışma zamanı ve onun ilişkili .Net Framework derlemelerinden (derleme birleştirici olarak başvurulan bir kavram) oluşan tek bir birim olarak kabul edilir. .Net Framework derlemelerinin diğer sürümlerini dahil etmek için derleme bağlamayı yönlendirebilirsiniz, ancak varsayılan derleme bağlamasını geçersiz kılma riskli olabilir ve dağıtım öncesinde ciddi bir şekilde test edilmesi gerekir.  
  
## <a name="locating-runtime-version-information"></a>Çalışma Zamanı Sürüm Bilgilerini Bulma  
 Hangi çalışma zamanı üzerinde bir uygulama veya bileşenin sürümü ile derlenen ve çalışma zamanının hangi sürümlerinin uygulama, çalışması için gerekli bilgileri iki konumda depolanır. Bir uygulama veya bileşenin derlendiğinde, derlemek için kullanılan çalışma zamanı sürümü hakkında bilgi Yönetilen yürütülebilir dosya olarak depolanır. Uygulama veya bileşen gerektirir çalışma zamanı sürümleri hakkında bilgi, uygulama yapılandırma dosyasında depolanır.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Yönetilen çalıştırılabilir dosyanın çalışma zamanı sürüm bilgisi  
 Her taşınabilir yürütülebilir (PE) dosya üstbilgisi, uygulama yönetilen ve bileşen ile oluşturulan çalışma zamanı sürümü hakkında bilgi içerir. Ortak dil çalışma zamanı, büyük olasılıkla bir uygulamayı çalıştırmak için gereken çalışma zamanı sürümünü belirlemek için bu bilgileri kullanır.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Uygulama yapılandırma dosyasında çalışma zamanı sürüm bilgileri  
 PE dosyasının üst bilgisindeki bilgilere ek olarak, bir uygulama çalışma zamanı sürüm bilgileri sağlayan bir uygulama yapılandırma dosyası ile dağıtılabilir. Uygulama yapılandırma dosyası uygulama geliştiricisi tarafından oluşturulur ve uygulama ile birlikte bir XML tabanlı dosyasıdır. [ \<RequiredRuntime > öğesini](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) , [ \<başlangıç > bölüm](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), bu dosyada, varsa, çalışma zamanının hangi sürümlerinin ve hangi sürümlerinin belirtir bir Uygulama bileşeni destekler. Bu dosya, test, farklı çalışma zamanı sürümleri ile uygulama uyumluluğu test etmek için de kullanabilirsiniz.  
  
 Yönetilmeyen kod, COM ve COM + uygulamaları dahil olmak üzere çalışma zamanı, yönetilen kod ile etkileşim kurmak için kullanır. uygulama yapılandırma dosyaları olabilir. Uygulama yapılandırma dosyası, COM içinden etkinleştirme herhangi bir yönetilen kod etkiler. Dosya, hangi çalışma zamanı sürümlerini destekliyorsa, aynı zamanda derleme yönlendiren belirtebilirsiniz. Varsayılan olarak, COM birlikte çalışma uygulamaları için arayan yönetilen kod kullanın bilgisayarda yüklü olan çalışma zamanı en son sürümünü'ü tıklatın.  
  
 Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Çalışma Zamanının Hangi Sürümünün Yükleneceğini Belirleme  
 Ortak dil çalışma zamanı, bir uygulama için çalışma zamanının hangi sürümünü belirlemek için aşağıdaki bilgileri kullanır:  
  
-   Kullanılabilir çalışma zamanı sürümleri.  
  
-   Bir uygulamanın desteklediği çalışma zamanı sürümleri.  
  
### <a name="supported-runtime-versions"></a>Desteklenen çalışma zamanı sürümleri  
 Çalışma zamanı, bir uygulamanın çalışma zamanının hangi sürümünün desteklediği belirlemek için uygulama yapılandırma dosyası ve taşınabilir yürütülebilir (PE) dosya üstbilgisi'ni kullanır. Herhangi bir uygulama yapılandırma dosyası varsa, çalışma zamanı bu sürüm varsa uygulamanın PE dosya üst bilgisinde belirtilen çalışma zamanı sürümü yükler.  
  
 Uygulama yapılandırma dosyası varsa, çalışma zamanı aşağıdaki işlemi sonuçlarına göre yüklemek için uygun çalışma zamanı sürümünü belirler:  
  
1.  Çalışma zamanı inceler [ \<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) uygulama yapılandırma dosyasında öğesi. Bir veya daha fazla belirtilen desteklenen çalışma zamanı sürümlerinin  **\<supportedRuntime >** öğesi, çalışma zamanını ilk tarafından belirtilen çalışma zamanı sürümü yükler  **\< supportedRuntime >** öğesi. Bu sürümü kullanılabilir durumda değilse, çalışma zamanının sonraki inceler  **\<supportedRuntime >** öğesini ve belirtilen çalışma zamanı sürümü yük dener. Bu çalışma zamanı sürümü değilse kullanılabilir, sonraki  **\<supportedRuntime >** öğeleri incelenir. Desteklenen çalışma zamanı sürümlerinin hiçbiri varsa, çalışma zamanı bir çalışma zamanı sürümü yüklenemiyor ve kullanıcıya bir ileti görüntüler (3. adıma bakın).  
  
2.  Çalışma zamanı, uygulamanın yürütülebilir dosyanın PE dosya üstbilgisi okur. PE dosyası üstbilgisi tarafından belirtilen çalışma zamanı sürümü varsa, çalışma zamanının bu sürümü yükler. Belirtilen çalışma zamanı sürümü kullanılabilir durumda değilse, çalışma zamanı PE üstbilgisinde çalışma zamanı sürümü ile uyumlu olacak şekilde, Microsoft tarafından belirlenen bir çalışma zamanı sürümünü arar. Bu sürüm bulunmazsa, işlemi 3. adımına devam eder.  
  
3.  Çalışma zamanı, uygulama tarafından desteklenen çalışma zamanı sürüm kullanılamaz olduğunu belirten bir ileti görüntüler. Çalışma zamanı yüklenmedi.  
  
    > [!NOTE]
    >  HKLM\Software\Microsoft kayıt defteri anahtarı altında NoGuiFromShim değerini kullanarak bu iletinin görüntülenmesini engelleyebilir\\. NETFramework veya COMPLUS_NoGuiFromShim ortam değişkenini kullanarak. Örneğin, katılımsız yüklemeleri veya Windows Hizmetleri gibi bir kullanıcı değil genellikle etkileşimli uygulamalarla için iletiyi gizleyebilirsiniz. Bu ileti görüntü atlandığında, çalışma zamanı olay günlüğüne bir ileti yazar.  Bir bilgisayardaki tüm uygulamalar için bu iletiyi engellemek için 1 NoGuiFromShim kayıt defteri değerini ayarlayın. Alternatif olarak, belirli bir kullanıcı bağlamında çalışan uygulamalar için iletiyi engellemek için 1 COMPLUS_NoGuiFromShim ortam değişkenini ayarlayın.  
  
> [!NOTE]
>  Bir çalışma zamanı sürümü yüklendikten sonra derleme bağlama yeniden yönlendirmeleri bağımsız bir .NET Framework derlemesi farklı bir sürümü yüklenebilir belirtebilirsiniz. Bu bağlama yeniden yönlendirmeleri yönlendirilen belirli derleme etkiler.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Kısmen Nitelenmiş Derleme Adları ve Yan Yana Yürütme  
 Yan yana sorunların olası bir kaynak olduklarından kısmen nitelenmiş derleme başvuruları, yalnızca uygulama dizini içindeki derlemeler bağlamak için kullanılabilir. Kısmen nitelenmiş derleme başvuruları, kodunuzda kaçının.  
  
 Kısmen nitelenmiş derleme başvuruları kod azaltmak için kullanabileceğiniz [ \<qualifyAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) öğe kısmen tam olarak nitelemek için bir uygulama yapılandırma dosyasında tam meydana gelen derleme başvuruları kodu. Kullanım  **\<qualifyAssembly >** yalnızca kısmi başvurusunda ayarlanmadı alanları belirlemek için öğesi. Listelenen derleme kimliği **fullName** özniteliği derleme adı tam olarak nitelemek için gerekli tüm bilgileri içermelidir: derleme adı, ortak anahtar, kültür ve sürüm.  
  
 Aşağıdaki örnekte adlı bir derleme tam olarak nitelemek için uygulama yapılandırma dosyası girdisi `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Her bir derlemeyi yüklemek deyimi başvuruları `myAssembly`, bu yapılandırma dosyası ayarlarının otomatik olarak kısmen nitelenmiş çevirmek çalışma zamanı neden `myAssembly` başvuru tam nitelikli bir başvuru. Örneğin, Assembly.Load("myAssembly") Assembly.Load olur ("myAssembly, sürüm 1.0.0.0, publicKeyToken =..., culture = neutral =").  
  
> [!NOTE]
>  Kullanabileceğiniz **LoadWithPartialName** yöntemi kısmen yasaklar ortak dil çalışma zamanı kısıtlama atlamak için başvurulan derlemeler genel bütünleştirilmiş kod önbelleğinden yüklenmedi. Kolayca yan yana yürütme sorunlara yol açabilir gibi bu yöntem yalnızca uzaktan iletişim senaryolarında kullanılmalıdır.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Otomatik bağlama yeniden yönlendirmesini devre dışı bırakma ve etkinleştirme](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Bir uygulamanın bir derlemenin belirli bir sürümüne nasıl bağlanacağını açıklar.|  
|[Bütünleştirilmiş Kod Bağlama Yönlendirmesini Yapılandırma](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Derleme bağlama başvurularının nasıl belirli bir sürümdeki .NET Framework derlemelerine yeniden yönlendirildiğini açıklar.|  
|[İşlem İçi Yan Yana Yürütme](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Tek bir işlemde CLR'nin birden çok sürümünü çalıştırılacak işlem içi yan yana çalışma zamanlı ana makine etkinleştirmenin nasıl kullanabileceğini açıklanır.|  
|[Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Derlemeler üzerine kavramsal bir genel bakış sağlar.|  
|[Uygulama Etki Alanları](../../../docs/framework/app-domains/application-domains.md)|Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.|  
  
## <a name="reference"></a>Başvuru  
 [\<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
