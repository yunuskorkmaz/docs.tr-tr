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
ms.openlocfilehash: 13e2661b67ba3b717b8917e80118175acb09e756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181672"
---
# <a name="how-the-runtime-locates-assemblies"></a>Çalışma Zamanının Derlemelerin Konumunu Bulması

.NET Framework uygulamanızı başarıyla dağıtmak için, ortak dil çalışma zamanının uygulamanızı oluşturan derlemeleri nasıl bulup bağlandığını anlamanız gerekir. Varsayılan olarak, çalışma zamanı, uygulamanın birlikte inşa edildiği bir derlemenin tam sürümüyle bağlanmayı dener. Bu varsayılan davranış yapılandırma dosya ayarları tarafından geçersiz kılınabilir.

Ortak dil çalışma süresi, bir derlemeyi bulmaya ve derleme başvurularını çözmeye çalışırken birkaç adım gerçekleştirir. Her adım aşağıdaki bölümlerde açıklanmıştır. Sondalama terimi genellikle çalışma zamanının derlemeleri nasıl bulabildiğini açıklarken kullanılır; adını ve kültürünü temel alan derlemeyi bulmak için kullanılan buluşsal kümeyi ifade eder.

> [!NOTE]
> Windows SDK'da yer alan [Derleme Bağlama Log Viewer'ı (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)kullanarak günlük dosyasındaki bağlayıcı bilgileri görüntüleyebilirsiniz.

## <a name="initiating-the-bind"></a>Bind başlatma

Bir derlemeyi bulma ve bağlama işlemi, çalışma zamanı başka bir derlemeye yapılan başvuruyu çözmeye çalıştığında başlar. Bu başvuru statik veya dinamik olabilir. Derleyici, derleme bildiriminin meta verilerinde statik başvuruları oluşturma zamanında kaydeder. Dinamik referanslar gibi <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>çeşitli yöntemler, çağrı sonucu anında inşa edilir.

Bir derlemeye başvurmanın tercih edilen yolu, derleme adı, sürüm, kültür ve ortak anahtar belirteci (varsa) dahil olmak üzere tam bir başvuru kullanmaktır. Çalışma zamanı, bu bölümde daha sonra açıklanan adımları izleyerek derlemeyi bulmak için bu bilgileri kullanır. Çalışma süresi, başvurunun statik veya dinamik bir derleme için olup olmadığına bakılmaksızın aynı çözümleme işlemini kullanır.

Arama yöntemini yalnızca derleme adını belirtmek gibi yalnızca kısmi bilgilerle sağlayarak bir derlemeye dinamik bir başvuru da yapabilirsiniz. Bu durumda, yalnızca uygulama dizini derleme için aranır ve başka bir denetim oluşur. Montajları yüklemek için çeşitli yöntemlerden herhangi birini kullanarak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>kısmi bir başvuru yaparsınız.

Son olarak, gibi bir yöntem kullanarak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dinamik bir başvuru yapabilir ve yalnızca kısmi bilgi sağlayabilirsiniz; daha sonra uygulama yapılandırma dosyasındaki [ \<qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) öğesini kullanarak başvuruyu hak kazanırsınız. Bu öğe, kodunuzda değil, uygulama yapılandırma dosyanızda tam başvuru bilgilerini (ad, sürüm, kültür ve varsa ortak anahtar belirteci) sağlamanıza olanak tanır. Bu tekniği, uygulama dizininin dışındaki bir derlemeye tam olarak nitelemek istiyorsanız veya genel derleme önbelleğinde bir derlemeye başvurmak istiyorsanız, ancak başvurunun tamamını kodunuzda yerine yapılandırma dosyası.

> [!NOTE]
> Bu tür kısmi başvuru, çeşitli uygulamalar arasında paylaşılan derlemelerle kullanılmamalıdır. Yapılandırma ayarları uygulama başına uygulandığından ve montaj başına uygulanmadığından, bu tür kısmi başvuruyu kullanan paylaşılan bir derleme, paylaşılan derlemeyi kullanan her uygulamanın yapılandırma dosyasında niteleme bilgilerine sahip olmasını gerektirir.

Çalışma zamanı, derleme başvurularını çözmek için aşağıdaki adımları kullanır:

1. Uygulama yapılandırma dosyası, yayımcı ilkesi dosyası ve makine yapılandırma dosyası da dahil olmak üzere geçerli yapılandırma dosyalarını inceleyerek [doğru derleme sürümünü belirler.](#step1) Yapılandırma dosyası uzak bir makinede bulunuyorsa, çalışma zamanı önce uygulama yapılandırma dosyasını bulmalı ve indirmelidir.

2. [Derleme adının daha önce bağlanıp bağlanmadığını denetler](#step2) ve varsa, önceden yüklenmiş derlemeyi kullanır. Derlemeyi yüklemek için önceki bir istek başarısız olursa, derlemeyi yüklemeye çalışmadan istek hemen başarısız olur.

    > [!NOTE]
    > Derleme bağlama hatalarının önbelleğe alma sönmesi .NET Framework sürüm 2.0'da yenidir.

3. [Genel derleme önbelleğini denetler.](#step3) Derleme orada bulunursa, çalışma zamanı bu derlemeyi kullanır.

4. Aşağıdaki adımları kullanarak [montaj için problar:](#step4)

    1. Yapılandırma ve yayımcı ilkesi özgün başvuruyu etkilemiyorsa ve <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> bağlama isteği yöntem kullanılarak oluşturulduysa, çalışma zamanı konum ipuçlarını denetler.

    2. Yapılandırma dosyalarında bir kod tabanı bulunursa, çalışma zamanı yalnızca bu konumu denetler. Bu sonda başarısız olursa, çalışma zamanı bağlama isteğinin başarısız olduğunu ve başka bir sonda oluşmadığını belirler.

    3. [Sondabölümünde](#step4)açıklanan buluşsal kullanarak montaj için sondalar. Sondalamadan sonra derleme bulunmazsa, çalışma zamanı Windows Yükleyici'den derlemeyi sağlamasını ister. Bu, isteğe bağlı yükleme özelliği olarak görev eder.

        > [!NOTE]
        > Güçlü adları olmayan derlemeler için sürüm denetimi yoktur ve güçlü adları olmayan derlemeler için genel derleme önbelleğinde çalışma zamanı denetimi yapılmaz.

<a name="step1"></a>

## <a name="step-1-examining-the-configuration-files"></a>Adım 1: Yapılandırma Dosyalarını İnceleme

Derleme bağlama davranışı üç XML dosyasına göre farklı düzeylerde yapılandırılabilir:

- Uygulama yapılandırma dosyası.

- Publisher ilke dosyası.

- Makine yapılandırma dosyası.

Bu dosyalar aynı sözdizimini izler ve bağlama yönlendirmeleri, kodun konumu ve belirli derlemeler için bağlama modları gibi bilgiler sağlar. Her yapılandırma dosyası [ \<](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) bağlama işlemini yeniden yönlendiren bir derleme> öğesi içerebilir. [ \<Derlemenin](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) alt öğeleriBağlama> öğesi [ \<bağımlıAssembly> öğesini](../configure-apps/file-schema/runtime/dependentassembly-element.md)içerir. [ \<BağımlıAssembly> öğesinin](../configure-apps/file-schema/runtime/dependentassembly-element.md) çocukları [ \<assemblyIdentity> öğesi,](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment) [ \<bağlayıcıRedirect> öğesi](../configure-apps/file-schema/runtime/bindingredirect-element.md)ve [ \<codeBase> öğesi](../configure-apps/file-schema/runtime/codebase-element.md)içerir.

> [!NOTE]
> Yapılandırma bilgileri üç yapılandırma dosyasında bulunabilir; tüm öğeler tüm yapılandırma dosyalarında geçerli değildir. Örneğin, bağlama modu ve özel yol bilgileri yalnızca uygulama yapılandırma dosyasında olabilir. Her dosyada bulunan bilgilerin tam listesi için, [Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma](../configure-apps/index.md)bölümüne bakın.

### <a name="application-configuration-file"></a>Uygulama Yapılandırma Dosyası

İlk olarak, ortak dil çalışma zamanı, çağrı derlemesi bildiriminde depolanan sürüm bilgilerini geçersiz kılan bilgiler için uygulama yapılandırma dosyasını denetler. Uygulama yapılandırma dosyası bir uygulama ile dağıtılabilir, ancak uygulama yürütme için gerekli değildir. Genellikle bu dosyanın alınması neredeyse anlıktır, ancak uygulama tabanının Internet Explorer Web tabanlı bir senaryo gibi uzak bir bilgisayarda olduğu durumlarda yapılandırma dosyasıindirilmelidir.

İstemci yürütülebilir ler için, uygulama yapılandırma dosyası uygulamanın yürütülebilir aynı dizinde bulunur ve .config uzantılı yürütülebilir ile aynı temel ada sahiptir. Örneğin, C:\Program Files\Myapp\Myapp.exe için yapılandırma dosyası C:\Program Files\Myapp\Myapp.exe.config'dir. Tarayıcı tabanlı bir senaryoda, HTML dosyasının yapılandırma dosyasına ** \<** açıkça işaret etmek için bağlantıyı>öğeyi kullanması gerekir.

Aşağıdaki kod, uygulama yapılandırma dosyasının basit bir örneğini sağlar. Bu örnek, <xref:System.Diagnostics.TextWriterTraceListener> bir <xref:System.Diagnostics.Debug.Listeners%2A> dosyaya hata ayıklama bilgilerini kaydetmeyi etkinleştirmek için koleksiyona bir ek.

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

### <a name="publisher-policy-file"></a>Publisher İlke Dosyası

İkinci olarak, çalışma zamanı varsa yayımcı ilke dosyasını inceler. Yayımcı ilke dosyaları, bir bileşen yayımcısı tarafından düzeltme veya paylaşılan bileşene güncelleştirme olarak dağıtılır. Bu dosyalar, paylaşılan bileşenin yayımcısı tarafından verilen ve derleme başvurularını yeni bir sürüme yönlendiren uyumluluk bilgilerini içerir. Uygulama ve makine yapılandırma dosyalarının aksine, yayımcı ilke dosyaları, genel derleme önbelleğine yüklenmesi gereken kendi derlemelerinde bulunur.

Yayımcı İlkesi yapılandırma dosyasının bir örneği aşağıda verilmiştir:

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

Derleme oluşturmak için [Al.exe (Derleme Bağlantı Aracı)](../tools/al-exe-assembly-linker.md) aracını aşağıdaki gibi bir komutla kullanabilirsiniz:

```console
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0
```

`compatkey.dat`güçlü bir ad anahtarı dosyasıdır. Bu komut, genel derleme önbelleğine yerleştirebileceğiniz güçlü adlandırılmış bir derleme oluşturur.

> [!NOTE]
> Yayımcı ilkesi paylaşılan bir bileşeni kullanan tüm uygulamaları etkiler.

Publisher ilkesi yapılandırma dosyası, uygulamadan (diğer bir şekilde derleme bildiriminden veya uygulama yapılandırma dosyasından) gelen sürüm bilgilerini geçersiz kılar. Uygulama yapılandırma dosyasında derleme bildiriminde belirtilen sürümü yeniden yönlendirmek için bir ifade yoksa, yayımcı ilkesi dosyası derleme bildiriminde belirtilen sürümü geçersiz kılar. Ancak, uygulama yapılandırma dosyasında yeniden yönlendirme bildirimi varsa, yayımcı ilkesi bildirimde belirtilen sürüm yerine bu sürümü geçersiz kılar.

Paylaşılan bir bileşen güncelleştirildiğinde yayımcı ilkesi dosyası kullanılır ve paylaşılan bileşenin yeni sürümü bu bileşeni kullanan tüm uygulamalar tarafından alınmalıdır. Uygulama yapılandırma dosyası güvenli modu zorladığı sürece, publisher ilkesi dosyasındaki ayarlar uygulama yapılandırma dosyasındaki ayarları geçersiz kılar.

#### <a name="safe-mode"></a>Güvenli Mod
Yayımcı ilke dosyaları genellikle bir hizmet paketinin veya program güncelleştirmesinin bir parçası olarak açıkça yüklenir. Yükseltilmiş paylaşılan bileşenle ilgili herhangi bir sorun varsa, güvenli modu kullanarak yayımcı ilkesi dosyasındaki geçersiz kılmaları yok sayabilirsiniz. Güvenli mod ** \<publisherPolicy apply="yes**&#124;**no"/>** öğesi tarafından belirlenir, yalnızca uygulama yapılandırma dosyasında bulunur. Yayımcı ilkesi yapılandırma bilgilerinin bağlama işleminden kaldırılıp kaldırılmayacağını belirtir.

Güvenli mod, tüm uygulama veya seçili derlemeler için ayarlanabilir. Diğer bir zamanda, uygulamayı oluşturan tüm derlemeler için ilkeyi kapatabilir veya bazı derlemeler için açabilirsiniz, ancak diğerleri için açabilirsiniz. Yayımcı ilkesini bir uygulamayı oluşturan derlemelere seçerek uygulamak için ** \<publisherPolicy'yi >'a ayarlayın\=** ve \< **bağımlıAssembly**> öğesini kullanarak hangi derlemelerin etkilenmesini istediğinizi belirtin. Yayımcı ilkesini uygulamayı oluşturan tüm derlemelere uygulamak için publisherPolicy'yi bağımlı derleme öğesi olmadan ** \<>'yi\=** ayarlayın. Yapılandırma hakkında daha fazla bilgi için Yapılandırma [Dosyalarını kullanarak Uygulamaları Yapılandırma'ya](../configure-apps/index.md)bakın.

### <a name="machine-configuration-file"></a>Makine Yapılandırma Dosyası
Üçüncü olarak, çalışma zamanı makine yapılandırma dosyasını inceler. Machine.config adı verilen bu dosya, çalışma zamanının yüklendiği kök dizininin Config alt dizininde yerel bilgisayarda bulunur. Bu dosya, yöneticiler tarafından bu bilgisayariçin yerel olan derleme bağlama kısıtlamalarını belirtmek için kullanılabilir. Makine yapılandırma dosyasındaki ayarlar diğer tüm yapılandırma ayarlarında önceliklidir; ancak, bu, tüm yapılandırma ayarlarının bu dosyaya konması gerektiği anlamına gelmez. Yönetici ilkesi dosyası tarafından belirlenen sürüm son dur ve geçersiz kılınamaz. Machine.config dosyasında belirtilen geçersiz kılmalar tüm uygulamaları etkiler. Yapılandırma dosyaları hakkında daha fazla bilgi için Yapılandırma [Dosyaları'nı kullanarak Uygulamaları Yapılandırma'ya](../configure-apps/index.md)bakın.

<a name="step2"></a>

## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Adım 2: Önceden Başvurulan Derlemeleri Denetleme

İstenen derleme önceki aramalarda da isteniyorsa, ortak dil çalışma süresi zaten yüklenen derlemeyi kullanır. Bu, bir uygulamayı oluşturan derlemeleri adlandırma yaparken bazı sonuçlar doğurabilir. Derlemeleri adlandırma hakkında daha fazla bilgi için [Montaj Adları'na](../../standard/assembly/names.md)bakın.

Derleme için önceki bir istek başarısız olursa, derleme için sonraki istekler derleme yüklemeye çalışılmaksızın hemen başarısız olur. .NET Framework sürüm 2.0'dan başlayarak, derleme bağlama hataları önbelleğe alınır ve önbelleğe alınan bilgiler, derlemeyi yüklemeye çalışıp çalışmayacağını belirlemek için kullanılır.

> [!NOTE]
> Bağlama hatalarını önbelleğe alamayan .NET Framework sürümleri 1.0 ve 1.1'in davranışına geri dönmek için yapılandırma [ \<dosyanızda cachingBindingFailures> Öğesi](../configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) içerir.

<a name="step3"></a>

## <a name="step-3-checking-the-global-assembly-cache"></a>Adım 3: Genel Derleme Önbelleğini Denetleme

Güçlü adlandırılmış derlemeler için bağlama işlemi genel derleme önbelleğine bakarak devam ediyor. Genel derleme önbelleği, bilgisayardaki çeşitli uygulamalar tarafından kullanılabilecek derlemeleri depolar. Genel derleme önbelleğindeki tüm derlemelerin güçlü adları olmalıdır.

<a name="step4"></a>

## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Adım 4: Kod Temelleri veya Algılama Aracılığıyla Derlemenin Konumunu Bulma

Doğru derleme sürümü çağrı derlemesi başvurusundaki ve yapılandırma dosyalarındaki bilgiler kullanılarak belirlendikten sonra ve genel derleme önbelleğinde (yalnızca güçlü adlandırılmış derlemeler için) işaretlendikten sonra, ortak dil derlemeyi bulmak için çalışma zamanı çalışır. Bir derlemeyi bulma işlemi aşağıdaki adımları içerir:

1. Uygulama yapılandırma dosyasında [ \<bir codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi bulunursa, çalışma zamanı belirtilen konumu denetler. Bir eşleşme bulunursa, bu derleme kullanılır ve sondalama oluşmaz. Derleme orada bulunmazsa, bağlama isteği başarısız olur.

2. Çalışma süresi daha sonra bu bölümde daha sonra belirtilen kuralları kullanarak başvurulan derleme için sondalar.

> [!NOTE]
> Bir dizinde bir derlemenin birden çok sürümü varsa ve bu derlemenin belirli bir sürümüne başvurmak istiyorsanız, [ \<sondalama>](../configure-apps/file-schema/runtime/probing-element.md) öğesinin özniteliği yerine `privatePath` [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesini kullanmanız gerekir. [ \<Sondalama>](../configure-apps/file-schema/runtime/probing-element.md) öğesini kullanırsanız, çalışma süresi, doğru bir eşleşme olsun veya olmasın, başvurulan basit derleme adıyla eşleşen bir derlemeyi ilk bulduğunda sondalamayı durdurur. Doğru bir eşleşme ise, bu derleme kullanılır. Doğru eşleşme değilse, sondalama durur ve bağlama başarısız olur.

### <a name="locating-the-assembly-through-codebases"></a>Codebases ile Montaj Bulma

Codebase bilgileri, yapılandırma dosyasındaki [ \<bir codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi kullanılarak sağlanabilir. Bu kod tabanı, başvurulan derleme için sondalama çalışmadan önce her zaman denetlenir. Son sürümü yeniden yönlendirmeyi içeren bir yayımcı ilkesi dosyası da bir [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi içeriyorsa, bu [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi kullanılır. Örneğin, uygulama yapılandırma dosyanızda bir [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi belirtilirse ve uygulama bilgilerini geçersiz kılan bir yayımcı ilkesi dosyası da bir [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi belirtirse, publisher ilkesi dosyasındaki [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi kullanılır.

codeBase>öğesi tarafından belirtilen konumda eşleşme bulunmazsa, bağlama isteği başarısız olur ve başka bir adım atılmaz. [ \<](../configure-apps/file-schema/runtime/codebase-element.md) Çalışma zamanı, bir derlemenin çağrı derlemesinin ölçütlerine eşleştiğini belirlerse, bu derlemeyi kullanır. Verilen [ \<kodBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi tarafından belirtilen dosya yüklendiğinde, çalışma zamanı, ad, sürüm, kültür ve ortak anahtarın çağrı derlemesinin başvurusuyla eşleştiğinden emin olmak için denetler.

> [!NOTE]
> Uygulamanın kök dizininin dışındaki başvurulan derlemeler güçlü adlara sahip olmalı ve genel derleme önbelleğine yüklenmiş olmalı veya [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi kullanılarak belirtilmelidir.

### <a name="locating-the-assembly-through-probing"></a>Sondalama yoluyla Meclis'in Bulunması

Uygulama yapılandırma dosyasında [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) öğesi yoksa, dört ölçüt kullanarak derleme için çalışma zamanı sondaları:

- Uygulama tabanı, uygulamanın yürütüldüğü kök konumdur.

- Kültür, hangi derlemenin kültür özelliği dir.

- Başvurulan derlemenin adı olan ad.

- `privatePath` Kök konumu altında alt dizinlerin kullanıcı tanımlı listesi olan [ \<sondalama>](../configure-apps/file-schema/runtime/probing-element.md) öğesi özniteliği. Bu konum, uygulama yapılandırma dosyasında ve yönetilen <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> kodda bir uygulama etki alanı için özellik kullanılarak belirtilebilir. Yönetilen kodda belirtildiğinde, `privatePath` yönetilen kod önce incelenir ve ardından uygulama yapılandırma dosyasında belirtilen yol izlenir.

#### <a name="probing-the-application-base-and-culture-directories"></a>Uygulama Tabanı ve Kültür Dizinlerinin Araştırılması

Çalışma süresi her zaman bir URL veya bir bilgisayarda uygulamanın kök dizini olabilir uygulamanın tabanında sondalama başlar. Başvurulan derleme uygulama tabanında bulunmazsa ve kültür bilgisi sağlanmadıysa, çalışma zamanı derleme adı olan alt dizinleri arar. Incelenen dizinler şunlardır:

- [uygulama tabanı] / [derleme adı].dll

- [uygulama tabanı] / [derleme adı] / [derleme adı].dll

Başvurulan derleme için kültür bilgileri belirtilirse, yalnızca aşağıdaki dizinler incelenir:

- [uygulama tabanı] / [kültür] / [derleme adı].dll

- [uygulama tabanı] / [kültür] / [derleme adı] / [derleme adı].dll

#### <a name="probing-with-the-privatepath-attribute"></a>privatePath Özniteliği ile sondalama

Kültür alt dizinleri ve başvurulan derleme için adlandırılmış alt dizinler ek olarak, `privatePath` çalışma süresi de [ \<sondalama>](../configure-apps/file-schema/runtime/probing-element.md) öğesi özniteliği kullanılarak belirtilen dizinleri inceler. Öznitelik kullanılarak `privatePath` belirtilen dizinler, uygulamanın kök dizininin alt dizinleri olmalıdır. Incelenen dizinler, kültür bilgilerinin başvurulan derleme isteğine dahil edilip edilmediğine bağlı olarak değişir.

Çalışma zamanı, doğru bir eşleşme olsun veya olmasın, başvurulan basit derleme adıyla eşleşen bir derlemeyi ilk bulduğunda sondalamayı durdurur. Doğru bir eşleşme ise, bu derleme kullanılır. Doğru eşleşme değilse, sondalama durur ve bağlama başarısız olur.

Kültür dahil edilirse, aşağıdaki dizinler incelenir:

- [uygulama tabanı] / [binpath] / [kültür] / [derleme adı].dll

- [uygulama tabanı] / [binpath] / [kültür] / [derleme adı] / [derleme adı].dll

Kültür bilgileri dahil edilmezse, aşağıdaki dizinler incelenir:

- [uygulama tabanı] / [binpath] / [derleme adı].dll

- [uygulama tabanı] / [binpath] / [derleme adı] / [derleme adı].dll

#### <a name="probing-examples"></a>Sondalama Örnekleri

Aşağıdaki bilgiler verilmiştir:

- Başvurulan montaj adı: myAssembly

- Uygulama kök dizini:`http://www.code.microsoft.com`

- yapılandırma dosyasında [>öğeyi sondalama belirtir: bin \<](../configure-apps/file-schema/runtime/probing-element.md)

- Kültür: de

Çalışma zamanı aşağıdaki URL'leri inceler:

- `http://www.code.microsoft.com/de/myAssembly.dll`

- `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`

##### <a name="multiple-assemblies-with-the-same-name"></a>Aynı Ada Sahip Birden Çok Derleme

Aşağıdaki örnek, aynı ada sahip birden çok derlemenin nasıl yapılandırılabildiğini gösterir.

```xml
<dependentAssembly>
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />
   <codeBase version="1.0.0.0" href="v1/Server.dll" />
   <codeBase version="2.0.0.0" href="v2/Server.dll" />
</dependentAssembly>
```

#### <a name="other-locations-probed"></a>Diğer Yerler Probed

Montaj konumu da geçerli bağlama bağlamı kullanılarak belirlenebilir. Bu genellikle <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntem kullanıldığında ve COM interop senaryolarında oluşur. Bir derleme başka <xref:System.Reflection.Assembly.LoadFrom%2A> bir derlemeye başvurmak için yöntemi kullanırsa, çağrı derlemesinin konumu başvurulan derlemenin nerede bulunacağı konusunda ipucu olarak kabul edilir. Bir eşleşme bulunursa, bu derleme yüklenir. Eşleşme bulunamazsa, çalışma zamanı arama semantikleriyle devam eder ve derlemeyi sağlamak için Windows Yükleyicisini sorgular. Bağlama isteğiyle eşleşen bir derleme sağlanmazsa, bir özel durum atılır. Bu özel <xref:System.TypeLoadException> durum, bir tür başvurulan veya <xref:System.IO.FileNotFoundException> yüklenen bir derleme bulunamadı ysa yönetilen koddur.

Örneğin, Assembly1, Assembly2 ve Assembly1'den `http://www.code.microsoft.com/utils`indirilmişse, bu konum Assembly2.dll'yi nerede bulacağı hakkında bir ipucu olarak kabul edilir. Çalışma süresi daha sonra montaj `http://www.code.microsoft.com/utils/Assembly2.dll` için `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`sondalar ve . Assembly2 bu konumlardan herhangi birinde bulunmazsa, çalışma zamanı Windows Yükleyicisini sorgular.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Yükleme için En İyi Yöntemler](best-practices-for-assembly-loading.md)
- [Dağıtım](index.md)
