---
title: İş akışı izleme
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 27e56933043c9eb955500cdd1c5bbd06cb33bde8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210899"
---
# <a name="workflow-tracing"></a>İş akışı izleme
İş akışı izleme, .NET Framework İzleme dinleyicisi kullanarak tanılama bilgilerini yakalamak için bir yol sunar. İzleme, uygulama ile ilgili bir sorun algılandığında, etkin ve sorun giderildikten sonra yeniden devre dışı bırakıldı. İş akışları için hata ayıklama izlemeyi sağlayabilir iki yolu vardır. İzleme Olay Görüntüleyicisi'ni kullanarak yapılandırabilirsiniz ya da <xref:System.Diagnostics> dosya izleme olayları göndermek için.  
  
## <a name="enabling-debug-tracing-in-etw"></a>ETW İzleme hata ayıklama etkinleştirme  
 ETW kullanarak izlemeyi etkinleştirmek için Olay Görüntüleyicisi'nde hata ayıklama kanal etkinleştir:  
  
1.  Analitik'ye gidin ve Olay görüntüleyicisindeki günlükleri düğüm hatalarını ayıklayın.  
  
2.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının**. Sağ **uygulama uygulamalarının** seçip **View'a Analitik ve hata ayıklama günlüklerini göster**. Sağ **hata ayıklama** seçip **günlüğü etkinleştir**.  
  
3.  Bir iş akışı hata ayıklama çalıştırır ve izlemeler ETW hata ayıklama kanala gönderilir, Olay Görüntüleyicisi'nde görüntülenebilir. Gidin **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının**. Sağ **hata ayıklama** seçip **Yenile**.  
  
4.  Yalnızca 4 kilobayt (KB); varsayılan analitik izleme arabellek boyutu olan 32 KB boyutunu artırmak için önerilir. Bunu yapmak için aşağıdaki adımları gerçekleştirin.  
  
    1.  Geçerli framework dizine (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203) aşağıdaki komutu yürütün: `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Değişiklik \<bufferSize > 32 Windows.ApplicationServer.Applications.man dosyasındaki değeri.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  Geçerli framework dizine (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203) aşağıdaki komutu yürütün: `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  .NET Framework 4 istemci profili kullanıyorsanız, önce için ETW bildirimini .NET Framework 4 dizininden aşağıdaki komutu çalıştırarak kaydetmeniz gerekir: `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>System.Diagnostics kullanarak hata ayıklama izlemeyi etkinleştirme  
 Dinleyiciler bir iş akışı hizmeti için iş akışı uygulamanın Web.config veya App.config dosyasında yapılandırılabilir. Bu örnekte, bir [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) MyTraceLog.txt dosyasını geçerli dizinde izleme bilgilerini kaydetmek için yapılandırılır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
