---
title: Özel Bulma Ölçütleri
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: a7f1b5996f3aefe1ccd77d3ddc117bc7c53ed2aa
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715458"
---
# <a name="custom-find-criteria"></a>Özel Bulma Ölçütleri
Bu örnek, mantığı kullanarak özel bir kapsam eşleşmesi oluşturmayı ve özel bulma hizmetinin nasıl uygulanacağını gösterir. İstemciler, WCF bulmanın sistem tarafından sağlanan bul işlevselliğinin üzerine getirmek ve daha fazla derleme yapmak için özel kapsam eşleştirme işlevlerini kullanır. Bu örneğin kapsamakta olduğu senaryo aşağıdaki gibidir:  
  
1. İstemci, hesap makinesi hizmetini arıyor.  
  
2. İstemcisinin aramasını iyileştirmek için, istemcinin özel bir kapsam eşleştirme kuralı kullanması gerekir.  
  
3. Bu kurala göre, bir hizmet, uç noktası istemci tarafından belirtilen kapsamlarla eşleşiyorsa istemciye geri yanıt verir.  
  
## <a name="demonstrates"></a>Gösterir  
  
- Özel bir keşif hizmeti oluşturuluyor.  
  
- Algoritmayla özel bir kapsam eşleşmesi uygulama.  
  
## <a name="discussion"></a>Tartışma  
 İstemci "veya" tür eşleştirme ölçütü arıyor. Bir hizmet, uç noktalardaki kapsamlar istemci tarafından belirtilen kapsamlardan biriyle eşleşiyorsa geri yanıt verir. Bu durumda, istemci aşağıdaki listede kapsamlardan herhangi birine sahip bir Hesaplayıcı hizmeti arıyor:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Bunu gerçekleştirmek için, istemci, bir özel kapsam eşleştirme kuralını URI ile eşleştirerek bir özel kapsam eşleştirme kuralı kullanmaya yönlendirir. Özel kapsam eşleşmesini kolaylaştırmak için, hizmet özel kapsam eşleştirme kuralını anlayan ve ilişkili eşleşen mantığı uygulayan özel bir keşif hizmeti kullanmalıdır.  
  
 İstemci projesinde, Program.cs dosyasını açın. `FindCriteria` nesnesinin `ScopeMatchBy` alanının belirli bir URI olarak ayarlandığını unutmayın. Bu tanımlayıcı hizmete gönderilir. Hizmet bu kuralı anlamaz, istemcinin bul isteğini yoksayar.  
  
 Hizmet projesini açın. Özel bulma hizmetini uygulamak için üç dosya kullanılır:  
  
1. **AsyncResult.cs**: Bu, bulma yöntemleri için gereken `AsyncResult` uygulamasıdır.  
  
2. **CustomDiscoveryService.cs**: Bu dosya özel bulma hizmetini uygular. Uygulama <xref:System.ServiceModel.Discovery.DiscoveryService> sınıfını genişletir ve gerekli yöntemleri geçersiz kılar. <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> yönteminin uygulanmasını aklınızda edin. Yöntemi, kuralla eşleşen özel kapsamın istemci tarafından belirtilmiş olup olmadığını denetler. Bu, istemcinin daha önce belirttiği özel URI 'dir. Özel kural belirtilmişse, "veya" Match mantığını uygulayan kod yolu izlenir.  
  
     Bu özel mantık, hizmetin sahip olduğu uç noktaların her birinde tüm kapsamlardan geçer. Uç noktanın kapsamlarından herhangi biri istemci tarafından sunulan kapsamlardan biriyle eşleşiyorsa, bulma hizmeti bu uç noktayı istemciye geri gönderilen yanıta ekler.  
  
3. **CustomDiscoveryExtension.cs**: Bulma hizmetini uygulamanın son adımı, özel bulma hizmetinin bu uygulamasını hizmet ana bilgisayarına bağlamak. Burada kullanılan yardımcı sınıf `CustomDiscoveryExtension` sınıfıdır. Bu sınıf <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> sınıfını genişletir. Kullanıcı <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> yöntemi geçersiz kılmalıdır. Bu durumda, yöntemi daha önce oluşturulmuş özel bulma hizmetinin bir örneğini döndürür. `PublishedEndpoints`, <xref:System.ServiceModel.ServiceHost>eklenen tüm uygulama uç noktalarını içeren bir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>. Özel keşif hizmeti, iç listesini doldurmak için bunu kullanır. Bir kullanıcı diğer uç nokta meta verilerini de ekleyebilir.  
  
 Son olarak, Program.cs öğesini açın. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve `CustomDiscoveryExtension` her ikisinin de konağa eklendiğini unutmayın. Bu işlem yapıldıktan ve konakta bulma iletilerinin alınacağı bir uç nokta varsa, uygulama özel bulma hizmetini kullanabilir.  
  
 İstemcinin adresini bilmeden hizmeti bulabildiğinin gözlemleyin.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Projeyi içeren çözümü açın.  
  
2. Projeyi oluşturun.  
  
3. Hizmet uygulamasını çalıştırın.  
  
4. İstemci uygulamasını çalıştırın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
