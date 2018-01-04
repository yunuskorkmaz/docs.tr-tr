---
title: ".NET Framework 1.1'den Geçiş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d54fac935e7b1fad6b07a3a6cf2031dbca702cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-from-the-net-framework-11"></a>.NET Framework 1.1'den Geçiş
[!INCLUDE[win7](../../../includes/win7-md.md)]ve Windows işletim sisteminin sonraki sürümlerini desteklemez [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]. Sonuç olarak, hedef uygulamalar [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] değişiklik yapmadan çalışmaz [!INCLUDE[win7](../../../includes/win7-md.md)] veya sonraki işletim sistemi sürümleri. Bu konuda hedefleyen bir uygulamayı çalıştırmak için gereken adımlar açıklanmaktadır [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] altında [!INCLUDE[win7](../../../includes/win7-md.md)] ve Windows işletim sisteminin sonraki sürümleri. Hakkında daha fazla bilgi için [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] ve [!INCLUDE[win8](../../../includes/win8-md.md)], bkz: [.NET Framework 1.1 uygulamalarını çalıştıran Windows 8 ve sonraki sürümlerde](../../../docs/framework/install/run-net-framework-1-1-apps.md).  
  
## <a name="retargeting-or-recompiling"></a>Yeniden hedefleme veya yeniden derlenmesi  
 Kullanarak derlenen bir uygulamayı almanın iki yolu vardır [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] çalıştırmak için [!INCLUDE[win7](../../../includes/win7-md.md)] veya sonraki bir Windows işletim sistemi:  
  
-   Uygulamayı altında çalışacak şekilde yeniden hedefleyin [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Yeniden hedefleme gerektirir eklediğiniz bir [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) öğesi altında çalıştırılmasına izin verir uygulamanın yapılandırma dosyasına [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Bu tür bir yapılandırma dosyası aşağıdaki biçimdedir:  
  
    ```xml  
    <configuration>   
       <startup>  
          <supportedRuntime version="v4.0"/>  
       </startup>  
    </configuration>  
    ```  
  
-   Uygulama hedefleyen bir derleyici ile derlemeniz [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Başlangıçta geliştirmek ve çözümünüzü derlemek için Visual Studio 2003 kullandıysanız, çözümdeki açabilirsiniz [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] ve **proje Uyumluluk** tarafından kullanılan biçimleri çözüm ve proje dosyalarını dönüştürmek için iletişim kutusu Visual Studio 2003 tarafından kullanılan Microsoft Build Engine (MSBuild) biçimine [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)].  
  
 Olup derlenir veya uygulamanızın yeniden hedefleyin tercih ettiğiniz bağımsız olarak, uygulamanız .NET Framework'ün daha sonraki sürümlerde sunulan herhangi bir değişiklikten etkilenen olup olmadığını belirlemeniz gerekir. Bu değişiklikler, iki tür şunlardır:  
  
-   Yeni arasında gerçekleşen değişiklikler [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] ve .NET Framework'ün sonraki sürümler.  
  
-   Türleri ve kullanım dışı olarak işaretlenmiş veya arasında eski tür üyeleri [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] ve .NET Framework'ün sonraki sürümler.  
  
 Uygulamanızı yeniden hedefleyin veya yeniden derleyin olup hem önemli değişiklikler ve eski türler ve üyeleri her sonra yayımlanmış olan .NET Framework sürümü için gözden geçirmeniz gereken [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
## <a name="breaking-changes"></a>Yeni Değişiklikler  
 Önemli bir değişiklik oluştuğunda belirli değişiklik bağlı olarak geçici bir çözüm kullanılabilir olan her ikisi için güncellendiyse ve uygulamaları yeniden derlenebileceğini gösterir. Bazı durumlarda, bir alt öğesi ekleyebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) önceki davranışını geri yüklemek için uygulamanızın yapılandırma dosyası öğesi. Örneğin, aşağıdaki yapılandırma dosyası kullanılan dize sıralama ve karşılaştırma davranışını geri yükler [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] ve ya bir güncellendiyse ya da derlenmiş bir uygulama ile kullanılabilir.  
  
```xml  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
 Ancak, bazı durumlarda, uygulamanızı derleyin ve kaynak kodunuzu değiştirmek olabilir.  
  
 Olası önemli değişiklikler, uygulamanızın üzerinde etkisi değerlendirmek için aşağıdaki değişiklikler listesini gözden geçirmeniz gerekir:  
  
-   [.NET Framework 2. 0 ' önemli değişiklikler](http://go.microsoft.com/fwlink/?LinkId=125263) değişiklikleri belgeleri [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] hedefleyen bir uygulama etkileyebilecek [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
-   [.NET Framework 3.5 SP1'deki değişiklikleri](http://go.microsoft.com/fwlink/?LinkID=186989) arasındaki değişiklikleri belgeleri [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].  
  
-   [.NET framework 4 geçiş sorunları](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) arasındaki değişiklikleri belgeleri [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
## <a name="obsolete-types-and-members"></a>Eski türler ve üyeleri  
 Kullanım dışı türleri ve üyeleri etkisini güncellendiyse uygulamalar için biraz farklıdır ve uygulamaları yeniden derlenebileceğini gösterir. Geçersiz tür veya üye kendi derlemesinden fiziksel olarak kaldırıldı sürece eski türler ve üyeleri kullanımını güncellendiyse uygulama etkilemez. Artık kullanılmayan türler veya üyeler genellikle kullanan bir uygulamayı yeniden derlenmesi derleyici hatası yerine uyarı derleyici üretir. Ancak, bazı durumlarda, bir derleyici hatası oluşturur ve eski tür veya üye kullanan kodu başarıyla derlenmiyor. Bu durumda, uygulamanızı derleyin önce eski tür veya üye çağıran kaynak kodu yeniden yazmanız gerekir. Eski türler ve üyeleri hakkında daha fazla bilgi için bkz: [Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md).  
  
 Tür ve yayımlandıktan sonra kullanım üyelerinin etkisini değerlendirmek için [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], bkz: [Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md). Eski türler ve üye için listelerini gözden [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].
