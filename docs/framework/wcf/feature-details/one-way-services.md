---
title: Tek Yönlü Hizmetler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 0d69af40e4b9a0133e44b64b45466f9aac84ffe2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598755"
---
# <a name="one-way-services"></a>Tek Yönlü Hizmetler
Bir hizmet işleminin varsayılan davranışı, istek-yanıt örünğidir. İstek-yanıt modelinde, hizmet işlemi kodda bir yöntem olarak gösterilse bile, istemci yanıt iletisini bekler `void` . Tek yönlü bir işlem ile yalnızca bir ileti iletilir. Alıcı bir yanıt iletisi göndermez ve gönderici bir ileti bekler.  
  
 Tek yönlü tasarım modelini kullanın:  
  
- İstemci işlemleri çağırmalıdır ve işlem düzeyinde işlemin sonuçlarından etkilenmez.  
  
- <xref:System.ServiceModel.NetMsmqBinding>Ya da <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfını kullanırken. (Bu senaryo hakkında daha fazla bilgi için bkz. [WCF 'de kuyruklar](queues-in-wcf.md).)  
  
 Bir işlem tek yönlü olduğunda hata bilgilerini istemciye geri taşımak için bir yanıt iletisi yoktur. Güvenilir oturumlar gibi temel bağlamanın özelliklerini kullanarak hata koşullarını algılayabilir 2 1 veya hizmet ile istemci arasında tek yönlü bir sözleşme (hizmetin, istemcinin uyguladığı bir geri çağırma kullanarak istemciye geri gönderebilmesi için, hizmet ve istemci arasında bir adet tek yönlü anlaşma) kullanarak hata koşullarını tespit edebilirsiniz ve bu sayede hizmetin hataları istemciye geri gönderebilmesini sağlayabilirsiniz.  
  
 Tek yönlü bir hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın, <xref:System.ServiceModel.OperationContractAttribute> her bir işleme sınıfı uygulayın ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` Aşağıdaki örnek kodda gösterildiği gibi özelliğini olarak ayarlayın.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Tam bir örnek için bkz. [tek yönlü](../samples/one-way.md) örnek.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Tek yönlü Işlemlerle engelleyen istemciler  
 Bazı tek yönlü uygulamalar, giden veriler ağ bağlantısına yazıldığında, bazı senaryolarda bir bağlamanın veya bir hizmetin uygulanması, bir WCF istemcisinin tek yönlü işlemler kullanılarak engellenmesine neden olabileceği unutulmamalıdır. WCF istemci uygulamalarında, WCF istemci nesnesi, giden veriler ağ bağlantısına yazıldıktan kadar döndürmez. Bu, tek yönlü işlemler de dahil olmak üzere tüm ileti değişimi desenleri için geçerlidir; Bu, verileri ulaşım 'e yazarken oluşan herhangi bir sorunun istemcinin döndürmesini önlediği anlamına gelir. Soruna bağlı olarak, sonuç bir özel durum veya hizmete ileti gönderilirken bir gecikme olabilir.  
  
 Örneğin, taşıma uç noktayı bulamazsa, <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> çok gecikmeden oluşan bir özel durum oluşturulur. Ancak, hizmetin verileri bazı nedenlerle okuyamasının yanı sıra, istemci aktarım gönderme işleminin döndürmesini engelleyen bir durum da olasıdır. Bu durumlarda, <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> istemci taşıma bağlamasındaki süre aşılırsa, bir oluşturulur, <xref:System.TimeoutException?displayProperty=nameWithType> ancak zaman aşımı süresi aşılana kadar olmaz. Hizmetin belirli bir noktadan sonra işleyememesi için bir hizmette çok sayıda ileti tetikleyede mümkündür. Bu durumda, tek yönlü istemci, hizmet iletileri işleyebilir veya bir özel durum oluşana kadar engeller.  
  
 Diğer bir çeşitleme, Service <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliğinin olarak ayarlandığı <xref:System.ServiceModel.ConcurrencyMode.Single> ve bağlamanın oturumları kullandığı durumdur. Bu durumda, dağıtıcı gelen iletiler (bir oturum gereksinimi) üzerinde sıralamayı zorlar ve bu, hizmet önceki iletiyi bu oturum için işleene kadar, sonraki iletilerin ağ üzerinden okunmasını önler. Yine, istemci engeller, ancak bir özel durumun oluşup oluşmadığını, hizmetin, istemci üzerindeki zaman aşımı ayarlarından önce bekleyen verileri işleyebiliyor olup olmamasına bağlıdır.  
  
 İstemci nesnesi ile istemci aktarımının gönderme işlemi arasında bir arabellek ekleyerek bu sorunun bazılarını azaltabilirsiniz. Örneğin, zaman uyumsuz çağrılar veya bellek içi ileti sırası kullanımı, istemci nesnesinin hızla dönmesini sağlayabilir. Her iki yaklaşım da işlevselliği artırabilir, ancak iş parçacığı havuzunun boyutu ve ileti sırası yine de sınırlara zorlanıyor.  
  
 Bunun yerine, hizmette ve istemci üzerindeki çeşitli denetimleri incelemenizi ve ardından her iki taraftan en iyi yapılandırmayı belirleyebilmek için uygulama senaryolarınızı test etmeniz önerilir. Örneğin, oturumların kullanımı hizmetinizdeki iletilerin işlenmesini engelliyorsa, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.InstanceContextMode.PerCall> her bir iletinin farklı bir hizmet örneği tarafından işlenebilmesi için özelliğini olarak ayarlayabilir ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> <xref:System.ServiceModel.ConcurrencyMode.Multiple> aynı anda birden fazla iş parçacığına ileti gönderimi için ' i ayarlamanız gerekir. Diğer bir yaklaşım ise hizmetin ve istemci bağlamalarının okuma kotalarını artırmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek Yönlü](../samples/one-way.md)
