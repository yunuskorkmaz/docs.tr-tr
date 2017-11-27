---
title: "Filtreleme My.Application.Log çıktısını (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fd445227e0c8290ad63fccf807d6d7bdf43ccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>İzlenecek Yol: My.Application.Log Çıktısını Filtreleme (Visual Basic)
Bu anlatımda için filtreleme varsayılan günlük değiştirmek nasıl gösterilir `My.Application.Log` hangi bilgilerin gelen geçirilen denetlemek için nesne `Log` nesne dinleyicileri ve hangi bilgilerin dinleyicileri tarafından yazılır. Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığı için bile uygulama oluşturduktan sonra günlüğe kaydetme davranışını değiştirebilirsiniz.  
  
## <a name="getting-started"></a>Başlarken  
 Her ileti `My.Application.Log` yazma hangi filtreleme mekanizması kullanıyor günlük çıktısı denetlemek için bir ilişkili önem düzeyi vardır. Bu örnek uygulama kullanır `My.Application.Log` birkaç yazma yöntemleri farklı önem düzeyleri ile iletileri günlüğe.  
  
#### <a name="to-build-the-sample-application"></a>Örnek uygulama oluşturmak için  
  
1.  Yeni bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows uygulama projesi.  
  
2.  Form1 button1 adlı bir düğme ekleyin.  
  
3.  İçinde <xref:System.Windows.Forms.Control.Click> Button1, olay işleyicisi aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  Hata ayıklayıcıda uygulamayı çalıştırın.  
  
5.  Tuşuna **Button1**.  
  
     Uygulama, aşağıdaki bilgileri uygulamanın hata ayıklama çıktı ve günlük dosyasına yazar.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  Uygulamayı kapatın.  
  
     Uygulamanın hata ayıklama çıktı penceresini görüntüleme hakkında daha fazla bilgi için bkz: [çıktı penceresi](/visualstudio/ide/reference/output-window). Uygulamanın günlük dosyasının konumunu hakkında daha fazla bilgi için bkz: [izlenecek yol: belirleme nerede My.Application.Log Yazar bilgisini](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
    > [!NOTE]
    >  Uygulama kapandığında varsayılan olarak, günlük dosyası çıkış uygulama aktarır.  
  
     İkinci çağrısı yukarıdaki örnekte <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> yöntemi ve çağrısı <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> yöntem ilk ve son çağrı sırasında günlük çıkışı üretir `WriteEntry` yöntemi yoktur. Bunun nedeni, önem derecesi düzeyleri `WriteEntry` ve `WriteException` "Bilgi" ve "Error" her ikisi de izin `My.Application.Log` nesnenin günlük filtreleme varsayılan. Ancak, "Başlat" ve "Durdur" önem düzeyleri ile olayları günlük çıkış üretmeyi engellenir.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Tüm My.Application.Log dinleyicileri için filtreleme  
 `My.Application.Log` Nesne kullanan bir <xref:System.Diagnostics.SourceSwitch> adlı `DefaultSwitch` hangi geçişleri gelen iletileri denetlemek `WriteEntry` ve `WriteException` günlük dinleyicileri yöntemleri. Yapılandırabileceğiniz `DefaultSwitch` değerini biri olarak ayarlayarak uygulamanın yapılandırma dosyasında <xref:System.Diagnostics.SourceLevels> numaralandırma değerleri. Varsayılan olarak, "Bilgi" değeri olduğu.  
  
 Bu tablo için belirli bir verilen dinleyicileri için bir ileti yazmak günlüğü gerekli önem derecesini gösterir `DefaultSwitch` ayarı.  
  
|DefaultSwitch değeri|Çıktı için gereken ileti önem derecesi|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical`veya`Error`|  
|`Warning`|`Critical`, `Error`, veya`Warning`|  
|`Information`|`Critical`, `Error`, `Warning`, veya`Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`, veya`Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`, veya`Transfer`|  
|`All`|Tüm iletileri izin verilir.|  
|`Off`|Tüm iletileri engellenir.|  
  
> [!NOTE]
>  `WriteEntry` Ve `WriteException` yöntemlerinin her bir önem düzeyi belirtmeyen bir aşırı yüklü. Örtük önem derecesini `WriteEntry` aşırı yüklemesi, "Bilgi" ve örtük önem derecesini `WriteException` aşırı yüklemesi, "Error".  
  
 Bu tabloda, önceki örnekte gösterilen günlük çıktısı açıklanmaktadır: varsayılan `DefaultSwitch` "Bilgi" ayarı, yalnızca ikinci çağrısı `WriteEntry` yöntemi ve çağrısı `WriteException` yöntemi ürettiği günlük çıktısı.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olayları günlüğe kaydetmek için  
  
1.  App.config dosyasında sağ **Çözüm Gezgini** seçip **açık**.  
  
     veya  
  
     Herhangi bir app.config dosyası ise:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2.  Bulun `<switches>` bulunduğu bölüm `<system.diagnostics>` üst düzey olan bölüm `<configuration>` bölümü.  
  
3.  Ekler öğesi bulunamıyor `DefaultSwitch` anahtarları koleksiyonuna. Bu öğeye benzer görünmelidir:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  Değerini değiştirme `value` özniteliği "ActivityTracing".  
  
5.  App.config dosyasının içeriğini aşağıdaki XML'e benzer olmalıdır:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  Hata ayıklayıcıda uygulamayı çalıştırın.  
  
7.  Tuşuna **Button1**.  
  
     Uygulama, aşağıdaki bilgileri uygulamanın hata ayıklama çıktı ve günlük dosyasına yazar:  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  Uygulamayı kapatın.  
  
9. Değerini değiştirme `value` özniteliğini geri "bilgileri için".  
  
    > [!NOTE]
    >  `DefaultSwitch` Anahtar yalnızca ayarı denetimlerini `My.Application.Log`. Değiştirme nasıl [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıfları davranır.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Tek tek My.Application.Log dinleyicileri için filtreleme  
 Önceki örnekte tüm filtreleme değiştirileceği gösterilmektedir `My.Application.Log` çıktı. Bu örnek, bir tek tek günlük dinleyicisi filtre gösterilmiştir. Varsayılan olarak, bir uygulama, yazma uygulamanın hata ayıklama çıktısı ve günlük dosyası için iki dinleyicileri sahiptir.  
  
 Yapılandırma dosyası her biri bir anahtar için benzer bir filtre olmasını sağlayarak günlük dinleyicileri davranışını denetleyen `My.Application.Log`. Yalnızca ileti önem derecesi hem günlüğün tarafından izin verilip verilmediğini günlük dinleyici bir çıktı mesajı göndereceğiz `DefaultSwitch` ve günlük dinleyicisi'nın Filtresi.  
  
 Bu örnek için yeni bir hata ayıklama dinleyici filtreleme yapılandırmak ve eklemek gösterilmiştir `Log` nesnesi. Varsayılan hata ayıklama dinleyicisi kaldırılmalı `Log` hata ayıklama iletileri yeni hata ayıklama dinleyicisi geldiğini açık olacak şekilde, nesne.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydedecek şekilde  
  
1.  App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     veya  
  
     Herhangi bir app.config dosyası ise:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2.  App.config dosyasında sağ **Çözüm Gezgini**. Seçin **açık**.  
  
3.  Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` altındaki "DefaultSource" özniteliği `<sources>` bölümü. `<sources>` Bölümdür altında `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
4.  Bu öğeye ekleyin `<listeners>` bölümü:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
6.  Bu öğe için eklemek `<sharedListeners>` bölümü:  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     <xref:System.Diagnostics.EventTypeFilter> Filtresi birini gerçekleştirir <xref:System.Diagnostics.SourceLevels> numaralandırma değerleri olarak kendi `initializeData` özniteliği.  
  
7.  App.config dosyasının içeriğini aşağıdaki XML'e benzer olmalıdır:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  Hata ayıklayıcıda uygulamayı çalıştırın.  
  
9. Tuşuna **Button1**.  
  
     Uygulama, aşağıdaki bilgileri uygulamanın günlük dosyasına yazar:  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     Uygulama daha kısıtlayıcı filtreleme nedeniyle daha az bilgi için uygulamanın hata ayıklama çıktısı yazar.  
  
     `Default Error   2   Error`  
  
10. Uygulamayı kapatın.  
  
 Dağıtımdan sonra günlük ayarları değiştirme hakkında daha fazla bilgi için bkz: [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [İzlenecek yol: Özel günlük dinleyicileri oluşturma](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 [Nasıl yapılır: günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [İzleme anahtarları](../../../../framework/debug-trace-profile/trace-switches.md)  
 [Uygulama içinden bilgileri günlüğe kaydetme](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
