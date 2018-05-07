---
title: Özel Bulma Ölçütleri
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 6c9363add13e38ded75685e4115a5084629d6505
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-find-criteria"></a>Özel Bulma Ölçütleri
Bu örnek mantığı kullanarak özel kapsam eşleşme oluşturma ve özel bulma hizmeti uygulama gösterir. İstemciler işlevselliği eşleşen özel kapsam daraltın ve WCF bulma sistem tarafından sağlanan Bul işlevselliği üzerinde daha fazla yapı için kullanır. Bu örnek kapsayan senaryo aşağıdaki gibidir:  
  
1.  Bir istemci için bir hesap makinesi hizmeti arıyor.  
  
2.  Kendi aramasını daraltmak için istemci kural eşleşen özel bir kapsam kullanmanız gerekir.  
  
3.  Bu kural göre bir hizmet, uç noktasında herhangi bir istemci tarafından belirtilen kapsamlar eşleşirse istemciye yanıt verir.  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Özel bulma hizmeti oluşturma.  
  
-   Bir özel kapsam eşleştirme algoritması tarafından uygulama.  
  
## <a name="discussion"></a>Tartışma  
 İstemci ölçütlerle eşleşen "Veya" türü için arıyor. Bir hizmet, kendi uç noktalarda kapsamları herhangi bir istemci tarafından sağlanan kapsamları eşleşiyorsa geri yanıt verir. Bu durumda, istemci, aşağıdaki listede kapsamları hiçbirini sahip bir hesap makinesi hizmeti için arıyor:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Bunu gerçekleştirmek için bir özel kapsam eşleşme URI tarafından geçirerek kural eşleşen özel bir kapsam kullanmak üzere hizmetlerin istemci yönlendirir. Özel kapsam eşleşen kolaylaştırmak için hizmet özel kapsam eşleşen kural anlar ve ilişkili eşleştirme mantığını uygulayan bir özel bulma hizmeti kullanmanız gerekir.  
  
 İstemci projesinde Program.cs dosyasını açın. Unutmayın `ScopeMatchBy` alanını `FindCriteria` nesne için belirli bir URI ayarlanır. Bu tanımlayıcı hizmetine gönderilir. Hizmet bu kural anlamıyorsa istemcinin bulma isteği yok sayar.  
  
 Hizmet projesini açın. Üç dosyaları özel bulma hizmeti uygulamak için kullanılır:  
  
1.  **AsyncResult.cs**: Bu uygulamasıdır `AsyncResult` bulma yöntemleri ile gereklidir.  
  
2.  **CustomDiscoveryService.cs**: özel bulma hizmeti bu dosyayı uygular. Uygulama genişletir <xref:System.ServiceModel.Discovery.DiscoveryService> sınıfı ve gerekli yöntemlerini geçersiz kılar. Uygulaması Not <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> yöntemi. Yöntemi, istemci tarafından özel kapsam eşleşme kuralı tarafından belirtilen olup olmadığını görmek için denetler. İstemci daha önce belirtilen aynı özel URI budur. Özel kural belirtilirse, "Veya" eşleştirme mantığını uygulayan kod yolu izlenir.  
  
     Bu özel mantık tüm kapsamlar her hizmet uç noktaları gider. Herhangi bir uç noktanın kapsamları herhangi bir istemci tarafından sağlanan kapsamları eşleşiyorsa, bulma hizmeti bu uç istemciye gönderilen yanıta ekler.  
  
3.  **CustomDiscoveryExtension.cs**: bulma hizmeti uygulama son adımı özel bu uygulama bağlamaktır hizmet ana bilgisayar hizmetine keşfedin. Burada kullanılan Yardımcısı sınıfı, `CustomDiscoveryExtension` sınıfı. Bu sınıfını genişleten <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> sınıfı. Kullanıcı geçersiz kılmanız gerekir <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> yöntemi. Bu durumda, yöntem önce oluşturulan özel bulma Hizmeti'nin bir örneğini döndürür. `PublishedEndpoints` olan bir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> eklenir uygulama bitiş noktalarının tümü içeren <xref:System.ServiceModel.ServiceHost>. Özel bulma hizmeti bu kendi iç listeyi doldurmak için kullanır. Bir kullanıcı de diğer uç nokta meta verileri eklemek için kullanabilirsiniz.  
  
 Son olarak, Program.cs açın. Unutmayın hem <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve `CustomDiscoveryExtension` ana bilgisayara eklenir. Bu yapılır ve ana bilgisayar üzerinden bulma iletileri almak bir uç nokta sonra uygulama için özel bulma hizmetini kullanabilirsiniz.  
  
 İstemci hizmet adresini bilmeden bulamıyor olup olmadığına bakın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Projeyi içeren çözümü açın.  
  
2.  Projeyi oluşturun.  
  
3.  Hizmet uygulaması çalıştırın.  
  
4.  İstemci uygulaması çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
