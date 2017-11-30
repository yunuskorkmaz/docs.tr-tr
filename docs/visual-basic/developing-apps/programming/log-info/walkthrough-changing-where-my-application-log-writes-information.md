---
title: "My.Application.Log (Visual Basic) bilgileri yazdığı yeri değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4cd2e675bf1be4f065ee116795a95dae64d13d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme (Visual Basic)
Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri. Bu kılavuz varsayılan ayarları geçersiz kılar ve neden gösterilmektedir `Log` diğer günlük dinleyicileri yazılacak nesne.  
  
## <a name="prerequisites"></a>Önkoşullar  
 `Log` Nesne için birden fazla günlük dinleyicileri bilgileri yazabilirsiniz. Yapılandırmaları değiştirmeden önce günlük dinleyicileri geçerli yapılandırmasını belirlemeniz gerekir. Daha fazla bilgi için bkz: [izlenecek yol: belirleme nerede My.Application.Log Yazar bilgisini](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Gözden geçirmek isteyebileceğiniz [nasıl yapılır: olay bilgilerini metin dosyasına yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) veya [nasıl yapılır: uygulama olay günlüğüne yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).  
  
### <a name="to-add-listeners"></a>Dinleyicileri eklemek için  
  
1.  App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     \-veya -  
  
     Herhangi bir app.config dosyası ise:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2.  Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource" özniteliğini `<sources>` bölümü. `<sources>` Bölümdür içinde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
3.  Bu öğeler olarak Ekle `<listeners>` bölümü.  
  
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
  
6.  Bu öğeler olarak Ekle `<sharedListeners>` bölümü.  
  
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
  
1.  Dinleyici 's bulun `<add>` öğesinden `<sharedListeners>` bölümü.  
  
2.  `type` Özniteliği dinleyicisi türünün adı sağlar. Bu tür öğesinden devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı. Doğru türde kullanıldığından emin olmak için kesin adlandırılmış tür adı kullanın. Daha fazla bilgi için aşağıdaki "kesin adlandırılmış bir türü başvurmak için" bölümüne bakın.  
  
     Kullanabileceğiniz bazı türleri şunlardır:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> bir dosyayı günlüğe yazar dinleyicisi.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> bilgileri tarafından belirtilen bilgisayar olay günlüğüne yazar dinleyici `initializeData` parametresi.  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> belirtilen dosyaya yazma dinleyicileri `initializeData` parametresi.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> komut satırı konsola dinleyicisi.  
  
     Burada günlük dinleyicileri diğer tür bilgilerini yazma hakkında daha fazla bilgi için bu tür belgelerine başvurun.  
  
3.  Uygulama günlüğü dinleyici nesne oluşturduğunda, geçirir `initializeData` Oluşturucu parametresi olarak özniteliği. Anlamını `initializeData` özniteliği üzerinde İzleme dinleyicisi bağlıdır.  
  
4.  Günlük dinleyicisi oluşturduktan sonra uygulama dinleyiciyi'nın özelliklerini ayarlar. Bu özellikleri diğer öznitelikleri tarafından tanımlanan `<add>` öğesi. Belli bir Dinleyicide özellikleri hakkında daha fazla bilgi için dinleyici'nın türü için belgelerine bakın.  
  
### <a name="to-reference-a-strongly-named-type"></a>Türü kesin adlandırılmış bir tür referansı  
  
1.  Doğru türde günlük dinleyici için kullanıldığından emin olmak için tam olarak nitelenmiş tür adını ve kesin adlandırılmış derleme adı kullandığınızdan emin olun. Türü kesin adlandırılmış bir türün söz dizimi aşağıdaki gibidir:  
  
     \<*tür adı*>, \< *derleme adı*>, \< *sürüm numarası*>, \< *kültür*>, \< *kesin adı*>  
  
2.  Bu kod örneği için tam type—"System.Diagnostics.FileLogTraceListener kesin adlandırılmış tür adını belirlemek bu durumda gösterilmiştir".  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     Bu çıktı ve benzersiz olduğu gibi "dinleyicileri eklemek için" Yukarıdaki yordamı kesin adlandırılmış bir türe başvuruda için kullanılabilir.  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [Nasıl yapılır: olay bilgilerini metin dosyasına yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [Nasıl yapılır: uygulama olay günlüğüne yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
