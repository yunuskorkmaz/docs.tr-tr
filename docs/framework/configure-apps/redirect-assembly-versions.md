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
ms.openlocfilehash: 0d55171e37ec056b3470d238a60bc32f2feb04fb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646039"
---
# <a name="redirecting-assembly-versions"></a>Derleme Sürümlerini Yönlendirme

Derleme zamanı bağlama başvurularını .NET Framework derlemelerine, üçüncü taraf derlemelerine veya kendi uygulamanızın derlemelerine yönlendirebilirsiniz. Uygulamanızı bir derlemenin farklı bir sürümünü çeşitli şekillerde kullanmak üzere yeniden yönlendirebilirsiniz: yayımcı ilkesi aracılığıyla, bir uygulama yapılandırma dosyası aracılığıyla; veya makine yapılandırma dosyası aracılığıyla. Bu makalede, .NET Framework'de derleme bağlamanın nasıl çalıştığı ve nasıl yapılandırılabildiği açıklanmıştır.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Montaj birleştirme ve varsayılan bağlama
 .NET Framework derlemelerine bağlanan bağlamalar bazen *derleme birleştirme*adı verilen bir işlem le yönlendirilir. .NET Framework, ortak dil çalışma zamanının bir sürümünden ve tür kitaplığını oluşturan yaklaşık iki düzine .NET Framework derlemesinden oluşur. Bu .NET Framework derlemeleri çalışma süresine göre tek bir birim olarak değerlendirilir. Varsayılan olarak, bir uygulama başlatıldığında, çalışma zamanı tarafından çalıştırılan kod türlerine yapılan tüm başvurular, bir işlemde yüklenen çalışma zamanıyla aynı sürüm numarasına sahip .NET Framework derlemelerine yönlendirilir. Bu modelle oluşan yeniden yönlendirmeler, çalışma zamanı için varsayılan davranıştır.

 Örneğin, uygulamanız System.XML ad alanında türlere başvuruyorsa ve .NET Framework 4.5 kullanılarak oluşturulmuşsa, çalışma zamanı sürümü 4.5 ile birlikte gönderen System.XML derlemesine statik başvurular içerir. Bağlama başvuruyu .NET Framework 4 ile birlikte gönderilen System.XML derlemesine yönlendirmek istiyorsanız, uygulama yapılandırma dosyasına yönlendirme bilgilerini koyabilirsiniz. Birleştirilmiş .NET Framework derlemesi için yapılandırma dosyasındaki bağlama yeniden yönlendirmesi, bu derlemenin birleştirilmesini iptal eder.

 Ayrıca, birden çok sürüm varsa, üçüncü taraf derlemeler için derleme bağlamayı el ile yeniden yönlendirmek isteyebilirsiniz.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Yayımcı ilkesini kullanarak derleme sürümlerini yeniden yönlendirme
 Derleme satıcıları, yeni derlemeye bir yayımcı ilkesi dosyası ekleyerek uygulamaları derlemenin daha yeni sürümüne yönlendirebilir. Genel derleme önbelleğinde bulunan yayımcı ilkesi dosyası, derleme yeniden yönlendirme ayarlarını içerir.

 Her *büyük.* derlemenin *küçük* bir sürümü kendi yayımcı ilke dosyasına sahiptir. Örneğin, sürüm 2.0.2.222'den 2.0.3.000'e ve sürüm 2.0.2.321'den sürüm 2.0.3.000 sürümüne yeniden yönlendirmeler aynı dosyaya gider, çünkü sürüm 2.0 ile ilişkilidir. Ancak, sürüm 3.0.0.999'dan sürüm 4.0.0.000 sürümüne yeniden yönlendirme, sürüm 3.0.999 için dosyaya gider. .NET Framework'ün her ana sürümünün kendi yayımcı ilke dosyası vardır.

 Bir derleme için yayımcı ilkesi dosyası varsa, çalışma zamanı derlemenin bildirimi ve uygulama yapılandırma dosyasını denetledikten sonra bu dosyayı denetler. Satıcılar yayımcı ilke dosyalarını yalnızca yeni derleme yeniden yönlendirilen derlemeyle geriye dönük uyumlu olduğunda kullanmalıdır.

 Uygulama yapılandırma dosyasındaki ayarları belirterek uygulamanızın yayımcı ilkesini atlayabilirsiniz, [yayıncı ilkesini atlayarak.](#bypass_PP)

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Derleme sürümlerini uygulama düzeyinde yönlendirme
 Uygulama yapılandırma dosyası aracılığıyla uygulamanızın bağlama davranışını değiştirmek için birkaç farklı teknik vardır: dosyayı el ile ayarlayabilir, otomatik bağlama yeniden yönlendirmesi üzerine güvenebilirsiniz veya yayımcı ilkesini atlayarak bağlama davranışı belirtebilirsiniz.

### <a name="manually-editing-the-app-config-file"></a>Uygulama config dosyasını el ile düzenleme
 Derleme sorunlarını gidermek için uygulama yapılandırma dosyasını el ile ayarlayabilirsiniz. Örneğin, bir satıcı, uygulamanızın yayımcı ilkesi sağlamadan kullandığı derlemenin daha yeni bir sürümünü serbest bırakabilirse, geriye dönük uyumluluğu garanti etmedikleri için, uygulamanızın yapılandırma dosyasına derleme bağlayıcı bilgileri aşağıdaki gibi koyarak uygulamanızı derlemenin yeni sürümünü kullanmaya yönlendirebilirsiniz.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Otomatik bağlama yeniden yönlendirmesi güvenerek

Visual Studio'da .NET Framework 4.5.1 veya daha sonraki bir sürümü hedefleyen bir masaüstü uygulaması oluşturduğunuzda, uygulama otomatik bağlama yönlendirmesini kullanır. Bu, iki bileşenaynı güçlü adlandırılmış derlemenin farklı sürümlerine başvuruyorsa, çalışma zamanının çıktı uygulaması yapılandırmasındaki (app.config) derlemenin yeni sürümüne otomatik olarak bağlama yeniden yönlendirmesi eklediği anlamına gelir. Bu yeniden yönlendirme, aksi takdirde gerçekleşebilecek derleme birleştirme geçersiz kılar. Kaynak app.config dosyası değiştirilmez. Örneğin, uygulamanızın doğrudan bant dışı bir .NET Framework bileşenine atıfta bulunuldığını, ancak aynı bileşenin eski bir sürümünü hedefleyen bir üçüncü taraf kitaplığı kullandığını varsayalım. Uygulamayı derlediğinizde, çıktı uygulaması yapılandırma dosyası bileşenin yeni sürümüne bağlayıcı bir yeniden yönlendirme içerecek şekilde değiştirilir. Bir web uygulaması oluşturursanız, bağlama çakışması yla ilgili bir yapı uyarısı alırsınız ve bu da size kaynak web yapılandırma dosyasına gerekli bağlama yönlendirmesini ekleme seçeneği sunar.

Kaynak app.config dosyasına el ile bağlama yönlendirmeleri eklerseniz, derleme zamanında Visual Studio eklediğiniz bağlama yönlendirmelerine göre derlemeleri birleşimmeye çalışır. Örneğin, bir derleme için aşağıdaki bağlayıcı yönlendirmeyi eklediğinizi varsayalım:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Uygulamanızdaki başka bir proje aynı derlemenin 1.0.0.0 sürümüne başvuruyorsa, otomatik bağlama yeniden yönlendirmesi çıktı uygulamasına aşağıdaki girişi ekler.config dosyası, uygulamanın bu derlemenin 2.0.0.0 sürümünde birleştirilmiş olması için aşağıdaki girişi ekler:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Uygulamanız .NET Framework'ün eski sürümlerini hedefliyorsa otomatik bağlama yönlendirmesini etkinleştirebilirsiniz. Bu varsayılan davranışı, herhangi bir derleme için app.config dosyasında bağlayıcı yeniden yönlendirme bilgileri sağlayarak veya bağlama yeniden yönlendirme özelliğini kapatarak geçersiz kabilirsiniz. Bu özelliğin nasıl açılabildiği veya kapatılabileceği hakkında bilgi için [bkz.](how-to-enable-and-disable-automatic-binding-redirection.md)

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Yayımcı ilkesini atlayarak
 Gerekirse uygulama yapılandırma dosyasındaki yayımcı ilkesini geçersiz kılabilirsiniz. Örneğin, geriye dönük uyumlu olduğunu iddia eden derlemelerin yeni sürümleri yine de bir uygulamayı bozabilir. Yayımcı ilkesini atlamak istiyorsanız, uygulama yapılandırma dosyasındaki [ \<bağımlıAssembly>](./file-schema/runtime/dependentassembly-element.md) öğesine bir [ \<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) öğesi ekleyin ve **uygulama** özniteliğini önceki **evet** ayarlarını geçersiz kılan **hayır**'a ayarlayın.

 `<publisherPolicy apply="no" />`

 Uygulamanızın kullanıcılarınız için çalışmasını sağlamak için yayımcı ilkesini atlayın, ancak sorunu montaj satıcısına rapor ettiğinizden emin olun. Bir derlemenin yayımcı ilkesi dosyası varsa, satıcı derlemenin geriye doğru uyumlu olduğundan ve istemcilerin yeni sürümü mümkün olduğunca kullanabileceğinden emin olmalıdır.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Montaj sürümlerini makine düzeyinde yönlendirme
 Bir makine yöneticisi, bilgisayardaki tüm uygulamaların derlemenin belirli bir sürümünü kullanmasını istediğinde nadir durumlar olabilir. Örneğin, bu sürüm bir güvenlik deliğini giderdiği için yönetici her uygulamanın belirli bir derleme sürümünü kullanmasını isteyebilir. Bir derleme makinenin yapılandırma dosyasına yönlendirilirse, eski sürümü kullanan makinedeki tüm uygulamalar yeni sürümü kullanmak üzere yönlendirilir. Makine yapılandırma dosyası, uygulama yapılandırma dosyasını ve yayımcı ilkesi dosyasını geçersiz kılar. Bu dosya % çalışma*zamanı yükleme yolu*%\Config dizininde bulunur. Genellikle ,.NET Framework %drive%\Windows\Microsoft.NET\Framework dizininde yüklenir.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Yapılandırma dosyalarında derleme bağlama belirtme
 Uygulama yapılandırma dosyasında, makine yapılandırma dosyasında veya yayımcı ilkesi dosyasında olsun, bağlama yönlendirmelerini belirtmek için aynı XML biçimini kullanırsınız. Bir derleme sürümünü diğerine yönlendirmek için [ \<bağlayıcıRedirect>](./file-schema/runtime/bindingredirect-element.md) öğesini kullanın. **eskiSürüm** özniteliği tek bir derleme sürümü veya çeşitli sürümler belirtebilir. Öznitelik `newVersion` tek bir sürüm belirtmelidir.  Örneğin, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` çalışma zamanının 1.1.0.0 ile 1.2.0.0 arasındaki derleme sürümleri yerine 2.0.0.0 sürümünü kullanması gerektiğini belirtir.

 Aşağıdaki kod örneği, çeşitli bağlama yönlendirme senaryolarını gösterir. Örnek, bir dizi sürüm için `myAssembly`bir yönlendirme ve . `mySecondAssembly` Örnek, yayımcı ilke dosyasının `myThirdAssembly`bağlayıcı yönlendirmeleri geçersiz kılmayacağını da belirtir.

 Bir derlemeyi bağlamak için derlemede **xmlns** özniteliği ile "urn:schemas-microsoft-com:asm.v1" [ \<dizesini](./file-schema/runtime/assemblybinding-element-for-runtime.md) belirtmeniz gerekir>etiketi.

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

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Montaj bağlamalarını belirli bir sürümle sınırlama
 Derleme bağlayıcı **appliesTo** başvuruları .NET Framework'ün [ \<](./file-schema/runtime/assemblybinding-element-for-runtime.md) belirli bir sürümüne yönlendirmek için bir uygulama yapılandırma dosyasındaki bağlama>öğesini kullanabilirsiniz. Bu isteğe bağlı öznitelik, hangi sürüme uygulandığını belirtmek için bir .NET Framework sürüm numarası kullanır. Hiçbir **öznitelik** belirtilmemişse, [ \<derlemeBağlama>](./file-schema/runtime/assemblybinding-element-for-runtime.md) öğesi .NET Framework'ün tüm sürümlerine uygulanır.

 Örneğin, bir .NET Framework 3.5 derlemesi için derleme bağlamayı yeniden yönlendirmek için uygulama yapılandırma dosyanıza aşağıdaki XML kodunu eklersiniz.

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

 Yeniden yönlendirme bilgilerini sürüm sırasına girmeniz gerekir. Örneğin, .NET Framework 3.5 derlemeleri ve ardından .NET Framework 4.5 derlemeleri için derleme bağlama yeniden yönlendirme bilgilerini girin. Son olarak, **geçerliliği** kullanmayan ve bu nedenle .NET Framework'ün tüm sürümleriiçin geçerli olan herhangi bir .NET Framework derleme yeniden yönlendirmesi için derleme bağlama yeniden yönlendirme bilgilerini girin. Yeniden yönlendirmede bir çakışma varsa, yapılandırma dosyasındaki ilk eşleşen yeniden yönlendirme deyimi kullanılır.

 Örneğin, bir başvuruyu .NET Framework 3.5 derlemesine ve başka bir başvuruyu bir .NET Framework 4 derlemesine yönlendirmek için aşağıdaki sözde kodda gösterilen deseni kullanın.

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
- [\<bağlayıcıRedirect> Elemanı](./file-schema/runtime/bindingredirect-element.md)
- [Derleme Bağlama Yönlendirmesi Güvenlik İzni](assembly-binding-redirection-security-permission.md)
- [.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)
- [Derlemelerle Programlama](../../standard/assembly/index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Uygulamaları Yapılandırma](index.md)
- [Çalışma Zamanı Ayarları Şeması](./file-schema/runtime/index.md)
- [Yapılandırma Dosya Şema](./file-schema/index.md)
- [Nasıl yapılır: Yayımcı İlkesi Oluşturma](how-to-create-a-publisher-policy.md)
