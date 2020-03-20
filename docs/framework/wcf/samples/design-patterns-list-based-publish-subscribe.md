---
title: 'Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 7342b3702338d5cd1fcc27d80e4e70cee019cc22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144766"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Tasarım Desenleri: Liste Tabanlı Yayımlama-Abone Olma
Bu örnek, Windows Communication Foundation (WCF) programı olarak uygulanan Liste tabanlı Yayımla-Abone oltasını göstermektedir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Liste tabanlı Yayımla-Abone Ol tasarım deseni, Microsoft Desenleri & Uygulamaları yayını, [Tümleştirme Desenleri'nde](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10))açıklanmıştır. Yayımla-Abone Ol deseni bilgileri bir bilgi konusuna abone olan alıcılar koleksiyonuna aktarıyor. Liste tabanlı publish-subscribe, abonelerin listesini tutar. Paylaşılaca bilgi olduğunda, listedeki her aboneye bir kopya gönderilir. Bu örnek, istemcilerin gerektiği sıklıkta abone olabileceği veya aboneliğini kaldırabileceği dinamik bir liste tabanlı yayımlama-abone olta sıcağı gösterir.  
  
 Liste tabanlı Yayımla-Abone Ol örneği bir istemci, bir hizmet ve bir veri kaynağı programından oluşur. Birden fazla istemci ve birden fazla veri kaynağı programı çalışıyor olabilir. İstemciler hizmete abone, bildirim alır ve aboneliğini iptal eder. Veri kaynağı programlar, mevcut tüm abonelerle paylaşılmak üzere hizmete bilgi gönderir.  
  
 Bu örnekte, istemci ve veri kaynağı konsol programlarıdır (.exe dosyaları) ve hizmet Internet Information Services (IIS) barındırılan bir kitaplıktır (.dll). İstemci ve veri kaynağı etkinliği masaüstünde görülebilir.  
  
 Hizmet çift yönlü iletişim kullanır. Hizmet `ISampleContract` sözleşmesi bir `ISampleClientCallback` geri arama sözleşmesiyle eşlenir. Hizmet, istemcilerin abone listesine katılmak veya abone listesini bırakmak için kullandıkları Abone Ol ve Aboneliği Kaldır hizmet işlemlerini uygular. Hizmet ayrıca, veri `PublishPriceChange` kaynağı programının hizmete yeni bilgiler sağlamak için çağırdığı hizmet işlemini de uygular. İstemci programı, `PriceChange` hizmetin tüm abonelere fiyat değişikliğini bildirmesini gerektirdiği hizmet işlemini uygular.  
  
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
  
 Hizmet, tüm aboneleri yeni bilgiler hakkında bilgilendirmek için bir .NET Framework olayı kullanır. Bir istemci Abone'yi arayarak hizmete katıldığında, bir olay işleyicisi sağlar. İstemci ayrıldığında, olay işleyicisinin aboneliğini olaydan iptal eder. Bir veri kaynağı hizmeti fiyat değişikliğini bildirmek için aradığında, hizmet olayı yükseltir. Bu, abone olan her istemci için bir hizmetin her örneğini çağırır ve olay işleyicilerinin yürütülmesine neden olur. Her olay işleyicisi, geri arama işlevi aracılığıyla bilgileri istemcisine iletir.  
  
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
  
 Örneği çalıştırdığınızda, birkaç istemci başlatın. Müşteriler hizmete abone dir. Ardından, hizmete bilgi gönderen veri kaynağı programını çalıştırın. Hizmet tüm abonelere bilgi aktarıyor. Her istemci konsolunda bilgilerin alındığını onaylayan etkinliği görebilirsiniz. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve oluşturmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Numuneyi aynı makinede çalıştırmak için  
  
1. Aşağıdaki adresi girerek bir tarayıcı kullanarak hizmete erişebileceğinizi test edin: `http://localhost/servicemodelsamples/service.svc`. Yanıt olarak bir onay sayfası görüntülenmelidir.  
  
2. İstemci.exe'yi dile\\özgü klasörün altından \client\bin'den çalıştırın. İstemci etkinliği istemci konsol penceresinde görüntülenir. Birkaç müşteri başlatın.  
  
3. Datasource.exe'yi dile özgü\\klasörün altından \datasource\bin'den çalıştırın. Veri kaynağı etkinliği konsol penceresinde görüntülenir. Veri kaynağı hizmete bilgi gönderdikten sonra, her istemciye aktarılmalıdır.  
  
4. İstemci, veri kaynağı ve hizmet programları iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-run-the-sample-across-machines"></a>Numuneyi makineler arasında çalıştırmak için  
  
1. Servis makinesini ayarlayın:  
  
    1. Servis makinesinde ServiceModelSamples adlı sanal bir dizin oluşturun. Windows Communication Foundation Samples için [Tek Seferlik Kurulum Yordamı'ndan](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) kurulum dosyası Setupvroot.bat disk dizini ve sanal dizini oluşturmak için kullanılabilir.  
  
    2. Hizmet programı dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples'ten serviceModelSamples sanal dizine kopyalayın. Dosyaları \bin dizinine eklediğinizden emin olun.  
  
    3. Bir tarayıcı kullanarak istemci makineden hizmete erişebileceğinizi test edin.  
  
2. İstemci makinelerini ayarlayın:  
  
    1. İstemci programı dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinelerine kopyalayın.  
  
    2. Her istemci yapılandırma dosyasında, hizmetinyeni adresiyle eşleşecek şekilde uç nokta tanımının adres değerini değiştirin. "Localhost" için yapılan başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.  
  
3. Veri kaynak makinesini ayarlama:  
  
    1. Veri kaynağı program dosyalarını dile özgü klasörün altındaki \datasource\bin\ klasöründen veri kaynağı makinesine kopyalayın.  
  
    2. Veri kaynağı yapılandırma dosyasında, hizmetinyeni adresiyle eşleşecek şekilde uç nokta tanımının adres değerini değiştirin. "Localhost" için yapılan başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.  
  
4. İstemci makinelerinde, Client.exe komut isteminden başlatın.  
  
5. Veri kaynağı makinesinde, Datasource.exe'yi komut isteminden başlatın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
