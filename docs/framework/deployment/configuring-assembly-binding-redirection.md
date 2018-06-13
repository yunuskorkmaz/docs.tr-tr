---
title: Derleme Bağlama Yönlendirmesini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04743dc7a0fc821f2e3b94929e2384eb25c69f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387191"
---
# <a name="configuring-assembly-binding-redirection"></a>Derleme Bağlama Yönlendirmesini Yapılandırma
Varsayılan olarak, uygulamaların uygulama derlemek için kullanılan çalışma zamanı sürümü ile birlikte gelen .NET Framework derlemeler kümesini kullanın. Kullanabileceğiniz **appliesTo** özniteliği [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) derleme bağlama başvuruları .NET belirli bir sürümüne yeniden yönlendirmek için bir uygulama yapılandırma dosyasında öğesi Framework'te derleme. Bu isteğe bağlı öznitelik uygulandığı hangi sürüm belirtmek için bir .NET Framework sürüm numarası kullanır. Öyle değilse **appliesTo** özniteliği belirtilirse  **\<assemblyBinding >** öğesi tüm .NET Framework sürümleri için geçerlidir.  
  
 **AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 göz ardı edilir. Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.  
  
> [!NOTE]
>  Kullanım **appliesTo** Derleme bağlaması yeniden yönlendirme çalışma zamanının belirli bir sürüme sınırlamak için öznitelik.  
  
 Örneğin, derleme için bir .NET Framework sürüm 1.0 Derleme bağlaması yeniden yönlendirme için uygulama yapılandırma dosyasında aşağıdaki XML kodunu içermesi.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<AssemblyBinding >** sipariş duyarlı öğeleridir. Derleme bağlaması yeniden yönlendirme bilgilerini tüm .NET Framework sürüm 1.1 derlemeler için arkasından Derleme bağlaması yeniden yönlendirme bilgilerini tüm .NET Framework sürüm 1.0 derlemeler için ilk olarak, girmeniz gerekir. Son olarak, Derleme bağlaması yeniden yönlendirme bilgilerini kullanmayan tüm .NET Framework derleme yeniden yönlendirme için girin **appliesTo** özniteliği ve bu nedenle, .NET Framework'ün tüm sürümleri için geçerlidir. Yeniden yönlendirme bir çakışma durumunda ilk eşleşen yeniden yönlendirme deyiminde yapılandırma dosyası kullanılır.  
  
 Örneğin, bir .NET Framework sürüm 1.0 derleme bir başvuru ve bir .NET Framework sürüm 1.1 derleme başka bir başvuru yeniden yönlendirmek için aşağıdaki yarı kodu içinde gösterilen düzeni kullanırsınız.  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
<! — .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
    <! — .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
<!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a>Yapılandırma Dosyası Hatalarını Ayıklama  
 Uygulama etki alanı oluşturulduğunda ve o uygulama etki alanına kod yükler çalışma zamanı yapılandırma dosyalarını bir kez ayrıştırır. Ortak dil çalışma zamanı, giriş yoksayılıyor tarafından bir yapılandırma dosyasına hatalarını ele alır. Hatalı biçimlendirilmiş XML içeriyorsa, çalışma zamanı tüm yapılandırma dosyası yok sayar. Geçersiz XML için yalnızca geçersiz bölüm göz ardı edilir.  
  
 Derleme bağlama yeniden yönlendirmeleri yaşanan olup olmadığını bir yapılandırma dosyası belirleyerek kullanılmakta olup olmadığını belirleyebilirsiniz. Kullanım [Derleme bağlaması Günlük Görüntüleyici (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) hangi derlemelerin yüklü görmek için. Tüm derleme bağlamalar görmek için bir girişi ayarlayın **ForceLog** kayıt defterinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
