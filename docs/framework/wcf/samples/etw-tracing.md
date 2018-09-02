---
title: ETW İzleme
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 3e4dd141bd5f6a9d137b2fe981b3b412ec0c81e2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407173"
---
# <a name="etw-tracing"></a>ETW İzleme
Bu örnek olay izleme için Windows (ETW) kullanarak uçtan uca (E2E) izleme uygulamak nasıl gösterir ve `ETWTraceListener` Bu örnek ile sağlanır. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve ETW İzleme içerir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
 Bu örnek, aşina olduğunuzu varsayar [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Her izleme kaynakta <xref:System.Diagnostics> izleme modeli, verilerin nerede ve nasıl izleneceğini belirlemek birden çok izleme dinleyicileri sahip olabilir. Dinleyici türü izleme verilerinin oturum açmış biçimini tanımlar. Aşağıdaki kod örneği, yapılandırmaya dinleyiciyi ekleyin gösterilmektedir.  
  
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
  
 Bu dinleyicisi kullanmadan önce bir ETW izleme oturumunu başlatılması gerekir. Bu oturumda Logman.exe veya Tracelog.exe kullanılarak başlatılabilir. Oturum kapatma ve günlük dosyası tamamlamak için bir CleanupETW.bat dosyasıyla birlikte ETW izleme oturumunu ayarlayabilirsiniz böylece bu örnekle SetupETW.bat dosya dahildir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır. Bu araçlar hakkında daha fazla bilgi için bkz. [https://go.microsoft.com/fwlink/?LinkId=56580](https://go.microsoft.com/fwlink/?LinkId=56580)  
  
 ETWTraceListener kullanırken, izlemeleri ikili .etl dosyaları günlüğe kaydedilir. Açık ServiceModel izleme ile oluşturulan tüm izlemeleri aynı dosyada görünür. Kullanım [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .etl ve .svclog günlük dosyalarını görüntülemek için. Görüntüleyici, bir ileti hedefine kaynağından izlemenizi olanaklı kılan sistem bir uçtan uca görünümünü ve tüketim noktası oluşturur.  
  
 ETW İzleme dinleyicisi döngüsel günlüğü destekler. Bu özelliği etkinleştirmek için Git **Başlat**, **çalıştırmak** ve türü `cmd` komut konsolunu başlatın. Aşağıdaki komutta `<logfilename>` parametresi, günlük dosyasının adı.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` Ve `-max` anahtarları isteğe bağlı. Bunlar en büyük günlük boyutunu 1000 MB ve döngüsel ikili biçimi sırasıyla belirtin. `-p` Anahtar izleme sağlayıcısı belirtmek için kullanılır. Bizim örneğimizde `"{411a0819-c24b-428c-83e2-26b41091702e}"` "XML ETW örnek sağlayıcısı için" GUID'dir.  
  
 Oturumu başlatmak için aşağıdaki komutu yazın.  
  
```  
Logman start Wcf  
```  
  
 Günlük kaydı tamamladıktan sonra aşağıdaki komutla oturum durdurabilirsiniz.  
  
```  
Logman stop Wcf  
```  
  
 Bu işlem, aracınızla ettiğiniz işleyebilen ikili döngüsel günlükleri oluşturan dahil olmak üzere [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) veya Tracerpt.  
  
 Ayrıca inceleyebilirsiniz [döngüsel izleme](../../../../docs/framework/wcf/samples/circular-tracing.md) döngüsel günlük gerçekleştirmek için alternatif bir dinleyici hakkında daha fazla bilgi için örnek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  RegisterProvider.bat ve SetupETW.bat CleanupETW.bat komutları kullanmak için bir yerel yönetici hesabı altında çalıştırmanız gerekir. Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)] veya daha sonra ayrıca komut isteminde yükseltilmiş ayrıcalıklarla çalıştırmanız gerekir. Bunu yapmak için komut istemi simgesini sağ tıklatın ve ardından **yönetici olarak çalıştır**.  
  
3.  RegisterProvider.bat, örneği çalıştırmadan önce istemci ve sunucu üzerinde çalıştırın. Bu, hizmet izleme görüntüleyicisini tarafından okunabilecek izlemeler üretmek için sonuçta elde edilen ETWTracingSampleLog.etl dosyasını ayarlar. Bu dosya C:\logs klasöründe bulunabilir. Bu klasör mevcut değilse oluşturulması gerekir veya izleme yok üretilir. Ardından SetupETW.bat ETW izleme oturumunu başlatmak için istemci ve sunucu bilgisayarları üzerinde çalıştırın. SetupETW.bat dosyası CS\Client klasörü altında bulunabilir.  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Örnek tamamlandığında CleanupETW.bat ETWTracingSampleLog.etl dosyası oluşturmayı tamamlamak için çalıştırın.  
  
6.  Hizmet izleme görüntüleyicisini içinde ETWTracingSampleLog.etl dosyasından açın. Biçimlendirilmiş bir ikili dosyası .svclog dosyası olarak kaydetmek için istenir.  
  
7.  ETW ve ServiceModel işlemlerini izlemeleri görüntülemek için hizmet izleme görüntüleyicisini içinde yeni oluşturulan .svclog dosyasını açın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
