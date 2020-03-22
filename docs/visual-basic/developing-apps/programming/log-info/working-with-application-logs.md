---
title: Uygulama Günlükleriyle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345894"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Visual Basic'te Uygulama Günlükleriyle Çalışma

Ve `My.Application.Log` `My.Log` nesneler günlüklere günlük ve izleme bilgilerini yazmayı kolaylaştırır.

## <a name="how-messages-are-logged"></a>İletiler Nasıl Günlüğe Kaydedilir?

İlk olarak, iletinin önem derecesi günlüğün <xref:System.Diagnostics.TraceSource.Switch%2A> <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> özelliğiyle denetlenir. Varsayılan olarak, yalnızca önem "Bilgi" ve daha yüksek iletileri, log'un `TraceListener` koleksiyonunda belirtilen izleme dinleyicilerine aktarılır. Daha sonra, her dinleyici iletinin önem derecesini dinleyicinin <xref:System.Diagnostics.TraceSource.Switch%2A> özelliğiyle karşılaştırır. İletinin önem derecesi yeterince yüksekse, dinleyici iletiyi yazar.

Aşağıdaki diyagram, yönteme yazılan `WriteEntry` bir iletinin `WriteLine` log'un izleme dinleyicilerinin yöntemlerine nasıl iletildiğini gösterir:

![Günlük aramamı gösteren diyagram.](./media/working-with-application-logs/my-log-call-messages.png)

Uygulamanın yapılandırma dosyasını değiştirerek günlüğün ve izleme dinleyicilerinin davranışını değiştirebilirsiniz. Aşağıdaki diyagram, günlük parçaları ve yapılandırma dosyası arasındaki yazışmaları gösterir.

![Günlük yapılandırmamı gösteren diyagram.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>İletilerin Günlüğe Kaydedildiği Yerler

Derlemede yapılandırma dosyası yoksa, `My.Application.Log` `My.Log` ve nesneler uygulamanın hata ayıklama çıktısına <xref:System.Diagnostics.DefaultTraceListener> (sınıf aracılığıyla) yazar. Buna ek `My.Application.Log` olarak, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> `My.Log` nesne derlemenin günlük dosyasına (sınıf aracılığıyla) yazarken, nesne ASP.NET Web <xref:System.Web.WebPageTraceListener> sayfasının çıktısına (sınıf aracılığıyla) yazar.

Hata ayıklama çıkışı, uygulamanızı hata ayıklama modunda çalıştırırken Visual Studio **Çıktı** penceresinde görüntülenebilir. **Çıktı** penceresini açmak için **Hata Ayıklama** menü öğesini tıklatın, **Windows'u**işaret edin ve sonra **Çıktı'yı**tıklatın. **Çıktı** penceresinde, **kutudan çıktıyı göster'den** **Hata Ayıklama'yı** seçin.

Varsayılan olarak, `My.Application.Log` kullanıcının uygulama verileri için yola günlük dosyası yazar. Yolu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> nesnenin özelliğinden alabilirsiniz. Bu yolun biçimi aşağıdaki gibidir:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

Için tipik `BasePath` bir değer aşağıdaki gibidir.

C:\Belgeler ve\\`username`Ayarlar \Uygulama Verileri

`CompanyName`, ve `ProductName` `ProductVersion` uygulamanın derleme bilgi gelen değerleri. Günlük dosya adının biçimi *AssemblyName*.log'dur, *AssemblyName* uzantısı olmadan derlemenin dosya adıdır. Başvuru nun günlüğe yazmaya çalıştığı zaman orijinal günlük kullanılamadığı nda birden fazla günlük dosyası gerekiyorsa, günlük dosyası adı için form *AssemblyName*-*yineleme*.log, pozitif `iteration` `Integer`olduğu yerdir.

Bilgisayarın ve uygulamanın yapılandırma dosyalarını ekleyerek veya değiştirerek varsayılan davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için [Bkz. Walkthrough: My.Application.Log Yazma Bilgileri Nerede Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Günlük Ayarlarını Yapılandırma

Nesne, `Log` uygulama yapılandırma dosyası, app.config olmadan çalışan varsayılan bir uygulama vardır. Varsayılanları değiştirmek için, yeni ayarlarla birlikte bir yapılandırma dosyası eklemeniz gerekir. Daha fazla bilgi için [bkz: Walkthrough: Filtreleme My.Application.Log Çıktı](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

Günlük yapılandırma bölümleri app.config dosyasının `<system.diagnostics>` `<configuration>` ana düğümünde düğüm bulunur. Günlük bilgileri birkaç düğümde tanımlanır:

- Nesnenin `Log` dinleyicileri VarsayılanKaynak adlı `<sources>` düğümde tanımlanır.

- Nesnenin `Log` önem derecesi filtresi Varsayılan `<switches>` Anahtar adlı düğümde tanımlanır.

- Günlük dinleyiciler `<sharedListeners>` düğümde tanımlanır.

 `<sources>`, , `<switches>`ve `<sharedListeners>` düğümörnekleri aşağıdaki kodda gösterilir:

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a>Dağıtımdan Sonra Günlük Ayarlarını Değiştirme

Bir uygulama geliştirdiğinizde, yapılandırma ayarları yukarıdaki örneklerde gösterildiği gibi app.config dosyasında depolanır. Uygulamanızı dağıttıktan sonra, yapılandırma dosyasını düzenleyerek günlüğü yapılandırmaya devam edebilirsiniz. Windows tabanlı bir uygulamada, bu dosyanın adı *applicationName*.exe.config'dir ve yürütülebilir dosyayla aynı klasörde bulunmalıdır. Bir Web uygulaması için bu, projeyle ilişkili Web.config dosyasıdır.

Uygulamanız ilk kez bir sınıfın örneğini oluşturan kodu çalıştırdığında, nesne hakkında bilgi için yapılandırma dosyasını denetler. Nesne `Log` için bu, nesneye `Log` ilk kez erişici olduğunda gerçekleşir. Sistem yapılandırma dosyasını belirli bir nesne için yalnızca bir kez inceler ve uygulamanız nesneyi ilk kez oluşturduğunda. Bu nedenle, değişikliklerin etkili olması için uygulamayı yeniden başlatmanız gerekebilir.

Dağıtılan bir uygulamada, uygulamanız başlamadan önce anahtar nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirin. Genellikle, bu, anahtar nesnelerini açıp kapatmayı veya izleme düzeylerini değiştirerek ve ardından uygulamanızı yeniden başlatmayı içerir.

## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler

Günlüğe veri yazarken aşağıdakileri göz önünde bulundurun:

- **Kullanıcı bilgilerini sızdırmaktan kaçının.** Uygulamanızın yalnızca onaylanmış bilgileri günlüğüne yazdığından emin olun. Örneğin, uygulama günlüğünün kullanıcı adları içermesi kabul edilebilir, ancak kullanıcı parolaları içermeyebilir.

- **Günlük konumlarını güvenli hale getirin.** Hassas olabilecek bilgiler içeren tüm günlükler güvenli bir konumda depolanmalıdır.

- **Yanıltıcı bilgilerden kaçının.** Genel olarak, uygulamanız bu verileri kullanmadan önce bir kullanıcı tarafından girilen tüm verileri doğrulamalıdır. Bu, uygulama günlüğüne veri yazmayı içerir.

- **Hizmet reddi kaçının.** Uygulamanız günlüğe çok fazla bilgi yazıyorsa, günlüğü doldurabilir veya önemli bilgileri bulmayı zorlaştırabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/index.md)
