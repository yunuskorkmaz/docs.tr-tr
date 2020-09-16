---
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 02668962afff5f760fc02692a92e72e765089545
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545586"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma
Bu örnek, Windows Communication Foundation (WCF) programı olarak uygulanan liste tabanlı yayımla-abone ol modelini gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Liste tabanlı yayımlama-abone ol tasarım deseni, Microsoft düzenleri & uygulamalar yayımı, [tümleştirme desenleri](/previous-versions/msp-n-p/ff647309(v=pandp.10))' nde açıklanmaktadır. Yayımla-abone ol, bilgileri bir bilgi konusuna abone olan bir alıcı koleksiyonuna geçirir. Liste tabanlı yayımlama-abone ol, abonelerin bir listesini tutar. Paylaşılacak bilgiler olduğunda, listedeki her aboneye bir kopya gönderilir. Bu örnek, istemcilerin abone olabileceği veya aboneliği kaldırmak için gerekli olan dinamik bir liste tabanlı yayımlama-abonelik modelini gösterir.  
  
 Liste tabanlı yayımlama-abone olma örneği bir istemciden, hizmetten ve bir veri kaynağı programından oluşur. Birden fazla istemci ve çalıştıran birden fazla veri kaynağı programı olabilir. İstemciler hizmete abone olur, bildirimler alabilir ve aboneliği kaldırın. Veri kaynağı programları, hizmete tüm geçerli aboneler ile paylaşılmak üzere bilgi gönderir.  
  
 Bu örnekte, istemci ve veri kaynağı konsol programlarıdır (. exe dosyaları) ve hizmet Internet Information Services (IIS) içinde barındırılan bir kitaplıktır (. dll). İstemci ve veri kaynağı etkinliği masaüstünde görülebilir.  
  
 Hizmet çift yönlü iletişimi kullanır. `ISampleContract`Hizmet sözleşmesi bir `ISampleClientCallback` geri çağırma sözleşmesiyle eşleştirilmiş. Hizmet, abone ve abonelik kaldırma hizmeti işlemlerini, istemcilerin abone listesini birleştirmek veya abone olmak için kullanır. Hizmet Ayrıca, `PublishPriceChange` veri kaynağı programının hizmeti yeni bilgi sağlamak üzere çağırdığı hizmet işlemini de uygular. İstemci programı `PriceChange` , hizmetin bir fiyat değişikliğinin tüm abonelerini bilgilendirmek için çağırdığı hizmet işlemini uygular.  
  
```csharp  
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
  
 Hizmet, tüm abonelere yeni bilgiler hakkında bilgilendirmek için mekanizma olarak bir .NET Framework olayı kullanır. Bir istemci, abone 'yı çağırarak hizmete katıldığında bir olay işleyicisi sağlar. İstemci ayrıldığında olay işleyicisinin aboneliğini olaydan kaldırır. Bir veri kaynağı bir fiyat değişikliğini raporlamak için hizmete çağrı yaptığı zaman, hizmet olayı başlatır. Bu, bir hizmetin her bir örneğini, abone olan her istemci için bir tane çağırır ve olay işleyicilerinin yürütülmesine neden olur. Her olay işleyicisi, geri çağırma işlevi aracılığıyla bilgileri istemcisine geçirir.  
  
```csharp
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
  
 Örneği çalıştırdığınızda birkaç istemciyi başlatın. İstemciler hizmete abone olur. Ardından, hizmete bilgi gönderen veri kaynağı programını çalıştırın. Hizmet, bilgileri tüm abonelere geçirir. Her istemci konsolunda, bilgilerin alındığını doğrulayan etkinlik görebilirsiniz. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Aşağıdaki adresi girerek bir tarayıcı kullanarak hizmete erişebilirsiniz: `http://localhost/servicemodelsamples/service.svc` . Yanıt olarak bir onay sayfası görüntülenmelidir.  
  
2. \ Client\bin \\ ' den dile özgü klasörden Client.exe çalıştırın. İstemci etkinliği istemci konsol penceresinde görüntülenir. Birkaç istemciyi başlatın.  
  
3. \ Datasource\bin \\ ' den dile özgü klasörden Datasource.exe çalıştırın. Veri kaynağı etkinliği konsol penceresinde görüntülenir. Veri kaynağı hizmete bilgi gönderdiğinde, her istemciye geçirilmesi gerekir.  
  
4. İstemci, veri kaynağı ve hizmet programları iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Örneği makineler arasında çalıştırmak için  
  
1. Hizmet makinesini ayarlama:  
  
    1. Hizmet makinesinde, ServiceModelSamples adlı bir sanal dizin oluşturun. [Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamından](one-time-setup-procedure-for-the-wcf-samples.md) toplu iş dosyası Setupvroot.bat disk dizini ve sanal dizin oluşturmak için kullanılabilir.  
  
    2. Hizmet programı dosyalarını%SystemDrive%\Inetpub\wwwroot\servicemodelsamples adresinden hizmet makinesindeki ServiceModelSamples sanal dizinine kopyalayın. Dosyaları \Bin dizinine dahil ettiğinizden emin olun.  
  
    3. Bir tarayıcı kullanarak hizmete istemci makineden erişebilme sınamasını yapın.  
  
2. İstemci makinelerini ayarlama:  
  
    1. İstemci program dosyalarını dile özgü klasör altındaki \client\bin\ klasöründen istemci makinelere kopyalayın.  
  
    2. Her istemci yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.  
  
3. Veri kaynağı makinesini ayarlama:  
  
    1. Veri kaynağı program dosyalarını dile özgü klasör altındaki \datasource\bin\ klasöründen veri kaynağı makinesine kopyalayın.  
  
    2. Veri kaynağı yapılandırma dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. "Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.  
  
4. İstemci makinelerde, bir komut isteminden Client.exe başlatın.  
  
5. Veri kaynağı makinesinde, bir komut isteminden Datasource.exe başlatın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`
