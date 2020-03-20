---
title: ETW İzleme
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183698"
---
# <a name="etw-tracing"></a>ETW İzleme
Bu örnek, Windows için Olay İzleme (ETW) `ETWTraceListener` ve bu örnekle sağlanan Ları kullanarak Uçlardan Uca (E2E) izlemenin nasıl uygulanacağını göstermektedir. Örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanmaktadır ve ETW izleme içerir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek, İzleme ve [İleti Günlüğe Kaydetme'ye](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)aşina olduğunuzu varsayar.  
  
 İzleme modelindeki <xref:System.Diagnostics> her izleme kaynağı, verilerin nerede ve nasıl izleyeceğini belirleyen birden çok izleme dinleyicisi olabilir. Dinleyici türü, izleme verilerinin günlüğe kaydedildiği biçimi tanımlar. Aşağıdaki kod örneği, dinleyicinin yapılandırmaya nasıl ekleyeceğini gösterir.  
  
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
  
 Bu dinleyiciyi kullanmadan önce bir ETW İzleme Oturumu başlatılmalıdır. Bu oturum Logman.exe veya Tracelog.exe kullanılarak başlatılabilir. Bir SetupETW.bat dosyası oturumu kapatmak ve günlük dosyasını tamamlamak için bir CleanupETW.bat dosyası ile birlikte ETW İzleme Oturumu ayarlayabilirsiniz, böylece bu örnek ile birlikte dahildir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır. Bu araçlar hakkında daha fazla bilgi için bkz.<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 ETWTraceListener kullanırken, izlemeler ikili .etl dosyalarında günlüğe kaydedilir. ServiceModel izleme açıkken, oluşturulan tüm izlemeler aynı dosyada görünür. .etl ve .svclog günlük dosyalarını görüntülemek için [Service Trace Viewer Aracı'nı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanın. Görüntüleyici, kaynağından hedefine ve tüketim noktasına kadar bir iletiyi izlemeyi mümkün kılan sistemin uçtan uca görünümünü oluşturur.  
  
 ETW Trace Listener dairesel günlüğe kaydetmeyi destekler. Bu özelliği etkinleştirmek için **Başlat,** `cmd` **Çalıştır'a** gidin ve komut konsolunu başlatmak için yazın. Aşağıdaki komutta, parametreyi `<logfilename>` günlük dosyanızın adı ile değiştirin.  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 Ve `-f` `-max` anahtarları isteğe bağlıdır. Onlar ikili dairesel biçim ve 1000MB sırasıyla maksimum günlük boyutunu belirtir. Geçiş, `-p` izleme sağlayıcısını belirtmek için kullanılır. Örneğimizde, `"{411a0819-c24b-428c-83e2-26b41091702e}"` "XML ETW Örnek Sağlayıcı" için GUID'dir.  
  
 Oturumu başlatmak için aşağıdaki komutu yazın.  
  
```console  
logman start Wcf  
```  
  
 Günlüğe kaydetmeyi bitirdikten sonra aşağıdaki komutla oturumu durdurabilirsiniz.  
  
```console  
logman stop Wcf  
```  
  
 Bu işlem, [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) veya Tracerpt dahil olmak üzere seçtiğiniz araçla işleyebileceğiniz ikili dairesel günlükler oluşturur.  
  
 Ayrıca dairesel günlük gerçekleştirmek için alternatif bir dinleyici hakkında daha fazla bilgi için [Dairesel İzleme](../../../../docs/framework/wcf/samples/circular-tracing.md) örneğini inceleyebilirsiniz.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinden emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
    > [!NOTE]
    > RegisterProvider.bat, SetupETW.bat ve CleanupETW.bat komutlarını kullanmak için yerel bir yönetici hesabı altında çalışmanız gerekir. Windows Vista veya daha sonra kullanıyorsanız, komut istemini yüksek ayrıcalıklarla da çalıştırmanız gerekir. Bunu yapmak için komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır'ı**tıklatın.  
  
3. Örneği çalıştırmadan önce, istemci ve sunucuda RegisterProvider.bat çalıştırın. Bu, Service Trace Viewer tarafından okunabilen izlemeler oluşturmak için ortaya çıkan ETWTracingSampleLog.etl dosyasını ayarlar. Bu dosya C:\logs klasöründe bulunabilir. Bu klasör yoksa, oluşturulmalı veya hiçbir iz oluşturulmamalıdır. Ardından, ETW İzleme Oturumu'nu başlatmak için istemci ve sunucu bilgisayarlarında SetupETW.bat çalıştırın. SetupETW.bat dosyası CS\Client klasörü altında bulunabilir.  
  
4. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
5. Örnek tamamlandığında, ETWTracingSampleLog.etl dosyasının oluşturulmasını tamamlamak için CleanupETW.bat'ı çalıştırın.  
  
6. ETWTracingSampleLog.etl dosyasını Service Trace Viewer içinden açın. İkili biçimlendirilmiş dosyayı .svclog dosyası olarak kaydetmeniz istenir.  
  
7. ETW ve ServiceModel izlerini görüntülemek için Service Trace Viewer içinden yeni oluşturulan .svclog dosyasını açın.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
