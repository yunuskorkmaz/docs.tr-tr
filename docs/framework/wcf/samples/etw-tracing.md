---
title: "ETW İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39164d6334be40de86f422e2faa4debf1d4f31f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="etw-tracing"></a>ETW İzleme
Bu örnek olay izleme için Windows (ETW) kullanarak uçtan uca (E2E) izleme uygulamak nasıl gösterir ve `ETWTraceListener` Bu örnek ile sağlanır. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve ETW İzleme içerir.  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
 Bu örnek aşina olduğunuzu varsayar [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Her izleme kaynağı <xref:System.Diagnostics> izleme model verileri nerede ve nasıl izleneceğini belirlemek birden fazla iz dinleyicileri sahip olabilir. Dinleyici türü izleme veriler günlüğe kaydedilir biçimini tanımlar. Aşağıdaki kod örneği, yapılandırmaya dinleyiciyi ekleyin gösterilmektedir.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"   
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 Bu dinleyici kullanmadan önce bir ETW izleme oturumunu başlatılması gerekir. Bu oturumda Logman.exe veya Tracelog.exe kullanılarak başlatılabilir. Oturumu kapatma ve günlük dosyası tamamlamak için bir CleanupETW.bat dosyasıyla birlikte ETW izleme oturumunu ayarlayabilirsiniz böylece SetupETW.bat dosya ile bu örnek dahil edilmiştir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır. Bu araçlar hakkında daha fazla bilgi için bkz: [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)  
  
 ETWTraceListener kullanırken, izlemeleri ikili .etl dosyaları günlüğe kaydedilir. ServiceModel izleme açık olan tüm oluşturulan izlemeleri aynı dosyada görünür. Kullanım [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .etl ve .svclog günlük dosyalarını görüntülemek için. Görüntüleyici bir ileti hedefine kaynağından izlemenizi olanaklı kılan sistem uçtan uca görünümünü ve tüketiminin noktası oluşturur.  
  
 ETW İzleme dinleyicisi döngüsel günlüğü destekler. Bu özelliği etkinleştirmek için şu adrese gidin **Başlat**, **çalıştırmak** ve türü `cmd` komut Konsolu'nu başlatın. Aşağıdaki komutta, `<logfilename>` parametresiyle birlikte, günlük dosyasının adı.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` Ve `-max` anahtarları isteğe bağlıdır. Bunlar ikili döngüsel biçimi ve 1000 MB maksimum günlük dosyası boyutu sırasıyla belirtin. `-p` Anahtar izleme sağlayıcısı belirtmek için kullanılır. Örneğimizde `"{411a0819-c24b-428c-83e2-26b41091702e}"` GUID "XML ETW örnek" sağlayıcısıdır.  
  
 Oturumu başlatmak için aşağıdaki komutu yazın.  
  
```  
Logman start Wcf  
```  
  
 Günlük kaydı tamamladıktan sonra aşağıdaki komutu oturumla durdurabilirsiniz.  
  
```  
Logman stop Wcf  
```  
  
 Bu işlem, seçeceğiniz araç ile işleyebilir ikili döngüsel günlükleri oluşturur dahil olmak üzere [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) veya Tracerpt.  
  
 Ayrıca gözden geçirebilirsiniz [döngüsel izleme](../../../../docs/framework/wcf/samples/circular-tracing.md) döngüsel günlüğü gerçekleştirmek için alternatif bir dinleyici hakkında daha fazla bilgi için örnek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  RegisterProvider.bat, SetupETW.bat ve CleanupETW.bat komutlarını kullanmak için bir yerel yönetici hesabı altında çalıştırmanız gerekir. Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)] veya daha sonra da komut isteminde yükseltilmiş ayrıcalıklarla çalıştırmanız gerekir. Bunu yapmak için komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**.  
  
3.  Örneği çalıştırmadan önce istemci ve sunucu üzerinde RegisterProvider.bat çalıştırın. Bu hizmet izleme görüntüleyicisini tarafından okunabilir izlemeleri oluşturmak için sonuçta elde edilen ETWTracingSampleLog.etl dosyasını ayarlar. Bu dosya C:\logs klasöründe bulunabilir. Bu klasör yoksa oluşturulması gerekir veya hiç izlemeleri üretilir. Ardından, SetupETW.bat ETW İzleme oturumu başlatmak için istemci ve sunucu bilgisayarda çalıştırın. SetupETW.bat dosya CS\Client klasörü altında bulunabilir.  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Örnek tamamlandığında ETWTracingSampleLog.etl dosya oluşturma işlemini tamamlamak için CleanupETW.bat çalıştırın.  
  
6.  Hizmet izleme görüntüleyicisini içinde ETWTracingSampleLog.etl dosyasını açın. Biçimlendirilmiş bir ikili dosyası .svclog dosyası olarak kaydetmeniz istenir.  
  
7.  ETW ve ServiceModel izlemeleri görüntülemek için hizmet izleme görüntüleyicisini içinde yeni oluşturulan .svclog dosyasını açın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
