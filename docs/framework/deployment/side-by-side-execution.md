---
title: .NET Framework'te Yan Yana Yürütme
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
ms.openlocfilehash: 5202e4c26220bc9ea08d6d941ee5a7821cbbdefd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122232"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>.NET Framework'te Yan Yana Yürütme

Yan yana yürütme uygulamanın veya bileşenin birden çok sürümünü aynı bilgisayarda çalıştırma yeteneğidir. Bir bilgisayar üzerinde ortak dil çalışma zamanı sürümünün ve bir uygulamanın ve çalışma zamanının bir sürümünü kullanan bileşenin çeşitli sürümlerine aynı anda sahip olabilirsiniz.  
  
Aynı bilgisayar üzerinde çalışma zamanının farklı iki versiyonunu kullanan çeşitli uygulamaların gösterildiği örnek aşağıdadır. D uygulaması çalışma zamanı sürüm 1.1 kullanırken A, B ve C uygulamaları çalışma zamanı sürüm 1.0 kullanıyor.  
  
![Farklı çalışma zamanı sürümlerinin yan yana yürütülmesi,](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
.NET Framework, ortak dil çalışma zamanı ve API türlerini içeren bir derleme koleksiyonundan oluşur. Çalışma zamanı ve .Net Framework derlemeleri ayrı ayrı uyarlandı. Örneğin, .Net Framework derleme sürümü 4.0 aslında sürüm 1.0.3300.0 iken, çalışma zamanı sürüm 1.0 aslında 4.0.319 sürümüdür.  
  
Aşağıdaki örnek çeşitli uygulamaların aynı bilgisayarda bir bileşenin iki farklı sürümünü kullandığını göstermektedir. Uygulama A ve B bileşenin 1.0 sürümünü kullanırken Uygulama C aynı bileşenin 2.0 sürümünü kullanır.  
  
![Bileşenin yan yana yürütmesini gösteren diyagram.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
Yan yana yürütme size bir bileşenin sürümüne bağlı olan uygulama ve uygulamanın kullandığı çalışma zamanı üzerinde daha fazla denetim, kontrol sağlar.  
  
## <a name="benefits-of-side-by-side-execution"></a>Yan Yana Yürütmenin Yararları  
 
Windows XP ve .NET Framework' den önce uygulamalar aynı kodun uyumsuz sürümleri arasında kararsız kaldığı için DLL çakışması oluşurdu. DLL içinde yer alan tür bilgileri yalnızca bir dosya adına bağlıydı. Bir uygulamanın bir DLL içinde yer alan tür bilgileriyle uygulamanın oluşturuldu türlerin aynı olduğunu bilmesinin imkanı yoktu. Sonuç olarak, bir bileşenin yeni bir sürümü eski bir sürümü üzerine yazılabilir ve uygulamaları durdurabilir.  
  
Yan yana yürütme ve .NET Framework DLL çakışmalarını gidermek için aşağıdaki özellikleri sağlar:  
  
- Tanımlayıcı adlandırılmış derlemeler.  
  
     Yan yana yürütme bir derlemenin belirli bir sürümüne tür bilgisi bağlamak için tanımlayıcı adlandırılmış derlemeler kullanır. Bu bir uygulama ya da bileşenin bir derlemenin geçersiz bir sürümüne bağlanmasını önler. Tanımlayıcı adlandırılmış derlemeler ayrıca bir bilgisayar üzerinde var olan bir dosyanın çeşitli sürümlerine ve uygulamalar tarafından kullanılmasına izin verir. Daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler](../../standard/assembly/strong-named.md).  
  
- Sürüm uyumlu kod depolama.  
  
     .NET Framework genel derleme önbelleğinde sürüm ile uyumlu kod depolamayı sağlar. Genel birleştirme önbelleği .NET Framework yüklü olan tüm bilgisayarlar üzerinde sunulan mevcut bilgisayar düzeyindeki kod önbelleğidir. Sürüm bazlı derlemeleri, kültür ve yayımcı bilgilerini depolar ve bileşenlerin ve uygulamaların birden çok sürümünü destekler. Daha fazla bilgi için bkz. [genel derleme önbelleği](../app-domains/gac.md).  
  
- Yalıtım.  
  
     .NET Framework kullanarak yalıtım modunda çalışan uygulamalar ve bileşenler oluşturabilirsiniz. Yalıtım, yan yana yürütmenin temel bir bileşenidir. Bir bileşenin ya da uygulamanın kullandığınız çeşitli sürümleri arasında güvenli olan kaynak paylaşmayı ve kaynaklarla uyumlu olmayı sağlar. Yalıtım ayrıca sürüme özgü bir şekilde dosya depolamayı da içerir. Yalıtım hakkında daha fazla bilgi için bkz. [yan yana yürütme Için bileşen oluşturmaya yönelik kılavuzlar](guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Sürüm Uyumluluğu  

.Net Framework 1.0 ve 1.1 sürümleri birbiriyle uyumlu olacak şekilde tasarlanmıştır. .NET Framework sürüm 1.0 ile oluşturulmuş bir uygulama sürüm 1.1 ile çalışması gerekir ve .Net Framework sürüm 1.1 ile oluşturulmuş bir uygulamada sürüm 1.0 ile çalışması gerekir. Ancak, unutmayın .Net Framework 1.1 sürümünde eklenen API özellikleri, .Net Framework 1.0 sürümüyle çalışmayacaktır. Sürüm 2.0 ile oluşturulan uygulamalar yalnızca sürüm 2.0 üzerinde çalışır. Sürüm 2.0 uygulamaları sürüm 1.1 veya daha öncesi sürümlerde çalışmayacaktır.  
  
.NET Framework sürümleri çalışma zamanı ve onun ilişkili .Net Framework derlemelerinden (derleme birleştirici olarak başvurulan bir kavram) oluşan tek bir birim olarak kabul edilir. .Net Framework derlemelerinin diğer sürümlerini dahil etmek için derleme bağlamayı yönlendirebilirsiniz, ancak varsayılan derleme bağlamasını geçersiz kılma riskli olabilir ve dağıtım öncesinde ciddi bir şekilde test edilmesi gerekir.  
  
## <a name="locating-runtime-version-information"></a>Çalışma Zamanı Sürüm Bilgilerini Bulma  

Bir uygulama veya bileşenin hangi çalışma zamanı sürümü ile derlendiğine ve uygulamanın çalışması için gereken çalışma zamanının hangi sürümlerinin, iki konumda depolanabileceği bilgiler. Bir uygulama veya bileşen derlendiğinde, derleme için kullanılan çalışma zamanı sürümü ile ilgili bilgiler yönetilen yürütülebilir dosyada depolanır. Uygulamanın veya bileşenin gerektirdiği çalışma zamanı sürümleri hakkında bilgi, uygulama yapılandırma dosyasında depolanır.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Yönetilen Çalıştırılabilirteki çalışma zamanı sürüm bilgileri  

Her bir yönetilen uygulamanın ve bileşeninin taşınabilir yürütülebilir (PE) dosya üstbilgisi, birlikte oluşturulduğu çalışma zamanı sürümü hakkında bilgi içerir. Ortak dil çalışma zamanı, uygulamanın çalışması gereken en olası çalışma zamanı sürümünü öğrenmek için bu bilgileri kullanır.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Uygulama yapılandırma dosyasındaki çalışma zamanı sürüm bilgileri  

PE dosya üstbilgisindeki bilgilere ek olarak, bir uygulama çalışma zamanı sürüm bilgilerini sağlayan bir uygulama yapılandırma dosyası ile dağıtılabilir. Uygulama yapılandırma dosyası, uygulama geliştiricisi tarafından oluşturulan ve bir uygulamayla birlikte gelen XML tabanlı bir dosyadır. [\<startup > bölümünün](../configure-apps/file-schema/startup/startup-element.md) [\<requiredRuntime > öğesi](../configure-apps/file-schema/startup/requiredruntime-element.md) bu dosyada mevcutsa, çalışma zamanının hangi sürümlerinin ve uygulamanın hangi sürümlerinin desteklediğini belirtir. Uygulamanın çalışma zamanının farklı sürümleriyle uyumluluğunu test etmek için bu dosyayı test içinde de kullanabilirsiniz.  
  
COM ve COM+ uygulamaları dahil olmak üzere yönetilmeyen kod, çalışma zamanının yönetilen kodla etkileşim kurmak için kullandığı uygulama yapılandırma dosyalarına sahip olabilir. Uygulama yapılandırma dosyası, COM aracılığıyla etkinleştirebileceğiniz tüm yönetilen kodları etkiler. Dosya, derleme yeniden yönlendirmelerinin yanı sıra desteklediği çalışma zamanı sürümlerini belirtebilir. Varsayılan olarak, yönetilen koda çağıran COM birlikte çalışma uygulamaları, bilgisayarda yüklü olan çalışma zamanının en son sürümünü kullanır.  
  
 Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [uygulamaları yapılandırma](../configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Çalışma Zamanının Hangi Sürümünün Yükleneceğini Belirleme  

Ortak dil çalışma zamanı, bir uygulama için hangi çalışma zamanının hangi sürümünün yükleneceğini belirlemede aşağıdaki bilgileri kullanır:  
  
- Kullanılabilir çalışma zamanı sürümleri.  
  
- Uygulamanın desteklediği çalışma zamanı sürümleri.  
  
### <a name="supported-runtime-versions"></a>Desteklenen çalışma zamanı sürümleri  

Çalışma zamanı, uygulama yapılandırma dosyasını ve taşınabilir yürütülebilir (PE) dosya üstbilgisini kullanarak bir uygulamanın hangi çalışma zamanı sürümünü desteklediğini belirleyebilir. Uygulama yapılandırma dosyası yoksa, çalışma zamanı, uygulamanın PE dosya üstbilgisinde belirtilen çalışma zamanı sürümünü yükler, bu sürüm kullanılabilir.  
  
Bir uygulama yapılandırma dosyası varsa, çalışma zamanı, aşağıdaki işlemin sonuçlarına göre yüklenecek uygun çalışma zamanı sürümünü belirler:  
  
1. Çalışma zamanı, uygulama yapılandırma dosyasında [\<supportedRuntime > öğesi](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesini inceler. **\<supportedruntime >** öğesinde belirtilen bir veya daha fazla desteklenen çalışma zamanı sürümü varsa, çalışma zamanı Ilk **\<supportedRuntime >** öğesi tarafından belirtilen çalışma zamanı sürümünü yükler. Bu sürüm kullanılamıyorsa, çalışma zamanı bir sonraki **\<supportedruntime >** öğesini inceler ve belirtilen çalışma zamanı sürümünü yüklemeye çalışır. Bu çalışma zamanı sürümü kullanılamıyorsa, sonraki **\<supportedRuntime >** öğeleri incelenir. Desteklenen çalışma zamanı sürümlerinin hiçbiri kullanılabilir değilse, çalışma zamanı bir çalışma zamanı sürümü yükleyemez ve kullanıcıya bir ileti görüntüler (bkz. Adım 3).  
  
2. Çalışma zamanı, uygulamanın yürütülebilir dosyasının PE dosya üstbilgisini okur. PE dosya üst bilgisi tarafından belirtilen çalışma zamanı sürümü kullanılabiliyorsa, çalışma zamanı bu sürümü yükler. Belirtilen çalışma zamanı sürümü kullanılamıyorsa, çalışma zamanı Microsoft tarafından, PE üstbilgisindeki çalışma zamanı sürümüyle uyumlu olacak şekilde belirlenen bir çalışma zamanı sürümü arar. Bu sürüm bulunamazsa, işlem adım 3 ' e devam eder.  
  
3. Çalışma zamanı, uygulama tarafından desteklenen çalışma zamanı sürümünün kullanılamadığını belirten bir ileti görüntüler. Çalışma zamanı yüklenmedi.  
  
    > [!NOTE]
    > Bu iletinin görüntülenmesini, HKLM\Software\Microsoft\\kayıt defteri anahtarı altındaki NoGuiFromShim değerini kullanarak gizleyebilirsiniz. NETFramework veya COMPLUS_NoGuiFromShim ortam değişkenini kullanma. Örneğin, katılımsız yüklemeler veya Windows Hizmetleri gibi genellikle kullanıcıyla etkileşimde bulunmayan uygulamalar için iletiyi gizleyebilirsiniz. Bu ileti görüntülendiğinde, çalışma zamanı olay günlüğüne bir ileti yazar.  Bir bilgisayardaki tüm uygulamalarda bu iletiyi bastırmak için NoGuiFromShim kayıt defteri değerini 1 olarak ayarlayın. Alternatif olarak, belirli bir kullanıcı bağlamında çalışan uygulamaların iletisini bastırmak için COMPLUS_NoGuiFromShim ortam değişkenini 1 olarak ayarlayın.  
  
> [!NOTE]
> Bir çalışma zamanı sürümü yüklendikten sonra, derleme bağlama yeniden yönlendirmeleri, tek bir .NET Framework derlemesinin farklı bir sürümünün yükleneceğini belirtebilir. Bu bağlama yeniden yönlendirmeleri yalnızca yeniden yönlendirilen belirli bir derlemeyi etkiler.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Kısmen Nitelenmiş Derleme Adları ve Yan Yana Yürütme  

Yan yana sorunların olası bir kaynağı olduklarından, kısmen nitelenmiş derleme başvuruları yalnızca bir uygulama dizini içindeki derlemelere bağlamak için kullanılabilir. Kodunuzda kısmen nitelikli derleme başvurularından kaçının.  
  
Kodda kısmen nitelikli derleme başvurularını azaltmak için bir uygulama yapılandırma dosyasında [\<qualifyAssembly >](../configure-apps/file-schema/runtime/qualifyassembly-element.md) öğesini kullanarak kodda oluşan kısmen nitelikli derleme başvurularını tam olarak niteleyebilirsiniz. Yalnızca kısmi başvuruda ayarlanmamış alanları belirtmek için **\<qualifyAssembly >** öğesini kullanın. **FullName** özniteliğinde listelenen derleme kimliği, derleme adını, ortak anahtarı, kültürü ve sürümü tam olarak nitelemek için gereken tüm bilgileri içermelidir.  
  
 Aşağıdaki örnek, `myAssembly`adlı bir derlemeyi tam olarak nitelendirmek için uygulama yapılandırma dosya girişini gösterir.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Bir derleme yükleme bildiriminde `myAssembly`her başvurduğunda, bu yapılandırma dosyası ayarları çalışma zamanının kısmen nitelenmiş `myAssembly` başvurusunu tam nitelikli bir başvuruya otomatik olarak çevirmesine neden olur. Örneğin, Assembly. Load ("myAssembly") derleme. Load ("myAssembly, Version = 1.0.0.0, publicKeyToken =..., Culture = neutral") olur.  
  
> [!NOTE]
> Genel derleme önbelleğinden kısmen Başvurulmuş derlemelerin yüklenmesini engelleyen ortak dil çalışma zamanı kısıtlamasını atlamak için **LoadWithPartialName** yöntemini kullanabilirsiniz. Bu yöntem, yan yana yürütmede sorunlara kolayca yol açabileceği için yalnızca uzaktan iletişim senaryolarında kullanılmalıdır.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Bir uygulamanın bir derlemenin belirli bir sürümüne nasıl bağlanacağını açıklar.|  
|[Bütünleştirilmiş Kod Bağlama Yönlendirmesini Yapılandırma](configuring-assembly-binding-redirection.md)|Derleme bağlama başvurularının nasıl belirli bir sürümdeki .NET Framework derlemelerine yeniden yönlendirildiğini açıklar.|  
|[İşlem İçi Yan Yana Yürütme](in-process-side-by-side-execution.md)|Tek bir işlemde CLR'nin birden çok sürümünü çalıştırılacak işlem içi yan yana çalışma zamanlı ana makine etkinleştirmenin nasıl kullanabileceğini açıklanır.|  
|[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)|Derlemeler üzerine kavramsal bir genel bakış sağlar.|  
|[Uygulama Etki Alanları](../app-domains/application-domains.md)|Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.|  
  
## <a name="reference"></a>Başvuru  

[\<supportedRuntime > öğesi](../configure-apps/file-schema/startup/supportedruntime-element.md)
