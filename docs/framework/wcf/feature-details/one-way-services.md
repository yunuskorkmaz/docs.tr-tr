---
title: Tek Yönlü Hizmetler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 03efc27f2ba54ca22f03e3ece84770fe0dcadbb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="one-way-services"></a>Tek Yönlü Hizmetler
İstek-yanıt desen bir hizmet işlemi, varsayılan davranıştır. Hizmet işlemini kodu olarak temsil edilir olsa bile bir istek-yanıt desende istemci yanıt iletisi için bekler. bir `void` yöntemi. Tek yönlü bir işlemle tek bir ileti iletilir. Alıcı bir yanıt iletisi göndermek veya gönderen bir beklediğiniz yapar.  
  
 Tek yönlü tasarım deseni kullanın:  
  
-   Ne zaman istemci işlemleri çağırmanız gerekir ve işlem düzeyinde işleminin sonucu etkilenmez.  
  
-   Kullanırken <xref:System.ServiceModel.NetMsmqBinding> veya <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfı. (Bu senaryo hakkında daha fazla bilgi için bkz: [wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Tek yönlü bir işlem olduğunda, istemciye hata bilgilerini taşımak için yanıt iletisi yok. Güvenilir oturumlar gibi temel bağlama özelliklerini kullanarak hata koşullarını algılayabilir veya çift yönlü hizmet sözleşmesi tasarlayarak iki yönlü işlem kullanan — ve başka bir hizmet işlemini çağırmak için tek yönlü sözleşme istemci hizmeti tek yönlü sözleşme hizmet ve istemci arasında hizmet istemci uygulayan bir geri çağırma kullanarak bunu istemciye geri hataları gönderebilirsiniz.  
  
 Tek yönlü hizmet sözleşmesi oluşturmak için hizmet sözleşmesini tanımlama, uygulama <xref:System.ServiceModel.OperationContractAttribute> sınıf her işleme ve ayarlayın <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true`, aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 Tam bir örnek için bkz: [tek yönlü](../../../../docs/framework/wcf/samples/one-way.md) örnek.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Tek yönlü işlemleriyle engelleme istemcileri  
 Giden veri bağlaması veya bir hizmet uygulaması çeşitli senaryolarda ağ bağlantısı için yazılmış hemen tek yönlü bazı uygulamalar döndürürken, tek yönlü işlemleri kullanarak engellemek bir WCF istemcisi neden olabilir hayata geçirmek önemlidir. Giden veri ağ bağlantısı yazılmış kadar WCF istemci uygulamalarında WCF istemci nesnesi döndürmez. Bu, tek yönlü işlemler de dahil olmak üzere tüm ileti exchange düzenleri için geçerlidir; Bu veri taşıma istemci döndürmesini önler yazma herhangi bir sorun anlamına gelir. Sorun bağlı olarak, sonuç bir özel durum veya hizmete gönderme bir gecikme olabilir.  
  
 Örneğin, taşıma uç noktası bulamazsa, bir <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> özel durumu kadar gecikme olmadan oluşur. Ancak, aynı zamanda hizmet döndürmesini işlemi istemci taşıması önleyen herhangi bir nedenle, kablo verileri gönder okuyamıyor mümkündür. Bu durumda, <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> istemci taşıması üzerinde dönem bağlama aşıldı, bir <xref:System.TimeoutException?displayProperty=nameWithType> atılır — ancak zaman aşımı süresi aşıldı kadar değil. Bir hizmeti çok fazla sayıda iletileri hizmeti bunları belirli bir noktaya işlemi işleyemiyor tetiklenecek mümkündür. Bu durumda, çok, tek yönlü istemci blokları hizmet iletileri işleyebilir kadar veya kadar bir özel durum oluşur.  
  
 Başka bir değişim durumda olan hizmet <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.ServiceModel.ConcurrencyMode.Single> ve bağlama oturumları kullanır. Bu durumda, gelen iletiler (gereksinimi oturumları), Ağ oturumunu kapatma hizmeti bu oturum için önceki iletiyi işleyene kadar okunmaya karşı sonraki iletiler önleyen sıralama dağıtıcı zorlar. İstemci blokları yeniden, ancak hizmet zaman aşımı ayarları istemcide öncesinde bekleyen verilerin işleyebilmesi olup üzerine bağlıdır olup bir özel durum oluşur.  
  
 Bu sorunu bazı istemci nesnesini ve istemci taşıması 's gönderme işlemi arasında bir arabellek ekleyerek azaltabilirsiniz. Örneğin, zaman uyumsuz çağrılar veya bir bellek içi ileti sırası kullanarak hızlı bir şekilde geri dönmek istemci nesne etkinleştirebilirsiniz. Her iki yaklaşımın işlevselliği artabilir, ancak iş parçacığı havuzu ve ileti sırası boyutu sınırları hala zorla.  
  
 Bu, bunun yerine, istemci yanı sıra hizmet çeşitli denetimleri inceleyin ve ardından her iki tarafında en iyi yapılandırma belirlemek için uygulama senaryolarınızı test önerilir. Oturumları kullanımını hizmetinizi üzerinde iletilerinin işlenmesini engelleyen varsa, örneğin, ayarlayabilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.InstanceContextMode.PerCall> böylece her ileti farklı hizmet örneği tarafından işlenen ve ayarlama <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> için <xref:System.ServiceModel.ConcurrencyMode.Multiple> aynı anda iletilerinin gönderilmesi birden çok iş parçacığı izin vermek üzere. Başka bir yaklaşım, hizmet ve istemci bağlamaları okuma kotaları artırmaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tek Yönlü](../../../../docs/framework/wcf/samples/one-way.md)
