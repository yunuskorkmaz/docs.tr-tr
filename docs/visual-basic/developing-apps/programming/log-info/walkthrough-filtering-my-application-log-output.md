---
title: My.Application.Log Çıktısını Filtreleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353598"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>İzlenecek Yol: My.Application.Log Çıktısını Filtreleme (Visual Basic)

Bu izlenecek yol, `Log` nesnesinden dinleyicilerine hangi bilgilerin geçtiğini ve hangi bilgilerin dinleyiciler tarafından yazıldığını denetlemek için `My.Application.Log` nesnesi için varsayılan günlük filtrelemesinin nasıl değiştirileceğini gösterir. Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığından, uygulamayı oluşturduktan sonra bile günlüğe kaydetme davranışını değiştirebilirsiniz.

## <a name="getting-started"></a>Başlarken

`My.Application.Log` yazmaları olan her ileti, bir ilişkili önem düzeyine sahiptir ve bu da filtreleme mekanizmalarının günlük çıkışını denetlemek için kullandığı bir önem derecesi vardır Bu örnek uygulama, farklı önem düzeylerindeki çeşitli günlük iletilerini yazmak için `My.Application.Log` yöntemler kullanır.

#### <a name="to-build-the-sample-application"></a>Örnek uygulamayı derlemek için

1. Yeni bir Visual Basic Windows uygulaması projesi açın.

2. Form1 adına button1 adlı bir düğme ekleyin.

3. Button1 için <xref:System.Windows.Forms.Control.Click> olay işleyicisinde aşağıdaki kodu ekleyin:

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Uygulamayı hata ayıklayıcıda çalıştırın.

5. **Button1**'e basın.

     Uygulama, uygulamanın hata ayıklama çıktısına ve günlük dosyasına aşağıdaki bilgileri yazar.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Uygulamayı kapatın.

     Uygulamanın hata ayıklama çıkış penceresini görüntüleme hakkında daha fazla bilgi için bkz. [Çıkış penceresi](/visualstudio/ide/reference/output-window). Uygulamanın günlük dosyasının konumu hakkında daha fazla bilgi için bkz [. Walkthrough: My. Application. log bilgisinin nereden yazabileceğini belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

    > [!NOTE]
    > Varsayılan olarak uygulama kapandığında günlük dosyası çıkışını temizler.

     Yukarıdaki örnekte, <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> yöntemine yapılan ikinci çağrı ve <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> yöntemine yapılan çağrı günlük çıktısını üretir, ancak `WriteEntry` yöntemine yapılan ilk ve son çağrılar değildir. Bunun nedeni, `WriteEntry` ve `WriteException` önem seviyelerinin, her ikisi de `My.Application.Log` nesnenin varsayılan günlük filtrelemesine izin verilen "bilgi" ve "hata" olmasından kaynaklanır. Bununla birlikte, "Başlat" ve "Durdur" önem derecesindeki olaylar günlük çıktısı üretmesinin engellenmektedir.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Tüm My. Application. log dinleyicileri için filtreleme

`My.Application.Log` nesnesi, `WriteEntry` ve `WriteException` yöntemlerinden günlük dinleyicilerine hangi iletilerin geçireceğini denetlemek için `DefaultSwitch` adlı bir <xref:System.Diagnostics.SourceSwitch> kullanır. Uygulamanın yapılandırma dosyasında `DefaultSwitch`, değerini <xref:System.Diagnostics.SourceLevels> sabit listesi değerlerinden birine ayarlayarak yapılandırabilirsiniz. Varsayılan olarak, değeri "bilgi" ' dir.

Bu tablo, belirli bir `DefaultSwitch` ayarı için, günlüğe kaydedilecek bir ileti yazmak üzere gereken önem derecesini gösterir.

|DefaultSwitch değeri|Çıkış için gereken ileti önem derecesi|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` veya `Error`|
|`Warning`|`Critical`, `Error`veya `Warning`|
|`Information`|`Critical`, `Error`, `Warning`veya `Information`|
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`veya `Verbose`|
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`veya `Transfer`|
|`All`|Tüm iletilere izin verilir.|
|`Off`|Tüm iletiler engellenir.|

> [!NOTE]
> `WriteEntry` ve `WriteException` yöntemlerinin her biri önem düzeyi belirtmeyen bir aşırı yüklemeye sahiptir. `WriteEntry` aşırı yüklemesi için örtük önem düzeyi "bilgi" ve `WriteException` aşırı yüklemesi için örtülü önem düzeyi "hata" dır.

Bu tabloda, önceki örnekte gösterilen günlük çıktısı açıklanmaktadır: "Information" öğesinin varsayılan `DefaultSwitch` ayarı ile, yalnızca `WriteEntry` yöntemine yapılan ikinci çağrı ve `WriteException` yöntemine yapılan çağrı günlük çıktısını üretir.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için

1. **Çözüm Gezgini** App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     veya

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'yi tıklatın.

2. Üst düzey `<configuration>` bölümünde olan `<system.diagnostics>` bölümündeki `<switches>` bölümünü bulun.

3. Anahtarlar koleksiyonuna `DefaultSwitch` ekleyen öğeyi bulun. Bu öğe şuna benzer görünmelidir:

     `<add name="DefaultSwitch" value="Information" />`

4. `value` özniteliğinin değerini "ActivityTracing" olarak değiştirin.

5. App. config dosyasının içeriği aşağıdaki XML 'e benzer olmalıdır:

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

6. Uygulamayı hata ayıklayıcıda çalıştırın.

7. **Button1**'e basın.

     Uygulama aşağıdaki bilgileri uygulamanın hata ayıklama çıktısına ve günlük dosyasına yazar:

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. Uygulamayı kapatın.

9. `value` özniteliğinin değerini "Information" olarak değiştirin.

    > [!NOTE]
    > `DefaultSwitch` Switch ayarı yalnızca `My.Application.Log`denetler. .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıflarının nasıl davranacağını değiştirmez.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>My. Application. log dinleyicileri Için bireysel filtreleme

Önceki örnekte, tüm `My.Application.Log` çıktısının filtrelemesinin nasıl değiştirileceği gösterilmektedir. Bu örnek, tek bir günlük dinleyicisinin nasıl filtreleneceğini gösterir. Varsayılan olarak, uygulamanın, uygulamanın hata ayıklama çıktısına ve günlük dosyasına yazan iki dinleyicisi vardır.

Yapılandırma dosyası, her birinin bir filtreye sahip olmasını sağlayarak, `My.Application.Log`için bir anahtara benzer olan günlük dinleyicilerinin davranışını denetler. Günlük dinleyicisi yalnızca, iletinin önem derecesine yalnızca günlüğün `DefaultSwitch` ve günlük dinleyicinin filtresi tarafından izin veriliyorsa bir ileti çıktı.

Bu örnek, yeni bir hata ayıklama dinleyicisi için filtrelemenin nasıl yapılandırılacağını ve `Log` nesnesine nasıl ekleneceğini gösterir. Varsayılan hata ayıklama dinleyicisi `Log` nesnesinden kaldırılmalıdır, bu nedenle hata ayıklama iletilerinin yeni hata ayıklama dinleyicisinden geldiği temizlenmelidir.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için

1. **Çözüm Gezgini** App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     \-veya-

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'yi tıklatın.

2. **Çözüm Gezgini**' de App. config öğesine sağ tıklayın. **Aç**' ı seçin.

3. `<source>` bölümündeki `<listeners>` bölümünü, `<sources>` bölümünün altında bulunan "DefaultSource" `name` özniteliğiyle bulun. `<sources>` bölümü, üst düzey `<configuration>` bölümünde `<system.diagnostics>` bölümünün altındadır.

4. Bu öğeyi `<listeners>` bölümüne ekleyin:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Üst düzey `<configuration>` bölümündeki `<system.diagnostics>` bölümünde `<sharedListeners>` bölümünü bulun.

6. Bu öğeyi bu `<sharedListeners>` bölümüne ekleyin:

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

     <xref:System.Diagnostics.EventTypeFilter> filtresi <xref:System.Diagnostics.SourceLevels> sabit listesi değerlerinden birini `initializeData` özniteliği olarak alır.

7. App. config dosyasının içeriği aşağıdaki XML 'e benzer olmalıdır:

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

8. Uygulamayı hata ayıklayıcıda çalıştırın.

9. **Button1**'e basın.

     Uygulama, uygulamanın günlük dosyasına aşağıdaki bilgileri yazar:

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     Uygulama daha kısıtlayıcı filtreleme nedeniyle uygulamanın hata ayıklama çıktısına daha az bilgi yazar.

     `Default Error   2   Error`

10. Uygulamayı kapatın.

Dağıtımdan sonra günlük ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzleme Anahtarları](../../../../framework/debug-trace-profile/trace-switches.md)
- [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/index.md)
