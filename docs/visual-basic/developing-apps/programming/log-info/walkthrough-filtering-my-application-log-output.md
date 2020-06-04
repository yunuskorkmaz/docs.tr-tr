---
title: My.Application.Log Çıktısını Filtreleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: aa63e7d23641ad71b135f15236e29399a535784f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398259"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>İzlenecek Yol: My.Application.Log Çıktısını Filtreleme (Visual Basic)

Bu izlenecek yol, nesneden `My.Application.Log` dinleyicilerine hangi bilgilerin geçtiğini `Log` ve hangi bilgilerin dinleyiciler tarafından yazıldığını denetlemek için nesnenin varsayılan günlük filtrelemesinin nasıl değiştirileceğini gösterir. Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığından, uygulamayı oluşturduktan sonra bile günlüğe kaydetme davranışını değiştirebilirsiniz.

## <a name="getting-started"></a>Başlarken

Yazan her ileti `My.Application.Log` , bir ilişkili önem düzeyine sahiptir ve bu da filtreleme mekanizmalarının günlük çıkışını denetlemek için kullandığı bir önem düzeyi vardır Bu örnek uygulama `My.Application.Log` , farklı önem düzeylerindeki çeşitli günlük iletilerini yazmak için yöntemler kullanır.

#### <a name="to-build-the-sample-application"></a>Örnek uygulamayı derlemek için

1. Yeni bir Visual Basic Windows uygulaması projesi açın.

2. Form1 adına button1 adlı bir düğme ekleyin.

3. <xref:System.Windows.Forms.Control.Click>Button1 için olay işleyicisinde aşağıdaki kodu ekleyin:

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. Uygulamayı hata ayıklayıcıda çalıştırın.

5. **Button1**'e basın.

     Uygulama, uygulamanın hata ayıklama çıktısına ve günlük dosyasına aşağıdaki bilgileri yazar.

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. Uygulamayı kapatın.

     Uygulamanın hata ayıklama çıkış penceresini görüntüleme hakkında daha fazla bilgi için bkz. [Çıkış penceresi](/visualstudio/ide/reference/output-window). Uygulamanın günlük dosyasının konumu hakkında daha fazla bilgi için bkz [. Walkthrough: My. Application. log bilgisinin nereden yazabileceğini belirleme](walkthrough-determining-where-my-application-log-writes-information.md).

    > [!NOTE]
    > Varsayılan olarak uygulama kapandığında günlük dosyası çıkışını temizler.

     Yukarıdaki örnekte, yöntemine yapılan ikinci çağrı ve yöntemine yapılan <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> çağrı <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> günlük çıktısını üretir, ancak yöntemin ilk ve son çağrıları `WriteEntry` değildir. Bunun nedeni, önem seviyelerinin `WriteEntry` `WriteException` "bilgi" ve "hata" olmasına ve her ikisinin de `My.Application.Log` nesnenin varsayılan günlük filtrelemesine izin verdiği anlamına gelir. Bununla birlikte, "Başlat" ve "Durdur" önem derecesindeki olaylar günlük çıktısı üretmesinin engellenmektedir.

## <a name="filtering-for-all-myapplicationlog-listeners"></a>Tüm My. Application. log dinleyicileri için filtreleme

`My.Application.Log`Nesnesi <xref:System.Diagnostics.SourceSwitch> `DefaultSwitch` , `WriteEntry` ve yöntemlerinden hangi iletilerin günlük dinleyicilerine geçireceğini denetlemek için adlandırılmış bir kullanır `WriteException` . `DefaultSwitch`Değerini sabit listesi değerlerinden birine ayarlayarak uygulamanın yapılandırma dosyasında yapılandırabilirsiniz <xref:System.Diagnostics.SourceLevels> . Varsayılan olarak, değeri "bilgi" ' dir.

Bu tablo, belirli bir ayar için, günlüğe kaydedilecek bir ileti yazmak için gereken önem derecesini gösterir `DefaultSwitch` .

|DefaultSwitch değeri|Çıkış için gereken ileti önem derecesi|
|---|---|
|`Critical`|`Critical`|
|`Error`|`Critical` veya `Error`|
|`Warning`|`Critical`, `Error` , veya`Warning`|
|`Information`|`Critical`, `Error` , `Warning` veya`Information`|
|`Verbose`|`Critical`,,, `Error` `Warning` `Information` veya`Verbose`|
|`ActivityTracing`|`Start`,,, `Stop` `Suspend` `Resume` veya`Transfer`|
|`All`|Tüm iletilere izin verilir.|
|`Off`|Tüm iletiler engellenir.|

> [!NOTE]
> `WriteEntry`Ve `WriteException` yöntemlerinin her biri önem düzeyi belirtmeyen bir aşırı yüklemeye sahiptir. Aşırı yükleme için örtülü önem düzeyi `WriteEntry` "bilgi" ve aşırı yükleme için örtülü önem düzeyi `WriteException` "hata" dır.

Bu tabloda, önceki örnekte gösterilen günlük çıktısı açıklanmaktadır: varsayılan `DefaultSwitch` "bilgi" ayarıyla, yönteme yalnızca ikinci çağrı `WriteEntry` ve yönteme yapılan çağrı `WriteException` günlük çıkışı oluşturur.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için

1. **Çözüm Gezgini** App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     -veya-

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. `<switches>`Üst düzey bölümde bulunan bölümünde olan bölümünü bulun `<system.diagnostics>` `<configuration>` .

3. Anahtarlar koleksiyonuna ekleyen öğeyi bulun `DefaultSwitch` . Bu öğe şuna benzer görünmelidir:

     `<add name="DefaultSwitch" value="Information" />`

4. `value`Özniteliğin değerini "ActivityTracing" olarak değiştirin.

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

9. `value`Özniteliğin değerini "Information" olarak değiştirin.

    > [!NOTE]
    > `DefaultSwitch`Yalnızca anahtar ayarı denetimleri `My.Application.Log` . .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıflarının nasıl davranacağını değiştirmez.

## <a name="individual-filtering-for-myapplicationlog-listeners"></a>My. Application. log dinleyicileri Için bireysel filtreleme

Önceki örnekte, tüm çıktılar için filtrelemenin nasıl değiştirileceği gösterilmektedir `My.Application.Log` . Bu örnek, tek bir günlük dinleyicisinin nasıl filtreleneceğini gösterir. Varsayılan olarak, uygulamanın, uygulamanın hata ayıklama çıktısına ve günlük dosyasına yazan iki dinleyicisi vardır.

Yapılandırma dosyası, her birinin bir filtreye benzer bir filtreye sahip olmasını sağlayarak günlük dinleyicilerinin davranışını denetler `My.Application.Log` . Günlük dinleyicisi yalnızca, iletinin önem derecesine yalnızca günlüğün `DefaultSwitch` ve günlük dinleyicinin filtresi tarafından izin veriliyorsa bir ileti çıktı.

Bu örnek, yeni bir hata ayıklama dinleyicisi için filtrelemenin nasıl yapılandırılacağını ve nesneye nasıl ekleneceğini gösterir `Log` . Varsayılan hata ayıklama dinleyicisi `Log` nesnesinden kaldırılmalıdır, bu nedenle hata ayıklama iletilerinin yeni hata ayıklama dinleyicisinden geldiği temizlenmelidir.

#### <a name="to-log-only-activity-tracing-events"></a>Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için

1. **Çözüm Gezgini** App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     \-veya

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. **Çözüm Gezgini**' de App. config öğesine sağ tıklayın. **Aç**' ı seçin.

3. Bölümünün `<listeners>` `<source>` altında bulunan `name` "DefaultSource" özniteliğine sahip bölümünde bölümünü bulun `<sources>` . `<sources>`Bölümü, `<system.diagnostics>` bölümünün üst düzey bölümünde yer aldığı bölümdür `<configuration>` .

4. Bu öğeyi `<listeners>` bölümüne ekleyin:

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .

6. Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :

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

     <xref:System.Diagnostics.EventTypeFilter>Filtre, <xref:System.Diagnostics.SourceLevels> sabit listesi değerlerinden birini özniteliği olarak alır `initializeData` .

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

Dağıtımdan sonra günlük ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma](walkthrough-creating-custom-log-listeners.md)
- [Nasıl yapılır: Günlük İletileri Yazma](how-to-write-log-messages.md)
- [İzleme Anahtarları](../../../../framework/debug-trace-profile/trace-switches.md)
- [Uygulamadan Günlüğe Bilgi Kaydetme](index.md)
