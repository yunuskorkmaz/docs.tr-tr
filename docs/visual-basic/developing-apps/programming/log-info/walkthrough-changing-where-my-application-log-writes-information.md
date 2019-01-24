---
title: My.Application.Log (Visual Basic) bilgileri yazdığı yeri değiştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: b0d9e40f3f41eac5b16037a89a3cac45cbfc8c57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574455"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek yol: My.Application.Log (Visual Basic) bilgileri yazdığı yeri değiştirme
Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri. Bu izlenecek yol varsayılan ayarları geçersiz kılar ve neden gösterilmektedir `Log` diğer günlük dinleyicileri için yazılacak nesne.  
  
## <a name="prerequisites"></a>Önkoşullar  
 `Log` Nesne için birkaç günlük dinleyicileri bilgileri yazabilirsiniz. Yapılandırmaları değiştirmeden önce geçerli yapılandırmasını günlük dinleyicileri belirlemek gerekir. Daha fazla bilgi için [izlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Gözden geçirmek isteyebilirsiniz [nasıl yapılır: Olay bilgilerini metin dosyasına yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) veya [nasıl yapılır: Uygulama olay günlüğüne yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).  
  
### <a name="to-add-listeners"></a>Dinleyiciler eklemek için  
  
1.  App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     \- veya -  
  
     App.config dosyası yoksa:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2.  Bulun `<listeners>` bölümündeki `<source>` ile bölümünde `name` "DefaultSource" özniteliğini `<sources>` bölümü. `<sources>` Bölümü olduğundan `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
3.  Bu öğeleri eklemek için `<listeners>` bölümü.  
  
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
  
4.  Almak istediğiniz günlük dinleyicileri açıklamadan çıkarın `Log` iletileri.  
  
5.  Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
6.  Bu öğeleri eklemek için `<sharedListeners>` bölümü.  
  
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
  
7.  App.config dosyasının içeriği aşağıdaki XML'e benzer olmalıdır:  
  
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
  
### <a name="to-reconfigure-a-listener"></a>Dinleyici yeniden yapılandırmak için  
  
1.  Dinleyicinin bulun `<add>` öğesinden `<sharedListeners>` bölümü.  
  
2.  `type` Özniteliği dinleyici türü adını verir. Bu tür devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı. Kesin adlandırılmış tür adı doğru tür kullanıldığından emin olmak için kullanın. Daha fazla bilgi için "kesin adlandırılmış tür başvurmak için" bölümüne bakın.  
  
     Kullanabileceğiniz bazı türleri şunlardır:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, bir dosyayı günlüğe yazar.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> bilgileri tarafından belirtilen bilgisayarın olay günlüğüne yazan dinleyici `initializeData` parametresi.  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> belirtilen dosyaya yazma dinleyici `initializeData` parametresi.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyici, komut satırı konsola yazar.  
  
     Burada günlük dinleyicileri diğer tür bilgilerini yazma hakkında daha fazla bilgi için bu türün belgelerine bakın.  
  
3.  Uygulama günlüğü dinleyici nesne oluşturduğunda, arabimini `initializeData` öznitelik oluşturucu parametresi olarak. Anlamını `initializeData` öznitelik üzerinde İzleme dinleyicisi bağlıdır.  
  
4.  Günlük dinleyici oluşturduktan sonra uygulama dinleyicinin özelliklerini ayarlar. Bu özellikler diğer öznitelikleri tarafından tanımlanan `<add>` öğesi. Belirli bir dinleyici özellikleri hakkında daha fazla bilgi için bu dinleyicinin türü için belgelere bakın.  
  
### <a name="to-reference-a-strongly-named-type"></a>Kesin adlandırılmış tür referansı  
  
1.  Doğru tür günlük dinleyicinize için kullanıldığından emin olmak için tam nitelikli tür adı ve türü kesin adlandırılmış bütünleştirilmiş kod adı kullandığınızdan emin olun. Kesin adlandırılmış tür söz dizimi aşağıdaki gibidir:  
  
     \<*tür adı*>, \< *derleme adı*>, \< *sürüm numarası*>, \< *kültür*>, \< *tanımlayıcı ad*>  
  
2.  Bu kod örneği için tam type—"System.Diagnostics.FileLogTraceListener kesin adlandırılmış tür adını belirlemek bu durumda gösterilmektedir".  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     Bu çıktı ve benzersiz olarak "dinleyiciler eklemek için" yordamı yukarıdaki olduğu gibi kesin adlandırılmış bir tür başvuru için kullanılabilir.  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Nasıl yapılır: Olay bilgilerini metin dosyasına yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Nasıl yapılır: Uygulama olay günlüğüne yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
