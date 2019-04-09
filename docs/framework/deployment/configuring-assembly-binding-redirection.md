---
title: Derleme Bağlama Yönlendirmesini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5df468b87c62f454f6a42fa7a80d92e5ec199fd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151547"
---
# <a name="configuring-assembly-binding-redirection"></a>Derleme Bağlama Yönlendirmesini Yapılandırma
Varsayılan olarak, uygulamalar, uygulama derlemek için kullanılan çalışma zamanı sürümü ile birlikte .NET Framework derlemeleri kümesini kullanın. Kullanabileceğiniz **appliesTo** özniteliği [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) derleme bağlama başvurularının nasıl belirli bir .NET sürümünü yeniden yönlendirmek için bir uygulama yapılandırma dosyasında öğesi Framework derlemeleri. İsteğe bağlı bu öznitelik, bir .NET Framework sürüm numarası geçerli hangi sürüm olduğunu belirlemek için kullanır. Hayır ise **appliesTo** özniteliği belirtilirse,  **\<assemblyBinding >** öğe tüm .NET Framework sürümleri için geçerlidir.  
  
 **AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 tarafından göz ardı edilir. Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.  
  
> [!NOTE]
>  Kullanım **appliesTo** belirli bir çalışma zamanı sürümünü derleme bağlama yeniden yönlendirme sınırlamak için özniteliği.  
  
 Örneğin, derleme için bir .NET Framework sürüm 1.0 derleme bağlamasına yönlendirmek için aşağıdaki XML kodunu uygulama yapılandırma dosyanızda verilebilir.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<AssemblyBinding >** sipariş duyarlı öğeleridir. Herhangi bir .NET Framework sürüm 1.1 derlemeler için derleme bağlama yönlendirme bilgisini ardından herhangi bir .NET Framework sürüm 1.0 derlemeler için derleme bağlama yönlendirme bilgisini ilk olarak girmeniz gerekir. Son olarak, kullanılmayan tüm .NET Framework derleme yeniden yönlendirmesi için derleme bağlama yönlendirme bilgisini girin **appliesTo** özniteliği ve bu nedenle tüm .NET Framework sürümleri için geçerlidir. Yeniden yönlendirme bir çakışma olması durumunda, yapılandırma dosyasındaki eşleşen ilk yönlendirme cümlesi kullanılır.  
  
 Örneğin, .NET Framework sürüm 1.0 derlemesine bir başvuru ve başka bir başvuru bir .NET Framework sürüm 1.1 derlemesine yönlendirmek için aşağıdaki sözde kod gösterilen yöntemi kullanın.  
  
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
 Uygulama etki alanı oluşturulduğunda ve kodu, uygulama etki alanına yükler, çalışma zamanı yapılandırma dosyalarını bir kez ayrıştırır. Ortak dil çalışma zamanı, giriş yoksayarak bir yapılandırma dosyası hatalarını ele alır. Hatalı biçimlendirilmiş XML içeriyorsa, çalışma zamanı, tüm yapılandırma dosyası yok sayar. Geçersiz XML için yalnızca geçersiz bölümlere göz ardı edilir.  
  
 Derleme bağlama yeniden yönlendirmeleri gerçekleşen olup olmadığını bir yapılandırma dosyası belirleyerek kullanılıp kullanılmadığını belirleyebilirsiniz. Kullanım [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) hangi derlemelerin yüklenen görmek için. Tüm derleme bağlamalarını öğrenmek için bir giriş ayarlamak **ForceLog** kayıt defteri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
