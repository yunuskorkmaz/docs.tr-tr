---
title: Çalışma Zamanının Derlemelerin Konumunu Bulması
ms.date: 03/30/2017
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 250e1764084ba3f7750867f2eea89e87cc7239eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342353"
---
# <a name="how-the-runtime-locates-assemblies"></a>Çalışma Zamanının Derlemelerin Konumunu Bulması
.NET Framework uygulamanızı başarıyla dağıtmak için ortak dil çalışma zamanının nasıl bulur ve uygulamanızı oluşturan derlemeleri bağlar anlamanız gerekir. Varsayılan olarak, çalışma zamanı tamamen aynı sürümünün uygulamanın derlendiği bir derleme ile bağlamak çalışır. Bu varsayılan davranışı yapılandırma dosyası ayarlarının tarafından geçersiz kılınabilir.  
  
 Ortak dil çalışma zamanının bir derlemeyi bulmak ve bir bütünleştirilmiş kod başvurusu çözmek çalışırken birkaç adımı gerçekleştirir. Her adım, aşağıdaki bölümlerde açıklanmıştır. Algılama dönemi genellikle, çalışma zamanı derlemeleri nasıl konumlandırır tanımlarken kullanılır; derlemenin adı ve kültür üzerinde bulmak için kullanılan bir buluşsal yöntem kümesi ifade eder.  
  
> [!NOTE]
>  Bağlama bilgileri kullanılarak günlük dosyasında görüntüleyebilirsiniz [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), içinde bulunan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
## <a name="initiating-the-bind"></a>Bağlama başlatma  
 Çalışma zamanı başka bir derlemeye başvuru çözümlemeye çalışırken bulmak ve bir bütünleştirilmiş kod bağlama işlemi başlar. Bu başvuru, statik veya dinamik olabilir. Derleme bildiriminin meta derleyici kayıtları statik başvuruları derleme zamanı. Dinamik başvuru oluşturulması gibi çeşitli yöntemleri çağırma sonucu olarak hareket halindeyken <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
 Bir derleme başvurusu için tercih edilen yol, derleme adı, sürüm, kültür ve ortak anahtar belirteci (varsa) dahil, tam bir başvuru kullanmaktır. Çalışma zamanı, daha sonra bu bölümde açıklanan adımları izleyerek bu derlemeyi bulmak için bu bilgileri kullanır. Çalışma zamanı için bir statik veya dinamik derleme başvurusu olmasına bakılmaksızın aynı çözümleme işlemi kullanır.  
  
 Ayrıca, yalnızca kısmi bilgiler gibi yalnızca derlemenin adını belirterek derleme hakkında çağırma yöntemi sağlayarak bir dinamik bir derlemeye başvuru yapabilirsiniz. Bu durumda, yalnızca uygulama dizini derlemeyi aranır ve hiçbir diğer denetim oluşur. Kısmi başvuru derlemeleri yüklemek için aşağıdaki gibi çeşitli yöntemlerden birini kullanarak yaptığınız <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.  
  
 Son olarak, aşağıdaki gibi bir yöntem kullanılarak dinamik başvuru yapabilirsiniz <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> ve yalnızca kısmi bilgiler; ardından başvurusu kullanarak uygun [ \<qualifyAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) uygulama öğesi yapılandırma dosyası. Bu öğenin tam başvuru bilgilerini sağlar (adı, sürüm, kültür ve uygunsa, ortak anahtar belirteci), uygulama yapılandırma dosyasında yerine kodunuzun içinde. Uygulama dizininin dışındaki bir derlemeye bir başvuru tam olarak nitelemek isterseniz veya genel derleme önbelleğindeki bir derleme başvurusu istedi, ancak tam başvuru belirtme kolaylık sağlamak istiyordu bu tekniği kullanması Kodunuzda yapılandırma dosyası yerine.  
  
> [!NOTE]
>  Bu kısmi başvuru türü birden fazla uygulama arasında paylaşılan derlemeler ile kullanılmamalıdır. Yapılandırma ayarları, uygulama başına uygulanır ve derleme her uygulamanın kendi yapılandırma dosyasında uygun bilgileri sağlamak için paylaşılan bir derleme kullanmakla bu türde bir kısmi başvuru kullanarak paylaşılan bir derleme gerek duymaz çünkü.  
  
 Çalışma zamanı bir bütünleştirilmiş kod başvurusu çözmek için aşağıdaki adımları kullanır:  
  
1. [Doğru derleme sürümünü belirler](#step1) uygulama yapılandırma dosyası, yayımcı ilkesi dosyası ve makine yapılandırma dosyası gibi geçerli yapılandırma dosyalarını inceleyerek. Yapılandırma dosyasını uzak makinede yer alıyorsa, çalışma zamanı bulun ve uygulama yapılandırma dosyasını indirmeniz gerekir.  
  
2. [Derleme adı için önce bağlı olup olmadığını denetler](#step2) ve bu durumda, daha önce yüklenen derleme kullanır. Assembly başarısız oldu yüklemek için önceki bir istek, istek hemen derleme yükleme girişimi başarısız oldu.  
  
    > [!NOTE]
    >  Derleme bağlamayı önbelleğe alma hataları, .NET Framework 2.0 sürümünde yenidir.  
  
3. [Genel derleme önbelleğini](#step3). Derleme var. bulunursa, çalışma zamanı Bu derlemeyi kullanır.  
  
4. [Derleme için araştırmaları](#step4) aşağıdaki adımları kullanarak:  
  
    1.  Yapılandırma ve yayımcı ilkesi özgün başvuruyu etkilemez ve bağlama isteği kullanılarak oluşturulmuşsa <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi, çalışma zamanı denetimleri için konum ipuçları.  
  
    2.  Bir kod temeli yapılandırma dosyalarında bulunması durumunda bu konum yalnızca çalışma zamanı denetler. Bu araştırma başarısız olursa, bağlama isteği başarısız oldu ve hiçbir diğer yoklama gerçekleşir çalışma zamanı belirler.  
  
    3.  Araştırmalar açıklanan buluşsal yöntemlerini kullanarak derleme [bölümü yoklama](#step4). Derleme araştırma bulunamazsa, çalışma zamanı derleme sağlamak için Windows Yükleyici ister. Bu, bir isteğe bağlı Yükleme özelliği olarak görev yapar.  
  
        > [!NOTE]
        >  Güçlü adı olmayan derlemeler için denetimi sürümü yoktur ve güçlü adı olmayan derlemeler için çalışma zamanı genel derleme önbelleğinde kontrol etmez.  
  
<a name="step1"></a>   
## <a name="step-1-examining-the-configuration-files"></a>1. Adım: Yapılandırma dosyalarını İnceleme  
 Derleme bağlama davranışı üç XML dosyalarını temel alan farklı düzeylerde yapılandırılabilir:  
  
-   Uygulama yapılandırma dosyası.  
  
-   Yayımcı ilkesi dosyası.  
  
-   Makine yapılandırma dosyası.  
  
 Bu dosyalar aynı sözdizimini izleyin ve bağlama yönlendirmeleri, kod, konumunu ve belirli derlemelerde modları bağlama gibi bilgiler sağlar. Her bir yapılandırma dosyası içerebilir bir [ \<assemblyBinding > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) , bağlama işlemini yeniden yönlendirir. Alt öğeleri [ \<assemblyBinding > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) dahil [ \<dependentAssembly > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md). Alt [ \<dependentAssembly > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) dahil [ \<assemblyIdentity > öğesi](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), [ \<bindingRedirect > öğe](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)ve [ \<codeBase > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
> [!NOTE]
>  Yapılandırma bilgilerini üç yapılandırma dosyalarında bulunabilir. tüm öğeleri tüm yapılandırma dosyalarında geçerli değil. Örneğin, modu ve özel yol bilgisi bağlama yalnızca uygulama yapılandırma dosyasında olabilir. Her dosyada yer alan bilgilerin tam listesi için bkz. [yapılandırma dosyalarını kullanarak uygulamaların yapılandırma](../../../docs/framework/configure-apps/index.md).  
  
### <a name="application-configuration-file"></a>Uygulama yapılandırma dosyası  
 İlk olarak, ortak dil çalışma zamanı arama derlemenin bildirimine depolanan sürüm bilgilerini geçersiz kılan bilgi için uygulama yapılandırma dosyasına denetler. Uygulama yapılandırma dosyası uygulama ile dağıtılabilir, ancak uygulama yürütme için gerekli değildir. Genellikle bu dosyayı alınmasını neredeyse anında, ancak uygulama temel uzak bir bilgisayarda olduğu durumlarda, gibi Internet Explorer Web tabanlı bir senaryoda, yapılandırma dosyasını indirilen gerekir.  
  
 İstemci yürütülebilir dosyaları, uygulama yapılandırma dosyası uygulamanın yürütülebilir dosya ile aynı dizinde bulunan ve .config uzantısına sahip bir yürütülebilir dosya olarak aynı temel ada sahiptir. Örneğin, C:\Program Files\Myapp\Myapp.exe yapılandırma dosyası C:\Program Files\Myapp\Myapp.exe.config ' dir. Tarayıcı tabanlı bir senaryoda HTML dosyasını kullanmanız gerekir  **\<bağlantı >** açıkça yapılandırma dosyasına işaret edecek şekilde öğesi.  
  
 Aşağıdaki kod, bir uygulama yapılandırma dosyası, basit bir örnek sağlar. Bu örnek ekler bir <xref:System.Diagnostics.TextWriterTraceListener> için <xref:System.Diagnostics.Debug.Listeners%2A> kaydı hata ayıklama bilgileri bir dosyaya etkinleştirmek için koleksiyon.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
### <a name="publisher-policy-file"></a>Yayımcı ilkesi dosyası  
 İkinci olarak, varsa Yayımcı ilkesi dosyası, çalışma zamanı inceler. Yayımcı ilke dosyaları, bir düzeltme veya güncelleştirmenin paylaşılan bir bileşen için bileşen yayıncıya dağıtılır. Bu dosyalar bir bütünleştirilmiş kod başvurusu yeni bir sürüme yönlendiren paylaşılan bileşen yayımcısı tarafından verilen uyumluluk bilgilerini içerir. Uygulama ve makine yapılandırma dosyalarını farklı olarak, kendi derleme genel derleme önbelleğine yüklenmelidir Yayımcı ilkesi dosyaları yer alır.  
  
 Bir yayımcı ilkesi yapılandırma dosyası örneği verilmiştir:  
  
```xml  
<configuration>  
    <runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
  
            <dependentAssembly>  
                <assemblyIdentity name="asm6" publicKeyToken="c0305c36380ba429" />   
                <bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0"/>    
            </dependentAssembly>  
  
        </assemblyBinding>  
    </runtime>  
</configuration>  
```  
  
 Bir derleme oluşturmak için kullanabileceğiniz [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md) aracı aşağıdaki gibi bir komut ile:  
  
```  
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0  
```  
  
 `compatkey.dat` bir tanımlayıcı ad anahtar dosyası var. Bu komut, genel derleme önbelleğinde yerleştirebilirsiniz tanımlayıcı adlı bir derleme oluşturur.  
  
> [!NOTE]
>  Yayımcı ilkesi paylaşılan bileşen kullanan tüm uygulamaları etkiler.  
  
 Yayımcı ilkesi yapılandırma dosyası, uygulamadan gelen sürüm bilgileri geçersiz kılar (diğer bir deyişle, derleme bildirimi ya da uygulama yapılandırma dosyası). Yayımcı ilkesi dosyası derleme bildiriminde belirtilen sürümü yeniden yönlendirmek için uygulama yapılandırma dosyasında herhangi bir deyimi yoksa, derleme bildiriminde belirtilen sürümü geçersiz kılar. Uygulama yapılandırma dosyasında bir yeniden yönlendirme deyimi varsa, ancak Yayımcı ilkesi bildiriminde belirtilen yerine bu sürümü geçersiz kılar.  
  
 Yayımcı ilkesi dosyası, paylaşılan bir bileşen olarak güncellenir ve o bileşen kullanan tüm uygulamalar tarafından çekilmesi gereken paylaşılan bileşenin yeni sürümünü kullanılır. Uygulama yapılandırma dosyasına güvenli mod zorunlu olmadıkça Yayımcı ilkesi dosyası ayarları uygulama yapılandırma dosyasında ayarları geçersiz kılar.  
  
#### <a name="safe-mode"></a>Güvenli mod  
 Yayımcı ilke dosyaları genellikle açıkça bir hizmet paketi veya program güncelleştirmenin bir parçası yüklenir. Yükseltilen bir paylaşılan bileşen herhangi bir sorun varsa, güvenli mod ile Yayımcı ilkesi dosyası geçersiz kılmaları yoksayabilirsiniz. Güvenli mod göre belirlenir  **\<publisherPolicy uygulama = "Evet**&#124;**yok" / >** öğesi, yalnızca uygulama yapılandırma dosyasında bulunur. Bu yayımcı ilkesi yapılandırma bilgilerini bağlama işlemden kaldırılması gerekip gerekmediğini belirtir.  
  
 Güvenli mod, uygulamanın tamamı için veya seçili derlemeler için ayarlanabilir. Diğer bir deyişle, uygulamayı oluşturan tüm derlemeleri için ilkesini etkinleştirmek ya da bazı derlemeler ancak diğerlerini açın. Bir uygulamayı oluşturan derlemeleri seçerek yayımcı ilkesini uygulamak için ayarlama  **\<publisherPolicy uygulamak\=yok / >** ve istediğiniz kullanarak etkilendiği için hangi derlemelerin belirtin \< **dependentAssembly**> öğesi. Uygulamayı oluşturan tüm derlemeleri yayımcı ilkesini uygulamak için ayarlanmış  **\<publisherPolicy uygulamak\=yok / >** ile herhangi bir bağımlı derleme öğesi. Yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](../../../docs/framework/configure-apps/index.md).  
  
### <a name="machine-configuration-file"></a>Makine yapılandırma dosyası  
 Üçüncü olarak, çalışma zamanı, makine yapılandırma dosyasını inceler. Machine.config, adlı bu dosya, yerel bilgisayarda yapılandırma alt çalışma zamanının yüklendiği kök dizininde bulunur. Bu dosya, o bilgisayarın yerel bütünleştirilmiş kod bağlama kısıtlamaları belirtmek için yöneticiler tarafından kullanılabilir. Makine yapılandırma dosyasındaki ayarları diğer tüm yapılandırma ayarlarını öncelik kazanır; Ancak, bu tüm yapılandırma ayarlarını bu dosyada yerleştirileceği anlamına gelmez. Yönetici ilke dosyası tarafından belirlenen sürüm kalıcıdır ve geçersiz kılınamaz. Geçersiz kılmalar Machine.config dosyasında belirtilen tüm uygulamaları etkiler. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](../../../docs/framework/configure-apps/index.md).  
  
<a name="step2"></a>   
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>2. Adım: İçin önceden başvurulan derlemeleri denetleme  
 İstenen derlemeyi, önceki çağrılarında istendi, ortak dil çalışma zamanı zaten yüklü olan derleme kullanır. Bir uygulamayı oluşturan derlemeleri adlandırırken bu sonuçları olabilir. Adlandırma derlemeler hakkında daha fazla bilgi için bkz. [derleme adları](../../../docs/framework/app-domains/assembly-names.md).  
  
 Önceki bir istek, başarısız derleme için sonraki istekleri için derleme derleme yükleme girişimi olmadan hemen getirilir. .NET Framework sürüm 2.0 ile başlayarak, derleme bağlama hataları önbelleğe alınır ve önbelleğe alınan bilgileri derlemenin yüklemeye belirlemek için kullanılır.  
  
> [!NOTE]
>  .NET Framework sürümleri 1.0 ve 1.1, bağlama hataları önbelleğe, davranıştır geri eklenecek [ \<disableCachingBindingFailures > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) yapılandırma dosyanızdaki.  
  
<a name="step3"></a>   
## <a name="step-3-checking-the-global-assembly-cache"></a>3. Adım: Genel derleme önbelleğini denetleme  
 Tanımlayıcı adlı derlemeler için genel derleme önbelleğinde bakarak bağlama işlemi devam ediyor. Bir bilgisayarda çeşitli uygulamalar tarafından kullanılan derlemeler genel derleme önbelleği depolar. Genel derleme önbelleğindeki derlemelerin tanımlayıcı adlara sahip olmalıdır.  
  
<a name="step4"></a>   
## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>4. Adım: Aracılığıyla derlemenin kod tabanlarında bulma veya algılama  
 Çağıran derleme başvurusu ve yapılandırma dosyalarındaki bilgileri kullanarak doğru derleme sürümünü belirlendikten sonra ve (yalnızca katı adlı derlemeler için), genel derleme önbelleğinde denetledi sonra ortak dil çalışma zamanı, derlemeyi bulmayı dener. Bütünleştirilmiş bulma işlemi aşağıdaki adımları içerir:  
  
1. Varsa bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi, çalışma zamanı denetimleri belirtilen konuma uygulama yapılandırma dosyasında bulunur. Bir eşleşme bulunursa, o derleme kullanılır ve hiçbir yoklama gerçekleşir. Derleme var. bulunmazsa, bağlama isteği başarısız olur.  
  
2. Çalışma zamanı, ardından daha sonra bu bölümde belirtilen kurallarını kullanarak başvurulan derlemenin araştırmaları.  
  
> [!NOTE]
>  Birden çok derleme sürümünü bir dizinde sahip ve bu derlemenin belirli bir sürümünü başvurmak istediğiniz, kullanmalısınız [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğe yerine `privatePath` özniteliği[ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi. Kullanırsanız [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi, çalışma zamanı durdurur doğru bir eşleşme olup olmadığına bakılmaksızın, başvurulan, basit bir derleme adıyla eşleşen bir derleme bulduğu ilk kez algılanıyor. Bu derleme, doğru bir eşleşme varsa kullanılır. Doğru bir eşleşme değilse, yoklama durdurur ve bağlama başarısız olur.  
  
### <a name="locating-the-assembly-through-codebases"></a>Kod tabanlarında aracılığıyla derlemenin bulma  
 Kod tabanı kullanarak bilgi sağlanabilir bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi bir yapılandırma dosyası. Başvurulan bütünleştirilmiş kod araştırma çalışma zamanı çalışmadan önce bu kod temelinin kontrol edilir. Son sürümüne yeniden yönlendirme de içeren bir yayımcı ilkesi dosyası varsa bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi, [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) kullanılan bir öğedir. Örneğin, uygulama yapılandırma dosyanızı belirten bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi ve uygulama bilgilerini geçersiz kılan bir yayımcı ilkesi dosyası ayrıca belirtir bir [ \< codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) Yayımcı ilkesi dosyası öğesinde kullanılır.  
  
 Tarafından belirtilen konumda eşleşme bulunursa [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi, bağlama isteği başarısız olur ve başka bir adım alınır. Çalışma zamanının bir derlemeyi çağıran derlemeye ait ölçütleriyle eşleşen belirlerse, bu derleme kullanır. Dosya belirtildiği zaman tarafından verilen [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi yüklenir, kullanıcının adı, sürüm, kültür ve ortak anahtar çağıran derlemeye eşleştiğinden emin olmak için başvuru çalışma zamanı denetimleri.  
  
> [!NOTE]
>  Başvurulan derlemeler uygulamanın kök dizini dışına güçlü adlar olmalıdır ve genel derleme önbelleğine yüklenmelidir ya da kullanarak belirtilen [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi.  
  
### <a name="locating-the-assembly-through-probing"></a>Algılama aracılığıyla derlemenin bulma  
 Yoksa hiçbir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi uygulama yapılandırma dosyasında, çalışma zamanı araştırmaları dört ölçütleri kullanarak bütünleştirilmiş kod:  
  
-   Uygulamayı nerede yürütülmekte olduğu kök konumu uygulama tabanı.  
  
-   Kültür, başvurulan derleme kültürü özniteliğidir.  
  
-   Adı, başvurulan derlemenin adıdır.  
  
-   `privatePath` Özniteliği [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) kök konumu altında alt dizinler kullanıcı tanımlı liste öğesi. Bu konum uygulama yapılandırma dosyasında ve yönetilen kod kullanarak belirtilen <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> uygulama etki alanı özelliği. Yönetilen kodda, yönetilen kod belirtildiğinde `privatePath` ilk araştırıldığı, uygulama yapılandırma dosyasında belirtilen yol izlediği.  
  
#### <a name="probing-the-application-base-and-culture-directories"></a>Kültür dizinleri ve uygulama temel algılama  
 Çalışma zamanı, her zaman bir URL veya uygulamanın kök dizini bir bilgisayarda olabilen uygulamanın Base yoklama başlar. Uygulama tabanı başvurulan derleme bulunamadı ve kültür bilgisi yok sağlanan, çalışma zamanı derleme adı ile alt dizinleri arar. Araştırılan dizinler şunlardır:  
  
 [uygulama tabanı] / [derleme adı] .dll  
  
 [uygulama tabanı] / [derleme adı] / [derleme adı] .dll  
  
 Başvurulan bütünleştirilmiş kod kültür bilgilerini belirtilmediği takdirde, sadece aşağıdaki dizinlerin araştırıldığı:  
  
 [uygulama tabanı] / [kültür] / [derleme adı] .dll  
  
 [uygulama tabanı] / [kültür] / [derleme adı] / [derleme adı] .dll  
  
#### <a name="probing-with-the-privatepath-attribute"></a>Öznitelik privatePath algılama  
 Kültür alt dizinleri ve başvurulan bütünleştirilmiş kod adında alt ek olarak, çalışma zamanı ayrıca kullanarak belirtilen dizinlerde araştırmaları `privatePath` özniteliği [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi. Kullanarak belirtilen dizinlerde `privatePath` özniteliği, uygulamanın kök dizininin alt dizinleri olmalıdır. Araştırılan dizinleri olup kültür bilgilerini başvurulan derleme isteğinde bağlı olarak farklılık gösterir.  
  
 Çalışma zamanı, doğru bir eşleşme olup olmadığına bakılmaksızın, başvurulan, basit bir derleme adıyla eşleşen bir derleme bulduğu ilk kez yoklama durdurur. Bu derleme, doğru bir eşleşme varsa kullanılır. Doğru bir eşleşme değilse, yoklama durdurur ve bağlama başarısız olur.  
  
 Kültür dahil ise, aşağıdaki dizinlerin araştırıldığı:  
  
 [uygulama tabanı] / [binpath] / [kültür] / [derleme adı] .dll  
  
 [uygulama tabanı] / [binpath] / [kültür] / [derleme adı] / [derleme adı] .dll  
  
 Kültür bilgilerini dahil edilmezse, aşağıdaki dizinlerin araştırıldığı:  
  
 [uygulama tabanı] / [binpath] / [derleme adı] .dll  
  
 [uygulama tabanı] / [binpath] / [derleme adı] / [derleme adı] .dll  
  
#### <a name="probing-examples"></a>Örneklerini yoklama  
 Verilen aşağıdaki bilgilerle:  
  
-   Başvurulan bütünleştirilmiş kod adı: myAssembly  
  
-   Uygulama kök dizini: `http://www.code.microsoft.com`  
  
-   [\<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi yapılandırma dosyasında belirtir: depo  
  
-   Kültür: Gizle  
  
 Çalışma zamanı, aşağıdaki URL'ler araştırmaları:  
  
 `http://www.code.microsoft.com/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`
  
##### <a name="multiple-assemblies-with-the-same-name"></a>Aynı ada sahip birden çok derleme  
 Aşağıdaki örnek, aynı ada sahip birden çok derleme yapılandırma gösterilmektedir.  
  
```xml  
<dependentAssembly>  
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />   
   <codeBase version="1.0.0.0" href="v1/Server.dll" />  
   <codeBase version="2.0.0.0" href="v2/Server.dll" />  
</dependentAssembly>  
```  
  
#### <a name="other-locations-probed"></a>Araştırılan diğer konumlar  
 Bütünleştirilmiş kod konumu ayrıca geçerli bağlama içeriğini kullanarak belirlenebilir. Bu genellikle gerçekleşir, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi kullanılır ve COM birlikte çalışabilirlik senaryolarında. Bir derlemeyi kullanıyorsa <xref:System.Reflection.Assembly.LoadFrom%2A> başka bir derlemeye başvuru yöntemi çağıran derlemenin konumunu başvurulan derlemeyi nerede bulacağını hakkında bir ipucu olarak kabul edilir. Bu derleme, bir eşleşme bulunursa yüklenir. Eşleşme bulunursa, çalışma zamanı, arama semantik ile devam eder ve derleme sağlamak için Windows Installer'ı sorgular. Derleme bağlama isteğini eşleşen sağlanmazsa, bir özel durum oluşturulur. Bu özel durum bir <xref:System.TypeLoadException> bir tür başvurulan, yönetilen kodda veya <xref:System.IO.FileNotFoundException> , yüklenen derleme bulunamadı.  
  
 Assembly1 Assembly2 ve Assembly1 başvuruyorsa, indirildiğini `http://www.code.microsoft.com/utils`, konum Assembly2.dll nerede bulunacağı hakkında bir ipucu olarak değerlendirilir. Çalışma zamanı sonra derlemede için araştırmaları `http://www.code.microsoft.com/utils/Assembly2.dll` ve `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`. Çalışma zamanı, Assembly2 konumların birini bulunmazsa, Windows Installer sorgular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Dağıtım](../../../docs/framework/deployment/index.md)
