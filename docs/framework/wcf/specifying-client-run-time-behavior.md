---
title: "İstemci Çalışma Zamanı Davranışını Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8c05dc56ec8fac0a77b1a21536d815b5b65f830
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-client-run-time-behavior"></a>İstemci Çalışma Zamanı Davranışını Belirtme
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]istemciler, ister [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmetleri, istemci uygulaması uyacak şekilde çalışma zamanı davranışını değiştirmek için yapılandırılabilir. Üç öznitelikler, istemci çalışma zamanı davranışını belirtmek için kullanılabilir. Çift yönlü istemci geri araması nesneleri kullanabileceğiniz <xref:System.ServiceModel.CallbackBehaviorAttribute> ve <xref:System.ServiceModel.Description.CallbackDebugBehavior> kendi çalışma zamanı davranışını değiştirmek için öznitelikler. Başka bir öznitelik <xref:System.ServiceModel.Description.ClientViaBehavior>, hemen ağ hedef mantıksal hedef ayırmak için kullanılır. Ayrıca, çift yönlü istemci geri araması türlerine bazı hizmet tarafı davranışları kullanabilirsiniz. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hizmeti çalışma zamanı davranışını belirtme](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>CallbackBehaviorAttribute kullanma  
 Yapılandırma veya bir istemci uygulaması bir geri çağırma sözleşme uygulamasında yürütme davranışını kullanarak genişletme <xref:System.ServiceModel.CallbackBehaviorAttribute> sınıfı. Bu öznitelik geri çağırma sınıfı için benzer bir işlevi gerçekleştiren <xref:System.ServiceModel.ServiceBehaviorAttribute> davranışı ve işlem ayarları depolamasına dışında sınıfı.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> Sınıfı geri çağırma sözleşme uygulayan sınıfa uygulanması gerekir. Bir nonduplex sözleşmesi uygulama uyguladıysanız bir <xref:System.InvalidOperationException> çalışma zamanında özel durum. Aşağıdaki örnekte gösterildiği kod bir <xref:System.ServiceModel.CallbackBehaviorAttribute> kullanan bir geri çağırma nesnesi üzerinde sınıf <xref:System.Threading.SynchronizationContext> için hazırlamak için iş parçacığı belirlemek için nesne <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> ileti doğrulama zorlamak için özellik ve <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> döndürülecek özelliği özel durumlar olarak <xref:System.ServiceModel.FaultException> hata ayıklama amacıyla hizmet nesneleri.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Yönetilen özel durum bilgi akışını etkinleştirmek için CallbackDebugBehavior kullanma  
 Bir istemci geri çağırma nesnesindeki tekrar ayarlayarak hata ayıklama amacıyla hizmet yönetilen özel durum bilgi akışını etkinleştirebilirsiniz <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliğine `true` program aracılığıyla ya da bir uygulama yapılandırma dosyası.  
  
 Yönetilen özel durum bilgilerini hizmetlerine, bir güvenlik riski olabilir, özel durum ayrıntıları bilgilerini kullanıma sunmak için döndürme hakkında iç İstemci Hizmetleri yetkisiz uygulamasını kullanabilirsiniz. Ayrıca, ancak <xref:System.ServiceModel.Description.CallbackDebugBehavior> özellikleri de ayarlanabilir program aracılığıyla, devre dışı bırakmak unuttunuz kolay olabilir <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> dağıtırken.  
  
 İlgili güvenlik sorunları nedeniyle, kesinlikle önerilir:  
  
-   Uygulama yapılandırma dosyası değerini ayarlamak için kullandığınız <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliğine `true`.  
  
-   Denetimli senaryolar hata ayıklama yaptığınız yalnızca.  
  
 Aşağıdaki kod örneğinde bir istemci bildirir yapılandırma dosyası gösterir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yönetilen özel durum bilgilerini bir istemciden geri çağırma nesnesi SOAP iletilerinde dönün.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>ClientViaBehavior davranışı kullanma  
 Kullanabileceğiniz <xref:System.ServiceModel.Description.ClientViaBehavior> davranışı taşıma kanalı oluşturulmalıdır Tekdüzen Kaynak Tanımlayıcısı belirtin. Bu davranış, hemen Ağ hedefi iletinin hedeflenen işlemci olmadığında kullanın. Bu çoklu atlamalı görüşmeleri veya çağrı yapan uygulamanın ultimate hedef emin değilseniz zaman sağlar hedef `Via` üstbilgi bir adresi değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Çalışma Zamanı Davranışını Belirtme](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
