---
title: "Bir metin dosyası kullanarak izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1d4b3f319d86dd463dabc8b71be7c76c7fef41f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-using-a-text-file"></a>Bir metin dosyası kullanarak izleme
Bu örnek izlemede genişletmek gösterilmiştir [!INCLUDE[wf](../../../../includes/wf-md.md)] özel izleme katılımcı oluşturarak. İzleme katılımcıları yayılan gibi çalışma zamanını şuradan izleme kayıtları aldığınız .NET Framework sınıflarıdır. Hangi hedef senaryonuz için gerekli izleme olayları taşıma için bir izleme katılımcı oluşturabilirsiniz. Örneğin, (Windows için olay izleme) ETW İzleme katılımcı parçası olarak sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Bu örnekte izleme katılımcı kayıtları XML biçiminde bir metin dosyasına yazar.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 İzleme katılımcının sağlamlık ve yararlılığını iyileştirmek için bazı ek adımlar düzgün çalışma zamanına izleme katılımcı kablo tamamlanması gerekir. Aşağıdaki tabloda, en iyi yöntemlerle uyumlu bir izleme katılımcı oluşturmak için bu örnekte kullanılan sınıflar açıklanmaktadır.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> metin dosyası izleme katılımcı yapılandırmak için kullanılan yapılandırma bölümü tanımlamak için kullanılır. Bu, kullanıcıların standart .NET Framework yapılandırma dosyalarını kullanarak günlük dosyası hedef belirtmesine izin verir.|  
|`TextFileTrackingBehavior`|Davranışlarının [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanıcıların çalışma zamanına uzantıları eklemesine izin verin. Hizmet başlatıldığında bu davranış izleme katılımcı hizmete ekler.|  
|`TextFileTrackingParticipant`|Çalışma zamanında izleme katılımcıları alır ve bunları bir günlük dosyasına XML olarak depolayan izleme katılımcı.|  
  
## <a name="behavior-extension-elements-configuration"></a>Davranış uzantı öğeleri yapılandırması  
 Bir adım daha yapmak için gerekli .NET Framework yapılandırma dosyalarını kullanarak daha önce açıklanan davranış uzantı öğesinin kullanın. Aşağıdaki yapılandırma uzantısı kullanılacak olduğu yapılandırma dosyalarında yerleştirilmelidir.  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  Tam örnek kullanımı davranışı uzantı öğeleri yapılandırması için örnek Web.config dosyasına bakın.  
  
## <a name="custom-tracking-records"></a>Özel izleme kayıtları  
 GetStockPrices.cs dosya nasıl özel izleme kayıtları içinden oluşturulduğunu gösteren bir <xref:System.Activities.CodeActivity>. Bu kayıt için örnek çalıştırırken arayın.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WFStockPriceApplication.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
     Bir tarayıcı penceresi açar ve dizin için uygulama listesi gösterilir.  
  
4.  Tarayıcıda StockPriceService.xamlx'ı tıklatın.  
  
5.  Tarayıcı görüntüler **StockPriceService** sayfası, yerel hizmet wsdl adresini içerir. Bu adresini kopyalayın.  
  
     Yerel Hizmet wsdl adresi http://localhost:53797/StockPriceService.xamlx?wsdl örnektir.  
  
6.  Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]gidin, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (varsayılan yükleme klasörüdür %SystemDrive%\Program Files\Microsoft Visual Studio 10.0) klasör. Ardından Common7\IDE\ alt klasörü bulun.  
  
7.  WCF Test İstemcisi başlatmak için WcfTestClient.exe dosyasını çift tıklatın.  
  
8.  WCF Test İstemcisi seçin **Hizmet Ekle...** gelen **dosya** menüsü.  
  
9. Metin kutusuna kopyaladığınız URL'sini yapıştırın.  
  
10. Tıklatın **Tamam** iletişim kutusunu kapatmak için.  
  
11. WCF Test İstemcisi'ni kullanarak hizmetini sınayın.  
  
    1.  WCF Test istemcisi **GetStockPrice()** altında **IStockPriceService** düğümü.  
  
         **GetStockPrice()** yöntemi sağ bölmede, bir parametre ile görünür.  
  
    2.  Contoso'da parametresinin değeri olarak yazın.  
  
    3.  Tıklatın **çağırma**.  
  
12. İzlenen olayları, uygulama veri dizininde % APPDATA%\trackingRecords.log bulunan günlük dosyasına bakın.  
  
    > [!NOTE]
    >  % APPDATA % %SystemDrive%\Users için çözümleyen bir ortam değişkenidir\\< kullanıcı adı\>içinde \AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], veya Windows Server 2008.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
