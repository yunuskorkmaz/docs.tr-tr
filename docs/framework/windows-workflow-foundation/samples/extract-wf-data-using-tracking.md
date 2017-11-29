---
title: "WF izleme kullanarak veri ayıklamak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bbc9d72a55bd0affdccae9b735355c7e30c5d933
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="extract-wf-data-using-tracking"></a>WF izleme kullanarak veri ayıklamak
Bu örnek, iş akışı iş akışı değişkenleri ve bağımsız değişkenler etkinliklerden ayıklamak için izleme kullanımı gösterilmiştir. Ayrıca, kaydeder ve veri yükü özel izleme kayıtları içinde ayıklama izleme için ek açıklamalar eklenmesi gösterilmektedir. Örnek veri akışından ayıklamak için olay izleme için Windows (ETW) izleme katılımcı kullanır.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]bir iş akışı örneğini yürütmeyi görünürlük elde etmek için izleme sağlar. İzleme çalışma zamanı iş akışı iş akışı yürütme sırasında kayıtları izleme yayar. Kayıt iş akışı izleme yanı sıra, iş akışını iş akışı örneği verileri ayıklanabilir. Aşağıdaki listede kayıtları izleme ayıklanabilir veri türlerini Ayrıntılar verilmiştir:  
  
1.  Bir etkinlik ve etkinliği yürütülürken kayıtları izleme değişkenler iş akışı.  
  
     İş akışı değişkenleri ayıklamak için ayıklanacak değişkenleri, bir profilde belirtilir. Ayıklanacak değişkenleri yalnızca belirtilebilir ile `ActivityStateQueries`. Aşağıdaki kod örneğinde etkinliği iş akışı değişkeni çıkarmak için kullanılan bir izleme profili gösterilmektedir.  
  
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
  
2.  Etkinlik bağımsız değişkenleri ve kayıtları izleme etkinlik durumu.  
  
     Bağımsız değişkenleri tanımlayın yolu veri akışları içinde veya dışında bir etkinlik. Ayıklanacak bağımsız değişkenleri kullanılarak belirtilen bir <xref:System.Activities.Tracking.ActivityStateQuery>. Aşağıdaki kod örneğinde ayıklar bir izleme profilidir `Value` bağımsız değişkeni.  
  
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
  
3.  Ek açıklamalar yayılan tüm izleme kayıt eklenebilir anahtar/değer çiftleridir.  
  
     Ek açıklamalar kayıtları izleme için bir etiketleme mekanizması işlevini görür. Ek açıklamalar, bir izleme profili kayıtlarda izleme eklenir. Ek açıklama herhangi bir türde bir iş akışı izleme sorgu eklenebilir. Aşağıdaki kod örneğinde açıklamanın bir izleme kaydına nasıl eklenebileceğini gösteren bir izleme profilidir.  
  
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
  
4.  Özel izleme kayıtları kullanıcı tanımlı etkinliklerden gösterilen.  
  
     Özel kayıtları izleme, bu etkinlik içinde tanımlanan yükü veri taşıyabilir. İzleme profili özel izleme kayıtları için abone yükü izleme kaydı içinde ayıklama sağlar. Özel izleme kayıtları özel ayıklanabilir bir <xref:System.Activities.Tracking.TrackingQuery>. Aşağıdaki kod örneğinde özel izleme kaydı yük birlikte çıkaran bir izleme profilidir.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 Örnek bağımsız değişkenler, özel kaydeder ve bir Web.config dosyasında belirtilen bir profili kullanarak ekleme ek açıklamaları değişkenleri ayıklama gösterir. İzleme etkin örnek iş akışı hizmeti ekleyerek bir `<etwTracking>` davranışı öğesi. Aşağıdaki kod örnek etkinleştirir izleme `ExtractWorkflowVariables` profili izleme.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WFStockPriceApplication.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
     Bir tarayıcı penceresi açar ve dizin için uygulama listesi gösterilir.  
  
4.  Tarayıcıda StockPriceService.xamlx'ı tıklatın.  
  
5.  Tarayıcı yerel hizmet WSDL adresi içeren StockPriceService sayfa görüntüler. Bu adresini kopyalayın.  
  
     Aşağıdaki örnek, bir yerel hizmet WSDL adresi gösterir. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Hizmetini çağırmak önce Olay Görüntüleyicisi'ni başlatın ve iş akışı hizmetinden gösterilen olayları izlemek için olay günlüğüne dinlediğinden emin olun.  
  
7.  Gelen **Başlat** menüsünde, select **Yönetimsel Araçlar** ve ardından **Olay Görüntüleyicisi'ni**.  
  
8.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, ve **Microsoft**. Sağ **Microsoft** seçip **Görünüm** ve ardından **Analitik ve hata ayıklama günlüklerini göster**.  
  
     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.  
  
9. Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
10. Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test İstemcisi'ni açın.  
  
     WCF test istemcisi (WcfTestClient.exe) bulunan \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörü > \Common7\IDE\ klasör.  
  
     Varsayılan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörüdür C:\Program Files\Microsoft Visual Studio 10.0.  
  
11. WCF test istemcisi seçin **Hizmet Ekle** gelen **dosya** menüsü.  
  
     Yerel Hizmet giriş kutusuna daha önce kopyaladığınız WSDL adresi ekleyin.  
  
12. WCF test istemcisi `GetStockPrice`.  
  
     Bu açılır `GetStockPrice` yöntemi. İstek bir parametre kabul eder. Değeri kullanmak **Contoso**.  
  
13. Tıklatın **çağırma**.  
  
14. Olay Görüntüleyici'ye geçiş yapın ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**. Sağ **analitik** seçip **yenileme**. İş akışı olayları olay kimliği 100-199 aralıktır.  
  
     Olayları içeren ek açıklamalar, değişkenleri, bağımsız değişkenler ve olabilir özel izleme kayıtları Olay Görüntüleyicisi'ni görüntülenebilir.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Olay Görüntüleyicisi'ni temizleme  
 Analitik kanal olay günlüğündeki Olay Görüntüleyicisi'ni aşağıdakileri yaparak temizlenebilir.  
  
#### <a name="to-clean-up-optional"></a>(İsteğe bağlı) temizlemek için  
  
1.  Olay Görüntüleyicisi'ni açın.  
  
2.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **günlüğü devre dışı**.  
  
3.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**. Sağ **analitik** seçip **Günlüğü Temizle**.  
  
     Seçin **temizleyin** olayları temizlemek için seçeneği.  
  
## <a name="known-issue"></a>Bilinen bir sorun  
  
> [!NOTE]
>  Olay burada ETW olayları çözecek başlatılamayabilir Görüntüleyicisi'nde bilinen bir sorun yoktur. Aşağıdakine benzer bir hata iletisi görebilirsiniz.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Bu hatayla karşılaşırsanız, tıklatın **yenileme** Eylemler bölmesinde. Olay şimdi düzgün bir şekilde kod çözme.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
