---
title: My.Application.Log Çıktısını Filtreleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353598"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>İzlenecek Yol: My.Application.Log Çıktısını Filtreleme (Visual Basic)

Bu gözden geçirme, `My.Application.Log` nesne için varsayılan günlük filtrelemenin nasıl değiştirilebildiğini, `Log` nesneden dinleyicilere hangi bilgilerin aktarıldığını ve dinleyiciler tarafından hangi bilgilerin yazıldığını denetleyeceğini gösterir. Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığı için, uygulamayı yaptıktan sonra bile günlüğe kaydetme davranışını değiştirebilirsiniz.

## <a name="getting-started"></a>Başlarken

`My.Application.Log` Yazan her iletinin, filtreleme mekanizmalarının günlük çıktısını denetlemek için kullandığı ilişkili bir önem düzeyi vardır. Bu örnek `My.Application.Log` uygulama, farklı önem düzeyleri ile birkaç günlük iletileri yazmak için yöntemler kullanır.

#### <a name="to-build-the-sample-application"></a>Örnek uygulamayı oluşturmak için

1. Yeni bir Visual Basic Windows Application projesi açın.

2. Form1'e Button1 adlı bir düğme ekleyin.

3. Button1 <xref:System.Windows.Forms.Control.Click> için olay işleyicisi, aşağıdaki kodu ekleyin:

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Uygulamayı hata ayıklamada çalıştırın.

5. **Düğmeye Basın1**.

     Uygulama, uygulamanın hata ayıklama çıktısı ve günlük dosyasına aşağıdaki bilgileri yazar.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Uygulamayı kapatın.

     Uygulamanın hata ayıklama çıkış penceresinin nasıl görüntüleneğe ilişkin bilgi için [Çıktı Penceresi'ne](/visualstudio/ide/reference/output-window)bakın. Uygulamanın günlük dosyasının konumu hakkında bilgi için [bkz.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

    > [!NOTE]
    > Varsayılan olarak, uygulama kapandığında günlük dosyası çıktısını temize çıkar.

     Yukarıdaki örnekte, yönteme <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> ikinci çağrı ve <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> yönteme çağrı günlük çıkışı üretirken, `WriteEntry` yönteme yapılan ilk ve son çağrılar bunu yapmaz. Bunun nedeni, her ikisi `WriteEntry` `WriteException` de `My.Application.Log` nesnenin varsayılan günlük filtrelemesi tarafından izin verilen "Bilgi" ve "Hata" önem düzeyleridir. Ancak, "Başlat" ve "Durdur" önem düzeylerine sahip olayların günlük çıktısı üretmesini engeller.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Tüm My.Application.Log Dinleyiciler için Filtreleme

Nesne, `My.Application.Log` <xref:System.Diagnostics.SourceSwitch> `DefaultSwitch` hangi iletilerden geçtiğini `WriteEntry` ve `WriteException` günlük dinleyicilerine hangi yöntemleri denetlemeyi kullanır. Değerini numaralandırma `DefaultSwitch` değerlerinden birine ayarlayarak uygulamanın yapılandırma dosyasında <xref:System.Diagnostics.SourceLevels> yapılandırabilirsiniz. Varsayılan olarak, değeri "Bilgi"dir.

Bu tablo, Log'un belirli `DefaultSwitch` bir ayar göz önüne alındığında dinleyicilere ileti yazması için gereken önem düzeyini gösterir.

|Varsayılan Anahtar Değeri|Çıktı için gereken ileti önem derecesi|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` veya `Error`|
|`Warning`|`Critical`, `Error`veya`Warning`|
|`Information`|`Critical`, `Error` `Warning`, veya`Information`|
|`Verbose`|`Critical`, `Error` `Warning`, `Information`, veya`Verbose`|
|`ActivityTracing`|`Start`, `Stop` `Suspend`, `Resume`, veya`Transfer`|
|`All`|Tüm iletilere izin verilir.|
|`Off`|Tüm iletiler engellendi.|

> [!NOTE]
> Ve `WriteEntry` `WriteException` yöntemlerin her biri bir önem düzeyi belirtmeyen bir aşırı yük var. Aşırı yükleme için `WriteEntry` örtük önem düzeyi "Bilgi"dir ve `WriteException` aşırı yükleme için örtük önem düzeyi "Hata"dır.

Bu tablo, önceki örnekte gösterilen günlük çıktısını açıklar: varsayılan `DefaultSwitch` "Bilgi" ayarı ile, `WriteEntry` yönteme yalnızca ikinci çağrı ve `WriteException` yönteme yapılan çağrı günlük çıktısı üretir.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca olayları izleme etkinliğini günlüğe kaydetmek için

1. **Çözüm Gezgini'nde** app.config'e sağ tıklayın ve **Aç'ı**seçin.

     -veya-

     App.config dosyası yoksa:

    1. **Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.

    2. Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.

    3. **Ekle**’ye tıklayın.

2. Üst `<switches>` düzey `<configuration>` bölümde bulunan `<system.diagnostics>` bölümdeki bölümü bulun.

3. Anahtarların koleksiyonuna `DefaultSwitch` ekleyen öğeyi bulun. Bu öğeye benzer olmalıdır:

     `<add name="DefaultSwitch" value="Information" />`

4. Özniteliğin `value` değerini "ActivityTracing" olarak değiştirin.

5. app.config dosyasının içeriği aşağıdaki XML benzer olmalıdır:

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

6. Uygulamayı hata ayıklamada çalıştırın.

7. **Düğmeye Basın1**.

     Uygulama, uygulamanın hata ayıklama çıktısı ve günlük dosyasına aşağıdaki bilgileri yazar:

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. Uygulamayı kapatın.

9. Özniteliğin değerini `value` "Bilgi" olarak değiştirin.

    > [!NOTE]
    > Anahtar `DefaultSwitch` ayarı `My.Application.Log`yalnızca. .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıfların nasıl bir şekilde nasıl bir şekilde değiştiğini değiştirmez.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>My.Application.Log Dinleyiciler için Bireysel Filtreleme

Önceki örnek, tüm `My.Application.Log` çıktıiçin filtrelemenin nasıl değiştirilebildiğini gösterir. Bu örnek, tek bir günlük dinleyicisi filtrelemek için nasıl gösterir. Varsayılan olarak, bir uygulamanın hata ayıklama çıktısına ve günlük dosyasına yazan iki dinleyicisi vardır.

Yapılandırma dosyası, günlük dinleyicilerinin davranışını, her birinin bir filtreye sahip olmasını sağlayarak `My.Application.Log`denetler. Günlük dinleyicisi, yalnızca iletinin önem derecesine hem günlük `DefaultSwitch` hem de günlük dinleyicifiltresi tarafından izin verilirse bir ileti çıkar.

Bu örnek, yeni bir hata ayıklama dinleyicisi için filtrelemenin nasıl yapılandırılabildiğini ve `Log` nesneye nasıl ekleyeceğini gösterir. Varsayılan hata ayıklama dinleyicisi `Log` nesneden kaldırılmalıdır, bu nedenle hata ayıklama iletilerinin yeni hata ayıklama dinleyicisinden geldiği açıktır.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için

1. **Çözüm Gezgini'nde** app.config'e sağ tıklayın ve **Aç'ı**seçin.

     \-veya-

     App.config dosyası yoksa:

    1. **Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.

    2. Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.

    3. **Ekle**’ye tıklayın.

2. **Çözüm Gezgini'nde**app.config'e sağ tıklayın. **Aç'ı**seçin.

3. Bölümün altında yer `<source>` alan "DefaultSource" `name` özniteliğinin bulunduğu bölümdeki bölümü bulun. `<listeners>` `<sources>` Bölüm, `<sources>` üst `<system.diagnostics>` düzey `<configuration>` bölümde, bölüm altındadır.

4. Bu öğeyi `<listeners>` bölüme ekleyin:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. `<sharedListeners>` Bölümü, `<system.diagnostics>` bölümü, üst düzey `<configuration>` bölümü bulun.

6. Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:

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

     Filtre, <xref:System.Diagnostics.EventTypeFilter> özniteliği <xref:System.Diagnostics.SourceLevels> olarak `initializeData` numaralandırma değerlerinden birini alır.

7. app.config dosyasının içeriği aşağıdaki XML benzer olmalıdır:

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

8. Uygulamayı hata ayıklamada çalıştırın.

9. **Düğmeye Basın1**.

     Uygulama, uygulamanın günlük dosyasına aşağıdaki bilgileri yazar:

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     Uygulama, daha kısıtlayıcı filtreleme nedeniyle uygulamanın hata ayıklama çıktısına daha az bilgi yazar.

     `Default Error   2   Error`

10. Uygulamayı kapatın.

Dağıtımdan sonra günlük ayarlarını değiştirme hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzleme Anahtarları](../../../../framework/debug-trace-profile/trace-switches.md)
- [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/index.md)
