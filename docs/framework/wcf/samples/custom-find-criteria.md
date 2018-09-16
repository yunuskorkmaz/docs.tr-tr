---
title: Özel Bulma Ölçütleri
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 699260fcef7680710f721d213dbf1126ebf7a896
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678065"
---
# <a name="custom-find-criteria"></a>Özel Bulma Ölçütleri
Bu örnek, mantığı kullanarak özel kapsam eşleşme oluşturma ve bir özel bulma hizmeti uygulama gösterir. İstemciler işlevselliği eşleşen özel kapsam iyileştirmek ve daha fazla WCF bulma bulma sistem tarafından sağlanan işlevleri temel alarak oluşturmak için kullanın. Bu örnek kapsayan senaryo aşağıdaki gibidir:  
  
1.  Bir istemci için bir hesap makinesi hizmeti arıyor.  
  
2.  İstemci, arama daraltmak için kural eşleşen özel kapsam kullanmanız gerekir.  
  
3.  Herhangi bir istemci tarafından belirtilen kapsamlar, uç nokta eşleşmesi durumunda bu kuralına göre bir hizmet istemciye yanıt verir.  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Özel bulma hizmeti oluşturma.  
  
-   Özel kapsam eşleştirme algoritması tarafından uygulama.  
  
## <a name="discussion"></a>Tartışma  
 İstemci ölçütlerle eşleşen "Veya" türü için arıyor. Bir hizmeti, kendi uç kapsamlarda herhangi bir istemci tarafından sağlanan kapsamları eşleşiyorsa geri yanıt verir. Bu durumda, istemci tüm kapsamlar aşağıdaki listede olan bir hesap makinesi hizmetinde arayışındadır:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Bunu yapmak için URI tarafından bir özel kapsam eşleşme geçirerek kurala uyan özel bir kapsam kullanmak üzere hizmetlerin istemci yönlendirir. Özel kapsam eşleşen kolaylaştırmak için hizmetin özel kapsam eşleşme kuralı anlar ve ilişkili eşleştirme mantığını uygulayan bir özel bulma hizmeti kullanmanız gerekir.  
  
 İstemci projesinde Program.cs dosyasını açın. Unutmayın `ScopeMatchBy` alanını `FindCriteria` nesne için belirli bir URI ayarlayın. Bu tanımlayıcı, hizmete gönderilir. Bu kural hizmet anlamıyorsa, istemcinin bulma isteği yok sayar.  
  
 Hizmet projesi açın. Özel bulma hizmeti uygulamak için üç dosyayı kullanılır:  
  
1.  **AsyncResult.cs**: Bu uygulamasıdır `AsyncResult` bulma yöntemleri ile gereklidir.  
  
2.  **CustomDiscoveryService.cs**: özel bulma hizmeti bu dosyayı uygular. Uygulamayı yaygınlaştırır <xref:System.ServiceModel.Discovery.DiscoveryService> sınıfı ve gerekli yöntemleri geçersiz kılar. Uygulamasını Not <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> yöntemi. Yöntemi, istemci tarafından özel kapsam eşleşme kuralı tarafından belirtilip belirtilmediğini görmek için denetler. İstemci daha önce belirtilen aynı özel URI budur. Özel kural belirtilirse, "Veya" eşleştirme mantığını uygulayan kod yolu izler.  
  
     Bu özel mantık tüm kapsamlar her hizmetin uç noktalarına gider. Herhangi bir uç noktanın kapsamları herhangi bir istemci tarafından sağlanan kapsamları eşleşirse, Bulma Hizmeti uç noktanın istemciye gönderilen yanıta ekler.  
  
3.  **CustomDiscoveryExtension.cs**: bulma hizmeti uygulamanın son adımı, bu özel uygulanışı bağlamaktır hizmetine hizmet ana bilgisayarı bulmak. Burada kullanılan yardımcı sınıf `CustomDiscoveryExtension` sınıfı. Bu sınıf genişletir <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> sınıfı. Kullanıcı geçersiz kılmanız gerekir <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> yöntemi. Bu durumda, yöntem önce oluşturulmuş özel bulma Hizmeti'nin bir örneğini döndürür. `PublishedEndpoints` olan bir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> tüm eklenen uygulama uç noktaları içeren <xref:System.ServiceModel.ServiceHost>. Özel bulma hizmeti bu kendi iç listeyi doldurmak için kullanır. Bir kullanıcı de diğer uç nokta meta verileri eklemek için kullanabilirsiniz.  
  
 Son olarak, program.cs dosyasını açın. Unutmayın hem <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve `CustomDiscoveryExtension` ana bilgisayara eklenir. Sonra yapıldığını ve hangi bulma iletileri almak, uygulama özel bulma hizmeti kullanım bir uç nokta ana bilgisayar sahiptir.  
  
 İstemci hizmet adresini bilmeden bulamadı olup olmadığına bakın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Projeyi içeren çözümü açın.  
  
2.  Projeyi oluşturun.  
  
3.  Hizmet uygulaması çalıştırın.  
  
4.  İstemci uygulamasını çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
