---
title: "İş akışı izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4332b93175f4cb751ba88c7d2b05e4b462de7748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="workflow-tracing"></a>İş akışı izleme
İş akışı izleme .NET Framework izleme dinleyicilerini kullanarak tanılama bilgileri yakalamak için bir yol sunar. İzleme uygulama ile ilgili bir sorun algılandığında, etkin ve sorun çözüldükten sonra yeniden devre dışı bırakıldı. İş akışları için hata ayıklama izlemeyi etkinleştirebilir iki yolu vardır. Olay İzleme Görüntüleyicisi'ni kullanarak yapılandırabilirsiniz ya da kullanabilirsiniz <xref:System.Diagnostics> izleme olayları bir dosya göndermek için.  
  
## <a name="enabling-debug-tracing-in-etw"></a>ETW İzleme hata ayıklama etkinleştirme  
 ETW kullanarak izlemeyi etkinleştirmek için Olay Görüntüleyicisi'ndeki Debug kanal etkinleştirin:  
  
1.  Çok analitik gidin ve günlükleri düğümü Olay Görüntüleyicisi'ndeki debug.  
  
2.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının**. Sağ **uygulama uygulamalarının** seçip **View'a Analitik ve hata ayıklama günlüklerini göster**. Sağ **hata ayıklama** seçip **günlüğü etkinleştir**.  
  
3.  Bir iş akışı debug çalıştırdığında ve izlemeleri ETW hata ayıklama kanala gösterilen Olay Görüntüleyicisi'nde görüntülenebilir. Gidin **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının**. Sağ **hata ayıklama** seçip **yenileme**.  
  
4.  Yalnızca 4 kilobayt (KB); varsayılan çözümleme izleme arabellek boyutu değil 32 KB boyutunu artırmak için önerilir. Bunu yapmak için aşağıdaki adımları gerçekleştirin.  
  
    1.  Geçerli framework dizinde (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203) şu komutu çalıştırın:`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Değişiklik \<bufferSize > 32 Windows.ApplicationServer.Applications.man dosyasındaki değeri.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  Geçerli framework dizinde (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203) şu komutu çalıştırın:`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  .NET Framework 4 istemci profili kullanıyorsanız, önce ETW bildirimi .NET Framework 4 dizininden aşağıdaki komutu çalıştırarak kaydetmeniz gerekir:`ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Hata ayıklama System.Diagnostics kullanarak izlemeyi etkinleştirme  
 Bu dinleyicileri bir iş akışı hizmeti için iş akışı uygulamanın Web.config veya App.config dosyasında yapılandırılabilir. Bu örnekte, bir [olmalıdır](http://go.microsoft.com/fwlink/?LinkId=165424) MyTraceLog.txt dosyası geçerli dizinde izleme bilgilerini kaydetmek için yapılandırılır.  
  
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
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
