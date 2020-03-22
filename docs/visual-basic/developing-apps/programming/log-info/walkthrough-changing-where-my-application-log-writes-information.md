---
title: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: bdee0a91360580b156c1734ef4c82139b18ce2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74336732"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme (Visual Basic)

Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri kullanabilirsiniz. Bu gözden geçirme, varsayılan ayarları nasıl geçersiz `Log` kılındığını ve nesnenin diğer günlük dinleyicilerine yazmasına nasıl neden olduğunu gösterir.

## <a name="prerequisites"></a>Önkoşullar

Nesne `Log` birkaç günlük dinleyiciye bilgi yazabilir. Yapılandırmaları değiştirmeden önce günlük dinleyicilerinin geçerli yapılandırmasını belirlemeniz gerekir. Daha fazla bilgi için [bkz.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

Nasıl yapılacağını gözden geçirmek [isteyebilirsiniz: Metin Dosyasına Olay Bilgileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) veya Nasıl [Yazılır: Uygulama Olayı Günlüğüne Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).

### <a name="to-add-listeners"></a>Dinleyici eklemek için

1. **Solution Explorer'da** app.config'e sağ tıklayın ve **Aç'ı**seçin.

     \-veya -

     App.config dosyası yoksa:

    1. **Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.

    2. Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.

    3. **Ekle**’ye tıklayın.

2. Bölümdeki `<listeners>` "DefaultSource" `<source>` `name` özniteliğinin bulunduğu bölümün altındaki bölümü bulun. `<sources>` Bölüm, `<sources>` `<system.diagnostics>` üst düzey `<configuration>` bölümde.

3. Bu öğeleri bu `<listeners>` bölüme ekleyin.

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

4. İleti almak `Log` istediğiniz günlük dinleyicilerinin yorumlarını bırakın.

5. `<sharedListeners>` Bölümü, `<system.diagnostics>` bölümü, üst düzey `<configuration>` bölümü bulun.

6. Bu öğeleri bu `<sharedListeners>` bölüme ekleyin.

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

### <a name="to-reconfigure-a-listener"></a>Dinleyiciyi yeniden yapılandırmak için

1. Dinleyicinin `<add>` öğesini `<sharedListeners>` bölümden bulun.

2. Öznitelik `type` dinleyici türüadını verir. Bu tür <xref:System.Diagnostics.TraceListener> sınıftan devralınmalıdır. Doğru türün kullanıldığından emin olmak için güçlü adlandırılmış tür adını kullanın. Daha fazla bilgi için aşağıdaki "Güçlü adlandırılmış bir türe başvurmak için" bölümüne bakın.

     Kullanabileceğiniz bazı türler şunlardır:

    - Dosya <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> günlüğüne yazan bir dinleyici.

    - Parametre tarafından belirtilen bilgisayar olay günlüğüne bilgi yazan bir <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyici. `initializeData`

    - Parametrede <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> belirtilen dosyaya yazan ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyiciler. `initializeData`

    - Komut <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> satırı konsoluna yazan bir dinleyici.

     Diğer günlük dinleyici türlerinin nerede bilgi yazdıkları hakkında bilgi için, bu türbelgelerine başvurun.

3. Uygulama log-dinleyici nesnesi oluşturduğunda, özniteliği oluşturucu parametresi olarak geçirir. `initializeData` Özniteliğin `initializeData` anlamı izleme dinleyicisi bağlıdır.

4. Günlük dinleyicisini oluşturduktan sonra, uygulama dinleyicinin özelliklerini ayarlar. Bu özellikler `<add>` öğedeki diğer öznitelikler tarafından tanımlanır. Belirli bir dinleyicinin özellikleri hakkında daha fazla bilgi için, o dinleyicinin türüne ait belgelere bakın.

### <a name="to-reference-a-strongly-named-type"></a>Güçlü adlandırılmış bir türe başvurmak için

1. Günlük dinleyiciniz için doğru türün kullanıldığından emin olmak için, tam nitelikli tür adını ve güçlü bir şekilde adlandırılmış montaj adını kullandığınızdan emin olun. Güçlü adlandırılmış bir türün sözdizimi aşağıdaki gibidir:

     \<*tür adı* \<>, montaj \< *adı*>, sürüm \< *numarası* \<>, *kültür*>, güçlü *ad*>

2. Bu kod örneği, tam nitelikli bir tür için güçlü adlandırılmış tür adının nasıl belirlendiğini gösterir—"System.Diagnostics.FileLogTraceListener" bu durumda.

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     Bu çıktıdır ve yukarıdaki "Dinleyici eklemek için" yordamında olduğu gibi, güçlü bir şekilde adlandırılmış bir türe benzersiz bir şekilde başvurmak için kullanılabilir.

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Nasıl Yapılır: Olay Bilgilerini Metin Dosyasına Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
