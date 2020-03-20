---
title: Özel Kanal Dağıtıcı
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: ea1bdd470855d1b2f6572a15ce45f9b90d74fdca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145131"
---
# <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı
Bu örnek, <xref:System.ServiceModel.ServiceHostBase> doğrudan uygulayarak kanal yığınının nasıl özel bir şekilde oluşturulacağını ve Web ana bilgisayar ortamında özel bir kanal göndericisinin nasıl oluşturulacağını gösterir. Kanal göndericisi kanalları <xref:System.ServiceModel.Channels.IChannelListener> kabul etmek için etkileşime girer ve kanal yığınından iletileri alır. Bu örnek, web ana bilgisayar ortamında bir kanal yığınının nasıl <xref:System.ServiceModel.Activation.VirtualPathExtension>oluşturulabildiğini kullanarak göstermek için temel bir örnek de sağlar.  
  
## <a name="custom-servicehostbase"></a>Özel ServiceHostBase  
 Bu örnek, Windows <xref:System.ServiceModel.ServiceHostBase> Communication <xref:System.ServiceModel.ServiceHost> Foundation (WCF) yığın uygulamasının kanal yığınının üstündeki özel ileti işleme katmanıyla nasıl değiştirileceğine göstermek yerine temel türü uygular. Kanal dinleyicisi <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> ve kanal dağıtıcısı oluşturmak için sanal yöntemi geçersiz kılarsınız.  
  
 Web tarafından barındırılan bir hizmeti <xref:System.ServiceModel.Activation.VirtualPathExtension> uygulamak <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> için, hizmet uzantısını koleksiyondan alın ve aktarım katmanının kanal dinleyicisini barındırma ortamı ayarlarına, yani Internet Bilgi Hizmetleri (IIS)/Windows İşlem Etkinleştirme Hizmeti (WAS) ayarlarına göre nasıl yapılandıracağını bilmesi ne şekilde bildiğine ekleyin. <xref:System.ServiceModel.Channels.BindingParameterCollection>  
  
## <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı  
 Özel kanal gönderici türünü <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>genişletir. Bu tür kanal katmanı programlama mantığını uygular. Bu örnekte, <xref:System.ServiceModel.Channels.IReplyChannel> yalnızca istek-yanıt iletisi değişimi deseni için desteklenir, ancak özel kanal gönderici kolayca diğer kanal türlerine genişletilebilir.  
  
 Gönderen önce kanal dinleyicisini açar ve sonra singleton yanıt kanalını kabul eder. Kanal ile, sonsuz bir döngü içinde ileti (istekler) göndermeye başlar. Her istek için bir yanıt iletisi oluşturur ve istemciye geri gönderir.  
  
## <a name="creating-a-response-message"></a>Yanıt İletisi Oluşturma  
 İleti işleme türünde `MyServiceManager`uygulanır. `HandleRequest` Yöntemde, iletinin `Action` üstbilgisi ilk isteği desteklenip desteklenmediğini görmek için denetlenir. İleti filtreleme sağlamakhttp://tempuri.org/HelloWorld/Helloiçin önceden tanımlanmış bir SOAP eylemi " " tanımlanır. Bu WCF uygulamasında hizmet sözleşmesi kavramına <xref:System.ServiceModel.ServiceHost>benzer.  
  
 Doğru SOAP eylem örneği için, örnek istenen ileti verilerini alır ve <xref:System.ServiceModel.ServiceHost> istekte görülene benzer bir yanıt oluşturur.  
  
 Özel bir HTML iletisi döndürerek HTTP-GET fiilini özel olarak işlediniz, bu durumda, hizmete tarayıcıdan göz atarak doğru şekilde derlenmiş olduğunu görebilirsiniz. SOAP eylemi eşleşmiyorsa, isteğin desteklenmediğini belirtmek için bir hata iletisi gönderin.  
  
 Bu örneğin istemcisi, hizmetten hiçbir şey kabul etmeyen normal bir WCF istemcisidir. Bu nedenle, hizmet normal bir WCF<xref:System.ServiceModel.ServiceHost> uygulamasından elde ettiğiniz le eşleşecek şekilde özel olarak tasarlanmıştır. Sonuç olarak, yalnızca bir hizmet sözleşmesi istemci üzerinde gereklidir.  
  
## <a name="using-the-sample"></a>Örneği kullanma  
 İstemci uygulamasını çalıştırmak doğrudan aşağıdaki çıktıyı üretir.  
  
```output  
Client is talking to a request/reply WCF service.
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Ayrıca, bir HTTP-GET iletisinin sunucuda işlenmesi için hizmete tarayıcıdan da göz atabilirsiniz. Bu, iyi biçimlendirilmiş HTML metnini geri alır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
