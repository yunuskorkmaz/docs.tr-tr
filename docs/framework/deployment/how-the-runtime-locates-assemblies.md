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
ms.openlocfilehash: 7f8046852f847cd5493a2ed17b491a39e494ce2b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969117"
---
# <a name="how-the-runtime-locates-assemblies"></a>Çalışma Zamanının Derlemelerin Konumunu Bulması

.NET Framework uygulamanızı başarıyla dağıtmak için, ortak dil çalışma zamanının uygulamanızı oluşturan derlemelere nasıl konumlandırdığını ve bunların nasıl bağlanacağını anlamanız gerekir. Varsayılan olarak, çalışma zamanı, uygulamanın oluşturulduğu derlemenin tam sürümüyle bağlamayı dener. Bu varsayılan davranış, yapılandırma dosyası ayarları tarafından geçersiz kılınabilir.

Ortak dil çalışma zamanı, bir derlemeyi bulmaya ve derleme başvurusunu çözümlemeye çalışırken bir dizi adımı gerçekleştirir. Her adım aşağıdaki bölümlerde açıklanmıştır. Yoklama terimi genellikle çalışma zamanının derlemeleri nasıl konumlandırdığını açıklayarak kullanılır; Bu, adını ve kültürünü temel alarak derlemeyi bulmak için kullanılan buluşsal yöntemler kümesini ifade eder.

> [!NOTE]
> Bağlama bilgilerini, Windows SDK dahil edilen [derleme bağlama günlüğü görüntüleyicisini (Fuslogvw. exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)kullanarak günlük dosyasında görüntüleyebilirsiniz.

## <a name="initiating-the-bind"></a>Bağlama başlatılıyor

Bir derlemeyi bulma ve bağlama işlemi, çalışma zamanı başka bir derlemeye yönelik bir başvuruyu çözümlemeye çalıştığında başlar. Bu başvuru statik veya dinamik olabilir. Derleyici, derleme zamanında derleme bildiriminin meta verilerinde statik başvuruları kaydeder. Dinamik başvurular, gibi çeşitli yöntemlerin <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>çağrılmasının sonucu olarak anında oluşturulur.

Bir derlemeye başvurmak için tercih edilen yöntem, derleme adı, sürüm, kültür ve ortak anahtar belirteci (varsa) dahil olmak üzere tam bir başvuru kullanmaktır. Çalışma zamanı, bu bölümde daha sonra açıklanan adımları izleyerek derlemeyi bulmak için bu bilgileri kullanır. Çalışma zamanı, başvurunun statik veya dinamik bir derleme için olup olmamasına bakılmaksızın aynı çözüm işlemini kullanır.

Ayrıca, derleme hakkında yalnızca derleme adını belirtmek gibi kısmi bilgilerle birlikte çağırma yöntemi sağlayarak derlemeye dinamik bir başvuru da yapabilirsiniz. Bu durumda, derleme için yalnızca uygulama dizini aranır ve başka bir denetim gerçekleşmez. <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> Ya da<xref:System.AppDomain.Load%2A?displayProperty=nameWithType>gibi derlemeleri yüklemek için çeşitli yöntemlerden birini kullanarak kısmi bir başvuru yaparsınız.

Son olarak, gibi bir yöntemi <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> kullanarak dinamik bir başvuru yapabilir ve yalnızca kısmi bilgiler sağlayabilir; daha sonra başvuruyu uygulama yapılandırma dosyasında [ \<qualifyAssembly >](../configure-apps/file-schema/runtime/qualifyassembly-element.md) öğesini kullanarak niteleyebilirsiniz. Bu öğe, kodunuzun yerine uygulama yapılandırma dosyanızdaki tam başvuru bilgilerini (ad, sürüm, kültür ve varsa ortak anahtar belirteci) sağlamanıza olanak tanır. Bu tekniği, uygulama dizini dışındaki bir derlemeye yönelik başvuruyu tamamen nitelemek istiyorsanız veya genel derleme önbelleğindeki bir derlemeye başvurmak istiyorsanız, ancak tam başvuruyu ' de belirtmenin rahatlığını istiyordunuz. kodunuzda değil yapılandırma dosyası.

> [!NOTE]
> Bu tür kısmi başvuru, çeşitli uygulamalar arasında paylaşılan Derlemelerle kullanılmamalıdır. Yapılandırma ayarları, derleme başına değil, uygulama başına uygulandığından, bu tür kısmi başvuru kullanan paylaşılan bir derleme, paylaşılan derlemeyi kullanan her uygulamanın yapılandırma dosyasında uygun bilgilere sahip olmasını gerektirir.

Çalışma zamanı, bir derleme başvurusunu çözümlemek için aşağıdaki adımları kullanır:

1. Uygulama yapılandırma dosyası, yayımcı ilkesi dosyası ve makine yapılandırma dosyası dahil olmak üzere uygulanabilir yapılandırma dosyalarını inceleyerek [doğru derleme sürümünü belirler](#step1) . Yapılandırma dosyası uzak bir makinede bulunuyorsa, çalışma zamanının önce uygulama yapılandırma dosyasını bulması ve indirmesi gerekir.

2. [Derleme adının önce ve ' a bağlanıp bağlanmadığını denetler](#step2) , varsa, daha önce yüklenen derlemeyi kullanır. Derlemeyi yüklemeye yönelik önceki bir istek başarısız olduysa, istek derlemeyi yüklemeye çalışmadan hemen başarısız olur.

    > [!NOTE]
    > Derleme bağlama hatalarının önbelleğe alınması .NET Framework sürüm 2,0 ' de yenidir.

3. [Genel derleme önbelleğini denetler](#step3). Derleme orada bulunursa, çalışma zamanı bu derlemeyi kullanır.

4. Aşağıdaki adımları kullanarak [bütünleştirilmiş koda yönelik yoklamalar](#step4) :

    1. Yapılandırma ve yayımcı ilkesi özgün başvuruyu etkilemez ve bağlama isteği <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi kullanılarak oluşturulduysa, çalışma zamanı konum ipuçlarını denetler.

    2. Yapılandırma dosyalarında bir kod temeli bulunursa, çalışma zamanı yalnızca bu konumu denetler. Bu araştırma başarısız olursa, çalışma zamanı bağlama isteğinin başarısız olduğunu ve başka bir yoklama gerçekleşmeyeceğini belirler.

    3. [Araştırma bölümünde](#step4)açıklanan buluşsal yöntemler kullanılarak bütünleştirilmiş koda yönelik yoklamalar. Yoklama sonrasında derleme bulunamazsa, çalışma zamanı derlemeyi sağlamak için Windows Installer ister. Bu, isteğe bağlı bir install özelliği görevi görür.

        > [!NOTE]
        > Tanımlayıcı adları olmayan derlemeler için sürüm denetimi yoktur veya çalışma zamanı, tanımlayıcı adlar olmadan derlemeler için genel derleme önbelleğinde denetim yapmaz.

<a name="step1"></a>

## <a name="step-1-examining-the-configuration-files"></a>1\. Adım: Yapılandırma dosyalarını İnceleme

Derleme bağlama davranışı, üç XML dosyasına göre farklı düzeylerde yapılandırılabilir:

- Uygulama yapılandırma dosyası.

- Yayımcı ilkesi dosyası.

- Makine yapılandırma dosyası.

Bu dosyalar aynı sözdizimini izler ve bağlama yeniden yönlendirmeleri, kodun konumu ve belirli derlemeler için bağlama modları gibi bilgiler sağlar. Her yapılandırma dosyası, bağlama işlemini yeniden yönlendiren bir [ \<assemblyBinding > öğesi](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) içerebilir. AssemblyBinding [ >\<](../configure-apps/file-schema/runtime/dependentassembly-element.md)öğesinin alt öğeleri dependentAssembly > öğesini içerir. [ \<](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) DependentAssembly > [ \<](../configure-apps/file-schema/runtime/bindingredirect-element.md) [ \<öğesinin alt](../configure-apps/file-schema/runtime/dependentassembly-element.md) öğeleri [ ,AssemblyIdentity>öğesi,bindingRedirect\<](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)> öğesi ve [CODEBASE > öğesi içerir \< ](../configure-apps/file-schema/runtime/codebase-element.md).

> [!NOTE]
> Yapılandırma bilgilerini üç yapılandırma dosyasında bulabilirsiniz; tüm öğeler tüm yapılandırma dosyalarında geçerli değildir. Örneğin, bağlama modu ve özel yol bilgileri yalnızca uygulama yapılandırma dosyasında bulunabilir. Her dosyada bulunan bilgilerin tüm listesi için bkz. [yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](../configure-apps/index.md).

### <a name="application-configuration-file"></a>Uygulama yapılandırma dosyası

İlk olarak, ortak dil çalışma zamanı, çağıran derlemenin bildiriminde depolanan sürüm bilgilerini geçersiz kılan bilgiler için uygulama yapılandırma dosyasını denetler. Uygulama yapılandırma dosyası bir uygulamayla dağıtılabilir, ancak uygulama yürütmesi için gerekli değildir. Genellikle bu dosyanın alınması neredeyse anında yapılır, ancak uygulama tabanının, Internet Explorer Web tabanlı bir senaryoda olduğu gibi uzak bir bilgisayarda olduğu durumlarda yapılandırma dosyası indirilmelidir.

İstemci yürütülebilir dosyaları için, uygulama yapılandırma dosyası uygulamanın yürütülebilir dosyası ile aynı dizinde bulunur ve. config uzantısıyla yürütülebilir dosya ile aynı temel ada sahiptir. Örneğin, C:\Program Files\Myapp\Myapp.exe için yapılandırma dosyası C:\Program Files\Myapp\Myapp.exe.config. ' dir Tarayıcı tabanlı bir senaryoda, HTML dosyası doğrudan yapılandırma dosyasını işaret etmek için  **\<LINK >** öğesini kullanmalıdır.

Aşağıdaki kod, uygulama yapılandırma dosyasına basit bir örnek sağlar. Bu örnek, <xref:System.Diagnostics.Debug.Listeners%2A> hata <xref:System.Diagnostics.TextWriterTraceListener> ayıklama bilgilerinin bir dosyaya kaydedilmesini etkinleştirmek için koleksiyonuna bir ekler.

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

### <a name="publisher-policy-file"></a>Yayımcı Ilkesi dosyası

İkinci olarak, çalışma zamanı varsa Yayımcı ilke dosyasını inceler. Yayımcı ilke dosyaları bir bileşen yayımcısı tarafından bir çözüm veya paylaşılan bir bileşene güncelleştirme olarak dağıtılır. Bu dosyalar, bir derleme başvurusunu yeni bir sürüme yönlendiren paylaşılan bileşenin yayımcısı tarafından verilen uyumluluk bilgilerini içerir. Uygulama ve makine yapılandırma dosyalarının aksine, yayımcı ilkesi dosyaları, genel derleme önbelleğinde yüklenmesi gereken kendi derlemelerinde yer alır.

Aşağıda yayımcı Ilkesi yapılandırma dosyasına bir örnek verilmiştir:

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

Bir derleme oluşturmak için, [al. exe (bütünleştirilmiş kod bağlayıcı)](../tools/al-exe-assembly-linker.md) aracını aşağıdaki gibi bir komutla kullanabilirsiniz:

```console
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0
```

`compatkey.dat`, tanımlayıcı ad anahtar dosyasıdır. Bu komut, genel derleme önbelleğine yerleştirebileceğiniz, tanımlayıcı adlı bir derleme oluşturur.

> [!NOTE]
> Yayımcı ilkesi, paylaşılan bir bileşen kullanan tüm uygulamaları etkiler.

Yayımcı ilke yapılandırma dosyası, uygulamadan gelen sürüm bilgilerini (yani, derleme bildiriminden veya uygulama yapılandırma dosyasından) geçersiz kılar. Uygulama yapılandırma dosyasında, derleme bildiriminde belirtilen sürümü yeniden yönlendirmek için bir ifade yoksa, yayımcı ilke dosyası derleme bildiriminde belirtilen sürümü geçersiz kılar. Ancak, uygulama yapılandırma dosyasında bir yeniden yönlendirme bildirimi varsa, yayımcı ilkesi bildirimde belirtime yerine bu sürümü geçersiz kılar.

Bir yayımcı ilke dosyası, paylaşılan bir bileşen güncelleştirilirken ve paylaşılan bileşenin yeni sürümü bu bileşeni kullanan tüm uygulamalar tarafından çekilmelidir. Uygulama yapılandırma dosyası güvenli modu zorunlu kılarsa, yayımcı ilkesi dosyasındaki ayarlar uygulama yapılandırma dosyasındaki ayarları geçersiz kılar.

#### <a name="safe-mode"></a>Güvenli mod
Yayımcı ilke dosyaları genellikle bir hizmet paketinin veya program güncelleştirmesinin bir parçası olarak açıkça yüklenir. Yükseltilen paylaşılan bileşenle ilgili herhangi bir sorun varsa, güvenli mod kullanarak yayımcı ilkesi dosyasındaki geçersiz kılmaları yoksayabilirsiniz. Güvenli mod, yalnızca uygulama yapılandırma dosyasında bulunan  **\<publisherPolicy apply = "Yes**&#124;**No"/>** öğesi tarafından belirlenir. Yayımcı ilkesi yapılandırma bilgilerinin bağlama işleminden kaldırılması gerekip gerekmediğini belirtir.

Güvenli mod tüm uygulama veya seçili derlemeler için ayarlanabilir. Diğer bir deyişle, uygulamayı oluşturan tüm derlemeler için ilkeyi kapatabilir veya bazı derlemeler için açabilirsiniz, ancak diğerlerini kullanamazsınız. Yayımcı ilkesini bir uygulamayı oluşturan derlemelere seçmeli olarak uygulamak için,  **\<publisherPolicy Ayarla/> uygulayın\=** ve \<dependentAssembly kullanarak hangi derlemeleri etkilemelerini istediğinizi belirtin> öğesi. Uygulamayı oluşturan tüm derlemelere yayımcı ilkesi uygulamak için, publisherPolicy ' ı bağımlı derleme öğeleri olmadan  **\<No/> Uygula\=** ' yı ayarlayın. Yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](../configure-apps/index.md).

### <a name="machine-configuration-file"></a>Makine yapılandırma dosyası
Üçüncü olarak, çalışma zamanı makine yapılandırma dosyasını inceler. Machine. config adlı bu dosya, çalışma zamanının yüklendiği kök dizinin yapılandırma alt dizinindeki yerel bilgisayarda bulunur. Bu dosya, yöneticiler tarafından bu bilgisayarda yerel olan derleme bağlama kısıtlamalarını belirtmek için kullanılabilir. Makine yapılandırma dosyasındaki ayarlar diğer tüm yapılandırma ayarlarından önceliklidir; Ancak, bu, tüm yapılandırma ayarlarının bu dosyaya konulacağı anlamına gelmez. Yönetici ilke dosyası tarafından belirlenen sürüm son, geçersiz kılınamaz. Machine. config dosyasında belirtilen geçersiz kılmalar tüm uygulamaları etkiler. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak uygulamaları yapılandırma](../configure-apps/index.md).

<a name="step2"></a> 
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>2\. Adım: Önceden başvurulan derlemeler denetleniyor
İstenen derleme önceki çağrılar için de istenirse, ortak dil çalışma zamanı zaten yüklü olan derlemeyi kullanır. Bu, bir uygulamayı oluşturan derlemeleri adlandırırken bu sonuçları içerebilir. Derlemeleri adlandırma hakkında daha fazla bilgi için bkz. [derleme adları](../../standard/assembly/names.md).

Derleme için önceki bir istek başarısız olduysa, derleme için sonraki istekler derlemeyi yükleme girişiminde bulunmadan hemen başarısız oldu. .NET Framework sürüm 2,0 ' den başlayarak, derleme bağlama sorunları önbelleğe alınır ve önbelleğe alınan bilgiler derlemeyi yüklemeyi denemesinin denenip denenmeyeceğini tespit etmek için kullanılır.

> [!NOTE]
> Bağlantı hatalarının önbelleğe alınmamasından 1,0 ve 1,1 .NET Framework sürümlerinin davranışına dönmek için, yapılandırma dosyanıza [ \<disablecachingbindinghatalarıyla > öğesini](../configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) ekleyin.

<a name="step3"></a>

## <a name="step-3-checking-the-global-assembly-cache"></a>3\. Adım: Genel bütünleştirilmiş kod önbelleği denetleniyor

Tanımlayıcı adlı derlemeler için bağlama işlemi, genel derleme önbelleğine bakarak devam eder. Genel bütünleştirilmiş kod önbelleği, bir bilgisayardaki çeşitli uygulamalar tarafından kullanılabilecek derlemeleri depolar. Genel derleme önbelleğindeki tüm derlemeler tanımlayıcı adlara sahip olmalıdır.

<a name="step4"></a>

## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>4\. Adım: Kod tabanları veya yoklama aracılığıyla derlemeyi bulma

Doğru derleme sürümü, çağıran derlemenin başvurusu ve yapılandırma dosyalarındaki bilgiler kullanılarak belirlendikten sonra ve genel derleme önbelleğini (yalnızca güçlü adlandırılmış derlemeler için) iade ettikten sonra, ortak dil çalışma zamanı derlemeyi bulmayı dener. Bir derlemeyi bulma işlemi aşağıdaki adımları içerir:

1. Uygulama yapılandırma dosyasında bir [ \<codebase >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi bulunursa, çalışma zamanı belirtilen konumu denetler. Bir eşleşme bulunursa, bu derleme kullanılır ve hiçbir yoklama gerçekleşmez. Derleme orada bulunmazsa bağlama isteği başarısız olur.

2. Çalışma zamanı daha sonra bu bölümün ilerleyen kısımlarında belirtilen kuralları kullanarak başvurulan derlemeye yönelik yoklamalar.

> [!NOTE]
> Bir dizinde derlemenin birden çok sürümüne sahipseniz ve bu derlemenin belirli bir sürümüne başvurmak istiyorsanız, `privatePath` [ \<](../configure-apps/file-schema/runtime/codebase-element.md) [ \<yoklama özniteliği yerine codebase > öğesini kullanmanız gerekir >](../configure-apps/file-schema/runtime/probing-element.md) öğesi. Yoklama > öğesini kullanıyorsanız [ \<](../configure-apps/file-schema/runtime/probing-element.md) , çalışma zamanı, belirtilen basit derleme adıyla eşleşen bir derlemeyi ilk kez bulduğunda, doğru bir eşleşme olup olmadığına göre yoklama işlemini durduruyor. Doğru bir eşleşmedir, bu derleme kullanılır. Doğru eşleşme değilse, araştırma durduruluyor ve bağlama başarısız olur.

### <a name="locating-the-assembly-through-codebases"></a>Kod tabanları aracılığıyla derlemeyi bulma

Kod temeli bilgileri bir yapılandırma dosyasında bir [ \<codebase >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi kullanılarak temin edilebilir. Bu kod temeli, başvurulan derleme için çalışma zamanı araştırmayı denemeden önce her zaman denetlenir. Son sürüm yeniden yönlendirmeyi içeren bir yayımcı ilke dosyası aynı zamanda bir [ \<codebase >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi içeriyorsa, bu [ \<codebase >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi kullanılan bir öğedir. Örneğin, uygulama yapılandırma dosyanız bir [ \<codebase >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi belirtiyorsa ve uygulama bilgilerini geçersiz kılan bir yayımcı ilke dosyası de bir [ \<codebase >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi belirtiyorsa, Yayımcı ilkesi dosyasındaki [kod temeli > öğesi kullanılıyor. \<](../configure-apps/file-schema/runtime/codebase-element.md)

CodeBase > öğesi tarafından [ \<](../configure-apps/file-schema/runtime/codebase-element.md) belirtilen konumda eşleşme bulunamazsa, bağlama isteği başarısız olur ve başka bir adım alınmaz. Çalışma zamanı, bir derlemenin çağıran derlemenin ölçütleriyle eşleşip eşleşmediğini belirlerse, bu derlemeyi kullanır. [ Verilen\<codebase >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi tarafından belirtilen dosya yüklendiğinde, çalışma zamanı, ad, sürüm, kültür ve ortak anahtarın çağıran derlemenin başvurusuyla eşleştiğinden emin olmak için kontrol eder.

> [!NOTE]
> Uygulamanın kök dizini dışındaki Başvurulmuş derlemeler tanımlayıcı adlara sahip olmalıdır ve genel derleme önbelleğinde yüklü olmalıdır ya da [ \<kod temeli >](../configure-apps/file-schema/runtime/codebase-element.md) öğesi kullanılarak belirtilmelidir.

### <a name="locating-the-assembly-through-probing"></a>Algılama yoluyla derlemeyi bulma

Uygulama yapılandırma dosyasında bir [ kodtemeli>öğesiyoksa,derlemeiçindörtölçütkullanarakçalışmazamanıaraştırmalar:\<](../configure-apps/file-schema/runtime/codebase-element.md)

- Uygulamanın yürütüldüğü kök konum olan uygulama tabanı.

- Başvurulan derlemenin kültür özniteliği olan kültür.

- Başvurulan derlemenin adı olan ad.

- Temel konum altındaki alt dizinlerin Kullanıcı tanımlı listesi olan [ \<yoklama >](../configure-apps/file-schema/runtime/probing-element.md) öğesinin özniteliği.`privatePath` Bu konum, uygulama yapılandırma dosyasında ve yönetilen kodda bir uygulama etki alanı için <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> özelliği kullanılarak belirtilebilir. Yönetilen kodda belirtildiğinde, yönetilen kod `privatePath` önce araştırılan uygulama yapılandırma dosyasında belirtilen yol gelir.

#### <a name="probing-the-application-base-and-culture-directories"></a>Uygulama tabanı ve kültür dizinlerini araştırma

Çalışma zamanı, uygulama tabanında her zaman bir URL ya da uygulamanın bir bilgisayardaki kök dizini olabilecek şekilde yoklama yapmaya başlar. Başvurulan derleme uygulama tabanında bulunmazsa ve hiçbir kültür bilgisi sağlanmazsa, çalışma zamanı derleme adına sahip tüm alt dizinleri arar. Araştırılan dizinler şunlardır:

- [uygulama temeli]/[derleme adı]. dll

- [uygulama temeli]/[derleme adı]/[derleme adı]. dll

Başvurulan derleme için kültür bilgileri belirtilmişse, yalnızca aşağıdaki dizinler araştırlanır:

- [uygulama temeli]/[kültür]/[derleme adı]. dll

- [uygulama temeli]/[kültür]/[derleme adı]/[derleme adı]. dll

#### <a name="probing-with-the-privatepath-attribute"></a>PrivatePath özniteliğiyle yoklama

Kültür alt dizinlerine ve başvurulan derleme için adlı alt dizinlere ek olarak, çalışma zamanı, `privatePath` [ \<araştırma >](../configure-apps/file-schema/runtime/probing-element.md) öğesinin özniteliği kullanılarak belirtilen dizinleri de yoklamaktadır. `privatePath` Özniteliği kullanılarak belirtilen dizinler, uygulamanın kök dizininin alt dizinleri olmalıdır. Araştırılan dizinler, başvurulan derleme isteğine kültür bilgilerinin dahil edilip edilmeyeceğini göre farklılık gösterir.

Çalışma zamanı, belirtilen basit derleme adıyla eşleşen bir derlemeyi ilk kez bulduğunda, doğru eşleşme olup olmadığına bakılmaksızın yoklama durduruyor. Doğru bir eşleşmedir, bu derleme kullanılır. Doğru eşleşme değilse, araştırma durduruluyor ve bağlama başarısız olur.

Kültür dahil edilmemişse, aşağıdaki dizinler araştırlanır:

- [uygulama temeli]/[binyol]/[kültür]/[derleme adı]. dll

- [uygulama temeli]/[binpath]/[kültür]/[derleme adı]/[derleme adı]. dll

Kültür bilgileri dahil edilmemişse, aşağıdaki dizinler araştırılan:

- [uygulama temeli]/[binyol]/[derleme adı]. dll

- [uygulama temeli]/[binpath]/[derleme adı]/[derleme adı]. dll

#### <a name="probing-examples"></a>Yoklama örnekleri

Aşağıdaki bilgiler veriliyor:

- Başvurulan derleme adı: myAssembly

- Uygulama kök dizini:`http://www.code.microsoft.com`

- yapılandırma dosyasındaki yoklama > öğesi şunları belirtir: bin [ \<](../configure-apps/file-schema/runtime/probing-element.md)

- Kültür: de

Çalışma zamanı aşağıdaki URL 'Leri yoklamalar:

- `http://www.code.microsoft.com/de/myAssembly.dll`

- `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`

##### <a name="multiple-assemblies-with-the-same-name"></a>Aynı ada sahip birden çok derleme

Aşağıdaki örnek, aynı ada sahip birden çok derlemenin nasıl yapılandırılacağını gösterir.

```xml
<dependentAssembly>
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />
   <codeBase version="1.0.0.0" href="v1/Server.dll" />
   <codeBase version="2.0.0.0" href="v2/Server.dll" />
</dependentAssembly>
```

#### <a name="other-locations-probed"></a>Araştırılan diğer konumlar

Derleme konumu geçerli bağlama bağlamı kullanılarak da belirlenebilir. Bu, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> genellikle yöntemi kullanıldığında ve com birlikte çalışma senaryolarında oluşur. Bir derleme başka bir derlemeye <xref:System.Reflection.Assembly.LoadFrom%2A> başvurmak için yöntemini kullanıyorsa, çağıran derlemenin konumu, başvurulan derlemenin nerede bulunacağı hakkında bir ipucu olarak değerlendirilir. Bir eşleşme bulunursa, bu derleme yüklenir. Hiçbir eşleşme bulunmazsa, çalışma zamanı arama semantiğine devam eder ve ardından derlemeyi sağlamak için Windows Installer sorgular. Bağlama isteğiyle eşleşen bir derleme sağlanmazsa, bir özel durum oluşturulur. Bu özel durum, <xref:System.TypeLoadException> bir türe başvuruluyorsa yönetilen bir kodda <xref:System.IO.FileNotFoundException> veya yüklenmekte olan bir derleme bulunamazsa.

Örneğin, Assembly1 başvuruları Assembly2 ve assembly1 ' den `http://www.code.microsoft.com/utils`indirildiyse, bu konum Assembly2. dll ' nin nerede bulunacağı hakkında bir ipucu olarak değerlendirilir. Çalışma zamanı daha sonra ve `http://www.code.microsoft.com/utils/Assembly2.dll` `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`içindeki bütünleştirilmiş koda yönelik yoklamalar. Assembly2 bu konumlardan birinde bulunmazsa, çalışma zamanı Windows Installer sorgular.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](best-practices-for-assembly-loading.md)
- [Dağıtım](index.md)
