---
title: "Tek Yönlü Hizmetler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53c5b42e1bc247c5c0e087a7f63a3ecf550af77d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="one-way-services"></a>Tek Yönlü Hizmetler
İstek-yanıt desen bir hizmet işlemi, varsayılan davranıştır. Hizmet işlemini kodu olarak temsil edilir olsa bile bir istek-yanıt desende istemci yanıt iletisi için bekler. bir `void` yöntemi. Tek yönlü bir işlemle tek bir ileti iletilir. Alıcı bir yanıt iletisi göndermek veya gönderen bir beklediğiniz yapar.  
  
 Tek yönlü tasarım deseni kullanın:  
  
-   Ne zaman istemci işlemleri çağırmanız gerekir ve işlem düzeyinde işleminin sonucu etkilenmez.  
  
-   Kullanırken <xref:System.ServiceModel.NetMsmqBinding> veya <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfı. ([!INCLUDE[crabout](../../../../includes/crabout-md.md)] bu senaryo, bkz: [wcf'de kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
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
 Ağ bağlantısı için giden veriler yazılır hemen tek yönlü bazı uygulamalar döndürürken, çeşitli senaryolarda bağlaması veya bir hizmet uygulaması neden olabilir hayata geçirmek önemli bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tek yönlü kullanarak engellemek için istemci işlemler. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] giden veri ağ bağlantısı yazılmış kadar istemci nesnesi döndürmez. Bu, tek yönlü işlemler de dahil olmak üzere tüm ileti exchange düzenleri için geçerlidir; Bu veri taşıma istemci döndürmesini önler yazma herhangi bir sorun anlamına gelir. Sorun bağlı olarak, sonuç bir özel durum veya hizmete gönderme bir gecikme olabilir.  
  
 Örneğin, taşıma uç noktası bulamazsa, bir <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> özel durumu kadar gecikme olmadan oluşur. Ancak, aynı zamanda hizmet döndürmesini işlemi istemci taşıması önleyen herhangi bir nedenle, kablo verileri gönder okuyamıyor mümkündür. Bu durumda, <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> istemci taşıması üzerinde dönem bağlama aşıldı, bir <xref:System.TimeoutException?displayProperty=nameWithType> atılır — ancak zaman aşımı süresi aşıldı kadar değil. Bir hizmeti çok fazla sayıda iletileri hizmeti bunları belirli bir noktaya işlemi işleyemiyor tetiklenecek mümkündür. Bu durumda, çok, tek yönlü istemci blokları hizmet iletileri işleyebilir kadar veya kadar bir özel durum oluşur.  
  
 Başka bir değişim durumda olan hizmet <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.ServiceModel.ConcurrencyMode.Single> ve bağlama oturumları kullanır. Bu durumda, gelen iletiler (gereksinimi oturumları), Ağ oturumunu kapatma hizmeti bu oturum için önceki iletiyi işleyene kadar okunmaya karşı sonraki iletiler önleyen sıralama dağıtıcı zorlar. İstemci blokları yeniden, ancak hizmet zaman aşımı ayarları istemcide öncesinde bekleyen verilerin işleyebilmesi olup üzerine bağlıdır olup bir özel durum oluşur.  
  
 Bu sorunu bazı istemci nesnesini ve istemci taşıması 's gönderme işlemi arasında bir arabellek ekleyerek azaltabilirsiniz. Örneğin, zaman uyumsuz çağrılar veya bir bellek içi ileti sırası kullanarak hızlı bir şekilde geri dönmek istemci nesne etkinleştirebilirsiniz. Her iki yaklaşımın işlevselliği artabilir, ancak iş parçacığı havuzu ve ileti sırası boyutu sınırları hala zorla.  
  
 Bu, bunun yerine, istemci yanı sıra hizmet çeşitli denetimleri inceleyin ve ardından her iki tarafında en iyi yapılandırma belirlemek için uygulama senaryolarınızı test önerilir. Oturumları kullanımını hizmetinizi üzerinde iletilerinin işlenmesini engelleyen varsa, örneğin, ayarlayabilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.InstanceContextMode.PerCall> böylece her ileti farklı hizmet örneği tarafından işlenen ve ayarlama <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> için <xref:System.ServiceModel.ConcurrencyMode.Multiple> aynı anda iletilerinin gönderilmesi birden çok iş parçacığı izin vermek üzere. Başka bir yaklaşım, hizmet ve istemci bağlamaları okuma kotaları artırmaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tek yönlü](../../../../docs/framework/wcf/samples/one-way.md)
