---
title: Özel İleti Kesici
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: d585e60c9b31e56873b0501425f55541bd647e02
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344279"
---
# <a name="custom-message-interceptor"></a>Özel İleti Kesici
Bu örnek, kanal genişletilebilirlik modeli kullanımını gösterir. Özellikle, kanal fabrikaları ve tüm gelen ve giden iletileri çalışma zamanı yığını olarak belirli bir noktada ele alınması için kanal dinleyicileri oluşturan özel bağlama öğesinin uygulanması gösterilmektedir. Örnek, bir istemci ve sunucu bu özel fabrikaları kullanımını gösteren de içerir.  
  
 Bu örnekte, hem istemci hem de hizmet Konsolu programlar (.exe) var. Hem de hizmet ve istemci özel bir bağlama öğesi ve onun ilişkili çalışma zamanı nesneleri içeren bir ortak kitaplığı (.dll) kullanın.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Örnek kanal çerçevesi kullanarak ve WCF en iyi uygulamaları izleyerek Windows Communication Foundation (WCF) özel katmanlı bir kanal oluşturmak için önerilen yordamı açıklar. Özel bir katmanlı kanal oluşturmak için adımlar aşağıdaki gibidir:  
  
1. Kanal şekillerinin kanal fabrikası ve kanal dinleyicisi destekleyecek karar verebilirsiniz.  
  
2. Kanal fabrikası ve kanal şekillerinizi destekleyen bir kanal dinleyicisi oluşturun.  
  
3. Bir kanal yığınına özel katmanlı kanal ekleyen bir bağlama öğesi ekleyin.  
  
4. Yeni bağlama öğesi yapılandırma sistemi için kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin.  
  
## <a name="channel-shapes"></a>Kanal şekiller  
 Özel bir katmanlı kanal yazarken ilk adım, hangi şekiller kanal için gerekli olduğuna karar sağlamaktır. Aşağıda bize katmanı destekleyen herhangi bir şekil destekliyoruz bizim ileti denetçisi için (örneğin, aşağıda bize katman oluşturabilirsiniz, <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, sonra da kullanıma sunuyoruz <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Kanal fabrikası ve dinleyici fabrikası  
 Sonraki adım özel bir katmanlı kanal yazma uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> ve istemci kanallar için <xref:System.ServiceModel.Channels.IChannelListener> hizmet kanalları için.  
  
 Bu sınıfların bir iç Fabrika ve dinleyici ve temsilci dışındaki tüm `OnCreateChannel` ve `OnAcceptChannel` iç Fabrika ve dinleyici çağrıları.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleniyor  
 Örnek bir özel bağlama öğesi tanımlar: `InterceptingBindingElement`. `InterceptingBindingElement` alan bir `ChannelMessageInterceptor` girdi olarak ve bu kullanır `ChannelMessageInterceptor` aracılığıyla iletileri işlemek için. Bu ortak olmalıdır, yalnızca bir sınıftır. Fabrika, dinleyici ve kanalları tüm ortak arabirimlerin çalışma zamanı iç uygulamaları olabilir.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Bağlama yapılandırması ile tümleştirmek için bir yapılandırma bölümü işleyicisi kitaplığı bir bağlama öğesi uzantısı bölümü tanımlar. İstemci ve sunucu yapılandırma dosyalarını bağlama öğesi uzantısı yapılandırma sistemi ile kaydetmeniz gerekir. Yapılandırma sistemi için kendi bağlama öğesi kullanıma sunmak istiyorsanız uygulayıcılar, bu sınıftan türetebilirsiniz.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>İlke ekleme  
 İlke sistemimiz ile tümleştirmek için `InterceptingBindingElement` biz ilkesi oluşturmak alması gereken sinyal IPolicyExportExtension uygular. İçeri aktarma İlkesi oluşturulan bir istemcide desteklemek için kullanıcı, türetilmiş bir sınıf kaydedebilirsiniz `InterceptingBindingElementImporter` ve geçersiz kılma `CreateMessageInterceptor`kendi ilke etkin oluşturmak için () `ChannelMessageInterceptor` sınıfı.  
  
## <a name="example-droppable-message-inspector"></a>Örnek: Droppable ileti denetçisi  
 Örnekte bulunan örnek uygulamasıdır `ChannelMessageInspector` iletilerini bırakır.  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Bunu yapılandırmasından aşağıdaki gibi erişebilirsiniz:  
  
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
  
 İstemci ve sunucu en düşük düzey (yukarıda aktarım düzeyi), çalışma zamanı kanal yığınlarının özel fabrikaları eklemek için bu yeni oluşturulan yapılandırma bölümü kullanın.  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 İstemcinin kullandığı `MessageInterceptor` bile özel bir başlık eklemek için kitaplık numaralı iletileri. Öte yandan hizmetin kullandığı `MessageInterceptor` kitaplığını kullanarak bu özel üstbilgi olmayan herhangi bir iletiyi bırak.  
  
 Hizmet ve istemci çalıştırdıktan sonra istemci aşağıdaki çıktıyı görmeniz gerekir.  
  
```  
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
  
 İstemci hizmete 10 farklı Rüzgar hızı raporları, ancak yalnızca yarısını özel üstbilginin onlarla etiketler.  
  
 Hizmette aşağıdaki çıktıyı görmeniz gerekir:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Client.exe çalıştırın ve her iki konsol penceresi çıktısı için izleme Service.exe çalıştırın.  
