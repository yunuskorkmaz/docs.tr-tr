---
title: Özel İleti Kesici
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 61f9bae24f5edb70430f4f3eaa16e42da221a7b4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978304"
---
# <a name="custom-message-interceptor"></a>Özel İleti Kesici
Bu örnek, kanal genişletilebilirlik modelinin kullanımını gösterir. Özellikle, çalışma zamanı yığınında belirli bir noktada tüm gelen ve giden iletileri kesmeye yönelik kanal fabrikaları ve kanal dinleyicileri oluşturan özel bir bağlama öğesinin nasıl uygulanacağını gösterir. Örnek ayrıca, bu özel fabrikaların kullanımını gösteren bir istemci ve sunucu içerir.  
  
 Bu örnekte, hem istemci hem de hizmet konsol programlarıdır (. exe). İstemci ve hizmet, özel bağlama öğesini ve ilişkili çalışma zamanı nesnelerini içeren ortak bir kitaplığı (. dll) kullanır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Örnek, kanal çerçevesini ve aşağıdaki WCF en iyi yöntemlerini kullanarak Windows Communication Foundation (WCF) içinde özel bir katmanlı kanal oluşturmak için önerilen yordamı açıklar. Özel katmanlı Kanal oluşturma adımları aşağıdaki gibidir:  
  
1. Kanal fabrikasının ve kanal dinleyicinizin hangi kanal şekillerinde destekleyeceği belirleyin.  
  
2. Kanal fabrikası ve kanal şekillerinizi destekleyen bir kanal dinleyicisi oluşturun.  
  
3. Özel katmanlı kanalı bir kanal yığınına ekleyen bir bağlama öğesi ekleyin.  
  
4. Yeni bağlama öğesini yapılandırma sistemine göstermek için bağlama öğesi uzantısı bölümü ekleyin.  
  
## <a name="channel-shapes"></a>Kanal şekilleri  
 Özel katmanlı kanal yazmanın ilk adımı, kanal için hangi şekillerin gerekli olduğuna karar vermeye yöneliktir. İleti denetçimiz için, altındaki katmanın desteklediği herhangi bir şekli destekliyoruz (örneğin, ABD altındaki katmanın <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>) de kullanıma sunarız.  
  
## <a name="channel-factory-and-listener-factory"></a>Kanal fabrikası ve dinleyici fabrikası  
 Özel katmanlı kanal yazmanın bir sonraki adımı, istemci kanalları için <xref:System.ServiceModel.Channels.IChannelFactory> ve hizmet kanalları için <xref:System.ServiceModel.Channels.IChannelListener> bir uygulama oluşturmaktır.  
  
 Bu sınıflar bir iç fabrika ve dinleyici alır ve tüm, iç fabrika ve dinleyiciye `OnCreateChannel` ve `OnAcceptChannel` çağrıları hariç değildir.  
  
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
  
## <a name="adding-a-binding-element"></a>Bağlama öğesi ekleme  
 Örnek, bir özel bağlama öğesi tanımlar: `InterceptingBindingElement`. `InterceptingBindingElement` giriş olarak bir `ChannelMessageInterceptor` alır ve bu `ChannelMessageInterceptor` üzerinden geçen iletileri işlemek için kullanır. Bu, genel olması gereken tek sınıftır. Fabrika, dinleyici ve kanalların hepsi, genel çalışma zamanı arabirimlerinin iç uygulamaları olabilir.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Bağlama yapılandırması ile tümleştirme için, kitaplık bir yapılandırma bölümü işleyicisini bağlama öğesi uzantısı bölümü olarak tanımlar. İstemci ve sunucu yapılandırma dosyaları, bağlama öğesi uzantısını yapılandırma sistemine kaydetmelidir. Bağlama öğelerini yapılandırma sistemine sunmak isteyen uygulayıcılar bu sınıftan türetilebilir.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement 
{ 
    //... 
}
```  
  
## <a name="adding-policy"></a>Ilke ekleniyor  
 İlke sistemimizi tümleştirmek için `InterceptingBindingElement`, ilke oluşturmaya katılabilmemiz için IPolicyExportExtension 'ı uygular. Oluşturulan bir istemcide ilke içeri aktarmayı desteklemek için, Kullanıcı `InterceptingBindingElementImporter` türetilen bir sınıf kaydedebilir ve ilke etkin `ChannelMessageInterceptor` sınıfını oluşturmak için `CreateMessageInterceptor`() geçersiz kılabilir.  
  
## <a name="example-droppable-message-inspector"></a>Örnek: açılan Ileti denetçisi  
 Örneğe dahil edilen örnek, iletileri bırakılanlar `ChannelMessageInspector` örnek bir uygulamasıdır.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Bu yapılandırmaya aşağıdaki gibi erişebilirsiniz:  
  
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
  
 İstemci ve sunucu, bu yeni oluşturulan yapılandırma bölümünü, özel fabrikaları çalışma zamanı kanal yığınlarının en düşük düzeyine (aktarım düzeyinin üzerinde) eklemek için kullanır.  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 İstemci, hatta numaralandırılmış iletilere özel bir üst bilgi eklemek için `MessageInterceptor` kitaplığını kullanır. Diğer taraftaki hizmet, bu özel üst bilgisine sahip olmayan iletileri bırakmak için `MessageInterceptor` kitaplığı kullanır.  
  
 Hizmetini ve ardından istemcisini çalıştırdıktan sonra aşağıdaki istemci çıktısını görmeniz gerekir.  
  
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
  
 İstemci, hizmete farklı bir rüzgar hızı bildirir, ancak yalnızca özel üst bilgiyle bu etiketlerin yarısını Etiketler.  
  
 Hizmette aşağıdaki çıktıyı görmeniz gerekir:  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
5. Önce Service. exe ' yi çalıştırın, sonra Client. exe ' yi çalıştırın ve her iki konsol pencerelerini de çıktı  
