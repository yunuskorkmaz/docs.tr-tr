---
title: Derleme Bağlama Yönlendirmesini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 5b24d99aa23358272eecd042c40001413965d7f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181692"
---
# <a name="configuring-assembly-binding-redirection"></a>Derleme Bağlama Yönlendirmesini Yapılandırma
Varsayılan olarak, uygulamalar, uygulamayı derlemek için kullanılan çalışma zamanı sürümüyle birlikte gönderilen .NET Framework derlemeleri kümesini kullanır. Derleme bağlama başvurularını .NET Framework derlemelerinin belirli bir sürümüne yönlendirmek için bir uygulama yapılandırma dosyasındaki [ \<>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) öğesini bağlama **özniteliğini** kullanabilirsiniz. Bu isteğe bağlı öznitelik, hangi sürüme uygulandığını belirtmek için bir .NET Framework sürüm numarası kullanır. Hiçbir **öznitelik** belirtilmemişse, ** \<derlemeBağlama>** öğesi .NET Framework'ün tüm sürümlerine uygulanır.  
  
 **AapplyTo** özniteliği .NET Framework sürüm 1.1'de tanıtıldı; .NET Framework sürüm 1.0 tarafından yoksayılır. Bu, .NET Framework sürüm 1.0 kullanılırken tüm ** \<derlemebağlayıcı>** öğelerinin **uygulandığı** anlamına gelir.  
  
> [!NOTE]
> Derleme bağlama yeniden yönlendirmesini çalışma zamanının belirli bir sürümüyle sınırlamak için **applyTo** özniteliğini kullanın.  
  
 Örneğin, bir .NET Framework sürüm 1.0 derlemesi için derleme bağlamayı yeniden yönlendirmek için, uygulama yapılandırma dosyanıza aşağıdaki XML kodunu eklersiniz.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 ** \<DerlemeBağlama>** elemanları siparişe duyarlıdır. Önce .NET Framework sürüm 1.0 derlemeleri için derleme bağlama yeniden yönlendirme bilgilerini girmeniz, ardından da herhangi bir .NET Framework sürüm 1.1 derlemeleri için derleme bağlama yeniden yönlendirme bilgileri girmeniz gerekir. Son olarak, **geçerliliği** kullanmayan ve bu nedenle .NET Framework'ün tüm sürümleriiçin geçerli olan herhangi bir .NET Framework derleme yeniden yönlendirmesi için derleme bağlama yeniden yönlendirme bilgilerini girin. Yeniden yönlendirmede bir çakışma olması durumunda, yapılandırma dosyasındaki ilk eşleşen yeniden yönlendirme deyimi kullanılır.  
  
 Örneğin, bir başvuruyu .NET Framework sürüm 1.0 derlemesine ve başka bir başvuruyu bir .NET Framework sürüm 1.1 derlemesine yönlendirmek için aşağıdaki pseudocode'da gösterilen deseni kullanırsınız.  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">
  <!-- .NET Framework version 1.0 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">
  <!-- .NET Framework version 1.1 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="...">
  <!-- Redirects meant for all versions of the .NET Framework. -->
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a>Yapılandırma Dosyası Hatalarını Ayıklama  
 Çalışma zamanı, bir uygulama etki alanı oluşturulduğunda yapılandırma dosyalarını bir kez ayrıştırır ve kodu bu uygulama etki alanına yükler. Ortak dil çalışma süresi, girişi yoksayarak yapılandırma dosyasındaki hataları işler. Çalışma süresi, hatalı biçimlendirilmiş XML içeriyorsa tüm yapılandırma dosyasını yoksa. Geçersiz XML için yalnızca geçersiz bölümler yoksayılır.  
  
 Derleme bağlama yönlendirmelerinin oluşup oluşmadığını belirleyerek yapılandırma dosyasının kullanılıp kullanılmayacağını belirleyebilirsiniz. Hangi derlemelerin yüklendiğini görmek için [Derleme Bağlama Günlük Görüntüleyici'ni (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) kullanın. Tüm montaj bağlarını görmek için, kayıt defterine **ForceLog** için bir giriş ayarlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
