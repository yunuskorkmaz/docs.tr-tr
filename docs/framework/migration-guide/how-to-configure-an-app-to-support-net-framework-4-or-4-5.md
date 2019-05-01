---
title: 'Nasıl yapılır: Uygulamayı .NET Framework 4 veya sonraki sürümleri destekleyecek şekilde yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40c19dc21bb2262ca1f23573cb89f764e4cd2627
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872696"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Nasıl yapılır: Destek .NET Framework 4 veya sonraki sürümler için uygulama yapılandırma

Başlamak için ortak dil çalışma zamanı (CLR) barındıran tüm uygulamaların gerekir veya *etkinleştirme*, yönetilen kodu çalıştırmak için CLR'yi. Genellikle bir .NET Framework uygulaması üzerinde derlendiği CLR sürümünde çalışır, ancak bir uygulama yapılandırma dosyası (bazen app.config dosyası olarak da anılır) kullanarak bu davranışı masaüstü uygulamalar için değiştirebilirsiniz. Ancak bir uygulama yapılandırma dosyası Windows Mağazası uygulamaları ya da Windows Phone uygulamaları için varsayılan etkinleştirme davranışını değiştiremezsiniz. Bu makale, Masaüstü uygulamanızın .NET Framework'ün başka bir sürümü üzerinde çalışmasını etkinleştirmek nasıl açıklamakta ve hedef sürüm 4 veya sonraki sürümler için ilişkin bir örnek sağlar.

 Bir uygulamanın üzerinde çalıştığı .NET Framework sürümü aşağıdaki sırada belirlenir:

- Yapılandırma dosyası.

     Uygulama yapılandırma dosyası içeriyorsa [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) kullanıcının bilgisayarında bulunan bir veya daha fazla .NET Framework sürümleri ve bu sürümlerinden birini belirtin. girişler varsa, uygulama o sürümde çalışır. . Yapılandırma dosyasını okur [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) girişlerini listelendikleri sırayla ve kullanıcının bilgisayarında bulunan listelenen ilk .NET Framework sürümünü kullanır. (Kullanım [ \<requiredRuntime > öğesini](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) sürüm 1.0 için.)

- Derlenmiş sürüm.

     Bir yapılandırma dosyası yoksa, ancak uygulamanın oluşturulduğu .NET Framework sürümü kullanıcının makinesinde mevcutsa, uygulama o sürümde çalışır.

- En son sürüm yüklendi.

     Uygulamanın üzerinde geliştirildiği .NET Framework sürümü mevcut değil ve bir yapılandırma dosyası bir sürümde belirtmiyor bir [ \<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), uygulama üzerinde .NET en son sürümünü çalıştırmayı dener Kullanıcının bilgisayarında bulunan çerçevesi.

     Ancak .NET Framework 1.0, 1.1, 2.0, 3.0 ve 3.5 uygulamaları, .NET Framework 4 ve sonraki sürümleri otomatik çalıştırmaz ve bazı durumlarda kullanıcı bir hata alabilir ve kullanıcının .NET Framework 3.5 yüklemesi istenebilir. Windows sisteminin farklı sürümleri .NET Framework'ün farklı sürümlerinin içerdiğinden etkinleştirme davranışı kullanıcının işletim sistemine de bağlı olabilir. Uygulamanız hem .NET Framework 3.5 hem de 4 ve üstünü destekliyorsa, .NET Framework başlatma hatalarını önlemek için bunu yapılandırma dosyasında birden çok giriş işe belirtmenizi öneririz. Daha fazla bilgi için [sürümler ve bağımlılıklar](versions-and-dependencies.md).

 .NET Framework 3.5 uygulamalarınızı .NET Framework 4 veya sonraki sürümlerinde, hatta .NET Framework 3.5, 4 sürümlerindeki performans iyileştirmelerinden ve sonraki sürümleri yüklü bilgisayarlarda çalışacak şekilde yapılandırmak isteyebilirsiniz.

> [!IMPORTANT]
> Uygulamanızı desteklediğiniz her .NET Framework sürümünde her zaman test etmenizi öneririz. Bkz: [sürüm uyumluluğu](version-compatibility.md) sonraki .NET Framework sürümlerini desteklemek üzere uygulamanızı yükseltme hakkında bilgi için.

 .NET Framework 1.0 ve 1.1 uygulamalarınızı Windows 7 ve Windows 8'i destekleyecek şekilde değiştirme hakkında daha fazla bilgi için bkz: [.NET Framework 1. 1 ' geçiş](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>.NET Framework 4 veya sonraki sürümler üzerinde çalıştırmak için uygulamanızı yapılandırma

1. .NET Framework projesinin yapılandırma dosyasını ekleyin ya da bulun. Bir uygulamanın yapılandırma dosyası aynı dizindedir ve uygulama ile aynı ada ancak .config uzantısına sahiptir. Örneğin, MyExecutable.exe adlı bir uygulama için uygulama yapılandırma dosyası MyExecutable.exe.config olarak adlandırılır.

     Visual Studio menü çubuğunda, bir yapılandırma dosyası eklemek için **proje**, **Yeni Öğe Ekle**. Seçin **genel** sol bölmeden seçip **yapılandırma dosyası**. Yapılandırma dosyası adı *appName*. exe.config olarak. Bu menü seçenekleri Windows Mağazası uygulaması veya Windows telefon uygulaması projelerinde kullanılamaz, çünkü bu platformlarda etkinleştirme ilkesini değiştiremezsiniz.

2. Ekleme [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) öğesi gibi uygulama yapılandırma dosyası:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="<version>"/>
      </startup>
    </configuration>
    ```

     Burada  *\<sürüm >* , uygulamanızın desteklediği .NET Framework sürümüyle eşleşen CLR sürümünü belirtir. Aşağıdaki dizeleri kullanın:

    - .NET Framework 1.0: "v1.0.3705"

    - .NET Framework 1.1: "v1.1.4322"

    - .NET Framework 2.0, 3.0 ve 3.5: "v2.0.50727"

    - .NET framework 4 ve üzeri sürümler: "v4.0"

     Birden çok ekleyebilirsiniz [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) öğeleri, birden çok .NET Framework sürümleri için destek belirtmek için tercih sırasına göre listelenir.

 Aşağıdaki tablo, bir bilgisayara yüklenen uygulama yapılandırma dosyası ayarlarının ve .NET Framework sürümlerinin bir .NET Framework 3.5 uygulamasının üzerinde çalıştığı sürümü nasıl belirlediğini göstermektedir. Örnekler, .NET Framework 3.5 uygulamasına özgüdür, ancak daha eski .NET Framework sürümlerini kullanarak oluşturulan hedef uygulamalar için de aynı mantığı kullanabilirsiniz. NET Framework 2.0 sürüm numarasının (v2.0.50727), uygulama yapılandırma dosyasında .NET Framework 3.5'i belirtmek için kullanıldığını unutmayın.

|App.config dosyası ayarı|3.5 sürümü yüklü bilgisayarda|Sürüm 3.5 ve 4 veya sonraki sürümler yüklü olan bilgisayarda|Sürüm 4 veya sonraki sürümleri yüklü bilgisayarda|
|-|-|-|-|
|Yok.|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|
|`<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|4 veya sonraki sürümleri çalıştıran|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|4 veya sonraki sürümleri çalıştıran|4 veya sonraki sürümleri çalıştıran|
|`<supportedRuntime version="v4.0"/>`|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|4 veya sonraki sürümleri çalıştıran|4 veya sonraki sürümleri çalıştıran|

 \* Bu hata iletisi ve onu önlemenin yolları hakkında daha fazla bilgi için bkz: [.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 1.1'den Geçiş](migrating-from-the-net-framework-1-1.md)
- [Geçiş Kılavuzu](index.md)