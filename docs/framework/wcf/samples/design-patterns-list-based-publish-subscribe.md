---
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a4f36c7231146811e4eb033cfb6a3433a58dbb2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma
Bu örnek olarak uygulanan liste tabanlı yayımlama-abone olma deseni gösterilmektedir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Liste tabanlı yayımlama-abone olma tasarım deseni Microsoft Patterns & yöntemler yayında açıklanan [tümleştirme desenleri](http://go.microsoft.com/fwlink/?LinkId=95894). Yayımla-abone olma deseni bir bilgi konuya abone olduğunuz alıcıları koleksiyonu bilgilerini geçirir. Liste tabanlı yayımlama-abone olma aboneleri listesini tutar. Bilgi paylaşmak için olduğunda bir kopyasını listedeki her abone gönderilir. Bu örnek dinamik bir listeye bağlı gösterir, istemcilerin abone veya gerekli sıklıkta aboneliği düzeni yayımlama-abonelik.  
  
 Liste tabanlı yayımlama-abone olma örnek, bir istemci, hizmet ve bir veri kaynağı programı oluşur. Birden fazla istemci ve çalışan birden fazla veri kaynağı program olabilir. İstemcileri hizmete abone olmak için bildirim almak ve aboneliği. Veri kaynağı programları ile tüm geçerli aboneleri paylaşılmak üzere hizmet bilgi gönderin.  
  
 Bu örnek, istemci ve veri kaynağındaki konsol program (.exe dosyaları) ve hizmet Internet Information Services (IIS) barındırılan bir kitaplık (.dll). İstemci ve veri kaynağı etkinlik masaüstünde görünür.  
  
 Hizmet, çift yönlü iletişimi kullanır. `ISampleContract` Hizmet sözleşmesini eşleştirilmiş ile bir `ISampleClientCallback` geri çağırma sözleşme. Hizmet katılma veya aboneleri listesi ayrılma hangi istemcilerin kullanmak abone ve aboneliği kaldırma hizmet işlemleri uygular. Ayrıca hizmeti uygulayan `PublishPriceChange` yeni bilgilerle hizmet sağlamak için veri kaynağı programı çağırır hizmet işlemi. İstemci programı uygulayan `PriceChange` fiyat değişikliği tüm aboneleri bildirmek için hizmet çağrıları hizmet işlemi.  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 Hizmet .NET Framework olay ilgili yeni bilgiler tüm aboneleri bildirmek için mekanizma olarak kullanır. Bir istemci hizmeti çağıran abone tarafından katıldığında, olay işleyicisi sağlar. Bir istemci ayrıldığında, olay işleyici olaydan aboneliğini kaldırır. Bir veri kaynağı bir fiyat değişikliği bildirmek için hizmet çağırdığında hizmet olayını başlatır. Bu hizmet bir abone ve bunların olay işleyicileri yürütülecek neden olan her istemci için her bir örneği çağırır. Her olay işleyicisi bilgileri kendi geri çağırma işlevini istemciye geçirir.  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 Örneği çalıştırdığınızda, çeşitli istemciler başlatın. İstemcilerin hizmetine abone olun. Ardından bilgi hizmetine gönderir veri kaynağı programını çalıştırın. Hizmeti hakkında bilgi için tüm aboneleri geçirir. Her istemci konsol bilgileri alındı onaylayan üzerinde etkinlik görebilirsiniz. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aynı makinede örneği çalıştırmak için  
  
1.  Test hizmeti aşağıdaki adresini girerek bir tarayıcı kullanarak erişebilirsiniz: http://localhost/servicemodelsamples/service.svc. Bir onay sayfasına yanıtta görüntülenmesi gerekir.  
  
2.  \Client\bin Client.exe çalıştırmak\\, dile özgü klasörü altında. İstemci etkinliği istemci konsol penceresi görüntülenir. Çeşitli istemciler başlatın.  
  
3.  \Datasource\bin DataSource.exe çalıştırmak\\, dile özgü klasörü altında. Veri kaynağı etkinliği konsol penceresi görüntülenir. Veri kaynağı bilgileri hizmetine gönderir. sonra her bir istemciye geçirilmelidir.  
  
4.  İstemci, veri kaynağı ve hizmet programlarını iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Makine genelinde örneği çalıştırmak için  
  
1.  Hizmet Makine'yi ayarlayın:  
  
    1.  Hizmeti makinede ServiceModelSamples adlı bir sanal dizin oluşturun. Toplu iş dosyası gelen Setupvroot.bat [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) disk dizini ve sanal dizini oluşturmak için kullanılabilir.  
  
    2.  Hizmet program dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti makinede ServiceModelSamples sanal dizine kopyalayın. Dosyaları \bin dizinine eklediğinizden emin olun.  
  
    3.  Test, hizmet bir tarayıcı kullanarak istemci makineden erişebilirsiniz.  
  
2.  İstemci makineleri ayarlayın:  
  
    1.  İstemci makinelerine dile özgü klasörü altındaki \client\bin\ klasöründen istemci program dosyaları kopyalayın.  
  
    2.  Her istemci yapılandırma dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin. Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.  
  
3.  Veri kaynağı Makine'yi ayarlayın:  
  
    1.  Veri kaynağı program dosyaları \datasource\bin\ klasöründen dile özgü klasörü altında veri kaynak makineye kopyalayın.  
  
    2.  Veri kaynağı yapılandırma dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin. Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.  
  
4.  İstemci bilgisayarlarında Client.exe bir komut isteminden başlatın.  
  
5.  Verileri kaynak makinede bir komut isteminden Datasource.exe başlatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a>Ayrıca Bkz.
