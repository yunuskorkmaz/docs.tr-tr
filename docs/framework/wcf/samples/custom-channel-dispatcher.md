---
title: Özel Kanal Dağıtıcı
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 20574b4c849f312cb2cf55709d8d5e2a9b5dbca7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519896"
---
# <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı
Bu örnek nasıl uygulayarak özel bir yöntemle kanal yığını oluşturulacağını gösterir <xref:System.ServiceModel.ServiceHostBase> doğrudan ve Web konak ortamında özel kanal dağıtıcı oluşturma. Kanal dağıtıcı etkileşimde <xref:System.ServiceModel.Channels.IChannelListener> kanal yığından Kanallar ve alır ileti kabul etmek için. Bu örnek ayrıca kullanarak bir Web ana bilgisayar ortamının kanal yığınında oluşturma işlemini göstermek için temel bir örnek sağlar <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Özel ServiceHostBase  
 Bu örnek, temel türün uyguladığı <xref:System.ServiceModel.ServiceHostBase> yerine <xref:System.ServiceModel.ServiceHost> kanal yığın üzerinde katman işleme özel bir ileti ile Windows Communication Foundation (WCF) yığını uygulama değiştirme işlemini göstermek için. Sanal yöntemini geçersiz kılma <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> kanal dinleyicileri ve kanal dağıtıcı oluşturun.  
  
 Bir Web barındırılan hizmeti uygulamak için hizmet uzantısı alma <xref:System.ServiceModel.Activation.VirtualPathExtension> gelen <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> koleksiyonu ve ekleyin <xref:System.ServiceModel.Channels.BindingParameterCollection> Aktarım katmanı barındırma ortamı ayarları temel alarak kanal dinleyicisi yapılandırma bilebilmesi, Internet Information Services (IIS) olan / Windows İşlem Etkinleştirme Hizmeti (WAS) ayarlar.  
  
## <a name="custom-channel-dispatcher"></a>Özel Kanal Dağıtıcı  
 Özel kanal dağıtıcı türü genişleten <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Bu tür kanal düzeyi programlama mantığını uygular. Bu örnekte, yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> diğer kanal türleri için istek-yanıt ileti değişim deseni, ancak özel kanal dağıtıcı kolayca genişletilebilir için desteklenir.  
  
 Dağıtıcı ilk kanal dinleyicisi açar ve ardından tek bir yanıt kanalına kabul eder. Kanalıyla sonsuz bir döngüde (istek) iletileri göndermeye başlar. Her istek için bir yanıt iletisi oluşturur ve bunu istemciye geri gönderir.  
  
## <a name="creating-a-response-message"></a>Bir yanıt iletisi oluşturma  
 İleti işleme türü uygulanan `MyServiceManager`. İçinde `HandleRequest` yöntemi `Action` iletisinin üst bilgi isteği desteklenip desteklenmediğini görmek için öncelikle denetlenir. Bir önceden tanımlanmış SOAP eylemi "http://tempuri.org/HelloWorld/Hello" İleti Filtresi sağlamak için tanımlanır. Bu WCF uygulamasında hizmet sözleşme kavramına benzer <xref:System.ServiceModel.ServiceHost>.  
  
 Doğru SOAP eylemi çalışması için örnek istenen ileti verileri alır ve ne de görülür için benzer isteğine karşılık gelen bir yanıt oluşturur <xref:System.ServiceModel.ServiceHost> çalışması.  
  
 Özel HTTP GET fiili hizmet düzgün derlenir görmek için bir tarayıcıdan göz atabilmenizi sağlayacak şekilde özel bir HTML ileti bu, servis talebi döndürerek işlenir. SOAP eylemi eşleşmiyorsa, bir hata gönderme isteği desteklenmediğini belirtmek için ileti geri.  
  
 Bu örnek hizmetinden gelen herhangi bir şey varsaymaz normal bir WCF istemcisi istemcisidir. Bu nedenle, hizmeti özel normal bir WCF alma eşleştirme için tasarlanmıştır<xref:System.ServiceModel.ServiceHost> uygulaması. Sonuç olarak, yalnızca bir hizmet sözleşmesini istemcide gereklidir.  
  
## <a name="using-the-sample"></a>Örnek kullanma  
 Doğrudan istemci uygulamasının çalışıp aşağıdaki çıktıyı üretir.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Bir HTTP GET iletisi sunucuda işlenir böylece hizmet tarayıcısından de göz atabilirsiniz. Bu, iyi biçimlendirilmiş HTML metni geri alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
