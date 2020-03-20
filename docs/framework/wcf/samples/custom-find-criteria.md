---
title: Özel Bulma Ölçütleri
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 3bafe89f5c114106eece02c41599cf485591c1cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183855"
---
# <a name="custom-find-criteria"></a>Özel Bulma Ölçütleri
Bu örnek, mantığı kullanarak özel bir kapsam eşleşmesi oluşturmanın ve özel bir bulma hizmetinin nasıl uygulanacağını gösterir. İstemciler, WCF Discovery'nin sistem tarafından sağlanan bulma işlevini hassaslaştırmak ve üzerine daha fazla inşa etmek için özel kapsam eşleştirme işlevlerini kullanır. Bu örneklemin kapsadığı senaryo aşağıdaki gibidir:  
  
1. Bir müşteri bir hesap makinesi hizmeti arıyor.  
  
2. Aramasını hassaslaştırmak için istemcinin özel kapsam eşleştirme kuralını kullanması gerekir.  
  
3. Bu kurala göre, bitiş noktası istemci tarafından belirtilen kapsamlardan herhangi biri ile eşleşirse, bir hizmet istemciye geri yanıt verir.  
  
## <a name="demonstrates"></a>Gösteriler  
  
- Özel bir bulma hizmeti oluşturma.  
  
- Algoritmaya göre özel bir kapsam eşleşmesi uygulama.  
  
## <a name="discussion"></a>Tartışma  
 İstemci "VEYA" türü eşleştirme ölçütlerini arıyor. Uç noktalarındaki kapsamlar istemci tarafından sağlanan kapsamlardan herhangi biri ile eşleşirse, bir hizmet yanıt verir. Bu durumda, istemci aşağıdaki listede kapsamlardan herhangi biri olan bir hesap makinesi hizmeti arıyor:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Bunu gerçekleştirmek için istemci, uri tarafından özel bir kapsam eşleşmesi geçirerek özel kapsam eşleştirme kuralı nı kullanmaya yönelik hizmetleri yönlendirir. Özel kapsam eşleştirmesini kolaylaştırmak için, hizmetin özel kapsam eşleşmekuralını anlayan ve ilişkili eşleşen mantığı uygulayan özel bir bulma hizmeti kullanması gerekir.  
  
 İstemci projesinde, Program.cs dosyasını açın. Nesnenin `ScopeMatchBy` alanının `FindCriteria` belirli bir URI olarak ayarladığını unutmayın. Bu tanımlayıcı servise gönderilir. Hizmet bu kuralı anlamıyorsa, istemcinin bulma isteğini yok sayar.  
  
 Servis projesini açın. Özel Bulma Hizmeti'ni uygulamak için üç dosya kullanılır:  
  
1. **AsyncResult.cs**: Discovery yöntemlerinin `AsyncResult` gerektirdiği uygulamadır.  
  
2. **CustomDiscoveryService.cs**: Bu dosya özel bulma hizmetini uygular. Uygulama <xref:System.ServiceModel.Discovery.DiscoveryService> sınıfı genişletir ve gerekli yöntemleri geçersiz kılar. Yöntemin uygulanmasına <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> dikkat edin. Yöntem, özel kapsam kuralına göre eşleşip eşleşmediğini istemci tarafından denetler. Bu, istemcinin daha önce belirttiği özel URI ile aynıdır. Özel kural belirtilirse, "VEYA" eşleç mantığını uygulayan kod yolu izlenir.  
  
     Bu özel mantık, hizmetin sahip olduğu uç noktaların her birinde tüm kapsamları geçer. Bitiş noktasının kapsamlarından herhangi biri istemci tarafından sağlanan kapsamlarla eşleşirse, bulma hizmeti istemciye geri gönderilen yanıta bu bitiş noktasını ekler.  
  
3. **CustomDiscoveryExtension.cs**: Keşif hizmetinin uygulanmasındaki son adım, özel keşif hizmetinin bu uygulamasını hizmet barındırıcısına bağlamaktır. Burada kullanılan yardımcı sınıf `CustomDiscoveryExtension` sınıftır. Bu sınıf sınıfı <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> genişletir. Kullanıcı yöntemi <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> geçersiz kılmalıdır. Bu durumda, yöntem daha önce oluşturulan özel bulma hizmetinin bir örneğini döndürür. `PublishedEndpoints`'ye <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> eklenen tüm uygulama uç noktalarını içeren <xref:System.ServiceModel.ServiceHost>bir noktadır. Özel bulma hizmeti, iç listesini doldurmak için bunu kullanır. Bir kullanıcı diğer uç nokta meta verileri de ekleyebilirsiniz.  
  
 Son olarak, açık Program.cs. Hem ana <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bilgisayara hem de ana bilgisayara `CustomDiscoveryExtension` eklenmiştir. Bu işlem tamamlandığında ve ana bilgisayar, bulma iletileri almak için üzerinde bir bitiş noktası vardır, uygulama özel bulma hizmeti kullanabilirsiniz.  
  
 Müşterinin hizmeti adresini bilmeden bulabildiğini gözlemleyin.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Projeyi içeren çözümü açın.  
  
2. Projeyi derleyin.  
  
3. Servis uygulamasını çalıştırın.  
  
4. İstemci uygulamasını çalıştırın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
