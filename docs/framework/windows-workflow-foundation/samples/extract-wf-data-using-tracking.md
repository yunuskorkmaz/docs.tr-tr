---
title: İzleme kullanarak WF verilerini ayıklama
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: ef8118df2c5834e32c40760ef31f75660893d89b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501589"
---
# <a name="extract-wf-data-using-tracking"></a>İzleme kullanarak WF verilerini ayıklama
Bu örnek, iş akışı değişkenleri ve bağımsız değişkenler etkinlikten ayıklamak için izleme iş akışını nasıl kullanacağınızı gösterir. Ayrıca, izleme kayıtları ve özel izleme kayıtları içinde veri yükü ayıklanması için ek açıklamalar eklenmesi gösterir. Örnek olay izleme için Windows (ETW) izleme katılımcı akışından verileri ayıklamak için kullanır.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Windows Workflow Foundation (WF) iş akışı örneğinin yürütme görünürlük elde etmek için izleme sağlar. İzleme çalışma zamanı iş akışı iş akışı yürütülürken kayıtları izleme yayar. Kayıtları izleme iş akışını yanı sıra, iş akışı örneği içinde veri akışından ayıklanabilir. Aşağıdaki liste kayıtları izleme alanından ayıklanması gereken veri türlerini ayrıntıları:  
  
1.  Bir etkinlik ve Etkinlik yürütme sırasında kayıtları izleme değişkenler iş akışı.  
  
     İş akışı değişkenlerini ayıklamak için bir profilde ayıklanacak değişkenleri belirtilir. Ayıklanacak değişkenleri yalnızca belirtilebilir `ActivityStateQueries`. Aşağıdaki kod örneği, etkinliği iş akışı değişkeni çıkarmak için kullanılan bir izleme profili gösterir.  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  Etkinlik bağımsız değişkenleri ve etkinlik durumu kayıtları izleme.  
  
     Bağımsız değişkenleri tanımlayın şekilde veri akışları içinde veya dışında bir etkinlik. Ayıklanacak bağımsız değişkenleri kullanılarak belirtilen bir <xref:System.Activities.Tracking.ActivityStateQuery>. Aşağıdaki kod örneği ayıklar bir izleme profili olan `Value` bağımsız değişken.  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  Ek açıklamalar yayıldığını herhangi bir izleme kaydını eklenebilir, anahtar/değer çiftleridir.  
  
     Ek açıklamalar, kayıtları izleme için bir etiketleme mekanizması görevi görür. Bir izleme profili aracılığıyla kayıtları izleme için ek açıklamalar eklenir. Herhangi bir iş akışı izleme sorgu türü için ek açıklamalar eklenebilir. Aşağıdaki kod örneği bir ek açıklama bir izleme kaydını için nasıl eklenebilir gösteren bir izleme profilidir.  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  Kullanıcı tanımlı etkinlikten özel izleme kayıtları yayılan.  
  
     Bu etkinlik içinde tanımlanan yük verisi kayıtları izleme özel gerçekleştirebilirsiniz. Bir izleme profili özel izleme kayıtları için abone ayıklama akıştaki yükün bir izleme kaydını sağlar. Özel ile özel izleme kayıt ayıklanabileceği bir <xref:System.Activities.Tracking.TrackingQuery>. Aşağıdaki kod örneğinde yük birlikte bir özel izleme kayıt ayıklayan bir izleme profilidir.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 Örnek, bir değişken, bağımsız değişkenler ve özel kayıtları Web.config dosyasında belirtilen bir profili kullanılarak ekleyerek ek açıklamaları ayıklama gösterir. İzleme etkin örnek iş akışı hizmeti ekleyerek bir `<etwTracking>` davranış öğesi. Aşağıdaki kod örneği etkinleştirir izleme `ExtractWorkflowVariables` izleme profili.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WFStockPriceApplication.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
     Tarayıcı penceresi açılır ve dizin için uygulama listesi gösterilir.  
  
4.  Tarayıcıda StockPriceService.xamlx tıklayın.  
  
5.  Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfası görüntüler. Bu adresini kopyalayın.  
  
     Aşağıdaki örnek, bir yerel hizmet WSDL adresi gösterir. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Hizmetini çağırmak önce Olay Görüntüleyicisi'ni başlatın ve iş akışı hizmetinden yayılan olayları izlemek için olay günlüğüne dinlediğinden emin olun.  
  
7.  Gelen **Başlat** menüsünde **Yönetimsel Araçlar** ardından **Olay Görüntüleyicisi'ni**.  
  
8.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, ve **Microsoft**. Sağ **Microsoft** seçip **görünümü** ardından **Analitik ve hata ayıklama günlüklerini göster**.  
  
     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.  
  
9. Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama uygulamalarının**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
10. Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test İstemcisi'ni açın.  
  
     WCF test istemcisi (WcfTestClient.exe) bulunan \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörü > \Common7\IDE\ klasör.  
  
     Varsayılan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörü C:\Program Files\Microsoft Visual Studio 10.0 bulunmaktadır.  
  
11. WCF test İstemcisi'nde seçin **Hizmet Ekle** gelen **dosya** menüsü.  
  
     Yerel Hizmet giriş kutusuna daha önce kopyaladığınız WSDL adresi ekleyin.  
  
12. WCF test İstemcisi'nde çift `GetStockPrice`.  
  
     Bu açılır `GetStockPrice` yöntemi. İstek, bir parametre kabul eder. Değeri kullanın **Contoso**.  
  
13. Tıklayın **çağırma**.  
  
14. Olay Görüntüleyicisi'ne geçin ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama uygulamalarının**. Sağ **analitik** seçip **Yenile**. İş akışı olayları olay kimliği 100 199 aralıktır.  
  
     Olabilir özel izleme kayıtları Olay Görüntüleyicisi'görüntülemesini ve olayları, ek açıklamalar, değişkenleri, bağımsız değişkenler içerir.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Olay Görüntüleyicisi'ni temizleniyor  
 Analitik kanal olay günlüğündeki Olay Görüntüleyicisi aşağıdakileri yaparak temizlenmesi.  
  
#### <a name="to-clean-up-optional"></a>(İsteğe bağlı) temizlemek için  
  
1.  Olay Görüntüleyicisi'ni açın.  
  
2.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **devre dışı günlük**.  
  
3.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **Günlüğü Temizle**.  
  
     Seçin **Temizle** olayları silmek için seçeneği.  
  
## <a name="known-issue"></a>Bilinen sorun  
  
> [!NOTE]
>  Burada ETW olaylarının kodunu çözmek için çalışmayabilir Olay Görüntüleyicisi'nde bilinen bir sorun yoktur. Aşağıdakine benzer bir hata iletisi görebilirsiniz.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Bu hatayla karşılaşırsanız, tıklayın **Yenile** Eylemler bölmesinde. Olay artık düzgün bir şekilde kod çözme.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
