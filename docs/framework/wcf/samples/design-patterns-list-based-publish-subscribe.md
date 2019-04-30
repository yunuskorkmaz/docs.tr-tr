---
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: e98fab5c8e7570917a4ba755fa372832fe0b26b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773067"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma
Bu örnek, bir Windows Communication Foundation (WCF) programı olarak uygulanan liste tabanlı yayımlama-abone olma deseni gösterilmektedir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Microsoft Patterns ve uygulamalar yayında liste tabanlı yayımlama-abone olma tasarım deseni açıklanan [tümleştirme desenleri](https://go.microsoft.com/fwlink/?LinkId=95894). Yayımlama-abone olma deseni bir koleksiyon bir bilgi konuya abone olduğunuz alıcıların bilgi geçirir. Liste tabanlı yayımlama-abone ol aboneleri listesini tutar. Bilgi paylaşmak için olduğunda, bir kopyasını listedeki her aboneye gönderilir. Bu örnek, dinamik bir liste tabanlı gösterir. burada istemciler abone olmak veya abonelikten gerektiği sıklıkta desen, yayımlama-abonelik.  
  
 Liste tabanlı yayımlama-abone olma örnek, bir istemci, hizmet ve veri kaynağı program oluşur. Birden fazla istemci ve çalışan birden fazla veri kaynağı program olabilir. İstemciler hizmete abone, bildirimleri alabilir ve aboneliği. Veri kaynağı programları tüm geçerli abonelerle paylaşılan hizmet bilgi gönderin.  
  
 Bu örnek, istemci ve veri kaynağını programlar (.exe dosyaları) ve hizmet Internet Information Services (IIS) barındırılan bir kitaplık (.dll). İstemci ve veri kaynağı etkinliği masaüstünde görünür.  
  
 Hizmet, çift yönlü iletişimi kullanır. `ISampleContract` Hizmet sözleşmesini eşleştirilmiştir ile bir `ISampleClientCallback` geri çağırma anlaşması. Hizmet, katılma veya aboneleri listesinin bırakın hangi istemcilerin kullanın, abone ve aboneliği kaldırma hizmet işlemleri uygular. Ayrıca hizmeti uygulayan `PublishPriceChange` hizmet yeni bilgiler sağlamak için veri kaynağı program çağıran hizmet işlemi. İstemci programı uygulayan `PriceChange` tüm aboneler bir fiyat değişikliği bildirmek için hizmeti çağıran hizmet işlemi.  
  
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
  
 Hizmet .NET Framework olayı ile ilgili yeni bilgiler tüm aboneler bildirmek için mekanizması olarak kullanır. Bir istemci hizmeti çağıran abone tarafından katıldığında, bir olay işleyicisi sağlar. İstemci çıktığında, olay işleyicisi olay aboneliğini kaldırır. Bir veri kaynağı bir fiyat değişikliği bildirmek için hizmet çağırdığında, hizmet olayını başlatır. Bu, hizmetin bir abone ve yürütülecek olay işleyicilerini neden her istemci için her örneği çağırır. Her bir olay işleyicisi, geri çağırma işlevi aracılığıyla kendi istemci bilgileri geçirir.  
  
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
  
 Örneği çalıştırdığında, çeşitli istemciler başlatın. İstemciler hizmete abone olun. Ardından bilgi hizmetine gönderir. veri kaynağı programı çalıştırın. Hizmet bilgileri tüm abonelerine geçirir. Her istemci konsol bilgi alındı onaylayan üzerinde etkinliği görebilirsiniz. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Test hizmeti aşağıdaki adresi girerek bir tarayıcı kullanarak erişebilirsiniz: `http://localhost/servicemodelsamples/service.svc`. Yanıtta bir onay sayfası gösterilmelidir.  
  
2. \Client\bin Client.exe çalıştırma\\, dile özgü klasörü altında. İstemci etkinliği istemci konsol penceresinde görüntülenir. Çeşitli istemciler başlatın.  
  
3. \Datasource\bin DataSource.exe çalıştırma\\, dile özgü klasörü altında. Veri kaynak etkinliği konsol penceresinde görüntülenir. Veri kaynağı bilgilerini hizmetine gönderir. sonra her bir istemciye geçirilmelidir.  
  
4. İstemci, veri kaynağı ve hizmet programlarını iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Makineler arasında örneği çalıştırmak için  
  
1. Hizmet Makine'yi ayarlayın:  
  
    1. Hizmeti makinede ServiceModelSamples adlı sanal bir dizin oluşturun. Toplu iş dosyası Setupvroot.bat gelen [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) disk dizini ve sanal dizin oluşturmak için kullanılabilir.  
  
    2. Hizmet program dosyaları %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti makinede ServiceModelSamples sanal dizinine kopyalayın. \Bin dizinine dosyaları eklemeyi unutmayın.  
  
    3. Test bir tarayıcı kullanarak istemci makine hizmete erişebilir.  
  
2. İstemci makineleri ayarlama:  
  
    1. İstemci makineler için dile özgü klasörü altında \client\bin\ klasöründen istemci program dosyaları kopyalayın.  
  
    2. Her istemci yapılandırma dosyasında adresi uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.  
  
3. Veri kaynağı Makine'yi ayarlayın:  
  
    1. Veri kaynak makineye \datasource\bin\ klasöründen dile özgü klasörü altında veri kaynağı program dosyaları kopyalayın.  
  
    2. Veri kaynağı yapılandırma dosyasında adresi uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.  
  
4. İstemci makinelerinde Client.exe bir komut istemi'nden başlatın.  
  
5. Veri kaynak makinede Datasource.exe bir komut istemi'nden başlatın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
