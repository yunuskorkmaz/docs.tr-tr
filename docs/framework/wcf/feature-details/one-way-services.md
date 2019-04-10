---
title: Tek Yönlü Hizmetler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 011bca07890e706b86f2a0b1dbf11acf77058548
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231285"
---
# <a name="one-way-services"></a>Tek Yönlü Hizmetler
İstek-yanıt deseni bir hizmet işlemi, varsayılan davranıştır. Hizmet işlemi kod olarak temsil edilir olsa bile bir istek-yanıt modelinde istemci yanıt iletisi için bekler. bir `void` yöntemi. Tek yönlü bir işlemle tek bir ileti iletilir. Alıcı bir yanıt iletisi göndermek ya da gönderen bir bekler.  
  
 Tek yönlü tasarım deseni kullanın:  
  
-   Ne zaman istemci işlemleri çağırmanız gerekir ve işlem düzeyinde işleminin sonucu etkilenmez.  
  
-   Kullanırken <xref:System.ServiceModel.NetMsmqBinding> veya <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfı. (Bu senaryo hakkında daha fazla bilgi için bkz. [wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Tek yönlü bir işlem olduğunda, hata bilgilerini istemciye geri taşımak için yanıt iletisi yok. Güvenilir oturumlar gibi temel alınan bağlama özelliklerini kullanarak hata durumları algılayabilir veya iki tek yönlü işlem kullanan bir çift yönlü hizmet sözleşmesi tasarlayarak — ve başka bir hizmet işlemi çağırmak için tek yönlü sözleşme istemciden hizmete tek yönlü sözleşme hizmet ve istemci arasında hizmet istemci uygulayan geri aramayı kullanarak istemciye geri hataları gönderebilmesi.  
  
 Tek yönlü hizmet sözleşmesi oluşturmak için hizmet sözleşmesini tanımlama, Uygula <xref:System.ServiceModel.OperationContractAttribute> sınıfı her işleme ve ayarlama <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `true`aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
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
  
 Tam bir örnek için bkz. [tek yönlü](../../../../docs/framework/wcf/samples/one-way.md) örnek.  
  
## <a name="clients-blocking-with-one-way-operations"></a>İstemcileri ile tek yönlü işlemlerini engelleme  
 Giden veri bağlama veya bir hizmet uygulaması birkaç senaryoda ağ bağlantısı, yazılan hemen sonra tek yönlü bazı uygulamalar olsa da tek yönlü işlem kullanarak engellemek bir WCF istemcisi neden olabilir bilmeniz önemlidir. WCF istemci uygulamalarının içinde ağ bağlantısı için giden veri yazıldı kadar WCF istemci nesnesi döndürmez. Bu, tek yönlü işlemleri dahil olmak üzere tüm ileti exchange desenleri için geçerlidir; Bu, veri taşıma istemci döndürmesini önler yazma herhangi bir sorun anlamına gelir. Sorun bağlı olarak, sonuç bir özel durum veya hizmete gönderme bir gecikme olabilir.  
  
 Örneğin, taşıma uç noktası bulamazsa, bir <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> kadar gecikme olmadan özel durum harekete geçirilir. Ancak, aynı zamanda hizmetin döndürmesini işlemi verileri istemci taşıması engelleyen nedenleri, kablo dışında göndermek okuyamıyor olduğunu mümkündür. Bu gibi durumlarda, varsa <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> dönem istemci taşıması üzerinde bağlama aşıldı, bir <xref:System.TimeoutException?displayProperty=nameWithType> oluşturulur; ancak zaman aşımı süresi aşıldı kadar değil. Bir hizmete çok sayıda iletileri hizmet bunları belirli bir noktaya işleme alınamıyor ateşlenmesine mümkündür. Bu durumda, tek yönlü istemci blokları kadar hizmet iletileri işleyebilir veya kadar bir özel durum oluşturulur.  
  
 Bu durumda başka bir çeşitlemedir hizmet <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.ConcurrencyMode.Single> ve oturumları bağlama kullanır. Bu durumda, gelen iletiler (oturumlarının bir gereksinim) hizmeti bu oturum için yukarıdaki iletiyi işleyene kadar ağa okunmasını daha sonraki iletileri önleyen sıralama dağıtıcı zorlar. İstemci blokları yeniden ancak olup özel bir durum oluştuğunda olup hizmet zaman aşımı ayarlarını istemcide önce bekleyen verileri işlemek bağlıdır.  
  
 Bu sorunun bazı istemci nesnesini ve istemci taşıması ait gönderme işlemi arasında bir tampon ekleyerek azaltabilirsiniz. Örneğin, zaman uyumsuz çağrıları veya bir bellek içi ileti kuyruğu kullanarak hızlı bir şekilde geri dönmek istemci nesne etkinleştirebilirsiniz. Her iki yaklaşım işlevselliği artırabilir, ancak iş parçacığı havuzu ve mesaj kuyruğu boyutunu sınırları hala zorla.  
  
 Bu, bunun yerine, çeşitli denetimleri hem istemcide hem de hizmet inceleyin ve ardından iki tarafındaki en iyi yapılandırma belirlemek için uygulama senaryolarınızı test önerilir. Oturumları kullanımını hizmetinizdeki iletilerinin işlenmesini engelliyorsa, örneğin, ayarlayabilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.InstanceContextMode.PerCall> her ileti farklı hizmet örneği tarafından işlenen ve ayarlama böylece <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> için <xref:System.ServiceModel.ConcurrencyMode.Multiple> aynı anda iletilerini dağıtmak birden fazla iş parçacığı izin vermek üzere. Hizmet ve istemci bağlamaları okuma kotaları artırmak başka bir yaklaşımdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek Yönlü](../../../../docs/framework/wcf/samples/one-way.md)
