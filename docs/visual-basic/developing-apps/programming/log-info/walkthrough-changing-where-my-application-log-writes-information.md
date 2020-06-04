---
title: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: f9e45cdf4507840f62e32678f4c0a7be2c0be054
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398298"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme (Visual Basic)

`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz. Bu izlenecek yol, varsayılan ayarların nasıl geçersiz kılınacağını ve `Log` nesnenin diğer günlük dinleyicilerine yazmasına neden olduğunu gösterir.

## <a name="prerequisites"></a>Önkoşullar

`Log`Nesnesi, çeşitli günlük dinleyicilerine bilgi yazabilir. Yapılandırmaları değiştirmeden önce günlük dinleyicilerinin geçerli yapılandırmasını belirlemeniz gerekir. Daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log bilgisinin nereden yazabileceğini belirleme](walkthrough-determining-where-my-application-log-writes-information.md).

[Nasıl yapılır: bir metin dosyasına olay bilgilerini yazma](how-to-write-event-information-to-a-text-file.md) veya [nasıl yapılır: uygulama olay günlüğüne yazma](how-to-write-to-an-application-event-log.md).

### <a name="to-add-listeners"></a>Dinleyicileri eklemek için

1. **Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.

     \-veya

     App. config dosyası yoksa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. Bölümünde `<listeners>` `<source>` `name` "DefaultSource" özniteliğine sahip bölümün altındaki bölümü bulun `<sources>` . `<sources>`Bölümü, `<system.diagnostics>` üst düzey bölümündeki bölümünde bulunur `<configuration>` .

3. Bu öğeleri bu bölüme ekleyin `<listeners>` .

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. İleti almak istediğiniz günlük dinleyicilerinin açıklamasını kaldırın `Log` .

5. Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .

6. Bu öğeleri bu bölüme ekleyin `<sharedListeners>` .

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

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
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
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
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a>Bir dinleyiciyi yeniden yapılandırmak için

1. Bölümünden dinleyicinin öğesini bulun `<add>` `<sharedListeners>` .

2. `type`Öznitelik, dinleyici türünün adını verir. Bu tür sınıfından devralması gerekir <xref:System.Diagnostics.TraceListener> . Doğru türün kullanıldığından emin olmak için kesin adlandırılmış tür adını kullanın. Daha fazla bilgi için, aşağıdaki "kesin adlandırılmış türe başvurmak Için" bölümüne bakın.

     Kullanabileceğiniz bazı türler şunlardır:

    - <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>Bir dosya günlüğüne yazan bir dinleyici.

    - <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>Parametresi tarafından belirtilen bilgisayar olay günlüğüne bilgi yazan bir dinleyici `initializeData` .

    - <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Parametresinde belirtilen dosyaya yazılan ve dinleyicileri `initializeData` .

    - <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>Komut satırı konsoluna yazan bir dinleyici.

     Diğer günlük dinleyicisi türlerinin yazma bilgileri hakkında daha fazla bilgi için, bu türün belgelerine başvurun.

3. Uygulama, log-Listener nesnesini oluşturduğunda, `initializeData` özniteliği Oluşturucu parametresi olarak geçirir. Özniteliğin anlamı, `initializeData` izleme dinleyicisine bağlıdır.

4. Günlük dinleyicisini oluşturduktan sonra uygulama, dinleyicinin özelliklerini ayarlar. Bu özellikler, öğesindeki diğer öznitelikler tarafından tanımlanır `<add>` . Belirli bir dinleyicinin özellikleri hakkında daha fazla bilgi için, bu dinleyicinin türüne yönelik belgelere bakın.

### <a name="to-reference-a-strongly-named-type"></a>Kesin adlandırılmış türe başvurmak için

1. Doğru türün günlük dinleyiciniz için kullanıldığından emin olmak için tam tür adı ve kesin adlandırılmış derleme adını kullandığınızdan emin olun. Kesin adlandırılmış türün sözdizimi aşağıdaki gibidir:

     \<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*>

2. Bu kod örneği, bu durumda "System. Diagnostics. FileLogTraceListener" tam türü için kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir.

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     Bu çıktı, yukarıdaki "dinleyicileri ekleme" yordamında olduğu gibi kesin adlandırılmış bir türe benzersiz olarak başvurmak için kullanılabilir.

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma](how-to-write-event-information-to-a-text-file.md)
- [Nasıl yapılır: Uygulama Olay Günlüğüne Yazma](how-to-write-to-an-application-event-log.md)
