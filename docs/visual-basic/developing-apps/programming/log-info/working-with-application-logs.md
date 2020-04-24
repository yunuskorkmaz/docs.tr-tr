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

`My.Application.Log` Ve `My.Log` nesneleri günlüğe kaydetme ve izleme bilgilerini günlüklere yazmayı kolaylaştırır.

## <a name="how-messages-are-logged"></a>Iletiler günlüğe nasıl kaydedilir?

İlk olarak, iletinin önem derecesi günlüğün <xref:System.Diagnostics.TraceSource.Switch%2A> <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> özelliğinin özelliği ile denetlenir. Varsayılan olarak, günlük `TraceListener` koleksiyonunda belirtilen izleme dinleyicilerine yalnızca önem derecesi "bilgi" ve üzeri iletiler geçirilir. Ardından, her dinleyici iletinin önem derecesini dinleyicinin <xref:System.Diagnostics.TraceSource.Switch%2A> özelliği ile karşılaştırır. İletinin önem derecesi yeterince yüksekse, dinleyici iletiyi yazar.

Aşağıdaki diyagramda, `WriteEntry` yönteme yazılan bir iletinin günlüğün izleme dinleyicilerinin `WriteLine` yöntemlerine nasıl geçirildiği gösterilmektedir:

![Günlük çağrımı gösteren diyagram.](./media/working-with-application-logs/my-log-call-messages.png)

Uygulamanın yapılandırma dosyasını değiştirerek günlük ve izleme dinleyicilerinin davranışını değiştirebilirsiniz. Aşağıdaki diyagramda, günlüğün bölümleri ile yapılandırma dosyası arasındaki yazışma gösterilmektedir.

![Günlük yapılandırmanızın gösterildiği diyagram.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>Iletiler günlüğe kaydedilir

Derlemenin yapılandırma dosyası yoksa, `My.Application.Log` ve `My.Log` nesneleri uygulamanın hata ayıklama çıktısına ( <xref:System.Diagnostics.DefaultTraceListener> sınıfı aracılığıyla) yazar. Ayrıca, `My.Application.Log` nesnesi derlemenin günlük dosyasına ( <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> sınıfı aracılığıyla) yazar, `My.Log` nesne ASP.NET Web sayfasının çıktısına ( <xref:System.Web.WebPageTraceListener> sınıfı aracılığıyla) yazar.

Hata ayıklama çıktısı, uygulamanızı hata ayıklama modunda çalıştırırken Visual Studio **çıktı** penceresinde görüntülenebilir. **Çıkış** penceresini açmak Için, **Hata Ayıkla** menü öğesine tıklayın, **Windows**' ın üzerine gelin ve ardından **Çıkış**' a tıklayın. **Çıkış** penceresinde, **çıktıyı göster** kutusundan **Hata Ayıkla** ' yı seçin.

Varsayılan olarak, `My.Application.Log` günlük dosyasını kullanıcının uygulama verileri yoluna yazar. <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> Nesnenin <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> özelliğinden yolunu alabilirsiniz. Yolun biçimi aşağıdaki gibidir:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

İçin `BasePath` tipik bir değer aşağıdaki gibidir.

C:\Documents and Settings\\`username`\Application Data

`CompanyName`, `ProductName`Ve `ProductVersion` değerleri uygulamanın derleme bilgileriyle gelir. Günlük dosyası adının biçimi *AssemblyName*. log biçimindedir, burada *AssemblyName* uzantısı olmayan derlemenin dosya adıdır. Birden çok günlük dosyası gerekiyorsa (örneğin, uygulama günlüğe yazmaya çalıştığında özgün günlüğün kullanılamadığı durumlar gibi), günlük dosyası adı için form *AssemblyName*-*yineleme*. log ' dur ve burada `iteration` pozitif `Integer`olur.

Bilgisayar ve uygulamanın yapılandırma dosyalarını ekleyerek veya değiştirerek varsayılan davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için bkz [. Izlenecek yol: My. Application. log bilgisinin nereden yazabileceğini değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Günlük ayarlarını yapılandırma

`Log` Nesnesi, uygulama yapılandırma dosyası, App. config olmadan çalışacak varsayılan bir uygulamaya sahiptir. Varsayılanları değiştirmek için yeni ayarlara sahip bir yapılandırma dosyası eklemeniz gerekir. Daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

Günlük yapılandırma bölümleri, App. config dosyasının `<system.diagnostics>` ana `<configuration>` düğümündeki düğümünde bulunur. Günlük bilgileri çeşitli düğümlerde tanımlanmıştır:

- `Log` Nesnenin dinleyicileri DefaultSource adlı `<sources>` düğümde tanımlanmıştır.

- `Log` Nesnesi için önem derecesi, DefaultSwitch adlı `<switches>` düğümde tanımlanmıştır.

- Günlük dinleyicileri, `<sharedListeners>` düğümde tanımlanmıştır.

 Aşağıdaki kodda `<sources>`, `<switches>`, ve `<sharedListeners>` düğümleri örnekleri gösterilmiştir:

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

## <a name="changing-log-settings-after-deployment"></a>Dağıtımdan sonra günlük ayarlarını değiştirme

Bir uygulama geliştirirken, yapılandırma ayarları Yukarıdaki örneklerde gösterildiği gibi App. config dosyasında depolanır. Uygulamanızı dağıttıktan sonra yapılandırma dosyasını düzenleyerek günlüğü yapılandırmaya devam edebilirsiniz. Windows tabanlı bir uygulamada, bu dosyanın adı *ApplicationName*. exe. config olur ve yürütülebilir dosyayla aynı klasörde bulunmalıdır. Bir Web uygulaması için, bu, projeyle ilişkili Web. config dosyasıdır.

Uygulamanız bir sınıfın bir örneğini ilk kez oluşturan kodu yürüttüğünde, nesne hakkında bilgi için yapılandırma dosyasını kontrol eder. `Log` Nesnesi için, bu `Log` nesne ilk kez erişildiğinde gerçekleşir. Sistem, yapılandırma dosyasını belirli bir nesne için yalnızca bir kez inceler — uygulamanız nesneyi ilk kez oluşturduğunda. Bu nedenle, değişikliklerin etkili olması için uygulamayı yeniden başlatmanız gerekebilir.

Dağıtılan bir uygulamada, uygulama başlamadan önce geçiş nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirin. Genellikle bu, anahtar nesnelerinin açık ve kapalı olduğunu ya da izleme düzeylerini değiştirerek ve sonra uygulamanızı yeniden başlatarak içerir.

## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler

Günlüğe veri yazarken aşağıdakileri göz önünde bulundurun:

- **Kullanıcı bilgilerinin sızmasını önleyin.** Uygulamanızın günlüğe yalnızca onaylanan bilgileri yazdığından emin olun. Örneğin, uygulama günlüğü Kullanıcı adlarını içermesi, ancak kullanıcı parolalarını içermemesi için kabul edilebilir olabilir.

- **Günlük konumlarını güvenli hale getirin.** Potansiyel olarak hassas bilgiler içeren herhangi bir günlüğün güvenli bir konumda depolanması gerekir.

- **Yanıltıcı bilgilerden kaçının.** Genel olarak, uygulamanız bu verileri kullanmadan önce bir kullanıcı tarafından girilen tüm verileri doğrulamalıdır. Bu, uygulama günlüğüne veri yazılmasını içerir.

- **Hizmet reddine engel olmaz.** Uygulamanız günlüğe çok fazla bilgi yazdığında, günlüğü doldurabilir veya önemli bilgileri bulmayı zorlaştırır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/index.md)
