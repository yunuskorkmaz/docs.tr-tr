---
title: "Özel İleti Kesici"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cdc547c26b23c74bb77640e826272da933f45a0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-message-interceptor"></a>Özel İleti Kesici
Bu örnek kanal genişletilebilirlik modeli kullanımını göstermektedir. Özellikle, kanal fabrikaları ve çalışma zamanı yığınında belirli bir noktada tüm gelen ve giden iletileri izlemesine kanal dinleyicileri oluşturur özel bağlama öğesi uygulamak nasıl gösterir. Örnek, bir istemci ve bu özel oluşturucuları kullanımını gösteren sunucu de içerir.  
  
 Bu örnekte, hem istemci hem de hizmet konsol (.exe) programlarıdır. İstemci ve hizmet hem de özel bağlama öğesi ve ilişkili çalışma zamanı nesnelerini içeren bir ortak kitaplığı (.dll) kullanın.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Örnek özel bir katmanlı kanalı oluşturmak için önerilen yordamı açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], kanal çerçevesi kullanarak ve aşağıdaki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en iyi uygulamalar. Özel bir katmanlı kanal oluşturmak için adımlar aşağıdaki gibidir:  
  
1.  Kanal şekillerin kanal fabrikası ve kanal dinleyicisi destekleyecek karar verebilirsiniz.  
  
2.  Kanal fabrikası ve kanal şekiller destekleyen bir kanal dinleyicisi oluşturun.  
  
3.  Bir kanal yığınına özel katmanlı kanal ekler bir bağlama öğesi ekleyin.  
  
4.  Yapılandırma sistemi için yeni bir bağlama öğesi kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin.  
  
## <a name="channel-shapes"></a>Kanal şekiller  
 Özel bir katmanlı kanal yazma ilk adımı, hangi şekillere kanalı gerekli karar vermektir. Bizim ileti denetçisi için desteklediğimiz katmanını bize altındaki destekleyen herhangi bir şekli (örneğin, bize altında katman oluşturabilirsiniz, <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, biz de kullanıma sonra <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Kanal fabrikası ve dinleyici fabrikası  
 Özel bir katmanlı kanal yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> ve istemci kanallar için <xref:System.ServiceModel.Channels.IChannelListener> hizmet kanalları.  
  
 Bu sınıfların bir iç Fabrika ve dinleyici gerçekleştirin ve temsilci dışındaki tüm `OnCreateChannel` ve `OnAcceptChannel` iç Fabrika ve dinleyici çağrıları.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleme  
 Özel bağlama öğesi örneği tanımlar: `InterceptingBindingElement`. `InterceptingBindingElement`alan bir `ChannelMessageInterceptor` bir girdi olarak ve bu kullanır `ChannelMessageInterceptor` üzerinden geçirmek iletileri işlemek için. Genel tek sınıftır. Fabrika, dinleyiciyi ve kanallar tüm ortak çalışma zamanı arabirimlerin dahili uygulamalardan olabilir.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Yapılandırma desteği ekleme  
 Bağlama yapılandırması ile tümleştirmek için kitaplık yapılandırma bölümü işleyicisi bağlama öğesi uzantısı bölüm olarak tanımlar. İstemci ve sunucu yapılandırma dosyaları bağlama öğesi uzantısı yapılandırma sistemi ile kaydetmeniz gerekir. Yapılandırma sistemi için kendi bağlama öğesi kullanıma sunmak istediğiniz Implementers bu sınıftan türeyen.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>İlke ekleme  
 İlke sistemimizde ile tümleştirmek için `InterceptingBindingElement` biz ilkesi oluşturma alması gereken sinyal IPolicyExportExtension uygular. İçeri aktarma İlkesi oluşturulan bir istemcide desteklemek için kullanıcı, türetilmiş bir sınıf kaydedebilirsiniz `InterceptingBindingElementImporter` ve geçersiz kılma `CreateMessageInterceptor`kendi ilke etkinleştirilmiş oluşturmak için () `ChannelMessageInterceptor` sınıfı.  
  
## <a name="example-droppable-message-inspector"></a>Örnek: Droppable ileti denetçisi  
 Aşağıdaki örnekte dahil bir örnek uygulamasıdır `ChannelMessageInspector` iletilerini bırakır.  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Yapılandırmasından gibi erişebildiğinizi:  
  
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
  
 İstemci ve sunucu kendi çalışma zamanı kanal yığınları (yukarıda aktarım düzeyi) en düşük-düzeyi özel oluşturucuları eklemek için bu yeni oluşturulan yapılandırma bölümü kullanın.  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 İstemcinin kullandığı `MessageInterceptor` özel bir üstbilgisi bile eklemek için kitaplık numaralı iletileri. Öte yandan hizmetin kullandığı `MessageInterceptor` kitaplığı bu özel üstbilgi olmayan herhangi bir iletisi bırakın.  
  
 Hizmet ve istemci çalıştırdıktan sonra aşağıdaki istemci çıktı görmeniz gerekir.  
  
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
  
 İstemci hizmete 10 farklı Rüzgar hızı raporlar, ancak yalnızca özel üstbilgi bunlarla yarısı etiketler.  
  
 Hizmette şu çıktı görmeniz gerekir:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Client.exe çalıştırın ve her iki konsol penceresi çıktısı için izleme Service.exe önce çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
