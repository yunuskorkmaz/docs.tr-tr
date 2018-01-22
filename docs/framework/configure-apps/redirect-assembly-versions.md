---
title: "Derleme Sürümlerini Yönlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
caps.latest.revision: "26"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 26475a543950b4f7161243d72252cc1982adf93f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="redirecting-assembly-versions"></a>Derleme Sürümlerini Yönlendirme
.NET Framework derlemeleri, üçüncü taraf derlemeleri ya da kendi uygulamanın derlemelerini derleme zamanı bağlama başvuruları yönlendirebilirsiniz. Çeşitli yollarla bütünleştirilmiş farklı bir sürümünü kullanmak için uygulamanızı yeniden yönlendirebilirsiniz: Yayımcı ilkesi, bir uygulama yapılandırma dosyası; aracılığıyla aracılığıyla makine yapılandırma dosyası aracılığıyla veya. Bu makalede, .NET Framework Derleme bağlama nasıl çalıştığını ve nasıl yapılandırılması anlatılmaktadır.  
  
<a name="BKMK_Assemblyunificationanddefaultbinding"></a>   
## <a name="assembly-unification-and-default-binding"></a>Birleştirici derleme ve varsayılan bağlama  
 .NET Framework derlemeleri bağlamalar bazen adlı bir işlem yeniden yönlendirilen *birleştirici derleme*. .NET Framework ortak dil çalışma zamanı ve tür kitaplığı olun yaklaşık iki düzine .NET Framework derlemeleri sürümünü oluşur. Bu .NET Framework derlemeleri çalışma zamanı tarafından tek bir birim olarak kabul edilir. Bir uygulama başlatıldığında, varsayılan olarak, bir işlemde yüklenen çalışma zamanı aynı sürüm numarasına sahip .NET Framework derlemeleri çalışma zamanı tarafından kod türlerinde yapılan tüm başvuruları yönlendirilir. Bu modelde ortaya yeniden yönlendirme çalışma zamanı için varsayılan davranış ' dir.  
  
 Örneğin, uygulamanızı başvuruyorsa türleri System.XML ad alanındaki ve kullanılarak oluşturulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], çalışma zamanı sürüm 4.5 ile birlikte gelen System.XML derleme statik başvuru içeriyor. .NET Framework 4 ile birlikte System.XML derleme işaret etmek için bağlama başvuru yönlendirmek istiyorsanız, uygulama yapılandırma dosyasında yeniden yönlendirme bilgi koyabilirsiniz. Birleştirilmiş bir .NET Framework derleme için bir yapılandırma dosyasına bağlama yeniden yönlendirme bu derleme Birleştirici iptal eder.  
  
 Ayrıca, el ile derleme kullanılabilir birden çok sürüm varsa, üçüncü taraf derlemeler için bağlama yeniden yönlendirme isteyebilirsiniz.  
  
<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>   
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Yayımcı ilkesi kullanarak derleme sürümlerini yönlendirme  
 Derlemeleri satıcıları uygulamaları derleme daha yeni bir sürümü için yeni bir derleme Yayımcı ilkesi dosyasıyla dahil ederek yönlendirebilirsiniz. Genel derleme önbelleğinde bulunan, yayımcı ilkesi dosyası derleme yeniden yönlendirme ayarlarını içerir.  
  
 Her *ana*. *küçük* bir derlemenin sürüm kendi Yayımcı ilkesi dosyası vardır. Örneğin, sürüm 2.0 ile ilişkili olduğundan yeniden yönlendirme için 2.0.2.222 2.0.3.000 sürümünden ve 2.0.2.321 sürümünden 2.0.3.000 sürümüne her ikisi de aynı dosyaya gidin. Ancak, bir yeniden yönlendirme 3.0.0.999 sürümünden sürüm 4.0.0.000 sürüm 3.0.999 dosyasına gider. .NET Framework'ün her ana sürüm kendi Yayımcı ilkesi dosyası vardır.  
  
 Bir derleme için bir yayımcı ilkesi dosyası zaten varsa, çalışma zamanı derleme bildirimi ve uygulama yapılandırma dosyası denetledikten sonra bu dosyayı denetler. Yalnızca yeni bir derleme yönlendirilmesini derleme ile geriye dönük olarak uyumlu olduğunda satıcılar yayımcı ilke dosyaları kullanmanız gerekir.  
  
 Yayımcı ilkesi uygulamanız için uygulama yapılandırma dosyasında ayarları belirterek anlatıldığı gibi atlayabilir [Yayımcı ilkesi bölümüne atlayarak](#bypass_PP).  
  
<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>   
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Uygulama düzeyinde derleme sürümlerini yönlendirme  
 Uygulama yapılandırma dosyası, uygulamanız için bağlama davranışı değiştirmek için birkaç farklı teknikler vardır: otomatik bağlama yönlendirmesini güvenebilirsiniz veya yayımcı ilkesi atlayarak bağlama davranışı belirtebilirsiniz dosyayı el ile düzenleyebilirsiniz.  
  
### <a name="manually-editing-the-app-config-file"></a>Uygulama yapılandırma dosyasını el ile düzenleme  
 El ile derleme sorunları gidermek için uygulama yapılandırma dosyasını düzenleyebilirsiniz. Örneğin, bir satıcının geriye dönük uyumluluk garanti değil çünkü bir yayımcı ilkesi girmeden uygulamanızı kullanan bir bütünleştirilmiş koda daha yeni bir sürümü kullanıma, derleme koyarak derlemesinin daha yeni sürümü kullanmak için uygulamanızı yönlendirebilirsiniz Uygulamanızın yapılandırma dosyasındaki bilgilere gibi bağlama.  
  
```xml  
<dependentAssembly>  
        <assemblyIdentity name="someAssembly"  
          publicKeyToken="32ab4ba45e0a69a1"  
          culture="en-us" />  
  
        <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />  
      </dependentAssembly>  
```  
  
### <a name="relying-on-automatic-binding-redirection"></a>Otomatik bağlama yönlendirmesini bağlı  
 İle başlayarak [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], hedef Yeni Masaüstü uygulamaları [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] otomatik bağlama yönlendirmesini kullanın. Başka bir deyişle, iki bileşenleri aynı tanımlayıcı adlı derlemenin farklı sürümleri başvurursanız, çalışma zamanı bağlama yeniden yönlendirme otomatik olarak derleme çıktı uygulama (app.config) yapılandırma dosyasında daha yeni sürümüne olarak ekler. Bu yeniden yönlendirme, aksi takdirde yer alabilir birleştirici derleme geçersiz kılar. Kaynak app.config dosyası değiştirilmez. Örneğin, uygulamanızın doğrudan bir bant dışı .NET Framework bileşenini başvuruyor ancak aynı bileşenin daha eski bir sürümü hedefleyen bir üçüncü taraf kitaplığını kullanan varsayalım. Uygulamayı derlediğinizde çıktı uygulama yapılandırma dosyası bağlama yeniden yönlendirme bileşeni'nin daha yeni sürümüne içerecek şekilde değiştirilir. Bir web uygulaması oluşturma, gerekli bağlama yeniden yönlendirme kaynak web yapılandırma dosyasına ekleme seçeneğini verir sırayla bağlama çakışması yükseltilmesiyle ilgili bir yapı uyarı alırsınız.  
  
 Bağlama yeniden yönlendirmelerini kaynak app.config dosyasına derleme zamanında el ile eklerseniz [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] eklediğiniz bağlama yeniden yönlendirmeleri bağlı derlemeler bütünleştirin dener. Örneğin, bir derleme için aşağıdaki bağlama yeniden yönlendirme Ekle varsayalım:  
  
 `<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`  
  
 Uygulamanızda başka bir projeye aynı bütünleştirilmiş kodda 1.0.0.0 sürümünü başvuruyorsa, böylece uygulama bu derleme sürüm 2.0.0.0 birleşik otomatik bağlama yönlendirmesini çıktı app.config dosyasına şu giriş ekler:  
  
 `<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`  
  
 Uygulamanız .NET Framework'ün daha eski sürümleri hedefliyorsa otomatik bağlama yönlendirmesini etkinleştirebilirsiniz [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]. Herhangi bir derleme için app.config dosyasına bağlama yeniden yönlendirme bilgileri sağlayarak bu varsayılan davranışı geçersiz kılma veya bağlama yeniden yönlendirme özelliğini kapatın. Bu özellik açma veya kapatma hakkında daha fazla bilgi için bkz: [nasıl yapılır: etkinleştirme ve devre dışı bırakmak, bağlama otomatik yeniden yönlendirme](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).  
  
<a name="bypass_PP"></a>   
### <a name="bypassing-publisher-policy"></a>Yayımcı ilkesi atlama  
 Yayımcı ilkesi gerekirse, uygulama yapılandırma dosyasında geçersiz kılabilirsiniz. Örneğin, geriye dönük uyumluluk için talep derlemeleri yeni sürümlerini hala bir uygulama bozulabilir. Yayımcı ilkesi atlamak istiyorsanız, eklemeniz bir [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) öğesine [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) uygulama yapılandırma dosyası ve kümesi öğesi**uygulamak** özniteliğini **hiçbir**, tüm önceki etkisiz kılan **Evet** ayarlar.  
  
 `<publisherPolicy apply="no" />`  
  
 Uygulamanızı kullanıcılarınız için tutmak için yayımcı ilkesi atlama ancak derleme satıcıya sorunu bildirmek emin olun. Bir derlemeyi Yayımcı ilkesi dosyası varsa, satıcı derleme geriye dönük olarak uyumlu olduğunu ve istemciler yeni sürüm mümkün olduğunca kullanabilir emin olmanız gerekir.  
  
<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>   
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Makine düzeyinde derleme sürümlerini yönlendirme  
 Bir Makine Yöneticisi bütünleştirilmiş belirli bir sürümünü kullanmak için bir bilgisayardaki tüm uygulamalar istediğinde nadiren olabilir. Örneğin, yönetici güvenlik delik sürümünün düzeltmeler için belirli derleme sürümü kullanmak için her uygulama isteyebilirsiniz. Makinenin yapılandırma dosyasında bir derlemeyi yönlendirilir, yeni sürümü kullanmak için eski sürümünü kullanan tüm uygulamalar bu makinede yönlendirilir. Makine yapılandırma dosyası uygulama yapılandırma dosyası ve yayımcı ilkesi dosyası geçersiz kılar. Bu dosya % bulunur*çalışma zamanı yükleme yolu*%\Config dizini. Genellikle, .NET Framework %drive%\Windows\Microsoft.NET\Framework dizine yüklenir.  
  
<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>   
## <a name="specifying-assembly-binding-in-configuration-files"></a>Derleme yapılandırma dosyalarında bağlama belirtme  
 Bağlama yeniden yönlendirmelerini uygulama yapılandırma dosyası, makine yapılandırma dosyası veya yayımcı ilkesi dosyası olup olmadığını belirlemek için aynı XML biçimi kullanır. Başka bir derleme sürümü yönlendirmek için kullandığınız [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) öğesi. **OldVersion** özniteliği tek derleme sürümü veya sürüm aralığı belirtebilirsiniz. `newVersion` Özniteliği tek sürümü belirtmeniz gerekir.  Örneğin, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` çalışma zamanı sürüm 2.0.0.0 veya derleme sürümlerini yerine 1.1.0.0 1.2.0.0 arasındaki kullanması gerektiğini belirtir.  
  
 Aşağıdaki kod örneğinde çeşitli bağlama yeniden yönlendirme senaryoları gösterilmektedir. Örnek sürümleri için bir aralığı için bir yeniden yönlendirme belirtir `myAssembly`ve için tek bağlama yeniden yönlendirme `mySecondAssembly`. Örnek, ayrıca bu Yayımcı ilkesi dosyası için bağlama yeniden yönlendirmeleri değil kılar belirtir `myThirdAssembly`.  
  
 Bir derlemeyi bağlamak için dizeyi belirtin "urn: şemaları-microsoft-com:asm.v1" ile **xmlns** özniteliğini [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) etiketi.  
  
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
  
### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Derleme bağlamaları belirli bir sürüme sınırlama  
 Kullanabileceğiniz **appliesTo** özniteliği [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) derleme bağlama başvuruları .NET belirli bir sürümüne yeniden yönlendirmek için bir uygulama yapılandırma dosyasında öğesi Çerçeve. Bu isteğe bağlı öznitelik uygulandığı hangi sürümünün belirtmek için bir .NET Framework sürüm numarası kullanır. Öyle değilse **appliesTo** özniteliği belirtilirse [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) öğesi tüm .NET Framework sürümleri için geçerlidir.  
  
 Örneğin, derleme için bir .NET Framework 3.5 Derleme bağlaması yeniden yönlendirmek için aşağıdaki XML kodunu uygulama yapılandırma dosyanızda içerir.  
  
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
  
 Sürüm sırayla yeniden yönlendirme bilgileri girmeniz gerekir. Örneğin, .NET Framework 4.5 derlemeleri tarafından izlenen .NET Framework 3.5 derlemeler için derleme bağlaması yeniden yönlendirme bilgilerini girin. Son olarak, Derleme bağlaması yeniden yönlendirme bilgilerini kullanmayan tüm .NET Framework derleme yeniden yönlendirme için girin **appliesTo** özniteliği ve bu nedenle, .NET Framework'ün tüm sürümleri için geçerlidir. Yeniden yönlendirmeyi bir çakışma varsa, ilk eşleşen yeniden yönlendirme deyiminde yapılandırma dosyası kullanılır.  
  
 Örneğin, bir .NET Framework 3.5 bütünleştirilmiş koduna bir başvuru ve bir .NET Framework 4 derleme başka bir başvuru yönlendirmek için aşağıdaki yarı kodu gösterilen düzeni kullanın.  
  
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
 [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [\<bindingRedirect> Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Bütünleştirilmiş Kod Bağlama Yönlendirmesi Güvenlik İzni](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Uygulamaları Yapılandırma](../../../docs/framework/configure-apps/index.md)  
 [.NET Framework uygulamaları yapılandırma](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Çalışma Zamanı Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Nasıl yapılır: Yayımcı İlkesi Oluşturma](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
