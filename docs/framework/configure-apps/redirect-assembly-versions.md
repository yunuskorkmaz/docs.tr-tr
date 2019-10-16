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
ms.openlocfilehash: e6d680097a63f3a7acc919c8503b9d18a09fcff0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319742"
---
# <a name="redirecting-assembly-versions"></a>Derleme Sürümlerini Yönlendirme

Derleme zamanı bağlama başvurularını .NET Framework derlemelere, üçüncü taraf derlemelerine veya kendi uygulamanızın derlemelerinize yeniden yönlendirebilirsiniz. Uygulamanızı çeşitli yollarla bir derlemenin farklı bir sürümünü kullanacak şekilde yeniden yönlendirebilirsiniz: Yayımcı ilkesi aracılığıyla uygulama yapılandırma dosyası aracılığıyla; veya makine yapılandırma dosyası aracılığıyla. Bu makalede, derleme bağlamasının .NET Framework nasıl çalıştığı ve nasıl yapılandırılabileceği açıklanmaktadır.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Derleme birleşme ve varsayılan bağlama
 .NET Framework derlemelerine bağlamalar bazen *derleme birleşme*adlı bir işlem aracılığıyla yeniden yönlendirilir. .NET Framework, ortak dil çalışma zamanının bir sürümünden ve tür kitaplığını oluşturan iki düzine .NET Framework bütünleştirilmiş kod ile oluşur. Bu .NET Framework derlemeleri çalışma zamanı tarafından tek bir birim olarak değerlendirilir. Varsayılan olarak, bir uygulama başlatıldığında, çalışma zamanı tarafından çalıştırılan koddaki türlere yapılan tüm başvurular, bir işlemde yüklenen çalışma zamanıyla aynı sürüm numarasına sahip .NET Framework derlemelere yönlendirilir. Bu modelde gerçekleşen yeniden yönlendirmeler, çalışma zamanının varsayılan davranışıdır.

 Örneğin, uygulamanız System. XML ad alanındaki türlere başvuruyorsa ve .NET Framework 4,5 kullanılarak oluşturulduysa, çalışma zamanı sürüm 4,5 ile birlikte gelen System. XML derlemesine statik başvuruları içerir. Bağlama başvurusunu .NET Framework 4 ile birlikte gelen System. XML derlemesine işaret etmek istiyorsanız, yeniden yönlendirme bilgilerini uygulama yapılandırma dosyasına yerleştirebilirsiniz. Birleştirilmiş bir .NET Framework derlemesi için yapılandırma dosyasında bir bağlama yeniden yönlendirmesi, bu derleme için birleşme işlemini iptal eder.

 Ayrıca, birden çok sürüm varsa, üçüncü taraf derlemeler için derleme bağlamayı el ile yeniden yönlendirmek isteyebilirsiniz.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Yayımcı ilkesini kullanarak derleme sürümlerini yeniden yönlendirme
 Derlemelerin satıcıları, yeni derlemeyle bir yayımcı ilke dosyası ekleyerek uygulamaları bir derlemenin daha yeni bir sürümüne yönlendirebilir. Genel derleme önbelleğinde bulunan Yayımcı ilke dosyası, derleme yeniden yönlendirme ayarlarını içerir.

 Her *önemli*. bir derlemenin *İkincil* sürümünün kendi yayımcı ilkesi dosyası vardır. Örneğin, sürüm 2,0 ile ilişkili olduklarından, 2.0.2.222 sürümünden 2.0.3.000 'e ve sürüm 2.0.2.321 'den sürüm 2.0.3.000 'e yeniden yönlendirmeler aynı dosyaya gider. Ancak, sürüm 3.0.0.999 'den sürüm 4.0.0.000 'e yeniden yönlendirme, sürüm 3.0.999 için dosyaya gider. .NET Framework her ana sürümünün kendi yayımcı ilkesi dosyası vardır.

 Bir derleme için yayımcı ilke dosyası varsa, çalışma zamanı derlemenin bildirimini ve uygulama yapılandırma dosyasını denetledikten sonra bu dosyayı denetler. Satıcıların Yayımcı ilke dosyalarını yalnızca yeni derleme yeniden yönlendirilmekte olan derleme ile geriye dönük olarak uyumlu olduğunda kullanması gerekir.

 [Yayımcı Ilkesini atlama bölümünde](#bypass_PP)açıklandığı gibi, uygulama yapılandırma dosyasında ayarları belirterek uygulamanız için yayımcı ilkesini atlayabilirsiniz.

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Uygulama düzeyinde derleme sürümlerini yeniden yönlendirme
 Uygulama yapılandırma dosyası aracılığıyla uygulamanız için bağlama davranışını değiştirmek için birkaç farklı teknik vardır: dosyayı el ile düzenleyebilirsiniz, otomatik bağlama yeniden yönlendirmesine güvenebilirsiniz veya yayımcı ilkesini atlayarak bağlama davranışını belirtebilirsiniz.

### <a name="manually-editing-the-app-config-file"></a>Uygulama yapılandırma dosyasını el ile düzenleyin
 Derleme sorunlarını gidermek için uygulama yapılandırma dosyasını el ile düzenleyebilirsiniz. Örneğin, bir satıcı bir yayımcının bir yayımcı ilkesi sağlamadan kullandığı daha yeni bir sürümünü serbest bırakabilir, çünkü geriye dönük uyumluluğu garanti etmez, derlemeyi, derlemeyi yerleştirerek derlemenin daha yeni bir sürümünü kullanmak üzere yönlendirebilirsiniz. bilgileri uygulamanızın yapılandırma dosyasında aşağıdaki şekilde bağlama.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Otomatik bağlama yeniden yönlendirmesine bağlı

Visual Studio 'da .NET Framework 4.5.1 veya sonraki bir sürümü hedefleyen bir masaüstü uygulaması oluşturduğunuzda, uygulama otomatik bağlama yeniden yönlendirme kullanır. Bu, iki bileşen aynı tanımlayıcı adlı derlemenin farklı sürümlerine başvurmışsa, çalışma zamanının çıkış uygulama yapılandırması (App. config) dosyasındaki derlemenin daha yeni sürümüne otomatik olarak bir bağlama yeniden yönlendirmesi eklemesi anlamına gelir. Bu yeniden yönlendirme, başka bir şekilde gerçekleşmiş olabilecek derleme birleşme özelliğini geçersiz kılar. Kaynak app.config dosyası değiştirilmez. Örneğin, uygulamanızın bir bant dışı .NET Framework bileşenine doğrudan başvurmasına, ancak aynı bileşenin eski bir sürümünü hedefleyen bir üçüncü taraf kitaplığı kullandığını varsayalım. Uygulamayı derlerken, çıkış uygulama yapılandırma dosyası, bileşenin daha yeni sürümüne bir bağlama yeniden yönlendirmesi içerecek şekilde değiştirilir. Bir Web uygulaması oluşturursanız, bağlama çakışmasıyla ilgili olarak bir derleme uyarısı alırsınız, bu da kaynak Web yapılandırma dosyasına gerekli bağlama yeniden yönlendirmesini ekleme seçeneği sunar.

Kaynak App. config dosyasına bağlama yeniden yönlendirmeleri el ile eklerseniz, derleme sırasında Visual Studio, eklediğiniz bağlama yeniden yönlendirmeleri temelinde derlemeleri birleştirmeye çalışır. Örneğin, bir derleme için aşağıdaki bağlama yeniden yönlendirmesini eklemenizi söyleyin:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Uygulamanızdaki başka bir proje aynı derlemenin 1.0.0.0 sürümüne başvuruyorsa, otomatik bağlama yeniden yönlendirme, uygulamanın bu derlemenin sürüm 2.0.0.0 üzerinde birleştirilmiş olması için çıkış App. config dosyasına aşağıdaki girişi ekler:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Uygulamanız .NET Framework eski sürümlerini hedefliyorsa otomatik bağlama yeniden yönlendirmesini etkinleştirebilirsiniz. Herhangi bir derleme için App. config dosyasında bağlama yeniden yönlendirme bilgilerini sağlayarak veya bağlama yeniden yönlendirme özelliğini kapatarak bu varsayılan davranışı geçersiz kılabilirsiniz. Bu özelliğin nasıl etkinleştirileceği veya devre dışı bırakılacağı hakkında bilgi için bkz. [nasıl yapılır: etkinleştirme ve devre dışı bırakma otomatik bağlama yeniden yönlendirme](how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Yayımcı ilkesi atlanıyor
 Gerekirse, uygulama yapılandırma dosyasında yayımcı ilkesini geçersiz kılabilirsiniz. Örneğin, geriye dönük olarak uyumlu olması talep eden derlemelerin yeni sürümleri de bir uygulamayı bozabilir. Yayımcı ilkesini atlamak istiyorsanız, uygulama yapılandırma dosyasındaki [\<dependentAssembly >](./file-schema/runtime/dependentassembly-element.md) öğesine bir [\<publisherpolicy >](./file-schema/runtime/publisherpolicy-element.md) öğesi ekleyin ve **Uygula** özniteliğini **Hayır**olarak ayarlayın. önceki **Evet** ayarları.

 `<publisherPolicy apply="no" />`

 Uygulamanızı kullanıcılarınız için çalıştırmaya devam etmek için yayımcı ilkesini atlayın, ancak sorunu derleme satıcısına bildirdiğinizden emin olun. Bir derlemenin yayımcı ilke dosyası varsa, satıcı derlemenin geriye dönük olarak uyumlu olduğundan ve istemcilerin yeni sürümü mümkün olduğunca kullanabilmesini sağlamalıdır.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Makine düzeyinde derleme sürümlerini yeniden yönlendirme
 Bir makine yöneticisi bir bilgisayardaki tüm uygulamaların belirli bir derleme sürümünü kullanmasını istediğinde nadir durumlar olabilir. Örneğin, yönetici her uygulamanın belirli bir derleme sürümünü kullanmasını isteyebilir, çünkü bu sürüm bir güvenlik deliği düzeltir. Bir derleme makinenin yapılandırma dosyasında yeniden yönlendirilirse, eski sürümü kullanan bu makinede bulunan tüm uygulamalar yeni sürümü kullanmak üzere yönlendirilir. Makine yapılandırma dosyası, uygulama yapılandırma dosyasını ve yayımcı ilkesi dosyasını geçersiz kılar. Bu dosya%*Runtime Install Path*% \ config dizininde bulunur. Genellikle, .NET Framework%drive%\Windows\Microsoft.NET\Framework dizinine yüklenir.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Yapılandırma dosyalarında bütünleştirilmiş kod bağlamayı belirtme
 Uygulama yapılandırma dosyasında, makine yapılandırma dosyasında veya yayımcı ilke dosyasında olup olmadığı gibi bağlama yeniden yönlendirmeleri belirtmek için aynı XML biçimini kullanırsınız. Bir derleme sürümünü diğerine yeniden yönlendirmek için [\<bindingRedirect >](./file-schema/runtime/bindingredirect-element.md) öğesini kullanın. **OldVersion** özniteliği tek bir derleme sürümü veya bir dizi sürüm belirtebilir. @No__t-0 özniteliği tek bir sürüm belirtmelidir.  Örneğin, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>`, çalışma zamanının 1.1.0.0 ve 1.2.0.0 arasındaki derleme sürümleri yerine 2.0.0.0 sürümünü kullanması gerektiğini belirtir.

 Aşağıdaki kod örneğinde çeşitli bağlama yeniden yönlendirme senaryoları gösterilmektedir. Örnek, `myAssembly` için bir dizi sürüm için yeniden yönlendirme ve `mySecondAssembly` için tek bir bağlama yeniden yönlendirme belirtir. Örnek ayrıca yayımcı ilke dosyasının `myThirdAssembly` için bağlama yeniden yönlendirmelerini geçersiz kılmayacağını belirtir.

 Bir derlemeyi bağlamak için, ' urn: schemas-microsoft-com: asm. v1 ' dizesini [\<assemblyBinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md) etiketinde **xmlns** özniteliğiyle birlikte belirtmeniz gerekir.

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

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Derleme bağlamalarını belirli bir sürümle sınırlandırma
 Derleme bağlama başvurularını belirli bir .NET Framework sürümüne yönlendirmek için bir uygulama yapılandırma dosyasında [\<assemblyBinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md) öğesinde **AppliesTo** özniteliğini kullanabilirsiniz. Bu isteğe bağlı öznitelik, hangi sürümün uygulanacağını göstermek için .NET Framework bir sürüm numarası kullanır. Hiçbir **AppliesTo** özniteliği belirtilmemişse, [\<assemblybinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md) öğesi .NET Framework tüm sürümleri için geçerlidir.

 Örneğin, bir .NET Framework 3,5 derlemesi için derleme bağlamayı yeniden yönlendirmek için, uygulama yapılandırma dosyanıza aşağıdaki XML kodunu dahil edersiniz.

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

 Yeniden yönlendirme bilgilerini sürüm sırasına girmeniz gerekir. Örneğin, .NET Framework 3,5 derlemeleri için derleme bağlama yeniden yönlendirme bilgilerini ve ardından .NET Framework 4,5 derlemelerini girin. Son olarak, **AppliesTo** özniteliğini kullanmayan ve bu nedenle .NET Framework tüm sürümleri için geçerli olan tüm .NET Framework bütünleştirilmiş kod yönlendirmesi için derleme bağlama yeniden yönlendirme bilgilerini girin. Yeniden yönlendirmede bir çakışma varsa, yapılandırma dosyasındaki ilk eşleşen yeniden yönlendirme ekstresi kullanılır.

 Örneğin, bir .NET Framework 3,5 derlemesine bir başvuruyu ve .NET Framework 4 derlemesine başka bir başvuruyu yeniden yönlendirmek için aşağıdaki sözde kodda gösterilen kalıbı kullanın.

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect > öğesi](./file-schema/runtime/bindingredirect-element.md)
- [Bütünleştirilmiş Kod Bağlama Yönlendirmesi Güvenlik İzni](assembly-binding-redirection-security-permission.md)
- [.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../standard/assembly/program.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Uygulamaları Yapılandırma](index.md)
- [Çalışma Zamanı Ayarları Şeması](./file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](./file-schema/index.md)
- [Nasıl yapılır: Yayımcı İlkesi Oluşturma](how-to-create-a-publisher-policy.md)
