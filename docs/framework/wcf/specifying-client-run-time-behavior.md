---
title: İstemci Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: 17031f2100c6760cd14aae57cd4efab7428eb362
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235902"
---
# <a name="specifying-client-run-time-behavior"></a>İstemci Çalışma Zamanı Davranışını Belirtme

Windows Communication Foundation (WCF) Hizmetleri gibi Windows Communication Foundation (WCF) istemcileri, çalışma zamanı davranışını istemci uygulamasına uyacak şekilde değiştirecek şekilde yapılandırılabilir. İstemci çalışma zamanı davranışını belirtmek için üç öznitelik mevcuttur. Çift yönlü istemci geri çağırma nesneleri, <xref:System.ServiceModel.CallbackBehaviorAttribute> ve <xref:System.ServiceModel.Description.CallbackDebugBehavior> özniteliklerini kullanarak çalışma zamanı davranışlarını değiştirebilir. Diğer özniteliği, <xref:System.ServiceModel.Description.ClientViaBehavior> mantıksal hedefi anlık ağ hedefi ' nden ayırmak için kullanılabilir. Ayrıca, çift yönlü istemci geri çağırma türleri bazı hizmet tarafı davranışlarını kullanabilir. Daha fazla bilgi için bkz. [hizmet Run-Time davranışını belirtme](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>CallbackBehaviorAttribute kullanma  

 Bir istemci uygulamasındaki geri çağırma sözleşmesi uygulamasının yürütme davranışını sınıfını kullanarak yapılandırabilir veya genişletebilirsiniz <xref:System.ServiceModel.CallbackBehaviorAttribute> . Bu öznitelik, <xref:System.ServiceModel.ServiceBehaviorAttribute> örnek oluşturma davranışı ve işlem ayarları dışında sınıf olarak geri çağırma sınıfı için benzer bir işlev gerçekleştirir.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>Sınıfın, geri çağırma sözleşmesini uygulayan sınıfa uygulanması gerekir. Çift yönlü olmayan bir sözleşme uygulamasına uygulanmışsa, çalışma zamanında bir <xref:System.InvalidOperationException> özel durum oluşturulur. Aşağıdaki kod örneği <xref:System.ServiceModel.CallbackBehaviorAttribute> , bir geri çağırma nesnesi üzerinde, <xref:System.Threading.SynchronizationContext> sıralama yapılacak iş parçacığını, <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> ileti doğrulamasını zorlamak için özelliğini ve <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> <xref:System.ServiceModel.FaultException> hata ayıklama amacıyla hizmete nesneler olarak özel durumlar döndürmek için özelliğini kullanan bir sınıfı gösterir.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Yönetilen özel durum bilgilerinin akışını etkinleştirmek için CallbackDebugBehavior kullanma  

 <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>Özelliği `true` programlı olarak veya bir uygulama yapılandırma dosyasından ayarlayarak, istemci geri çağırma nesnesinde yönetilen özel durum bilgilerinin, hata ayıklama amacıyla hizmete geri akışını sağlayabilirsiniz.  
  
 Özel durum ayrıntıları, yetkisiz hizmetlerin kullanabileceği iç istemci uygulamasıyla ilgili bilgileri kullanıma sunduğundan, yönetilen özel durum bilgilerini hizmetlere döndürmek güvenlik riski oluşturabilir. Ayrıca, <xref:System.ServiceModel.Description.CallbackDebugBehavior> Özellikler programlama yoluyla da ayarlanabilir, ancak dağıtma sırasında devre dışı bırakmak kolay olabilir <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> .  
  
 Dahil olan güvenlik sorunları nedeniyle, şunları yapmanız önemle önerilir:  
  
- Özelliğin değerini olarak ayarlamak için bir uygulama yapılandırma dosyası kullanın <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> `true` .  
  
- Bunu yalnızca denetimli hata ayıklama senaryolarında yapabilirsiniz.  
  
 Aşağıdaki kod örneği, WCF 'nin yönetilen özel durum bilgilerini SOAP iletileri içindeki bir istemci geri çağırma nesnesinden döndürmesini sağlayan bir istemci yapılandırma dosyası gösterir.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  

## <a name="using-the-clientviabehavior-behavior"></a>ClientViaBehavior davranışını kullanma  

 <xref:System.ServiceModel.Description.ClientViaBehavior>Taşıma kanalının oluşturulması gereken Tekdüzen Kaynak tanımlayıcısını belirtmek için davranışını kullanabilirsiniz. Anlık ağ hedefi iletinin amaçlanan işlemcisi olmadığında bu davranışı kullanın. Bu, çağıran uygulama en son hedefi bilmiyor veya hedef `Via` üst bilgi bir adres olmadığında çok atlamalı konuşmaları mümkün değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Çalışma Zamanı Davranışını Belirtme](specifying-service-run-time-behavior.md)
