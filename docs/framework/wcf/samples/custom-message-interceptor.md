---
title: Özel İleti Kesici
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145092"
---
# <a name="custom-message-interceptor"></a>Özel İleti Kesici
Bu örnek kanal genişletilebilirlik modelinin kullanımını göstermektedir. Özellikle, çalışma zamanı yığınının belirli bir noktasında gelen ve giden tüm iletileri engellemek için kanal fabrikaları ve kanal dinleyicileri oluşturan özel bir bağlama öğesinin nasıl uygulanacağını gösterir. Örnek, bu özel fabrikaların kullanımını gösteren bir istemci ve sunucu da içerir.  
  
 Bu örnekte, hem istemci hem de hizmet konsol programlarıdır (.exe). İstemci ve hizmet, özel bağlama öğesini ve ilişkili çalışma zamanı nesnelerini içeren ortak bir kitaplığı (.dll) kullanır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Örnek, kanal çerçevesini kullanarak ve WCF en iyi uygulamalarını izleyerek Windows Communication Foundation'da (WCF) özel katmanlı bir kanal oluşturmak için önerilen yordamı açıklar. Özel katmanlı kanal oluşturma adımları aşağıdaki gibidir:  
  
1. Kanal şekillerinin hangisinin kanal fabrikanıza ve kanal dinleyicisinin destekleyeceğine karar verin.  
  
2. Kanal şekillerinizi destekleyen bir kanal fabrikası ve kanal dinleyicisi oluşturun.  
  
3. Özel katmanlı kanalı kanal yığınına ekleyen bağlayıcı bir öğe ekleyin.  
  
4. Yapılandırma sistemine yeni bağlama öğesi ortaya çıkarmak için bağlayıcı öğe uzantısı bölümü ekleyin.  
  
## <a name="channel-shapes"></a>Kanal Şekilleri  
 Özel katmanlı bir kanal yazmanın ilk adımı, kanal için hangi şekillerin gerekli olduğuna karar vermektir. İleti denetçimiz için, altımızdaki katmanın desteklediği herhangi bir şekli destekliyoruz <xref:System.ServiceModel.Channels.IOutputChannel> (örneğin, altımızdaki katman oluşturabilir ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>sonra biz de ortaya çıkarız). <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
## <a name="channel-factory-and-listener-factory"></a>Kanal Fabrikası ve Dinleyici Fabrikası  
 Özel katmanlı kanal yazmanın bir sonraki adımı, <xref:System.ServiceModel.Channels.IChannelFactory> istemci kanalları ve <xref:System.ServiceModel.Channels.IChannelListener> servis kanalları için bir uygulama oluşturmaktır.  
  
 Bu sınıflar bir iç fabrika ve dinleyici almak `OnCreateChannel` `OnAcceptChannel` ve tüm ama ve iç fabrika ve dinleyici çağırır delege.  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a>Bağlama Öğesi Ekleme  
 Örnek özel bir bağlama öğesi `InterceptingBindingElement`tanımlar: . `InterceptingBindingElement`bir `ChannelMessageInterceptor` girdi olarak alır ve `ChannelMessageInterceptor` içinden geçen iletileri işlemek için bunu kullanır. Halka açık olması gereken tek sınıf bu. Fabrika, dinleyici ve kanalların tümü, genel çalışma zamanı arabirimlerinin dahili uygulamaları olabilir.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Yapılandırma Desteği Ekleme  
 Bağlama yapılandırmasıyla tümleştirmek için kitaplık, yapılandırma kesiti işleyicisini bağlayıcı öğe uzantısı bölümü olarak tanımlar. İstemci ve sunucu yapılandırma dosyaları bağlayıcı öğe uzantısını yapılandırma sistemine kaydetmelidir. Bağlama öğelerini yapılandırma sistemine maruz bırakmak isteyen uygulayıcılar bu sınıftan türetilebilir.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a>İlke Ekleme  
 Politika sistemimizle entegre `InterceptingBindingElement` olmak için, iPolicyExportExtension'ı uygulayarak politika oluşturmaya katılmamız gerektiğini niçin işaret edeceğiz. Oluşturulan istemcide alma ilkesini desteklemek için, kullanıcı ilke `InterceptingBindingElementImporter` etkin `CreateMessageInterceptor` `ChannelMessageInterceptor` sınıfını oluşturmak için türetilmiş bir sınıf kaydedebilir ve geçersiz kılınabilir ()  
  
## <a name="example-droppable-message-inspector"></a>Örnek: Droppable İleti Denetçisi  
 Örnekte, iletilerin düştüğü bir `ChannelMessageInspector` örnek uygulama da yer alıyor.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Yapılandırmadan aşağıdaki gibi erişebilirsiniz:  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 İstemci ve sunucu, özel fabrikaları çalışma zamanı kanal yığınlarının en düşük düzeyine (aktarım düzeyinin üzerinde) eklemek için bu yeni oluşturulan yapılandırma bölümünü kullanır.  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 İstemci, `MessageInterceptor` çift numaralı iletilere özel bir üstbilgi eklemek için kitaplığı kullanır. Diğer taraftan hizmet, `MessageInterceptor` bu özel üstbilgiye sahip olmayan iletileri bırakmak için kitaplığı kullanır.  
  
 Hizmeti çalıştırdıktan sonra aşağıdaki istemci çıktısını ve ardından istemciyi görmeniz gerekir.  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 İstemci hizmete 10 farklı rüzgar hızı bildirir, ancak bunların yalnızca yarısını özel üstbilgiyle etiketler.  
  
 Hizmette aşağıdaki çıktıyı görmeniz gerekir:  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
3. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
5. Önce Service.exe'yi çalıştırın sonra Client.exe'yi çalıştırın ve çıkış için her iki konsol penceresini de izleyin.  
