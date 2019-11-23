---
title: Özel Kanal Dağıtıcı
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 0bd83e068de7cfa9cc531ee6b46b9b51c44c1b1d
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291546"
---
# <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı
Bu örnek, doğrudan <xref:System.ServiceModel.ServiceHostBase> uygulayarak ve Web ana bilgisayarı ortamında özel bir kanal dağıtıcısı oluşturmak yoluyla kanal yığınının özel bir şekilde nasıl oluşturulacağını gösterir. Kanal dağıtıcısı, kanalları kabul etmek ve kanal yığınından iletileri almak için <xref:System.ServiceModel.Channels.IChannelListener> ile etkileşime girer. Bu örnek ayrıca, <xref:System.ServiceModel.Activation.VirtualPathExtension>kullanarak bir Web ana bilgisayarı ortamında bir kanal yığınının nasıl oluşturulacağını göstermek için temel bir örnek de sağlar.  
  
## <a name="custom-servicehostbase"></a>Özel ServiceHostBase  
 Bu örnek, Windows Communication Foundation (WCF) yığın uygulamasının kanal yığınının üst kısmında özel bir ileti işleme katmanıyla nasıl değiştirileceğini göstermek için <xref:System.ServiceModel.ServiceHost> yerine <xref:System.ServiceModel.ServiceHostBase> temel türünü uygular. Kanal dinleyicileri ve kanal dağıtıcısı oluşturmak için <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> sanal metodunu geçersiz kılabilirsiniz.  
  
 Web 'de barındırılan bir hizmeti uygulamak için, <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> koleksiyonundan hizmet uzantısı <xref:System.ServiceModel.Activation.VirtualPathExtension> alın ve bunu <xref:System.ServiceModel.Channels.BindingParameterCollection> ekleyerek aktarım katmanının, barındırma ortamı ayarları, diğer bir deyişle, Internet Information Services (IIS)/Windows Işlem etkinleştirme hizmeti (WAS) ayarları temelinde kanal dinleyicisinin nasıl yapılandırılacağını bilmesini sağlayın.  
  
## <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı  
 Özel kanal dağıtıcısı <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>türünü genişletir. Bu tür, kanal katmanı programlama mantığını uygular. Bu örnekte, istek-yanıt iletisi değişim düzeniyle yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> desteklenir, ancak özel kanal dağıtıcısı, diğer kanal türlerine kolayca genişletilebilir.  
  
 Dağıtıcı önce kanal dinleyicisini açar ve ardından Singleton yanıt kanalını kabul eder. Kanal ile, sonsuz bir döngüde ileti (istekler) gönderilmeye başlar. Her istek için bir yanıt iletisi oluşturur ve istemciye geri gönderir.  
  
## <a name="creating-a-response-message"></a>Yanıt Iletisi oluşturma  
 İleti işleme `MyServiceManager`tür ' de uygulanır. `HandleRequest` yönteminde, isteğin desteklenip desteklenmediğini öğrenmek için önce iletinin `Action` üstbilgisi denetlenir. Önceden tanımlanmış "http://tempuri.org/HelloWorld/Hello" SOAP eylemi, ileti filtrelemesi sağlamak için tanımlanmıştır. Bu, <xref:System.ServiceModel.ServiceHost>WCF uygulamasındaki hizmet sözleşmesi kavramıyla benzerdir.  
  
 Doğru SOAP eylemi durumu için örnek, istenen ileti verilerini alır ve <xref:System.ServiceModel.ServiceHost> durumda görüldüğü gibi isteğe karşılık gelen bir yanıt üretir.  
  
 HTTP-GET fiilini özel bir HTML iletisi döndürerek özel olarak işleirsiniz, bu durumda, bir tarayıcıdan hizmete gözatıp doğru şekilde derlendiğini görebilirsiniz. SOAP eylemi eşleşmiyorsa, isteğin desteklenmediğini göstermek için bir hata mesajı geri gönderin.  
  
 Bu örneğin istemcisi, hizmetten herhangi bir şeyi varsaymayan normal bir WCF istemcörnektir. Bu nedenle, hizmet, normal bir WCF<xref:System.ServiceModel.ServiceHost> uygulamasından aldığınız şekilde eşleşecek şekilde özel olarak tasarlanmıştır. Sonuç olarak, istemcide yalnızca bir hizmet sözleşmesi gereklidir.  
  
## <a name="using-the-sample"></a>Örneği kullanma  
 İstemci uygulamasını çalıştırmak aşağıdaki çıktıyı doğrudan üretir.  
  
```output  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
