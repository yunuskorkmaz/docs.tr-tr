---
title: Visual Basic'te Uygulama Günlükleriyle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 9e62224ba4d53e09416819ca68004063dd189551
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592047"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Visual Basic'te Uygulama Günlükleriyle Çalışma
`My.Applicaton.Log` Ve `My.Log` nesneleri kolaylaştırır günlüğe kaydetme ve izleme bilgilerini günlüklere yazılır.  
  
## <a name="how-messages-are-logged"></a>İletileri nasıl kaydedilir  
 İlk olarak, ileti önem ile işaretli <xref:System.Diagnostics.TraceSource.Switch%2A> günlüğün özelliğinin <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> özelliği. Tarafından varsayılan, önem derecesi "Bilgi", yalnızca iletiler ve daha yüksek günlüğün içinde belirtilen izleme dinleyicileri için geçirilir `TraceListener` koleksiyonu. Ardından, iletinin önem derecesini dinleyiciye'nın her dinleyicisi karşılaştırır <xref:System.Diagnostics.TraceSource.Switch%2A> özelliği. İleti önem derecesi yeterince yüksekse, dinleyiciyi iletisi yazar.  
  
 Yazılan bir ileti nasıl gösterir Aşağıdaki diyagramda `WriteEntry` yöntemi geçirilen `WriteLine` günlüğün yöntemlerinin izleme dinleyicilerini:  
  
 ![My günlük çağrısı](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")  
  
 Günlük ve izleme dinleyicilerini davranışını uygulamanın yapılandırma dosyasını değiştirerek değiştirebilirsiniz. Aşağıdaki diyagramda günlük bölümlerini ve yapılandırma dosyası arasındaki ilişkiyi gösterir.  
  
 ![Günlük yapılandırma](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")  
  
## <a name="where-messages-are-logged"></a>İleti günlüğe nerede kaydedildiğini  
 Derleme herhangi bir yapılandırma dosyası varsa `My.Application.Log` ve `My.Log` nesneleri yazmak için uygulamanın hata ayıklama çıktısı (aracılığıyla <xref:System.Diagnostics.DefaultTraceListener> sınıfı). Ayrıca, `My.Application.Log` nesneyi derlemenin günlük dosyasına yazar (aracılığıyla <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> sınıfı), sırada `My.Log` nesnesi Yazar ASP.NET Web sayfasının çıkış (aracılığıyla <xref:System.Web.WebPageTraceListener> sınıfı).  
  
 Visual Studio'da hata ayıklama çıktısı görüntülenebilir **çıkış** uygulamanızı hata ayıklama modunda çalışırken penceresi. Açmak için **çıkış** penceresinde tıklatın **hata ayıklama** menü öğesi, noktasına **Windows**ve ardından **çıkış**. İçinde **çıkış** penceresinde, seçin **hata ayıklama** gelen **Göster çıktı** kutusu.  
  
 Varsayılan olarak, `My.Application.Log` yolunda kullanıcının uygulama verileri için günlük dosyasına yazar. Yolundan alabilirsiniz <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> özelliği <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> nesnesi. Bu yol biçimi aşağıdaki gibidir:  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 İçin tipik bir değer `BasePath` aşağıdaki gibidir.  
  
 C:\Documents and Settings\\`username`\Application veri  
  
 Değerlerini `CompanyName`, `ProductName`, ve `ProductVersion` uygulamanın derleme bilgilerinden gelir. Günlük dosyası adı biçimidir *AssemblyName*.log, burada *AssemblyName* dosya adı uzantısı olmadan derlemenin. Özgün günlüğü kullanılamadığında uygulama günlüğüne yazılması çalıştığında gibi birden fazla günlük dosyası gerekli olursa, günlük dosyası adı için formdur *AssemblyName*-*yineleme* .log, burada `iteration` bir pozitif olan `Integer`.  
  
 Ekleyerek veya bilgisayarın ve uygulamanın yapılandırma dosyalarını değiştirerek varsayılan davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için bkz: [izlenecek yol: değiştirmeyi burada My.Application.Log Yazar bilgi](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).  
  
## <a name="configuring-log-settings"></a>Günlük ayarlarını yapılandırma  
 `Log` Nesnesi, bir uygulama yapılandırma dosyası çalışır bir varsayılan uygulama sahip app.config. Varsayılanları değiştirmek için yeni ayarlar ile bir yapılandırma dosyası eklemeniz gerekir. Daha fazla bilgi için bkz: [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Günlük yapılandırma bölümlerinin bulunan `<system.diagnostics>` ana düğümünde `<configuration>` app.config dosyasının düğümü. Günlük bilgilerini birkaç düğümü tanımlanır:  
  
-   Dinleyicileri için `Log` nesne tanımlanmış `<sources>` DefaultSource adlı düğüm.  
  
-   Önem derecesi filtresi `Log` nesne tanımlanmış `<switches>` DefaultSwitch adlı düğüm.  
  
-   Günlük dinleyicileri tanımlanan `<sharedListeners>` düğümü.  
  
 Örnekleri `<sources>`, `<switches>`, ve `<sharedListeners>` düğümleri aşağıdaki kodda gösterildiği:  
  
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
 Bir uygulama geliştirirken, yapılandırma ayarlarını Yukarıdaki örneklerde gösterildiği gibi app.config dosyasında depolanır. Uygulamanızı dağıttıktan sonra yapılandırma dosyasını düzenleyerek günlük yapılandırabilirsiniz. Windows tabanlı bir uygulama, bu dosyanın adıdır *applicationName*. exe.config ve yürütülebilir dosya ile aynı klasörde bulunmalıdır. Bir Web uygulaması için bu yöntem, projeyle ilişkili Web.config dosyasıdır.  
  
 Uygulamanızı ilk kez bir sınıfının bir örneği oluşturan kodu yürütüldüğünde, nesne hakkında bilgi için yapılandırma dosyasını denetler. İçin `Log` nesnesi, ilk defa aşması `Log` nesne erişilir. Yapılandırma dosyası herhangi belirli bir nesnesi için yalnızca bir kez sistem inceler — ilk kez uygulamanızı nesnesi oluşturur. Bu nedenle, değişikliklerin etkili olması uygulamanın yeniden başlatmanız gerekebilir.  
  
 Dağıtılan bir uygulama, uygulama başlatılmadan önce anahtar nesneleri yapılandırarak izleme kodu etkinleştirin. Genellikle, bu anahtar nesneleri ve devre dışı veya üzerinde izleme düzeylerini değiştirme ve uygulamanızı yeniden başlatmayı içerir.  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Aşağıdaki veriler günlüğe yazılırken göz önünde bulundurun:  
  
-   **Kullanıcı bilgilerini sızmasını önleyin.** Uygulama yazma günlüğe yazılacak bilgi yalnızca onaylanan emin olun. Örneğin, kullanıcı adları, ancak kullanıcı parolalarını içerecek şekilde için Uygulama günlüğünü kabul edilebilir olabilir.  
  
-   **Günlük konumları güvenli olun.** Olası hassas bilgiler içeren günlük güvenli bir konumda depolanması gerekir.  
  
-   **Yanıltıcı bilgi kaçının.** Genel olarak, uygulamanız bu verileri kullanmadan önce bir kullanıcı tarafından girilen tüm veriler doğrulamalıdır. Bu veri uygulama günlüğüne yazma içerir.  
  
-   **Hizmet reddi kaçının.** Uygulamanız çok fazla bilgileri günlüğe yazar. varsa, bu günlük doldurun veya önemli bilgiler zor bulabilmek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
