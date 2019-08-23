---
title: İş Akışı İzleme
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 7bca78b24963d94bfa0f2e2245a677b7dce455c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933436"
---
# <a name="workflow-tracing"></a>İş Akışı İzleme
İş akışı izleme .NET Framework İzleme dinleyicilerini kullanarak tanılama bilgilerini yakalamak için bir yol sunar. Uygulama ile ilgili bir sorun algılanırsa izleme etkinleştirilebilir ve sorun çözümlendikten sonra yeniden devre dışı bırakılabilir. İş akışları için hata ayıklama izlemeyi etkinleştirmenin iki yolu vardır. Bunu olay izleme görüntüleyicisini kullanarak yapılandırabilir veya <xref:System.Diagnostics> izleme olaylarını bir dosyaya göndermek için ' i kullanabilirsiniz.  
  
## <a name="enabling-debug-tracing-in-etw"></a>ETW 'de hata ayıklama Izlemeyi etkinleştirme  
 ETW kullanarak izlemeyi etkinleştirmek için Olay Görüntüleyicisi hata ayıklama kanalını etkinleştirin:  
  
1. Olay Görüntüleyicisi 'de analitik ve hata ayıklama günlükleri düğümüne gidin.  
  
2. Olay Görüntüleyicisi 'daki ağaç görünümünde, **Olay Görüntüleyicisi > uygulamalar ve hizmet günlükleri-> Microsoft-> Windows-> uygulama sunucusu-uygulamalar**' a gidin. **Uygulama sunucusu-uygulamalar** ' a sağ tıklayın ve **Görünüm-> analitik ve hata ayıklama günlüklerini göster**' i seçin. **Hata Ayıkla** ' ya sağ tıklayın ve **günlüğü etkinleştir**' i seçin.  
  
3. Bir iş akışı, hata ayıklamayı çalıştırdığında ve izlemeler ETW hata ayıklama kanalına yayıldıklarında, Olay Görüntüleyicisi görüntülenebilirler. **Olay Görüntüleyicisi > uygulamalar ve hizmet günlükleri-> Microsoft-> Windows-> uygulama sunucusu-uygulamalar '** a gidin. **Hata Ayıkla** ' ya sağ tıklayın ve **Yenile**' yi seçin.  
  
4. Varsayılan analitik izleme arabelleği boyutu yalnızca 4 kilobayttır (KB); boyutu 32 KB olarak artırmanız önerilir. Bunu yapmak için aşağıdaki adımları gerçekleştirin.  
  
    1. Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2. Windows. ApplicationServer. Applications. Man dosyasındaki bufferSize>değerini32olarakdeğiştirin.\<  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
> .NET Framework 4 Istemci profilini kullanıyorsanız, önce .NET Framework 4 dizininden aşağıdaki komutu çalıştırarak ETW bildirimini kaydetmeniz gerekir:`ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>System. Diagnostics kullanarak hata ayıklama Izlemeyi etkinleştirme  
 Bu dinleyiciler iş akışı uygulamasının App. config dosyasında veya bir iş akışı hizmeti için Web. config ' de yapılandırılabilir. Bu örnekte bir [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) , izleme bilgilerini geçerli dizindeki mytracelog. txt dosyasına kaydedecek şekilde yapılandırılmıştır.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
