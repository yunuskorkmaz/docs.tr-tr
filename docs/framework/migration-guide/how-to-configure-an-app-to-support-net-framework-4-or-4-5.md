---
title: "Nasıl yapılır: Bir Uygulamayı .NET Framework 4 veya 4.5'i Destekleyecek Şekilde Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring apps to support .NET Framework 4
- .NET Framework 4, configuring apps
- .NET Framework 4.5, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ba3d248dbdd81cf2e2e4445d1e1eb160605542c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-45"></a>Nasıl yapılır: Bir Uygulamayı .NET Framework 4 veya 4.5'i Destekleyecek Şekilde Yapılandırma
Ortak dil çalışma zamanı (CLR) barındıran tüm uygulamalar başlatmanız gerekir veya *etkinleştirme*, yönetilen kod çalıştırmak için CLR. Genellikle bir .NET Framework uygulaması üzerinde derlendiği CLR sürümünde çalışır, ancak bir uygulama yapılandırma dosyası (bazen app.config dosyası olarak da anılır) kullanarak bu davranışı masaüstü uygulamalar için değiştirebilirsiniz. Ancak bir uygulama yapılandırma dosyası Windows Mağazası uygulamaları ya da Windows Phone uygulamaları için varsayılan etkinleştirme davranışını değiştiremezsiniz. Bu makale, masaüstü uygulamanızın .NET Framework'ün başka bir sürümünde çalışmasının nasıl sağlanacağını açıklamakta ve 4 veya 4.5 sürümünün nasıl hedefleneceğine bir örnek vermektedir.  
  
 Bir uygulamanın üzerinde çalıştığı .NET Framework sürümü aşağıdaki sırada belirlenir:  
  
-   Yapılandırma dosyası.  
  
     Uygulama yapılandırma dosyasını içeriyorsa [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) kullanıcının bilgisayarında bir veya birden çok .NET Framework sürümleri ve bu sürümlerinden birini belirtin girişleri varsa, bu sürümünde uygulama çalıştıran . Yapılandırma dosyasını okur [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) girişleri listelenen sırayla ve kullanıcının bilgisayarda var olan ilk .NET Framework sürüm listelenen kullanır. (Kullanım [ \<requiredRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) sürüm 1.0 için.)  
  
-   Derlenmiş sürüm.  
  
     Bir yapılandırma dosyası yoksa, ancak uygulamanın oluşturulduğu .NET Framework sürümü kullanıcının makinesinde mevcutsa, uygulama o sürümde çalışır.  
  
-   En son sürüm yüklendi.  
  
     Uygulama yerleşik bir .NET Framework sürümü mevcut değil ve bir yapılandırma dosyası bir sürümde belirtmiyorsa bir [ \<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), uygulamanın en son sürümünü .NET üzerinde çalışmayı dener Kullanıcının bilgisayarda var çerçevesi.  
  
     Ancak .NET Framework 1.0, 1.1, 2.0, 3.0 ve 3.5 uygulamaları, .NET Framework 4 ve sonraki sürümleri otomatik çalıştırmaz ve bazı durumlarda kullanıcı bir hata alabilir ve kullanıcının .NET Framework 3.5 yüklemesi istenebilir. Windows sisteminin farklı sürümleri .NET Framework'ün farklı sürümlerinin içerdiğinden etkinleştirme davranışı kullanıcının işletim sistemine de bağlı olabilir. Uygulamanız hem .NET Framework 3.5 hem de 4 ve üstünü destekliyorsa, .NET Framework başlatma hatalarını önlemek için bunu yapılandırma dosyasında birden çok giriş işe belirtmenizi öneririz. Daha fazla bilgi için bkz: [sürümleri ve bağımlılıkları](../../../docs/framework/migration-guide/versions-and-dependencies.md).  
  
 Ayrıca, .NET Framework 3.5 uygulamalarınızı, .NET Framework 4 ve 4.5 sürümlerindeki performans iyileştirmelerinden yararlanmak üzere, .NET Framework 3.5 yüklü bilgisayarlarda bile .NET Framework 4'te veya 4.5'te çalışacak şekilde yapılandırmak isteyebilirsiniz.  
  
> [!IMPORTANT]
>  Uygulamanızı desteklediğiniz her .NET Framework sürümünde her zaman test etmenizi öneririz. Bkz: [sürüm uyumluluğu](../../../docs/framework/migration-guide/version-compatibility.md) sonraki .NET Framework sürümleri desteklemek için uygulamanızın yükseltme hakkında bilgi için.  
  
 Windows 7 ve Windows 8 desteklemek için .NET Framework 1.0 ve 1.1 uygulamalarınızı değiştirme hakkında daha fazla bilgi için bkz: [.NET Framework 1. 1 ' geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
### <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-45"></a>Uygulamanızı .NET Framework 4 veya 4.5'te çalışacak şekilde yapılandırma  
  
1.  .NET Framework projesinin yapılandırma dosyasını ekleyin ya da bulun. Bir uygulamanın yapılandırma dosyası aynı dizindedir ve uygulama ile aynı ada ancak .config uzantısına sahiptir. Örneğin, MyExecutable.exe adlı bir uygulama için uygulama yapılandırma dosyası MyExecutable.exe.config olarak adlandırılır.  
  
     Visual Studio menü çubuğunda, bir yapılandırma dosyası eklemek için **proje**, **Yeni Öğe Ekle**. Seçin **genel** sol bölmeden ve ardından **yapılandırma dosyası**.  Yapılandırma dosyası adı *appName*. exe.config. Bu menü seçenekleri Windows Mağazası uygulaması veya Windows telefon uygulaması projelerinde kullanılamaz, çünkü bu platformlarda etkinleştirme ilkesini değiştiremezsiniz.  
  
2.  Ekleme [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) öğesini aşağıdaki gibi uygulama yapılandırma dosyası:  
  
    ```xml  
    <configuration>  
      <startup>  
        <supportedRuntime version="<version>"/>  
      </startup>  
    </configuration>  
    ```  
  
     Burada  *\<sürüm >* uygulamanızı destekleyen .NET Framework sürüm ile hizalar CLR sürümü belirtir. Aşağıdaki dizeleri kullanın:  
  
    -   .NET Framework 1.0: "v1.0.3705"  
  
    -   .NET Framework 1.1: "v1.1.4322"  
  
    -   .NET Framework 2.0, 3.0 ve 3.5: "v2.0.50727"  
  
    -   .NET Framework 4 ve 4.5 (4.5.1 gibi nokta sürümleri dahil): "v4.0"  
  
     Birden çok ekleyebilirsiniz [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) öğeleri, birden çok .NET Framework sürümleri için destek belirtmek için tercih sırasına göre listelenen.  
  
 Aşağıdaki tablo, bir bilgisayara yüklenen uygulama yapılandırma dosyası ayarlarının ve .NET Framework sürümlerinin bir .NET Framework 3.5 uygulamasının üzerinde çalıştığı sürümü nasıl belirlediğini göstermektedir. Örnekler, .NET Framework 3.5 uygulamasına özgüdür, ancak daha eski .NET Framework sürümlerini kullanarak oluşturulan hedef uygulamalar için de aynı mantığı kullanabilirsiniz. NET Framework 2.0 sürüm numarasının (v2.0.50727), uygulama yapılandırma dosyasında .NET Framework 3.5'i belirtmek için kullanıldığını unutmayın.  
  
|App.config dosyası ayarı|3.5 sürümü yüklü bilgisayarda|3.5 ve 4 veya 4.5 sürümleri yüklü bilgisayarda|4 veya 4.5 sürümü yüklü bilgisayarda|  
|-|-|-|-|  
|Yok.|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|  
|`<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|  
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|4 veya 4.5 üzerinde çalışır|  
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|4 veya 4.5 üzerinde çalışır|4 veya 4.5 üzerinde çalışır|  
|`<supportedRuntime version="v4.0"/>`|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|4 veya 4.5 üzerinde çalışır|4 veya 4.5 üzerinde çalışır|  
  
 \*Bu hata iletisi ve bunu önlemenin yolu hakkında daha fazla bilgi için bkz: [.NET Framework başlatma hataları: kullanıcı deneyimini yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework 1.1'den Geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Geçiş Kılavuzu](../../../docs/framework/migration-guide/index.md)
