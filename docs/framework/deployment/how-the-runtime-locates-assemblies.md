---
title: Çalışma Zamanının Derlemelerin Konumunu Bulması
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e154e0658534018ccd1086631cad6d350528b5d
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="how-the-runtime-locates-assemblies"></a>Çalışma Zamanının Derlemelerin Konumunu Bulması
.NET Framework uygulamanız başarıyla dağıtmak için ortak dil çalışma zamanı nasıl bulur ve uygulamayı oluşturan derlemeler bağlar anlamanız gerekir. Varsayılan olarak, çalışma zamanı, uygulama ile oluşturulmuş bir derlemenin tam sürümü ile bağlamak çalışır. Bu varsayılan davranışı yapılandırma dosyası ayarları tarafından geçersiz kılınabilir.  
  
 Ortak dil çalışma zamanı bütünleştirilmiş bulun ve bir derleme başvurusu çözmek çalışırken çeşitli adımları gerçekleştirir. Her adım aşağıdaki bölümlerde açıklanmıştır. Yoklama terimi genellikle nasıl çalışma zamanının derlemelerin konumunu bulması açıklanırken kullanılır; buluşsal yöntemler, adı ve kültür temel alarak derleme bulmak için kullanılan kümesini ifade eder.  
  
> [!NOTE]
>  Bağlama bilgileri kullanılarak günlük dosyasında görüntüleyebilirsiniz [Derleme bağlaması Günlük Görüntüleyici (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), içinde bulunan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
## <a name="initiating-the-bind"></a>Bağ başlatılıyor  
 Çalışma zamanı başka bir derleme başvurusu çözümlemeye çalışırken bulmak ve bir derlemeye bağlama işlemi başlar. Bu başvuru, statik veya dinamik olabilir. Derleme süresi sırasında derleme bildirim meta verilerde başvurularını statik derleyici kaydeder. Dinamik başvuruları kolay bir şekilde gibi çeşitli yöntemleri çağırma sonucu olarak oluşturulan <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
 Bir derleme başvurusu için tercih edilen yol (varsa) derleme adı, sürüm, kültür ve ortak anahtar belirteci dahil olmak üzere, tam bir başvuru kullanmaktır. Çalışma zamanı bu bilgiler daha sonra bu bölümde açıklanan adımları izleyerek derleme bulmak için kullanır. Çalışma zamanı için bir statik veya dinamik derleme başvurusu olmasına bakılmaksızın aynı çözümleme işlemi kullanır.  
  
 Arama yöntemi yalnızca derleme adını belirtme gibi derleme, yalnızca kısmi bilgilerini sağlayarak, bir derlemeyi dinamik başvuru duruma getirebilirsiniz. Bu durumda, yalnızca uygulama dizini için derleme aranır ve hiçbir diğer denetimi gerçekleştirilir. Derlemeleri gibi yükleme için çeşitli yöntemlerden birini kullanarak kısmi bir başvuru yaptığınız <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.  
  
 Son olarak, bir yöntem kullanılarak dinamik bir başvuru yapabileceğiniz <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> yalnızca kısmi bilgi; ardından başvuru kullanarak nitelemek [ \<qualifyAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) uygulama öğesinde yapılandırma dosyası. Bu öğe, tam başvuru bilgileri sağlamanıza olanak verir (ad, sürüm, kültür ve (varsa), ortak anahtar belirteci), uygulama yapılandırma dosyasında yerine kodunuzu. Bu teknik başvuru uygulama dizininin dışındaki bir derleme tam olarak nitelemek istediyseniz veya genel derleme önbelleğindeki bir derleme başvurusu istedi, ancak tam başvurusunda belirtmenin kolaylık sağlamak isteyen kullanırsınız yapılandırma dosyasında yerine kodunuzu.  
  
> [!NOTE]
>  Bu tür bir kısmi başvuru çeşitli uygulamalar arasında paylaşılan derlemeler ile kullanılmamalıdır. Yapılandırma ayarları yok derleme başına ve uygulama başına uygulandığından, bu türde bir kısmi başvuru kullanarak paylaşılan bir derleme, yapılandırma dosyasında uygun bilgileri sağlamak için paylaşılan derlemeyi kullanarak her bir uygulama gerektirir.  
  
 Çalışma zamanı, bir derleme başvurusu çözmek için aşağıdaki adımları kullanır:  
  
1.  [Doğru derleme sürümünü belirler](#step1) geçerli yapılandırma dosyalarını inceleyerek, uygulama yapılandırma dosyası, yayımcı ilkesi dosyası ve makine yapılandırma dosyası dahil. Yapılandırma dosyası uzak makinede yer alıyorsa, çalışma zamanı bulun ve ilk uygulama yapılandırma dosyasını indirin.  
  
2.  [Derleme adı için önce bağlı olup olmadığını denetler](#step2) ve bu durumda, önceden yüklenen derleme kullanır. Assembly başarısız oldu yüklemek için önceki bir istek, isteği hemen derleme yüklenmeye çalışılıyor olmadan başarısız oldu.  
  
    > [!NOTE]
    >  Derleme bağlama önbelleğe alma hataları, .NET Framework 2.0 sürümünde yenidir.  
  
3.  [Genel derleme önbelleği denetler](#step3). Derleme var. bulunursa, çalışma zamanı bu derleme kullanır.  
  
4.  [Derleme için yoklamaları](#step4) aşağıdaki adımları kullanarak:  
  
    1.  Yapılandırma ve yayımcı ilkesi özgün başvuru etkilemez ve bağlanma isteği kullanarak oluşturduysanız <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi, çalışma zamanı için konum ipuçları denetler.  
  
    2.  Yapılandırma dosyalarında bir codebase bulunursa, çalışma zamanı bu konum yalnızca denetler. Bu araştırma başarısız olursa, çalışma zamanı belirler: bağlama isteği başarısız oldu ve hiçbir diğer yoklama oluşur.  
  
    3.  Yoklamaları açıklanan buluşsal yöntemler kullanılarak derleme için [bölüm yoklama](#step4). Derleme yoklama sonra bulunamazsa çalışma zamanı derlemesi sağlamak için Windows Installer ister. Bu, bir isteğe bağlı Yükleme özelliği olarak işlev görür.  
  
        > [!NOTE]
        >  Tanımlayıcı adlar olmadan derlemeler için denetimi sürümü yoktur ve çalışma zamanı genel derleme önbelleğinde derlemeleri tanımlayıcı adlar olmadan denetlemez.  
  
<a name="step1"></a>   
## <a name="step-1-examining-the-configuration-files"></a>Adım 1: Yapılandırma Dosyalarını İnceleme  
 Derleme bağlama davranışı üç XML dosyalarını temel alan farklı düzeylerde yapılandırılabilir:  
  
-   Uygulama yapılandırma dosyası.  
  
-   Yayımcı ilke dosyası.  
  
-   Makine yapılandırma dosyası.  
  
 Bu dosyalar aynı sözdizimini izleyin ve bağlama yeniden yönlendirmeleri, kod, konumunu ve modları için belirli derlemeleri bağlama gibi bilgiler sağlar. Her yapılandırma dosyasında içerebilir bir [ \<assemblyBinding > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) bağlama işlemi yönlendirir. Alt öğeleri [ \<assemblyBinding > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) dahil [ \<dependentAssembly > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md). Alt [ \<dependentAssembly > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) dahil [ \<assemblyIdentity > öğesi](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), [ \<bindingRedirect > öğe](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)ve [ \<codeBase > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
> [!NOTE]
>  Yapılandırma bilgilerini üç yapılandırma dosyalarında bulunabilir; tüm öğeleri tüm yapılandırma dosyalarını geçerlidir. Örneğin, modu ve özel yol bilgisi bağlama yalnızca uygulama yapılandırma dosyasında olabilir. Her dosyasında yer alan bilgileri tam bir listesi için bkz: [yapılandırma uygulamaları kullanarak yapılandırma dosyaları tarafından](../../../docs/framework/configure-apps/index.md).  
  
### <a name="application-configuration-file"></a>Uygulama yapılandırma dosyası  
 İlk olarak, ortak dil çalışma zamanı arama derlemenin bildiriminde depolanan sürüm bilgileri geçersiz kılmalar bilgi için uygulama yapılandırma dosyasını denetler. Uygulama yapılandırma dosyasına sahip bir uygulama dağıtılabilir, ancak uygulama yürütme için gerekli değildir. Genellikle bu dosya alma neredeyse anlık olarak ancak uygulama temel bir uzak bilgisayarda olduğu durumlarda gibi Internet Explorer Web tabanlı bir senaryo, yapılandırma dosyasını karşıdan yüklenmesi gerekir.  
  
 İstemci yürütülebilir dosyaları için uygulama yapılandırma dosyası uygulamanın yürütülebilir dosya ile aynı dizinde bulunan ve temel yürütülebilir aynı adı taşıyan bir .config uzantılı vardır. Örneğin, C:\Program Files\Myapp\Myapp.exe için yapılandırma dosyası C:\Program Files\Myapp\Myapp.exe.config olur. Tarayıcı tabanlı bir senaryoda HTML dosyasını kullanmanız gerekir  **\<bağlantı >** açıkça yapılandırma dosyasına işaret edecek şekilde öğesi.  
  
 Aşağıdaki kod, bir uygulama yapılandırma dosyasının basit bir örnek sağlar. Bu örnek, bir <xref:System.Diagnostics.TextWriterTraceListener> için <xref:System.Diagnostics.Debug.Listeners%2A> kaydı hata ayıklama bilgileri bir dosyaya etkinleştirmek için koleksiyonu.  
  
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
  
### <a name="publisher-policy-file"></a>Yayımcı ilke dosyası  
 İkinci olarak, varsa, çalışma zamanı Yayımcı ilkesi dosyası inceler. Yayımcı ilke dosyaları, bir düzeltme veya güncelleştirmenin paylaşılan bir bileşen için bileşen yayıncıya göre dağıtılır. Bu dosyalar bir derleme başvurusu yeni bir sürüme yönlendirir paylaşılan bileşen yayımcısı tarafından verilen uyumluluk bilgilerini içerir. Uygulama ve makine yapılandırma dosyaları aksine, yayımcı ilke dosyaları genel derleme önbelleğinde yüklenmelidir kendi derlemesindeki yer alır.  
  
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
  
 Bir derlemeyi oluşturmak için kullanabileceğiniz [Al.exe (derleme bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md) aşağıdaki gibi bir komut aracıyla:  
  
```  
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0  
```  
  
 `compatkey.dat` Güçlü ad anahtar dosyası değil. Bu komut, genel derleme önbelleğinde yerleştirebilirsiniz tanımlayıcı adlı bir derleme oluşturur.  
  
> [!NOTE]
>  Yayımcı ilkesi paylaşılan bir bileşen kullanan tüm uygulamaları etkiler.  
  
 Yayımcı ilkesi yapılandırma dosyası uygulamadan gelen sürüm bilgileri geçersiz kılmalar (diğer bir deyişle, derleme bildirimi veya uygulama yapılandırma dosyası). Derleme bildiriminde belirtilen sürüm yönlendirmek için uygulama yapılandırma dosyasında deyimi yok ise, yayımcı ilkesi dosyası derleme bildiriminde belirtilen sürümü geçersiz kılar. Uygulama yapılandırma dosyasına yeniden yönlendiriliyor deyiminde varsa, ancak Yayımcı ilkesi bildiriminde belirtilen bir yerine bu sürümü geçersiz kılar.  
  
 Yayımcı ilke dosyasını paylaşılan bir bileşen güncelleştirilir ve bu bileşen kullanan tüm uygulamalar tarafından çekilmesi gereken paylaşılan bileşen yeni sürümü olduğunda kullanılır. Uygulama yapılandırma dosyası güvenli mod zorlar sürece Yayımcı ilkesi dosyasındaki ayarları uygulama yapılandırma dosyasında ayarları geçersiz kılar.  
  
#### <a name="safe-mode"></a>Güvenli mod  
 Yayımcı ilke dosyaları genellikle açıkça bir hizmet paketi veya program güncelleştirmesi bir parçası olarak yüklenir. Yükseltilen paylaşılan bileşeni ile herhangi bir sorun varsa, güvenli mod ile Yayımcı ilkesi dosyasında geçersiz kılmaları yoksayabilirsiniz. Güvenli mod belirlenir  **\<publisherPolicy uygulamak = "Evet**&#124;**yok" / >** öğesi, yalnızca uygulama yapılandırma dosyasında bulunur. Yayımcı ilkesi yapılandırma bilgilerini bağlama işleminden kaldırılması gerekip gerekmediğini belirtir.  
  
 Güvenli mod, tüm uygulama veya seçili derlemeler için ayarlanabilir. Diğer bir deyişle, uygulamayı oluşturan tüm derlemeler için ilke devre dışı bırakma ya da bazı derlemeleri ancak diğer açın. Bir uygulamayı oluşturan derlemeler seçerek Yayımcı ilkesi uygulamak için ayarlanmış  **\<publisherPolicy uygulamak\=hiçbir / >** ve istediğiniz kullanarak etkilenecek hangi derlemelerin belirtin \< **dependentAssembly**> öğesi. Uygulamayı oluşturan tüm derlemelerde Yayımcı ilkesi uygulamak için ayarlanmış  **\<publisherPolicy uygulamak\=hiçbir / >** bağımlı derlemenin öğe ile. Yapılandırması hakkında daha fazla bilgi için bkz: [yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](../../../docs/framework/configure-apps/index.md).  
  
### <a name="machine-configuration-file"></a>Makine yapılandırma dosyası  
 Üçüncü, çalışma zamanı makine yapılandırma dosyası inceler. Machine.config adlı bu dosya yerel bilgisayarda Config alt çalışma zamanı yüklendiği kök dizininde bulunur. Bu dosya, o bilgisayarın yerel derleme bağlama kısıtlamaları belirtmek için yöneticiler tarafından kullanılabilir. Makine yapılandırma dosyası ayarlarında diğer tüm yapılandırma ayarlarını öncelik kazanır; Ancak, bu tüm yapılandırma ayarlarını bu dosyada sokulmalıdır anlamına gelmez. Yönetici ilke dosyası tarafından belirlenen sürüm son ve değiştirilemiyor. Machine.config dosyasında belirtilen geçersiz kılmalar, tüm uygulamaları etkiler. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](../../../docs/framework/configure-apps/index.md).  
  
<a name="step2"></a>   
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Adım 2: Önceden Başvurulan Derlemeleri Denetleme  
 İstenen derlemeyi, önceki çağrılarında istendi, ortak dil çalışma zamanı önceden yüklenen derleme kullanır. Bir uygulamayı oluşturan derlemeler adlandırırken bu ayrımlar olabilir. Adlandırma derlemeler hakkında daha fazla bilgi için bkz: [derleme adları](../../../docs/framework/app-domains/assembly-names.md).  
  
 Önceki bir istek için assembly başarısız oldu, sonraki istekleri derleme için hemen derleme yüklenmeye çalışılıyor olmadan başarısız. .NET Framework sürüm 2.0 ile başlayarak, derleme bağlama hataları önbelleğe alınır ve önbelleğe alınan bilgileri derleme yükleme denemesi verilmeyeceğini belirlemek için kullanılır.  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 ve 1.1 bağlama hataları önbelleğe almaz, davranışa geri dönmek için dahil [ \<disableCachingBindingFailures > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) yapılandırma dosyanızda.  
  
<a name="step3"></a>   
## <a name="step-3-checking-the-global-assembly-cache"></a>Adım 3: Genel Derleme Önbelleğini Denetleme  
 Tanımlayıcı adlı derlemeler için genel derleme önbelleğinde bakarak bağlama işlemi devam eder. Genel Derleme Önbelleği bir bilgisayarda çeşitli uygulamalar tarafından kullanılan derlemelerini depolar. Tüm derlemeleri genel derleme önbelleğinde güçlü adlara sahip olmalıdır.  
  
<a name="step4"></a>   
## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Adım 4: Kod Temelleri veya Algılama Aracılığıyla Derlemenin Konumunu Bulma  
 Arama derleme başvurusu'nda ve yapılandırma dosyalarında bilgileri kullanarak doğru derleme sürümünü belirlendikten sonra ve (yalnızca tanımlayıcı adlı derlemeler için), genel derleme önbelleğinde denetledi sonra ortak dil çalışma zamanı derlemesi bulmaya çalışır. Bir derlemeyi bulma işlemi aşağıdaki adımları içerir:  
  
1.  Varsa bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi bulundu uygulama yapılandırma dosyasında belirtilen konum çalışma zamanı denetler. Bir eşleşme bulunamazsa, hiçbir yoklama oluşur ve bu derleme kullanılır. Derleme var. bulunamadı bağlama isteği başarısız olur.  
  
2.  Çalışma zamanı sonra bu bölümde daha sonra belirtilen kuralları kullanarak başvurulan derlemeyi araştırmalar.  
  
> [!NOTE]
>  Bir dizindeki bir derleme birden çok sürümünün yüklü ve bu derleme belirli bir sürümü başvuru yapmak istediğinizi, kullanmalısınız [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi yerine `privatePath` özniteliği[ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi. Kullanırsanız [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi, çalışma zamanı durdurur başvurulan, basit derleme adı doğru bir eşleşme olup olmadığına bakılmaksızın eşleşen bir derlemeyi bulduğu ilk kez algılanıyor. Bu derleme doğru bir eşleşme varsa kullanılır. Doğru bir eşleşme değil yoklama durdurur ve bağlama başarısız olur.  
  
### <a name="locating-the-assembly-through-codebases"></a>Derleme aracılığıyla bulma olarak kullanılabilecek kod temeli  
 Codebase kullanarak bilgi sağlanabilir bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi bir yapılandırma dosyası. Başvurulan bütünleştirilmiş kod araştırma çalışma zamanı çalışmadan önce bu codebase her zaman denetlenir. Son sürüme yeniden yönlendirme de içeren bir yayımcı ilkesi dosya içeriyorsa bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi, [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) kullanılan bir öğedir. Örneğin, uygulama yapılandırma dosyanızı belirten bir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi ve uygulama bilgilerini geçersiz kılma bir yayımcı ilkesi dosyası ayrıca belirtir bir [ \< codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi, [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğe Yayımcı ilkesi dosyası kullanılır.  
  
 Eşleşme tarafından belirtilen konumda bulunursa [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi, bağlanma isteği başarısız olur ve başka bir adım alınır. Çalışma zamanı bütünleştirilmiş arama derlemenin ölçütlerle eşleşen belirlerse, bu derleme kullanır. Dosya belirtildiği zaman tarafından verilen [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi yüklenir, kullanıcının adı, sürüm, kültür ve ortak anahtar çağrıyı yapan derlemeyi eşleştiğinden emin olmak için başvuru çalışma zamanı denetler.  
  
> [!NOTE]
>  Başvurulan derlemeler uygulama kök dizini dışındaki güçlü adlara sahip olmalıdır ve genel derleme önbelleğinde ya da yüklü olmalıdır veya kullanarak belirtilen [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) öğesi.  
  
### <a name="locating-the-assembly-through-probing"></a>Yoklama aracılığıyla derleme bulma  
 Varsa hiçbir [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) uygulama yapılandırma dosyası öğesi, çalışma zamanı yoklamaları dört ölçütleri kullanarak derleme için:  
  
-   Uygulama burada yürütülmekte olduğu kök konumu uygulama tabanı.  
  
-   Kültür başvurulan derleme kültür özniteliğidir.  
  
-   Adı, başvurulan derlemeyi adıdır.  
  
-   `privatePath` Özniteliği [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) kök konumu dizinler kullanıcı tanımlı listesi öğesi. Bu konum uygulama yapılandırma dosyasında ve yönetilen kod kullanarak belirtilen <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> özelliği için uygulama etki alanı. Yönetilen kod, yönetilen kod belirtildiğinde `privatePath` ilk araştırılan, uygulama yapılandırma dosyasında belirtilen yol arkasından.  
  
#### <a name="probing-the-application-base-and-culture-directories"></a>Uygulama temel ve kültür dizinleri yoklama  
 Çalışma zamanı her zaman bir URL veya uygulamanızın kök dizininde bir bilgisayarda olabilir uygulamanın Base yoklama başlar. Başvurulan derlemeyi uygulama temel bulunamadı ve kültür bilgilerini sağlanan, çalışma zamanı derleme adı ile herhangi bir alt dizine arar. Araştırılan dizinleri şunları içerir:  
  
 [uygulama temel] / [derleme adı] .dll  
  
 [uygulama temel] / [derleme adı] / [derleme adı] .dll  
  
 Kültür bilgilerini başvurulan bütünleştirilmiş kod belirtilirse, yalnızca aşağıdaki dizinleri sıklığının:  
  
 [uygulama temel] / [kültür] / [derleme adı] .dll  
  
 [uygulama temel] / [kültür] / [derleme adı] / [derleme adı] .dll  
  
#### <a name="probing-with-the-privatepath-attribute"></a>Öznitelik privatePath ile yoklama  
 Kültür alt dizinleri ve başvurulan bütünleştirilmiş kod adlı alt dizinleri ek olarak, çalışma zamanı da kullanılarak belirtilen dizinleri yoklamaları `privatePath` özniteliği [ \<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi. Kullanılarak belirtilen dizinleri `privatePath` özniteliği, uygulamanızın kök dizininde alt dizinleri olmalıdır. Araştırılan dizinleri olup kültür bilgilerini başvurulan derlemeyi isteğinde bağlı olarak farklılık gösterir.  
  
 Çalışma zamanı doğru bir eşleşme olup olmadığına bakılmaksızın, başvurulan, basit derleme adı ile eşleşen bir derlemeyi bulduğu ilk kez yoklama durdurur. Bu derleme doğru bir eşleşme varsa kullanılır. Doğru bir eşleşme değil yoklama durdurur ve bağlama başarısız olur.  
  
 Kültür eklenirse, aşağıdaki dizinlerin sıklığının:  
  
 [uygulama temel] / [binpath] / [kültür] / [derleme adı] .dll  
  
 [uygulama temel] / [binpath] / [kültür] / [derleme adı] / [derleme adı] .dll  
  
 Kültür bilgilerini dahil edilmezse, aşağıdaki dizinlerin sıklığının:  
  
 [uygulama temel] / [binpath] / [derleme adı] .dll  
  
 [uygulama temel] / [binpath] / [derleme adı] / [derleme adı] .dll  
  
#### <a name="probing-examples"></a>Örnekler yoklama  
 Aşağıdaki bilgiler verilir:  
  
-   Başvurulan derleme adı: myAssembly  
  
-   Uygulama kök dizini: http://www.code.microsoft.com  
  
-   [\<yoklama >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) öğesi yapılandırma dosyasında belirtir: depo  
  
-   Kültür: Gizle  
  
 Çalışma zamanı aşağıdaki URL'ler yoklamaları:  
  
 http://www.code.microsoft.com/de/myAssembly.dll  
  
 http://www.code.microsoft.com/de/myAssembly/myAssembly.dll  
  
 http://www.code.microsoft.com/bin/de/myAssembly.dll  
  
 http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll  
  
##### <a name="multiple-assemblies-with-the-same-name"></a>Aynı ada sahip birden çok derleme  
 Aşağıdaki örnek, aynı ada sahip birden çok derleme yapılandırma gösterilmektedir.  
  
```xml  
<dependentAssembly>  
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />   
      <codeBase version="1.0.0.0" href="v1/Server.dll"/>  
      <codeBase version="2.0.0.0" href="v2/Server.dll"/>  
</dependentAssembly>  
```  
  
#### <a name="other-locations-probed"></a>Araştırılan diğer konumları  
 Derleme konumu, geçerli bağlama bağlamını kullanarak da belirlenebilir. Bu en sık oluşur, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi kullanılır ve COM birlikte çalışma senaryolarda. Bir derlemeyi kullanıyorsa <xref:System.Reflection.Assembly.LoadFrom%2A> başka bir derleme başvurusu yöntemi çağırma derlemenin konumunu başvurulan derlemeyi nerede bulacağını hakkında ipucu olarak kabul edilir. Bir eşleşme bulunursa, o derleme yüklenir. Eşleşme bulunamazsa, çalışma zamanı kendi arama semantiği ile devam eder ve derleme sağlamak için Windows Installer sorgular. Derleme bağlama isteği ile eşleşen sağlanan ise, bir özel durum oluşur. Bu özel durum bir <xref:System.TypeLoadException> türü başvuruldu, yönetilen kodda veya <xref:System.IO.FileNotFoundException> yüklenen bir derleme bulunamazsa.  
  
 Assembly1 Assembly2 ve Assembly1 başvuruyorsa Örneğin, gelen indirilen http://www.code.microsoft.com/utils, konumu Assembly2.dll nerede bulacağını hakkında ipucu olarak değerlendirilir. Çalışma zamanı sonra derlemede araştırmalar http://www.code.microsoft.com/utils/Assembly2.dll ve http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll. Çalışma zamanı Assembly2 da bu konumların bulunmazsa, Windows Installer sorgular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 [Dağıtım](../../../docs/framework/deployment/index.md)
