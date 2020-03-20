---
title: 'Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
ms.openlocfilehash: 586f39fc9b50dcd45bb959ebd0063e3c38d9c3ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716241"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Nasıl yapilir: Bir Uygulamayı Destekle .NET Framework 4 veya sonraki sürümlerini yapılandırma

Ortak dil çalışma zamanını (CLR) barındıran tüm uygulamaların yönetilen kodu çalıştırmak için CLR'yi başlatması veya *etkinleştirmesi*gerekir. Genellikle bir .NET Framework uygulaması üzerinde derlendiği CLR sürümünde çalışır, ancak bir uygulama yapılandırma dosyası (bazen app.config dosyası olarak da anılır) kullanarak bu davranışı masaüstü uygulamalar için değiştirebilirsiniz. Ancak bir uygulama yapılandırma dosyası Windows Mağazası uygulamaları ya da Windows Phone uygulamaları için varsayılan etkinleştirme davranışını değiştiremezsiniz. Bu makalede, masaüstü uygulamanızın .NET Framework'ün başka bir sürümünde nasıl çalıştırılacağına nasıl olanak sağlanmıştır ve sürüm 4 veya sonraki sürümlerinasıl hedeflenene ilgili bir örnek verilmektedir.

 Bir uygulamanın üzerinde çalıştığı .NET Framework sürümü aşağıdaki sırada belirlenir:

- Yapılandırma dosyası.

     Uygulama yapılandırma dosyası, bir veya daha fazla .NET Framework sürümünü belirten [ \<desteklenen Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) girişleri içeriyorsa ve bu sürümlerden biri kullanıcının bilgisayarında varsa, uygulama bu sürümde çalışır. Yapılandırma [ \<dosyası, desteklenen Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) girişleri listelenme sırasına göre okur ve kullanıcının bilgisayarında bulunan listelenen ilk .NET Framework sürümünü kullanır. (Sürüm 1.0 için [ \<gerekli Runtime> öğesini](../configure-apps/file-schema/startup/requiredruntime-element.md) kullanın.)

- Derlenmiş sürüm.

     Bir yapılandırma dosyası yoksa, ancak uygulamanın oluşturulduğu .NET Framework sürümü kullanıcının makinesinde mevcutsa, uygulama o sürümde çalışır.

- En son sürüm yüklendi.

     .NET Framework'ün üzerine inşa edildiği sürümü yoksa ve yapılandırma dosyası [ \<desteklenen Runtime> öğesinde](../configure-apps/file-schema/startup/supportedruntime-element.md)bir sürüm belirtmiyorsa, uygulama kullanıcının bilgisayarında bulunan .NET Framework'ün en son sürümünde çalıştırmaya çalışır.

     Ancak .NET Framework 1.0, 1.1, 2.0, 3.0 ve 3.5 uygulamaları, .NET Framework 4 ve sonraki sürümleri otomatik çalıştırmaz ve bazı durumlarda kullanıcı bir hata alabilir ve kullanıcının .NET Framework 3.5 yüklemesi istenebilir. Windows sisteminin farklı sürümleri .NET Framework'ün farklı sürümlerinin içerdiğinden etkinleştirme davranışı kullanıcının işletim sistemine de bağlı olabilir. Uygulamanız hem .NET Framework 3.5 hem de 4 ve üstünü destekliyorsa, .NET Framework başlatma hatalarını önlemek için bunu yapılandırma dosyasında birden çok giriş işe belirtmenizi öneririz. Daha fazla bilgi için Bkz. [Sürümler ve Bağımlılıklar.](versions-and-dependencies.md)

 .NET Framework 3.5 uygulamalarınızı,.NET Framework 4 veya sonraki sürümlerde, .NET Framework 3.5 yüklü bilgisayarlarda bile çalışacak şekilde yapılandırmak isteyebilirsiniz, sürüm 4 ve sonraki sürümlerde performans iyileştirmelerinden yararlanmak için.

> [!IMPORTANT]
> Uygulamanızı desteklediğiniz her .NET Framework sürümünde her zaman test etmenizi öneririz. Uygulamanızı daha sonra .NET Framework sürümlerini desteklemek üzere yükseltme hakkında bilgi için [Sürüm Uyumluluğu'na](version-compatibility.md) bakın.

 .NET Framework 1.0 ve 1.1 uygulamalarınızı Windows 7 ve Windows 8'i desteklemek için değiştirme hakkında bilgi için [bkz.](migrating-from-the-net-framework-1-1.md)

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Uygulamanızı .NET Framework 4 veya sonraki sürümlerinde çalışacak şekilde yapılandırmak için

1. .NET Framework projesinin yapılandırma dosyasını ekleyin ya da bulun. Bir uygulamanın yapılandırma dosyası aynı dizindedir ve uygulama ile aynı ada ancak .config uzantısına sahiptir. Örneğin, MyExecutable.exe adlı bir uygulama için uygulama yapılandırma dosyası MyExecutable.exe.config olarak adlandırılır.

     Visual Studio menü çubuğunda yapılandırma dosyası eklemek için **Project**, **Yeni Öğe Ekle'yi**seçin. Sol bölmeden **Genel'i** seçin ve ardından **Configuration File'yi**seçin. Yapılandırma dosyası *appName*.exe.config adını. Bu platformlardaki etkinleştirme ilkesini değiştiremeyeceğiniz için bu menü seçenekleri Windows Mağazası uygulaması veya Windows phone uygulaması projeleri için kullanılamaz.

2. Desteklenen [ \<Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesini uygulama yapılandırma dosyasına aşağıdaki gibi ekleyin:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="<version>"/>
      </startup>
    </configuration>
    ```

     sürüm>uygulamanızın desteklediği .NET Framework sürümüyle hizalayan CLR sürümünü belirtir. * \<* Aşağıdaki dizeleri kullanın:

    - .NET Framework 1.0: "v1.0.3705"

    - .NET Framework 1.1: "v1.1.4322"

    - .NET Framework 2.0, 3.0 ve 3.5: "v2.0.50727"

    - .NET Framework 4 ve sonraki sürümler: "v4.0"

     .NET Framework'ün birden çok sürümü için destek belirtmek için tercih sırasına göre listelenen birden çok [ \<desteklenen Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesi ekleyebilirsiniz.

 Aşağıdaki tablo, bir bilgisayara yüklenen uygulama yapılandırma dosyası ayarlarının ve .NET Framework sürümlerinin bir .NET Framework 3.5 uygulamasının üzerinde çalıştığı sürümü nasıl belirlediğini göstermektedir. Örnekler, .NET Framework 3.5 uygulamasına özgüdür, ancak daha eski .NET Framework sürümlerini kullanarak oluşturulan hedef uygulamalar için de aynı mantığı kullanabilirsiniz. NET Framework 2.0 sürüm numarasının (v2.0.50727), uygulama yapılandırma dosyasında .NET Framework 3.5'i belirtmek için kullanıldığını unutmayın.

|App.config dosyası ayarı|3.5 sürümü yüklü bilgisayarda|3.5 ve 4 veya daha sonraki sürümleri yüklü bilgisayarda|Sürüm 4 veya daha sonraki sürümleri yüklü bilgisayarda|
|-|-|-|-|
|None|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|
|`<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|4 veya daha sonraki sürümlerde çalışır|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|4 veya daha sonraki sürümlerde çalışır|4 veya daha sonraki sürümlerde çalışır|
|`<supportedRuntime version="v4.0"/>`|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|4 veya daha sonraki sürümlerde çalışır|4 veya daha sonraki sürümlerde çalışır|

 \*Bu hata iletisi ve bunu önleme yolları hakkında daha fazla bilgi için [.NET Framework Initialization Errors: Managing the User Experience](../deployment/initialization-errors-managing-the-user-experience.md)(Kullanıcı Deneyimini Yönetme)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 1.1'den Geçiş](migrating-from-the-net-framework-1-1.md)
- [Geçiş Kılavuzu](index.md)
