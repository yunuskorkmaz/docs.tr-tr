---
description: 'Daha fazla bilgi edinin: özel kanal dağıtıcısı'
title: Özel Kanal Dağıtıcı
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: cb56c21b540f359d78e71d8769e9f2d9ccf65a63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732598"
---
# <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı

Bu örnek, <xref:System.ServiceModel.ServiceHostBase> doğrudan ve Web ana bilgisayarı ortamında özel bir kanal dağıtıcısı oluşturma yoluyla, kanal yığınının özel bir şekilde nasıl oluşturulacağını gösterir. Kanal dağıtıcısı, <xref:System.ServiceModel.Channels.IChannelListener> kanalları kabul etmek ve kanal yığınından iletileri almak için ile etkileşime girer. Bu örnek ayrıca kullanarak bir Web konak ortamında bir kanal yığınının nasıl oluşturulacağını göstermek için temel bir örnek sağlar <xref:System.ServiceModel.Activation.VirtualPathExtension> .  
  
## <a name="custom-servicehostbase"></a>Özel ServiceHostBase  

 Bu örnek, <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost> WINDOWS COMMUNICATION FOUNDATION (WCF) yığın uygulamasının kanal yığınının üst kısmında özel bir ileti işleme katmanıyla nasıl değiştirileceğini göstermek için yerine temel türü uygular. <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A>Kanal dinleyicileri ve kanal dağıtıcısı oluşturmak için sanal yöntemi geçersiz kılabilirsiniz.  
  
 Web 'de barındırılan bir hizmeti uygulamak için, koleksiyondan hizmet uzantısını alın <xref:System.ServiceModel.Activation.VirtualPathExtension> <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> ve bunu, <xref:System.ServiceModel.Channels.BindingParameterCollection> Aktarım katmanının barındırma ortamı ayarları, diğer bir deyişle, Internet Information Services (IIS)/Windows işlem ETKINLEŞTIRME hizmeti (was) ayarları temelinde kanal dinleyicisinin nasıl yapılandırılacağını bilmesini sağlayacak şekilde ' a ekleyin.  
  
## <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı  

 Özel kanal dağıtıcısı türü genişletir <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase> . Bu tür, kanal katmanı programlama mantığını uygular. Bu örnekte, yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> istek-yanıt iletisi değişim düzeniyle desteklenir, ancak özel kanal dağıtıcısı diğer kanal türlerine kolayca genişletilebilir.  
  
 Dağıtıcı önce kanal dinleyicisini açar ve ardından Singleton yanıt kanalını kabul eder. Kanal ile, sonsuz bir döngüde ileti (istekler) gönderilmeye başlar. Her istek için bir yanıt iletisi oluşturur ve istemciye geri gönderir.  
  
## <a name="creating-a-response-message"></a>Yanıt Iletisi oluşturma  

 İleti işleme, türünde uygulanır `MyServiceManager` . `HandleRequest`Yönteminde, `Action` isteğin desteklenip desteklenmediğini görmek için ileti üst bilgisi ilk denetlenir. Önceden tanımlanmış "" SOAP eylemi http://tempuri.org/HelloWorld/Hello , ileti filtrelemesi sağlamak için tanımlandı. Bu, WCF uygulamasındaki hizmet sözleşmesi kavramıyla benzerdir <xref:System.ServiceModel.ServiceHost> .  
  
 Doğru SOAP eylemi durumu için örnek, istenen ileti verilerini alır ve söz konusu durumda görüldüğü gibi isteğe karşılık gelen bir yanıt üretir <xref:System.ServiceModel.ServiceHost> .  
  
 HTTP-GET fiilini özel bir HTML iletisi döndürerek özel olarak işleirsiniz, bu durumda, bir tarayıcıdan hizmete gözatıp doğru şekilde derlendiğini görebilirsiniz. SOAP eylemi eşleşmiyorsa, isteğin desteklenmediğini göstermek için bir hata mesajı geri gönderin.  
  
 Bu örneğin istemcisi, hizmetten herhangi bir şeyi varsaymayan normal bir WCF istemcörnektir. Bu nedenle, hizmet, normal bir WCF uygulamasından aldığınız şekilde eşleşecek şekilde özel olarak tasarlanmıştır <xref:System.ServiceModel.ServiceHost> . Sonuç olarak, istemcide yalnızca bir hizmet sözleşmesi gereklidir.  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
