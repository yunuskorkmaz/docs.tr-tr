---
title: İstemci Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: 075f62526ace1ac49d12e1bdec39d8df4b0a3ff1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321403"
---
# <a name="specifying-client-run-time-behavior"></a>İstemci Çalışma Zamanı Davranışını Belirtme
Windows Communication Foundation (WCF) Hizmetleri gibi Windows Communication Foundation (WCF) istemcileri, çalışma zamanı davranışını istemci uygulamasına uyacak şekilde değiştirecek şekilde yapılandırılabilir. İstemci çalışma zamanı davranışını belirtmek için üç öznitelik mevcuttur. Çift yönlü istemci geri çağırma nesneleri <xref:System.ServiceModel.CallbackBehaviorAttribute> ve <xref:System.ServiceModel.Description.CallbackDebugBehavior> özniteliklerini kullanarak çalışma zamanı davranışlarını değiştirebilir. Diğer <xref:System.ServiceModel.Description.ClientViaBehavior>özniteliği, mantıksal hedefi anlık ağ hedefi ' nden ayırmak için kullanılabilir. Ayrıca, çift yönlü istemci geri çağırma türleri bazı hizmet tarafı davranışlarını kullanabilir. Daha fazla bilgi için bkz. [hizmet çalışma zamanı davranışını belirtme](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>CallbackBehaviorAttribute kullanma  
 Bir istemci uygulamasındaki geri çağırma sözleşmesi uygulamasının yürütme davranışını <xref:System.ServiceModel.CallbackBehaviorAttribute> sınıfını kullanarak yapılandırabilir veya genişletebilirsiniz. Bu öznitelik, örnek oluşturma davranışı ve işlem ayarları dışında <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıfı olarak geri çağırma sınıfı için benzer bir işlev gerçekleştirir.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> sınıfı, geri çağırma sözleşmesini uygulayan sınıfa uygulanmalıdır. Çift yönlü olmayan bir sözleşme uygulamasına uygulanmışsa, çalışma zamanında bir <xref:System.InvalidOperationException> özel durumu oluşturulur. Aşağıdaki kod örneği, bir geri çağırma nesnesi üzerinde, sıralama yapılacak iş parçacığını, ileti doğrulamasını zorlamak için <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> özelliğini ve hata ayıklama amacıyla hizmete <xref:System.ServiceModel.FaultException> nesneleri olarak özel durumlar döndürmek için <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> özelliğini <xref:System.Threading.SynchronizationContext> kullanan bir <xref:System.ServiceModel.CallbackBehaviorAttribute> sınıfını gösterir.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Yönetilen özel durum bilgilerinin akışını etkinleştirmek için CallbackDebugBehavior kullanma  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliğini program aracılığıyla veya bir uygulama yapılandırma dosyasından `true` olarak ayarlayarak, istemci geri çağırma nesnesindeki yönetilen özel durum bilgilerinin, hata ayıklama amacıyla hizmete geri akışını sağlayabilirsiniz.  
  
 Özel durum ayrıntıları, yetkisiz hizmetlerin kullanabileceği iç istemci uygulamasıyla ilgili bilgileri kullanıma sunduğundan, yönetilen özel durum bilgilerini hizmetlere döndürmek güvenlik riski oluşturabilir. Ayrıca, <xref:System.ServiceModel.Description.CallbackDebugBehavior> Özellikler programlı olarak ayarlanabilse de, dağıtma sırasında <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> devre dışı bırakmayı unutmak kolay olabilir.  
  
 Dahil olan güvenlik sorunları nedeniyle, şunları yapmanız önemle önerilir:  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliğinin değerini `true`olarak ayarlamak için bir uygulama yapılandırma dosyası kullanın.  
  
- Bunu yalnızca denetimli hata ayıklama senaryolarında yapabilirsiniz.  
  
 Aşağıdaki kod örneği, WCF 'nin yönetilen özel durum bilgilerini SOAP iletileri içindeki bir istemci geri çağırma nesnesinden döndürmesini sağlayan bir istemci yapılandırma dosyası gösterir.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>ClientViaBehavior davranışını kullanma  
 Taşıma kanalının oluşturulması gereken Tekdüzen Kaynak tanımlayıcısını belirtmek için <xref:System.ServiceModel.Description.ClientViaBehavior> davranışını kullanabilirsiniz. Anlık ağ hedefi iletinin amaçlanan işlemcisi olmadığında bu davranışı kullanın. Bu, çağıran uygulama en son hedefi bilmiyor veya hedef `Via` üst bilgisi bir adres olmadığında çok atlamalı konuşmaları mümkün değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Çalışma Zamanı Davranışını Belirtme](specifying-service-run-time-behavior.md)
