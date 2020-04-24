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

Bu izlenecek yol, nesneden dinleyicilerine hangi bilgilerin geçtiğini `My.Application.Log` `Log` ve hangi bilgilerin dinleyiciler tarafından yazıldığını denetlemek için nesnenin varsayılan günlük filtrelemesinin nasıl değiştirileceğini gösterir. Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığından, uygulamayı oluşturduktan sonra bile günlüğe kaydetme davranışını değiştirebilirsiniz.

## <a name="getting-started"></a>Başlarken

`My.Application.Log` Yazan her ileti, bir ilişkili önem düzeyine sahiptir ve bu da filtreleme mekanizmalarının günlük çıkışını denetlemek için kullandığı bir önem düzeyi vardır Bu örnek uygulama, `My.Application.Log` farklı önem düzeylerindeki çeşitli günlük iletilerini yazmak için yöntemler kullanır.

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

     Yukarıdaki örnekte, yöntemine yapılan <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> ikinci çağrı ve yöntemine yapılan çağrı <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> günlük çıktısını üretir, ancak `WriteEntry` yöntemin ilk ve son çağrıları değildir. Bunun nedeni, önem seviyelerinin `WriteEntry` `WriteException` "bilgi" ve "hata" olmasına ve her ikisinin de `My.Application.Log` nesnenin varsayılan günlük filtrelemesine izin verdiği anlamına gelir. Bununla birlikte, "Başlat" ve "Durdur" önem derecesindeki olaylar günlük çıktısı üretmesinin engellenmektedir.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Tüm My. Application. log dinleyicileri için filtreleme

`My.Application.Log` Nesnesi, `WriteEntry` ve `WriteException` yöntemlerinden <xref:System.Diagnostics.SourceSwitch> hangi `DefaultSwitch` iletilerin günlük dinleyicilerine geçireceğini denetlemek için adlandırılmış bir kullanır. Değerini <xref:System.Diagnostics.SourceLevels> sabit listesi `DefaultSwitch` değerlerinden birine ayarlayarak uygulamanın yapılandırma dosyasında yapılandırabilirsiniz. Varsayılan olarak, değeri "bilgi" ' dir.

Bu tablo, belirli `DefaultSwitch` bir ayar Için, günlüğe kaydedilecek bir ileti yazmak için gereken önem derecesini gösterir.

|DefaultSwitch değeri|Çıkış için gereken ileti önem derecesi|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` veya `Error`|
|`Warning`|`Critical`, `Error`, veya`Warning`|
|`Information`|`Critical``Warning`, `Error`, veya`Information`|
|`Verbose`|`Critical``Warning`,, `Error` `Information`, veya`Verbose`|
|`ActivityTracing`|`Start``Suspend`,, `Stop` `Resume`, veya`Transfer`|
|`All`|Tüm iletilere izin verilir.|
|`Off`|Tüm iletiler engellenir.|

> [!NOTE]
> `WriteEntry` Ve `WriteException` yöntemlerinin her biri önem düzeyi belirtmeyen bir aşırı yüklemeye sahiptir. `WriteEntry` Aşırı yükleme için örtülü önem düzeyi "bilgi" ve `WriteException` aşırı yükleme için örtülü önem düzeyi "hata" dır.

Bu tabloda, önceki örnekte gösterilen günlük çıktısı açıklanmaktadır: varsayılan `DefaultSwitch` "bilgi" ayarıyla, `WriteEntry` yönteme yalnızca ikinci çağrı ve `WriteException` yönteme yapılan çağrı günlük çıkışı oluşturur.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için

1. **Çözüm Gezgini** App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     -veya-

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. Üst düzey `<switches>` `<system.diagnostics>` `<configuration>` bölümde bulunan bölümünde olan bölümünü bulun.

3. Anahtarlar koleksiyonuna ekleyen `DefaultSwitch` öğeyi bulun. Bu öğe şuna benzer görünmelidir:

     `<add name="DefaultSwitch" value="Information" />`

4. `value` Özniteliğin değerini "ActivityTracing" olarak değiştirin.

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

9. `value` Özniteliğin değerini "Information" olarak değiştirin.

    > [!NOTE]
    > Yalnızca `DefaultSwitch` `My.Application.Log`anahtar ayarı denetimleri. .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıflarının nasıl davranacağını değiştirmez.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>My. Application. log dinleyicileri Için bireysel filtreleme

Önceki örnekte, tüm `My.Application.Log` çıktılar için filtrelemenin nasıl değiştirileceği gösterilmektedir. Bu örnek, tek bir günlük dinleyicisinin nasıl filtreleneceğini gösterir. Varsayılan olarak, uygulamanın, uygulamanın hata ayıklama çıktısına ve günlük dosyasına yazan iki dinleyicisi vardır.

Yapılandırma dosyası, her birinin bir filtreye benzer bir filtreye sahip olmasını sağlayarak günlük dinleyicilerinin davranışını denetler `My.Application.Log`. Günlük dinleyicisi yalnızca, iletinin önem derecesine yalnızca günlüğün `DefaultSwitch` ve günlük dinleyicinin filtresi tarafından izin veriliyorsa bir ileti çıktı.

Bu örnek, `Log` yeni bir hata ayıklama dinleyicisi için filtrelemenin nasıl yapılandırılacağını ve nesneye nasıl ekleneceğini gösterir. Varsayılan hata ayıklama dinleyicisi `Log` nesnesinden kaldırılmalıdır, bu nedenle hata ayıklama iletilerinin yeni hata ayıklama dinleyicisinden geldiği temizlenmelidir.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için

1. **Çözüm Gezgini** App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     \-veya

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. **Çözüm Gezgini**' de App. config öğesine sağ tıklayın. **Aç**' ı seçin.

3. Bölümünün altında `<sources>` bulunan "DefaultSource" `name` özniteliğine sahip bölümünde bölümünü bulun. `<listeners>` `<source>` `<sources>` Bölümü, `<system.diagnostics>` bölümünün üst düzey `<configuration>` bölümünde yer aldığı bölümdür.

4. Bu öğeyi `<listeners>` bölümüne ekleyin:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Bölümünde, `<sharedListeners>` üst düzey `<configuration>` bölümünde bölümünde `<system.diagnostics>` bulunan bölümünü bulun.

6. Bu öğeyi bu `<sharedListeners>` bölüme ekleyin:

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

     <xref:System.Diagnostics.EventTypeFilter> Filtre, <xref:System.Diagnostics.SourceLevels> sabit listesi değerlerinden birini `initializeData` özniteliği olarak alır.

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

- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [Nasıl yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzleme Anahtarları](../../../../framework/debug-trace-profile/trace-switches.md)
- [Uygulamadan Günlüğe Bilgi Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/index.md)
