---
title: Derleme Sürümlerini Yönlendirme
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c4c96b874456297ede61c96e46fee8d90ebcafb6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231231"
---
# <a name="redirecting-assembly-versions"></a>Derleme Sürümlerini Yönlendirme

Derleme zamanı başvuruları .NET Framework derlemelerini, üçüncü parti derlemelerini veya kendi derlemelerini yönlendirebilirsiniz. Bir derlemenin farklı bir sürümünü çeşitli şekillerde kullanmak için uygulamanızı yönlendirebilirsiniz: yayıncı İlkesi, bir uygulama yapılandırma dosyası; aracılığıyla veya makine yapılandırma dosyası aracılığıyla. Bu makalede, derleme bağlamanın .NET Framework nasıl çalıştığı ve nasıl yapılandırılabileceği açıklanmaktadır.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Derleme birleştirme ve varsayılan bağlama
 .NET Framework derlemeleri bağlamalar bazen adlı bir işlem yeniden yönlendirilen *derleme birleştirme*. .NET Framework ortak dil çalışma zamanı ve yaklaşık iki düzine tür kitaplığını oluşturan .NET Framework derlemeleri bir sürümünü içerir. Bu .NET Framework derlemeleri çalışma zamanı tarafından tek bir birim olarak kabul edilir. Uygulama başlatıldığında, varsayılan olarak, bir işlemde yüklü çalışma zamanı ile aynı sürüm numarasına sahip .NET Framework derlemeleri çalışma zamanı tarafından çalıştırılan kod türleri için tüm başvuruları yönlendirilir. Bu modelle ortaya çıkan yönlendirmeler çalışma zamanı için varsayılan davranışı ' dir.

 Örneğin, uygulamanızın başvuruyorsa System.XML ad alanındaki türleri ve kullanılarak oluşturulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], çalışma zamanı sürüm 4.5 ile birlikte gelen System.XML derlemesine statik başvuruları içerir. Bağlama başvurusunu .NET Framework 4 ile birlikte gelen System.XML derlemesine işaret edecek şekilde yönlendirmek isterseniz, uygulama yapılandırma dosyasına yönlendirme bilgilerini koyabilirsiniz. Birleştirilmiş bir .NET Framework derlemesi için bir yapılandırma dosyası bağlama yeniden yönlendirmesi bu derleme için birleştirmeyi iptal eder.

 Ayrıca, varsa birden çok sürümü kullanılabilir üçüncü taraf derlemeler için derleme bağlamasını el ile yönlendirmek isteyebilirsiniz.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Yayımcı ilkesi kullanarak derleme sürümlerini yeniden yönlendirme
 Derleme satıcıları yeni derlemeye bir yayımcı ilkesi dosyası dahil ederek bir derlemenin daha yeni bir sürümüne uygulamaları yönlendirebilir. Genel derleme önbelleğinde bulunan Yayımcı ilkesi dosyası, derleme yeniden yönlendirme ayarlarını içerir.

 Her *ana*. *küçük* bir derlemenin sürümü kendi Yayımcı ilkesi dosyası vardır. Örneğin, sürüm 2.0 ile ilişkili olduğundan 2.0.2.222 için 2.0.3.000 sürümüne ve 2.0.2.321 sürümünden 2.0.3.000 sürümüne yeniden yönlendirmeleri her ikisi de aynı dosyaya gider. Ancak 3.0.0.999 sürümünden 4.0.0.000 sürümüne yeniden yönlendirme, 3.0.999 sürümü için dosyaya gider. .NET Framework'ün her ana sürümünün kendi Yayımcı ilkesi dosyası vardır.

 Bir derleme için yayımcı ilkesi dosyası varsa, çalışma zamanı derlemenin bildirimini ve uygulama yapılandırma dosyasını denetledikten sonra bu dosyayı denetler. Satıcılar, yeni bir derleme yönlendirilen derleme ile geriye dönük uyumlu olduğunda Yayımcı ilkesi dosyaları kullanmanız gerekir.

 Yayımcı ilkesi uygulamanız için uygulama yapılandırma dosyasında ayarları belirterek bölümünde açıklandığı gibi devre dışı bırakabilir [Yayımcı ilkesi bölümü atlayarak](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Uygulama düzeyinde derleme sürümlerini yeniden yönlendirme
 Uygulama yapılandırma dosyası aracılığıyla, uygulamanız için bağlama davranışını değiştirmek için birkaç farklı teknik vardır: dosyayı el ile düzenleyebilirsiniz, otomatik bağlama yeniden yönlendirmeye güvenebilirsiniz veya yayımcı ilkesini atlayarak bağlama davranışını belirleyebilirsiniz.

### <a name="manually-editing-the-app-config-file"></a>Uygulama yapılandırma dosyasını el ile düzenleme
 Derleme sorunlarını gidermek için uygulama yapılandırma dosyasını el ile düzenleyebilirsiniz. Örneğin, bir satıcı, geriye dönük uyumluluğu garanti edemediğinden, bir yayımcı ilkesi sağlamadan uygulamanızın kullandığı bir derlemenin daha yeni bir sürümünü yayınlayabilir, derleme koyarak derlemenin daha yeni sürümü kullanmak için uygulamanızı yönlendirebilirsiniz. bağlama bilgilerini uygulamanızın yapılandırma dosyasında aşağıdaki gibi.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Otomatik bağlama yeniden yönlendirmeye güvenmek

Oluşturduğunuzda, bir masaüstü uygulaması Visual Studio'da hedefleyen [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] veya uygulamayı sonraki bir sürümünü otomatik bağlama yeniden yönlendirme kullanır. Başka bir deyişle, iki bileşen aynı kesin adlandırılmış derlemenin farklı sürümleri başvuruyorsa, çalışma zamanı bağlama yeniden yönlendirme otomatik olarak çıktı uygulama yapılandırma (app.config) dosyasında derlemenin daha yeni sürüme olarak ekler. Bu yeniden yönlendirme, aksi halde yer alabilen Birleştirici derlemesini geçersiz kılar. Kaynak app.config dosyası değiştirilmez. Örneğin, uygulamanızın doğrudan bant dışı bir .NET Framework bileşenini başvuruyor ancak aynı bileşenin eski bir sürümünü hedefleyen bir üçüncü taraf kitaplığı kullandığını varsayalım. Uygulamayı derlediğinizde, çıktı uygulama yapılandırma dosyasına bağlama yeniden yönlendirme bileşenin daha yeni sürümünü içerecek biçimde değiştirilir. Bir web uygulaması oluşturma, buna karşılık, kaynak web yapılandırma dosyasına gerekli bağlama yeniden yönlendirmesini ekleme seçeneği sunar bağlama çakışma ile ilgili bir yapı uyarısı alırsınız.

El ile bağlama yeniden yönlendirmeleri kaynak app.config dosyasına, derleme zamanında eklerseniz, Visual Studio, eklediğiniz bağlama yeniden yönlendirmelerini temel alarak derlemeleri birleştirmeyi dener. Örneğin, bir derleme için aşağıdaki bağlama yeniden yönlendirmesini ekleme varsayalım:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Uygulamanız başka bir projede aynı derlemenin 1.0.0.0 sürümüne başvuruyorsa, böylece bu derlemenin 2.0.0.0 sürümünde uygulamanın birleşiktir otomatik bağlama yeniden yönlendirme çıktı app.config dosyasına şu girdiyi ekler:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Uygulamanızı .NET Framework'ün eski sürümlerini hedefliyorsa, otomatik bağlama yeniden yönlendirmesini etkinleştirebilirsiniz. Herhangi bir derleme için app.config dosyasında bağlama yeniden yönlendirme bilgileri sağlayarak ya da bağlama yeniden yönlendirme özelliğini kapatarak bu varsayılan davranışı geçersiz kılabilirsiniz. Bu özellik açma veya kapatma hakkında daha fazla bilgi için bkz: [nasıl yapılır: etkinleştirme ve devre dışı otomatik bağlama yeniden yönlendirme](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Yayımcı ilkesini atlama
 Gerekirse, uygulama yapılandırma dosyasında yayımcı ilkesini geçersiz kılabilirsiniz. Örneğin, geriye dönük uyumlu olduğu iddia edilen derlemelerin yeni sürümleri yine de bir uygulamayı kesebilir. Yayımcı ilkesini atlama istiyorsanız ekleme bir [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) öğesine [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) öğe kümesi veuygulamayapılandırmadosyası**uygulamak** özniteliğini **hiçbir**, daha önceki etkisiz kılan **Evet** ayarları.

 `<publisherPolicy apply="no" />`

 Uygulamanızı kullanıcılarınızın çalışır durumda tutmak amacıyla yayımcı ilkesini atlayın, ancak sorunu derleme satıcısına bildirdiğinizden emin olun. Bir derlemenin Yayımcı ilkesi dosyası varsa satıcı derlemenin geriye dönük uyumlu olduğundan ve istemcilerin mümkün olduğunca yeni sürümü kullanabilirsiniz emin olmanız gerekir.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Makine düzeyinde derleme sürümlerini yeniden yönlendirme
 Bir makine yöneticisinin bir bilgisayardaki bir derlemenin belirli bir sürümünü kullanan tüm uygulamalar istediği ender durumlar olabilir. Örneğin, bu sürüm bir güvenlik açığını düzelttiğinden yönetici her uygulamanın belirli bir derleme sürümünü, kullanmasını isteyebilirsiniz. Bir derleme makinenin yapılandırma dosyasında yeniden yönlendirilirse, o makinedeki eski sürümü kullanan tüm uygulamalar yeni sürümü kullanmak için yönlendirilir. Makine yapılandırma dosyası, uygulama yapılandırma dosyası ve yayımcı ilkesi dosyasını geçersiz kılar. Bu dosya % bulunur*çalışma zamanı yükleme yolu*%\Config dizininde. Genellikle, .NET Framework %drive%\Windows\Microsoft.NET\Framework dizinine yüklenir.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Yapılandırma dosyalarında derleme bağlama belirtme
 Uygulama yapılandırma dosyası, makine yapılandırma dosyasında veya yayıncı ilkesi dosyasında olsun, bağlama yönlendirmelerini belirtmek için aynı XML biçimini kullanın. Bir derleme sürümünü diğerine yeniden yönlendirmek için [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) öğesi. **OldVersion** öznitelik, bir tek bir derleme sürümünü veya bir sürüm aralığı belirtebilirsiniz. `newVersion` Özniteliği, tek bir sürüm belirtmelidir.  Örneğin, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` çalışma zamanı sürüm 2.0.0.0 derleme sürümleri yerine 1.1.0.0 ile 1.2.0.0 arasındaki kullanması gerektiğini belirtir.

 Aşağıdaki kod örneği, çeşitli bağlama yeniden yönlendirme senaryoları göstermektedir. Örnek bir sürüm aralığı için bir yeniden yönlendirme belirtir `myAssembly`ve bir tek bir bağlama yeniden yönlendirmesi `mySecondAssembly`. Örnekte ayrıca Yayımcı ilkesi dosyasının bağlama yönlendirmelerini geçersiz belirtir `myThirdAssembly`.

 Bir derleme bağlama için bir dize belirtin "urn: schemas-microsoft-com:asm.v1" ile **xmlns** özniteliğini [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) etiketi.

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
  <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Derleme bağlamaları belirli bir sürümle sınırlama
 Kullanabileceğiniz **appliesTo** özniteliği [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) derleme bağlama başvurularının nasıl belirli bir .NET sürümünü yeniden yönlendirmek için bir uygulama yapılandırma dosyasında öğesi Çerçeve. İsteğe bağlı bu öznitelik, bir .NET Framework sürüm numarası geçerli hangi sürüm olduğunu belirlemek için kullanır. Hayır ise **appliesTo** özniteliği belirtilirse, [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) öğe tüm .NET Framework sürümleri için geçerlidir.

 Örneğin, derleme için bir .NET Framework 3.5 derleme bağlamasına yönlendirmek için aşağıdaki XML kodunu uygulama yapılandırma dosyanızda verilebilir.

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 Sürüm sırayla yeniden yönlendirme bilgileri girmeniz gerekir. Örneğin, .NET Framework 4.5 derlemelerinin takip ettiği .NET Framework 3.5 derlemeleri için derleme bağlama yönlendirme bilgisini girin. Son olarak, kullanılmayan tüm .NET Framework derleme yeniden yönlendirmesi için derleme bağlama yönlendirme bilgisini girin **appliesTo** özniteliği ve bu nedenle tüm .NET Framework sürümleri için geçerlidir. Yeniden yönlendirmeyi bir çakışma varsa, yapılandırma dosyasındaki eşleşen ilk yönlendirme cümlesi kullanılır.

 Örneğin, bir referansı .NET Framework 3.5 derlemesini ve diğer bir referansı da .NET Framework 4 derlemesine yönlendirmek için gösterilen aşağıdaki sözde kod modelini kullanın.

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!—.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!—.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Bütünleştirilmiş Kod Bağlama Yönlendirmesi Güvenlik İzni](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Uygulamaları Yapılandırma](../../../docs/framework/configure-apps/index.md)
- [.NET Framework uygulamalarını yapılandırma](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
- [Çalışma Zamanı Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../docs/framework/configure-apps/file-schema/index.md)
- [Nasıl yapılır: Yayımcı İlkesi Oluşturma](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
