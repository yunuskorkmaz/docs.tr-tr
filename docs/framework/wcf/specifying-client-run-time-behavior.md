---
title: İstemci Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f750978eaa617a5505bb27a1535797320a76b0d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164378"
---
# <a name="specifying-client-run-time-behavior"></a>İstemci Çalışma Zamanı Davranışını Belirtme
Windows Communication Foundation (WCF) Hizmetleri gibi Windows Communication Foundation (WCF) istemciler, istemci uygulaması uyacak şekilde çalışma zamanı davranışını değiştirmek için yapılandırılabilir. Üç öznitelikler, istemci çalışma zamanı davranışını belirtmek için kullanılabilir. Çift yönlü istemci geri çağırma nesnelerinin kullanabileceğiniz <xref:System.ServiceModel.CallbackBehaviorAttribute> ve <xref:System.ServiceModel.Description.CallbackDebugBehavior> kendi çalışma zamanı davranışını değiştirmek için öznitelikler. Başka bir öznitelik <xref:System.ServiceModel.Description.ClientViaBehavior>, hemen bir ağ hedef mantıksal hedef ayırmak için kullanılabilir. Ayrıca, çift yönlü istemci geri çağırma türlerini bazı hizmet tarafı davranışları kullanabilirsiniz. Daha fazla bilgi için [hizmet çalışma zamanı davranışını belirtme](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>CallbackBehaviorAttribute kullanma  
 Yapılandırma veya bir istemci uygulamasındaki bir geri çağırma anlaşması uygulaması yürütme davranışını kullanarak genişletme <xref:System.ServiceModel.CallbackBehaviorAttribute> sınıfı. Bu öznitelik geri çağırma sınıfı için benzer bir işlev gerçekleştirir <xref:System.ServiceModel.ServiceBehaviorAttribute> davranışı ve işlem ayarları depolamasına dışında sınıfı.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> Sınıfı geri çağırma anlaşması uygulayan bir sınıf için uygulanması gerekir. Nonduplex sözleşme uygulamasına uygulandığında bir <xref:System.InvalidOperationException> çalışma zamanında özel durum harekete geçirilir. Aşağıdaki kod örnekte gösterildiği bir <xref:System.ServiceModel.CallbackBehaviorAttribute> kullanan bir geri çağırma nesnesi üzerindeki sınıf <xref:System.Threading.SynchronizationContext> belirlemek için hazırlamak için iş parçacığı nesnesine <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> ileti doğrulama zorlamak için özellik ve <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> döndürülecek özelliği özel durumlar olarak <xref:System.ServiceModel.FaultException> hata ayıklama amacıyla hizmet nesneleri.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Yönetilen özel durum bilgilerinin akışını etkinleştirmek için CallbackDebugBehavior kullanma  
 İstemci geri çağırma nesnesi ayarlayarak hata ayıklama amacıyla yeniden hizmetine yönetilen özel durum bilgilerinin akışını etkinleştirebilirsiniz <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliğini `true` programlı olarak veya bir uygulama yapılandırma dosyası.  
  
 Yönetilen özel durum bilgilerini Hizmetleri için bir güvenlik riski olabilir, çünkü özel durum ayrıntıları bilgilerin açığa çıkmasına neden döndüren iç İstemci Hizmetleri yetkisiz uygulamasını kullanabilirsiniz. Buna karşın <xref:System.ServiceModel.Description.CallbackDebugBehavior> özellikleri de ayarlanabilir programlı olarak, devre dışı bırakmak unutmak çok kolaydır olabilir <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> dağıtırken.  
  
 İlgili güvenlik sorunları nedeniyle, kesinlikle önerilir:  
  
-   Değerini ayarlamak için kullandığınız bir uygulama yapılandırma dosyası <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliğini `true`.  
  
-   Hata ayıklama senaryoları denetlenen durumlarında yalnızca.  
  
 Aşağıdaki kod örneği, bir istemci yönetilen özel durum bilgilerini bir istemciden geri çağırma nesnesi SOAP iletileri döndürmek için WCF yönlendiren yapılandırma dosyası gösterir.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>ClientViaBehavior davranışını kullanarak  
 Kullanabileceğiniz <xref:System.ServiceModel.Description.ClientViaBehavior> davranışını taşıma kanalının oluşturulmalıdır Tekdüzen Kaynak tanımlayıcısını belirtin. Anlık ağ hedef iletinin hedeflenen işlemci olmadığında bu davranışı kullanın. Bu çoklu atlamalı yapılan görüşmeler arama uygulaması ultimate hedef emin değilseniz ne zaman veya zaman sağlar hedef `Via` üst bilgisi bir adres değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Çalışma Zamanı Davranışını Belirtme](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
