---
title: Visual Basic'te Uygulama Günlükleriyle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: c11e1f0c99b3189c7a353e6778c701667b0a1d12
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037473"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Visual Basic'te Uygulama Günlükleriyle Çalışma
`My.Applicaton.Log` Ve `My.Log` nesnelerini günlüğe kaydetme ve izleme bilgileri günlüklere yazılır kolaylaştırır.  
  
## <a name="how-messages-are-logged"></a>İletileri nasıl kaydedilir  
 İlk olarak, ileti önem derecesi ile denetlenir <xref:System.Diagnostics.TraceSource.Switch%2A> günlüğün özelliği <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> özelliği. Tarafından varsayılan, yalnızca önem derecesi "Bilgi" iletileri ve daha yüksek günlüğün içinde belirtilen izleme dinleyicilerine geçirilir `TraceListener` koleksiyonu. Ardından, her dinleyici şekilde dinleyicinin iletinin önem karşılaştırır <xref:System.Diagnostics.TraceSource.Switch%2A> özelliği. İleti önem derecesi yeterince yüksek ise dinleyici iletisi yazar.  
  
 Yazılan bir ileti nasıl gösterir Aşağıdaki diyagramda `WriteEntry` yöntemi geçirilen `WriteLine` günlüğün yöntemlerinin izleme dinleyicileri:  
  
 ![My günlük araması](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")  
  
 Günlük ve iz dinleyicileri davranışını, uygulamanın yapılandırma dosyasını değiştirerek değiştirebilirsiniz. Aşağıdaki diyagramda, günlük bölümlerini ve yapılandırma dosyası arasındaki ilişkiyi gösterir.  
  
 ![Günlük yapılandırma](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")  
  
## <a name="where-messages-are-logged"></a>Burada iletileri günlüğe kaydedilir  
 Derleme herhangi bir yapılandırma dosyası varsa `My.Application.Log` ve `My.Log` nesneleri yazmak için uygulamanın hata ayıklama çıkışını (aracılığıyla <xref:System.Diagnostics.DefaultTraceListener> sınıfı). Ayrıca, `My.Application.Log` nesneyi derlemenin günlük dosyasına yazar (aracılığıyla <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> sınıfı), ancak `My.Log` nesneyi ASP.NET Web sayfasına ilişkin çıktısına yazar (aracılığıyla <xref:System.Web.WebPageTraceListener> sınıfı).  
  
 Visual Studio'da hata ayıklama çıkışı görüntülenebilir **çıkış** uygulamanızı hata ayıklama modunda çalışırken penceresi. Açmak için **çıkış** penceresinde tıklayın **hata ayıklama** menü öğesi, noktasına **Windows**ve ardından **çıkış**. İçinde **çıkış** penceresinde **hata ayıklama** gelen **çıktıyı Göster** kutusu.  
  
 Varsayılan olarak, `My.Application.Log` yolunda kullanıcının uygulama verileri için günlük dosyasına yazar. Yolundan alabilirsiniz <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> özelliği <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> nesne. Yol biçimi aşağıdaki gibidir:  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 İçin tipik bir değer `BasePath` gibidir.  
  
 C:\Documents ve ayarları\\`username`\Application veri  
  
 Değerlerini `CompanyName`, `ProductName`, ve `ProductVersion` uygulamanın derleme bilgilerden gelir. Günlük dosyası adı biçimindedir *AssemblyName*.log, burada *AssemblyName* uzantısı olmadan bir derlemenin dosya adı. Orijinal günlüğü kullanılamadığında uygulama günlüğüne yazmak çalıştığında gibi birden fazla günlük dosyası gerekli olursa, günlük dosyası adı için formdur *AssemblyName*-*yineleme* .log, burada `iteration` bir pozitif `Integer`.  
  
 Ekleyerek veya değiştirerek bilgisayarın ve uygulama yapılandırma dosyaları varsayılan davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için [izlenecek yol: değiştirme burada My.Application.Log Yazar bilgileri](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).  
  
## <a name="configuring-log-settings"></a>Günlük ayarlarını yapılandırma  
 `Log` Nenesindeki çalışır ve varsayılan bir uygulama bir uygulama yapılandırma dosyası app.config. Varsayılan değerleri değiştirmek için yeni ayarlar ile bir yapılandırma dosyası eklemeniz gerekir. Daha fazla bilgi için [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Günlük yapılandırma bölümlerini bulunan `<system.diagnostics>` ana düğüm `<configuration>` app.config dosyasının düğümü. Günlük bilgilerini, çeşitli düğümler tanımlanır:  
  
-   Dinleyiciler için `Log` nesne tanımlanmış `<sources>` DefaultSource adlı düğüm.  
  
-   Önem derecesi filtresi `Log` nesne tanımlanmış `<switches>` DefaultSwitch adlı düğüm.  
  
-   Günlük dinleyicileri tanımlanan `<sharedListeners>` düğümü.  
  
 Örnekleri `<sources>`, `<switches>`, ve `<sharedListeners>` düğümleri, aşağıdaki kodda gösterilmiştir:  
  
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
 Bir uygulama geliştirdiğinizde, Yukarıdaki örneklerde gösterildiği gibi yapılandırma ayarlarını app.config dosyasında depolanır. Uygulamanızı dağıttıktan sonra yapılandırma dosyasını düzenleyerek günlük yapılandırabilirsiniz. Windows tabanlı bir uygulama, bu dosyanın adıdır *applicationName*. exe.config ve yürütülebilir dosyasıyla aynı klasörde bulunmalıdır. Bir Web uygulaması için bu yöntem, projeyle ilişkili Web.config dosyasıdır.  
  
 Uygulamanızı ilk kez bir sınıf örneği oluşturan kodu yürütüldüğünde, nesne hakkında bilgi için yapılandırma dosyasını denetler. İçin `Log` nesne, ilk kez böyle `Log` erişilen nesne. Sistem yapılandırma dosyası herhangi bir nesne için yalnızca bir kez inceler; ilk kez uygulama nesnesi oluşturur. Bu nedenle, değişikliklerin etkili olması uygulamayı yeniden başlatmanız gerekebilir.  
  
 Dağıtılan bir uygulamada izleme kodu, uygulama başlatılmadan önce anahtar nesneleri yeniden etkinleştirin. Genellikle, bu anahtar nesneler üzerinde ve devre dışı veya izleme düzeylerini değiştirip ardından uygulamanız yeniden kapatma içerir.  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Veri günlüğü için yazarken aşağıdakileri değerlendirin:  
  
-   **Kullanıcı bilgilerini sızmasını önleyin.** Uygulama yazma işlemlerini günlüğe yazılacak bilgi yalnızca onaylanan emin olun. Örneğin, kullanıcı adları, ancak kullanıcı parolalarının içermesi için Uygulama günlüğünü kabul edilebilir olabilir.  
  
-   **Günlük konumları güvenli hale.** Olası hassas bilgiler içeren herhangi bir günlüğü güvenli bir konumda depolanması gerekir.  
  
-   **Yanıltıcı bilgi kaçının.** Genel olarak, uygulamanızın verileri kullanmadan önce bir kullanıcı tarafından girilen tüm veriler doğrulamalıdır. Bu, verileri uygulama günlüğüne yazma içerir.  
  
-   **Hizmet reddi kaçının.** Uygulamanızı günlüğe çok bilgi yazar, bunu günlük dolgu yüklenemedi veya zor önemli bilgileri bulmanızı kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/index.md)
