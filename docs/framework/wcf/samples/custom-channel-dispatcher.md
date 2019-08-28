---
title: Özel Kanal Dağıtıcı
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: af225a0f31c843f2c3ca949af6d616f89dc83435
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039973"
---
# <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı
Bu örnek, <xref:System.ServiceModel.ServiceHostBase> doğrudan ve Web ana bilgisayarı ortamında özel bir kanal dağıtıcısı oluşturma yoluyla, kanal yığınının özel bir şekilde nasıl oluşturulacağını gösterir. Kanal dağıtıcısı, kanalları kabul <xref:System.ServiceModel.Channels.IChannelListener> etmek ve kanal yığınından iletileri almak için ile etkileşime girer. Bu örnek ayrıca kullanarak <xref:System.ServiceModel.Activation.VirtualPathExtension>bir Web konak ortamında bir kanal yığınının nasıl oluşturulacağını göstermek için temel bir örnek sağlar.  
  
## <a name="custom-servicehostbase"></a>Özel ServiceHostBase  
 Bu örnek, Windows Communication Foundation (WCF <xref:System.ServiceModel.ServiceHostBase> ) yığın <xref:System.ServiceModel.ServiceHost> uygulamasının kanal yığınının üst kısmında özel bir ileti işleme katmanıyla nasıl değiştirileceğini göstermek için yerine temel türü uygular. Kanal dinleyicileri ve kanal dağıtıcısı <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> oluşturmak için sanal yöntemi geçersiz kılabilirsiniz.  
  
 Web 'de barındırılan bir hizmeti uygulamak için, <xref:System.ServiceModel.Activation.VirtualPathExtension> <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> koleksiyondan hizmet uzantısını alın ve aktarım katmanının, barındırma ortamı ayarlarına bağlı <xref:System.ServiceModel.Channels.BindingParameterCollection> olarak kanal dinleyicisinin nasıl yapılandırılacağını bilmesi için, ' a ekleyin. , Internet Information Services (IIS)/Windows Işlem etkinleştirme hizmeti (WAS) ayarıdır.  
  
## <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı  
 Özel kanal dağıtıcısı türü <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>genişletir. Bu tür, kanal katmanı programlama mantığını uygular. Bu örnekte, yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> istek-yanıt iletisi değişim düzeniyle desteklenir, ancak özel kanal dağıtıcısı diğer kanal türlerine kolayca genişletilebilir.  
  
 Dağıtıcı önce kanal dinleyicisini açar ve ardından Singleton yanıt kanalını kabul eder. Kanal ile, sonsuz bir döngüde ileti (istekler) gönderilmeye başlar. Her istek için bir yanıt iletisi oluşturur ve istemciye geri gönderir.  
  
## <a name="creating-a-response-message"></a>Yanıt Iletisi oluşturma  
 İleti işleme, türünde `MyServiceManager`uygulanır. Yönteminde, isteğin desteklenip desteklenmediğini görmek için ileti üstbilgisiilkdenetlenir.`Action` `HandleRequest` Önceden tanımlanmış "http://tempuri.org/HelloWorld/Hello" SOAP eylemi, ileti filtrelemesi sağlamak için tanımlandı. Bu, WCF uygulamasındaki <xref:System.ServiceModel.ServiceHost>hizmet sözleşmesi kavramıyla benzerdir.  
  
 Doğru SOAP eylemi durumu için örnek, istenen ileti verilerini alır ve <xref:System.ServiceModel.ServiceHost> söz konusu durumda görüldüğü gibi isteğe karşılık gelen bir yanıt üretir.  
  
 HTTP-GET fiilini özel bir HTML iletisi döndürerek özel olarak işleirsiniz, bu durumda, bir tarayıcıdan hizmete gözatıp doğru şekilde derlendiğini görebilirsiniz. SOAP eylemi eşleşmiyorsa, isteğin desteklenmediğini göstermek için bir hata mesajı geri gönderin.  
  
 Bu örneğin istemcisi, hizmetten herhangi bir şeyi varsaymayan normal bir WCF istemcörnektir. Bu nedenle, hizmet, normal bir WCF<xref:System.ServiceModel.ServiceHost> uygulamasından aldığınız şekilde eşleşecek şekilde özel olarak tasarlanmıştır. Sonuç olarak, istemcide yalnızca bir hizmet sözleşmesi gereklidir.  
  
## <a name="using-the-sample"></a>Örneği kullanma  
 İstemci uygulamasını çalıştırmak aşağıdaki çıktıyı doğrudan üretir.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Ayrıca, sunucuda bir HTTP-GET iletisi işlenebilmesi için bir tarayıcıdan hizmete de gidebilirsiniz. Bu, doğru biçimlendirilmiş HTML metnini alır.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
