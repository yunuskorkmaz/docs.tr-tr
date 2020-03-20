---
title: İstemci Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f9c22d25bedc36b3515538a8785b488aaa547990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143245"
---
# <a name="specifying-client-run-time-behavior"></a>İstemci Çalışma Zamanı Davranışını Belirtme
Windows Communication Foundation (WCF) istemcileri, Windows Communication Foundation (WCF) hizmetleri gibi, çalışma zamanı davranışını istemci uygulamasına uyacak şekilde değiştirmek üzere yapılandırılabilir. İstemci çalışma zamanı davranışını belirtmek için üç öznitelik kullanılabilir. Çift yönlü istemci geri arama <xref:System.ServiceModel.CallbackBehaviorAttribute> nesneleri, çalışma zamanı davranışlarını değiştirmek için öznitelikleri kullanabilir. <xref:System.ServiceModel.Description.CallbackDebugBehavior> Diğer öznitelik, <xref:System.ServiceModel.Description.ClientViaBehavior>mantıksal hedefi anında ağ hedefinden ayırmak için kullanılabilir. Buna ek olarak, çift yönlü istemci geri arama türleri bazı hizmet tarafı davranışları kullanabilirsiniz. Daha fazla bilgi için [bkz.](specifying-service-run-time-behavior.md)  
  
## <a name="using-the-callbackbehaviorattribute"></a>CallbackBehaviorAttribute kullanma  
 Sınıfı kullanarak istemci uygulamasında ki geri arama sözleşmesi uygulamasının yürütme davranışını <xref:System.ServiceModel.CallbackBehaviorAttribute> yapılandırabilir veya genişletebilirsiniz. Bu öznitelik, davranış ve hareket ayarları <xref:System.ServiceModel.ServiceBehaviorAttribute> instancing dışında, sınıf olarak geri arama sınıfı için benzer bir işlev gerçekleştirir.  
  
 Sınıf, <xref:System.ServiceModel.CallbackBehaviorAttribute> geri arama sözleşmesini uygulayan sınıfa uygulanmalıdır. Çift olmayan bir sözleşme uygulamasına <xref:System.InvalidOperationException> uygulanırsa, çalışma zamanında bir özel durum atılır. Aşağıdaki kod örneği, <xref:System.ServiceModel.CallbackBehaviorAttribute> <xref:System.Threading.SynchronizationContext> arama nesnesi üzerinde, mareşal için iş parçacığı <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> belirlemek için nesneyi kullanan <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> bir sınıf gösterir, ileti doğrulama zorlamak için özellik ve hata ayıklama amacıyla hizmete nesneler olarak <xref:System.ServiceModel.FaultException> özel durumlar dönmek için özellik.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Yönetilen Özel Durum Bilgilerinin Akışını Etkinleştirmek için CallbackDebugBehavior kullanma  
 İstemci geri arama nesnesindeki yönetilen özel durum bilgilerinin akışını, özelliği programlı `true` olarak veya bir uygulama yapılandırma dosyasından ayarlayarak hata ayıklama amacıyla hizmete geri döndürebilirsiniz. <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A>  
  
 Özel durum ayrıntıları yetkisiz hizmetlerin kullanabileceği dahili istemci uygulaması hakkındaki bilgileri ortaya çıkardığından, yönetilen özel durum bilgilerinin hizmetlere döndürülme riski olabilir. Buna ek olarak, <xref:System.ServiceModel.Description.CallbackDebugBehavior> özellikleri de programlı olarak ayarlanabilir, ancak dağıtırken <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> devre dışı bırakabilirsiniz unutmak kolay olabilir.  
  
 Söz konusu güvenlik sorunları nedeniyle, aşağıdakiler önerilir:  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> Özelliğin değerini `true`' e ayarlamak için bir uygulama yapılandırma dosyası kullanırsınız.  
  
- Bunu yalnızca kontrollü hata ayıklama senaryolarında yaparsınız.  
  
 Aşağıdaki kod örneği, WCF'ye SOAP iletilerinde istemci geri arama nesnesinden yönetilen özel durum bilgilerini döndürmesini söyleyen bir istemci yapılandırma dosyasını gösterir.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  

## <a name="using-the-clientviabehavior-behavior"></a>ClientViaBehavior Davranışını Kullanma  
 Aktarım kanalının <xref:System.ServiceModel.Description.ClientViaBehavior> oluşturulması gereken Tek düzen kaynak tanımlayıcısını belirtmek için davranışı kullanabilirsiniz. Hemen ağ hedefi iletinin amaçlanan işlemcisi değilse bu davranışı kullanın. Bu, arama uygulaması nihai hedefi mutlaka bilmiyorsa veya hedef `Via` üstbilgi bir adres olmadığında çoklu atlamalı konuşmalara olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Çalışma Zamanı Davranışını Belirtme](specifying-service-run-time-behavior.md)
