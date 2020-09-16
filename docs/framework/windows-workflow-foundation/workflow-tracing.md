---
title: İş Akışı İzleme
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: fc27be295cbf0a83b65ff03e36f2aeffeda12db9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557508"
---
# <a name="workflow-tracing"></a>İş Akışı İzleme
İş akışı izleme .NET Framework İzleme dinleyicilerini kullanarak tanılama bilgilerini yakalamak için bir yol sunar. Uygulama ile ilgili bir sorun algılanırsa izleme etkinleştirilebilir ve sorun çözümlendikten sonra yeniden devre dışı bırakılabilir. İş akışları için hata ayıklama izlemeyi etkinleştirmenin iki yolu vardır. Bunu olay Izleme görüntüleyicisini kullanarak yapılandırabilir veya <xref:System.Diagnostics> izleme olaylarını bir dosyaya göndermek için ' i kullanabilirsiniz.  
  
## <a name="enabling-debug-tracing-in-etw"></a>ETW 'de hata ayıklama Izlemeyi etkinleştirme  
 ETW kullanarak izlemeyi etkinleştirmek için Olay Görüntüleyicisi hata ayıklama kanalını etkinleştirin:  
  
1. Olay Görüntüleyicisi 'de analitik ve hata ayıklama günlükleri düğümüne gidin.  
  
2. Olay Görüntüleyicisi 'daki ağaç görünümünde, **Olay Görüntüleyicisi >uygulamalar ve hizmet günlükleri->Microsoft->Windows->uygulama sunucusu-uygulamalar**' a gidin. **Uygulama sunucusu-uygulamalar** ' a sağ tıklayın ve **Görünüm->analitik ve hata ayıklama günlüklerini göster**' i seçin. **Hata Ayıkla** ' ya sağ tıklayın ve **günlüğü etkinleştir**' i seçin.  
  
3. Bir iş akışı, hata ayıklamayı çalıştırdığında ve izlemeler ETW hata ayıklama kanalına yayıldıklarında, Olay Görüntüleyicisi görüntülenebilirler. **Olay Görüntüleyicisi >uygulamalar ve hizmet günlükleri->Microsoft->Windows->uygulama sunucusu-uygulamalar '** a gidin. **Hata Ayıkla** ' ya sağ tıklayın ve **Yenile**' yi seçin.  
  
4. Varsayılan analitik izleme arabelleği boyutu yalnızca 4 kilobayttır (KB); boyutu 32 KB olarak artırmanız önerilir. Bunu yapmak için aşağıdaki adımları uygulayın.  
  
    1. Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2. \<bufferSize>Windows. ApplicationServer. Applications. Man dosyasındaki değeri 32 olarak değiştirin.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
> .NET Framework 4 Istemci profilini kullanıyorsanız, önce .NET Framework 4 dizininden aşağıdaki komutu çalıştırarak ETW bildirimini kaydetmeniz gerekir: `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>System. Diagnostics kullanarak hata ayıklama Izlemeyi etkinleştirme  
 Bu dinleyiciler, iş akışı uygulamasının App.config dosyasında veya bir iş akışı hizmeti için Web.config yapılandırılabilir. Bu örnekte, <xref:System.Diagnostics.TextWriterTraceListener> izleme bilgilerini geçerli dizindeki MyTraceLog.txt dosyasına kaydedecek şekilde yapılandırılır.  
  
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

- [Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))
