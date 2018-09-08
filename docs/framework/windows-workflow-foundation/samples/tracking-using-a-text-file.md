---
title: Bir metin dosyası kullanarak izleme
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191293"
---
# <a name="tracking-using-a-text-file"></a>Bir metin dosyası kullanarak izleme
Bu örnek bir özel izleme katılımcı oluşturarak izleme Windows Workflow Foundation (WF) gösterilmektedir. İzleme katılımcıları yayılan gibi çalışma zamanını şuradan izleme kayıtları bildiren .NET Framework sınıflardır. Hangi hedef senaryonuz için gerekli izleme olayları taşımak için izleme katılımcı oluşturabilirsiniz. Örneğin, (olay izleme için Windows) ETW İzleme katılımcı bir parçası olarak sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Bu örnekte izleme katılımcı kayıtları XML biçiminde bir metin dosyasına yazar.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 İzleme katılımcı'ların sağlamlığını ve yararlılığını en iyi duruma getirmek için bazı ek adımlar izleme katılımcı çalışma zamanının düzgün kablo tamamlanmış olması gerekir. Bu örnekte, en iyi yöntemleriyle uyumlu bir izleme katılımcı oluşturmak için kullanılan sınıfları aşağıdaki tabloda açıklanmaktadır.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> metin dosyası izleme katılımcı yapılandırmak için kullanılan yapılandırma bölümü tanımlamak için kullanılır. Bu, kullanıcıların standart .NET Framework yapılandırma dosyalarını kullanarak günlük dosyasının hedef belirtmesine izin verir.|  
|`TextFileTrackingBehavior`|WCF davranışları, kullanıcıların çalışma zamanına uzantıları eklemesine izin verin. Hizmet başlatıldığında bu davranışı için hizmet izleme katılımcı ekler.|  
|`TextFileTrackingParticipant`|Çalışma zamanında izleme katılımcıları alır ve bunları bir günlük dosyasına XML olarak depolayan izleme katılımcı.|  
  
## <a name="behavior-extension-elements-configuration"></a>Davranış uzantı öğeleri yapılandırması  
 Bir adım daha hale getirmeniz için gereken .NET Framework yapılandırma dosyalarını kullanarak daha önce açıklanan davranışı uzantı öğesi kullanın. Aşağıdaki yapılandırmayı uzantısı kullanılacak olduğu yapılandırma dosyalarında yerleştirilmelidir.  
  
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
 GetStockPrices.cs dosyası içinden özel izleme kayıtları oluşturma işlemini gösterir bir <xref:System.Activities.CodeActivity>. Bu kayıt için örnek çalıştırırken arayın.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WFStockPriceApplication.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
     Tarayıcı penceresi açılır ve dizin için uygulama listesi gösterilir.  
  
4.  Tarayıcıda StockPriceService.xamlx tıklayın.  
  
5.  Tarayıcı görüntüler **StockPriceService** sayfası, yerel hizmet wsdl adresini içerir. Bu adresini kopyalayın.  
  
     Yerel Hizmet wsdl adresi örneğidir http://localhost:53797/StockPriceService.xamlx?wsdl.  
  
6.  Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]gidin, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (varsayılan yükleme klasörünü %SystemDrive%\Program Files\Microsoft Visual Studio 10.0) klasörü. Ardından Common7\IDE\ alt klasörü bulun.  
  
7.  WCF Test İstemcisi'ni başlatmak için WcfTestClient.exe dosyasına çift tıklayın.  
  
8.  WCF Test İstemcisi'nde seçin **Hizmet Ekle...** gelen **dosya** menüsü.  
  
9. Metin kutusuna kopyaladığınız URL'yi yapıştırın.  
  
10. Tıklayın **Tamam** iletişim kutusunu kapatmak için.  
  
11. WCF Test İstemcisi'ı kullanarak hizmeti test edin.  
  
    1.  WCF Test İstemcisi'nde çift **GetStockPrice()** altında **IStockPriceService** düğümü.  
  
         **GetStockPrice()** sağ bölmede, bir parametre içeren yöntemi görünür.  
  
    2.  Contoso ağında parametresinin değeri olarak yazın.  
  
    3.  Tıklayın **çağırma**.  
  
12. İzlenen olayları % APPDATA%\trackingRecords.log uygulama veri dizininde bulunan günlük dosyasına bakın.  
  
    > [!NOTE]
    >  % APPDATA % %SystemDrive%\Users için gideren bir ortam değişkenidir\\< kullanıcı adı\>içinde \AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], veya Windows Server 2008.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
