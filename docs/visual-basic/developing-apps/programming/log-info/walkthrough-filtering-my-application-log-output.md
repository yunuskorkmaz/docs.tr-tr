---
title: (Visual Basic) My.Application.Log çıktısını filtreleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: 25d2177eed9ef83ba8f2575668e72dc21c2cd43f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298402"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>İzlenecek yol: (Visual Basic) My.Application.Log çıktısını filtreleme
Bu yönerge için filtreleme varsayılan günlük değiştirmek nasıl gösterir `My.Application.Log` hangi bilgilerin gelen geçirilen denetlemek için nesne `Log` nesnesine dinleyicileri ve hangi bilgilerin dinleyicileri tarafından yazılır. Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığından uygulama oluşturduktan sonra bile günlüğe kaydetme davranışını değiştirebilirsiniz.  
  
## <a name="getting-started"></a>Başlarken  
 Her ileti `My.Application.Log` yazma hangi filtreleme mekanizmaları kullanma günlük çıktısını denetlemek için bir ilişkili önem derecesine sahip. Bu örnek uygulamanın kullandığı `My.Application.Log` birkaç yazma yöntemleri farklı önem düzeyleri ile iletileri günlüğe.  
  
#### <a name="to-build-the-sample-application"></a>Örnek uygulamayı oluşturmak için  
  
1. Yeni bir Visual Basic Windows uygulaması projesi açın.  
  
2. Form1 button1 adlı bir düğme ekleyin.  
  
3. İçinde <xref:System.Windows.Forms.Control.Click> Button1 için olay işleyicisi aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4. Uygulamayı Hata Ayıklayıcısı'nda çalıştırın.  
  
5. Tuşuna **Button1**.  
  
     Uygulama, aşağıdaki bilgileri uygulamanın hata ayıklama çıkışı ve günlük dosyasına yazar.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6. Uygulamayı kapatın.  
  
     Uygulama hata ayıklama çıktı penceresine görüntüleme hakkında daha fazla bilgi için bkz: [çıkış penceresine](/visualstudio/ide/reference/output-window). Uygulamanın günlük dosyasının konumu hakkında daha fazla bilgi için bkz: [izlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
    > [!NOTE]
    >  Uygulama kapandığında varsayılan olarak, uygulamanın günlük dosyasına çıkışı aktarır.  
  
     İçin yapılan ikinci çağrı yukarıdaki örnekte <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> yöntemi ve çağrısı <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> yöntemi ilk ve son çağrıları sırasında günlük çıktısı üreten `WriteEntry` yöntemi değildir. Bunun nedeni, önem derecesi düzeyleri `WriteEntry` ve `WriteException` "Bilgi" ve "Error" ikisi için de izin `My.Application.Log` nesnenin varsayılan günlük filtreleme. Ancak, günlük çıktı oluşturmuyor gelen "Başlangıç" ve "Durdur" önem düzeyleri ile olayları engellenir.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Tüm My.Application.Log dinleyicileri için filtreleme  
 `My.Application.Log` Nesnesini kullanan bir <xref:System.Diagnostics.SourceSwitch> adlı `DefaultSwitch` hangi geçişlerinin iletileri denetlemek `WriteEntry` ve `WriteException` günlük dinleyicileri için yöntemleri. Yapılandırabileceğiniz `DefaultSwitch` değerini biri olarak ayarlayarak uygulamanın yapılandırma dosyasında <xref:System.Diagnostics.SourceLevels> sabit listesi değerleri. Varsayılan olarak, "Bilgi" değerdir.  
  
 Bu tablo, belirli bir verilen dinleyicileri için ileti yazmak günlük için gerekli önem derecesini gösterir `DefaultSwitch` ayarı.  
  
|DefaultSwitch değeri|Çıkış için gerekli iletisi önem derecesi|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical` veya `Error`|  
|`Warning`|`Critical`, `Error`, veya `Warning`|  
|`Information`|`Critical`, `Error`, `Warning`, veya `Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`, veya `Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`, veya `Transfer`|  
|`All`|Tüm iletileri izin verilir.|  
|`Off`|Tüm iletileri engellenir.|  
  
> [!NOTE]
>  `WriteEntry` Ve `WriteException` yöntem her bir önem düzeyi belirtmeyen aşırı sahiptir. Örtük önem derecesi düzeyi `WriteEntry` aşırı yüklemesi, "Bilgi" ve örtük önem derecesi düzeyi `WriteException` aşırı yüklemesi olan "Error".  
  
 Bu tablo, önceki örnekte gösterilen günlük çıktısını açıklar: varsayılan `DefaultSwitch` "Bilgi" ayarını, yalnızca ikinci çağrı `WriteEntry` yöntemi ve çağrısı `WriteException` yöntemi Üretim günlük çıktısı.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydedecek şekilde  
  
1. App.config dosyasında sağ **Çözüm Gezgini** seçip **açık**.  
  
     -veya-  
  
     App.config dosyası yoksa:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2. Bulun `<switches>` bulunduğu bölüme `<system.diagnostics>` üst düzey olan bölüm `<configuration>` bölümü.  
  
3. Ekler öğesi bulma `DefaultSwitch` anahtarların koleksiyonu. Bu öğeye benzer görünmelidir:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4. Değiştirin `value` "ActivityTracing için" özniteliği.  
  
5. App.config dosyasının içeriği aşağıdaki XML'e benzer olmalıdır:  
  
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
  
6. Uygulamayı Hata Ayıklayıcısı'nda çalıştırın.  
  
7. Tuşuna **Button1**.  
  
     Uygulama, aşağıdaki bilgileri uygulamanın hata ayıklama çıkışı ve günlük dosyasına yazar:  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8. Uygulamayı kapatın.  
  
9. Değiştirin `value` geri "bilgileri için" özniteliği.  
  
    > [!NOTE]
    >  `DefaultSwitch` Anahtarı ayarı yalnızca `My.Application.Log`. Değiştirme nasıl [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıfları davranır.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Tek tek My.Application.Log dinleyicileri için filtreleme  
 Önceki örnekte, tüm filtreleme değiştirmek gösterilmektedir `My.Application.Log` çıktı. Bu örnek, tek tek günlük bir dinleyici nasıl filtreleme yapılacağını gösterir. Varsayılan olarak, bir uygulama iki dinleyici, yazma uygulamanın hata ayıklama çıkışını ve günlük dosyasına sahiptir.  
  
 Yapılandırma dosyası, her biri için bir anahtar benzer bir filtreye sahip vererek günlük dinleyicileri davranışını denetler `My.Application.Log`. Yalnızca ileti önem derecesi hem günlüğün tarafından izin veriliyorsa günlük dinleyici bir çıktı mesajı göndereceğiz `DefaultSwitch` ve günlük dinleyicinin filtre.  
  
 Bu örnek için yeni bir hata ayıklama dinleyici filtrelemeyi yapılandırma ve eklemek nasıl gösterir `Log` nesne. Varsayılan hata ayıklama dinleyici kaldırılması gerektiğini `Log` nesne, hata ayıklama iletilerinin yeni hata ayıklama dinleyicisinden geldiğini belirgin olacak şekilde.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydedecek şekilde  
  
1. App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     -veya-  
  
     App.config dosyası yoksa:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2. App.config dosyasında sağ **Çözüm Gezgini**. Seçin **açık**.  
  
3. Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` altındaki "DefaultSource" özniteliği `<sources>` bölümü. `<sources>` Bölümdür altında `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
4. Bu öğeye eklemek `<listeners>` bölümü:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5. Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
6. Bu öğe ekleyen `<sharedListeners>` bölümü:  
  
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
  
     <xref:System.Diagnostics.EventTypeFilter> Filtresi aşağıdakilerden birini gerçekleştirir <xref:System.Diagnostics.SourceLevels> sabit listesi değerleri olarak kendi `initializeData` özniteliği.  
  
7. App.config dosyasının içeriği aşağıdaki XML'e benzer olmalıdır:  
  
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
  
8. Uygulamayı Hata Ayıklayıcısı'nda çalıştırın.  
  
9. Tuşuna **Button1**.  
  
     Uygulama, aşağıdaki bilgileri için uygulamanın günlük dosyasına yazar:  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     Uygulama, daha kısıtlayıcı filtreleme nedeniyle, uygulamanın hata ayıklama çıkışı daha az bilgi yazar.  
  
     `Default Error   2   Error`  
  
10. Uygulamayı kapatın.  
  
 Dağıtımdan sonra günlük ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Nasıl yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzleme Anahtarları](../../../../framework/debug-trace-profile/trace-switches.md)
- [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/index.md)
