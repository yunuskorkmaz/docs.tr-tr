---
title: Özel Kanal Dağıtıcı
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 7cd27d485efe7fe91e7c59627bf14e188e85f386
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı
Bu örnek kanal yığını özel bir şekilde uygulayarak nasıl oluşturulacağını gösterir <xref:System.ServiceModel.ServiceHostBase> doğrudan ve Web ana bilgisayar ortamında özel kanal dağıtıcı oluşturma. Kanal dağıtıcı etkileşimde <xref:System.ServiceModel.Channels.IChannelListener> kanal yığından Kanallar ve alır iletileri kabul etmesini. Bu örnek ayrıca kullanarak bir Web ana bilgisayar ortamının kanal yığınında yapı göstermek için temel bir örnek sağlar <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Özel ServiceHostBase  
 Bu örnek temel türü uygulayan <xref:System.ServiceModel.ServiceHostBase> yerine <xref:System.ServiceModel.ServiceHost> kanal yığının en üstünde katman işleme özel bir ileti ile Windows Communication Foundation (WCF) yığın uygulama değiştirme göstermek için. Sanal yöntemi geçersiz kılma <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> kanal dinleyicileri ve kanal dağıtıcı oluşturmak için.  
  
 Web barındırılan bir hizmete uygulamak için hizmeti uzantı alınmaya <xref:System.ServiceModel.Activation.VirtualPathExtension> gelen <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> koleksiyonu ve ekleyin <xref:System.ServiceModel.Channels.BindingParameterCollection> böylece aktarım katmanı barındırma ortamı ayarlarına dayanarak kanal dinleyicisi yapılandırmak nasıl bilir, İş, Internet Information Services (IIS) / Windows İşlem Etkinleştirme Hizmeti (WAS) ayarlar.  
  
## <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı  
 Özel kanal dağıtıcı türünü genişleten <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Bu tür kanal düzeyi programlama mantığı uygular. Bu örnekte, yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> istek-yanıt ileti değişim deseni, ancak özel kanal dağıtıcı diğer kanal türleri için kolayca genişletilebilir için desteklenir.  
  
 Dağıtıcı ilk kanal dinleyicisi açar ve bir singleton yanıt kanalına kabul eder. Kanal ile sonsuz bir döngüde iletileri (istek) göndermek başlar. Her istek için bir yanıt iletisi oluşturur ve istemciye geri gönderir.  
  
## <a name="creating-a-response-message"></a>Bir yanıt iletisi oluşturma  
 İleti işleme türünü uygulanır `MyServiceManager`. İçinde `HandleRequest` yöntemi, `Action` iletinin üstbilgisi isteği desteklenip desteklenmediğini görmek için önce denetlenir. Bir SOAP eylemi önceden tanımlanmış "http://tempuri.org/HelloWorld/Hello" ileti filtreleme sağlamak için tanımlanmış. Bu hizmet sözleşmesi kavram olarak benzerdir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uyarlamasını <xref:System.ServiceModel.ServiceHost>.  
  
 Doğru SOAP eylemi çalışması için örnek istenen ileti verileri alır ve ne de görülen için benzer isteğine karşılık gelen bir yanıt oluşturur <xref:System.ServiceModel.ServiceHost> durumda.  
  
 HTTP GET fiili özel olarak doğru derlenmiş görmek için bir tarayıcı hizmetinden gözatması özel bir HTML ileti bu konuda, servis talebi döndürerek işlenir. SOAP eylemi eşleşmiyorsa, bir hata gönderme isteği desteklenmiyor göstermek için ileti geri.  
  
 Bu örnek istemci Normal'dir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetinden gelen herhangi bir şey varsaymaz istemci. Bu nedenle, hizmeti özel bir normal alma eşleşecek şekilde tasarlanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.ServiceHost> uygulaması. Sonuç olarak, yalnızca bir hizmet sözleşmesini istemcide gereklidir.  
  
## <a name="using-the-sample"></a>Örnek kullanma  
 İstemci uygulaması doğrudan çalıştırmak, şu çıkışı üretir.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Böylece bir HTTP GET iletisi sunucuda işlenen bir tarayıcı hizmetinden göz atabilirsiniz. Bu, iyi biçimlendirilmiş HTML metin geri alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
