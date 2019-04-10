---
title: WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: e42f44b5fa103d5c083bdce3086b6499c5bb3673
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211523"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Sınıfı kaç örnekler sınırlamak için kullanabilirsiniz veya oturumları uygulama düzeyinde oluşturulan özellikleri gösterir. Bu davranışı'nı kullanarak Windows Communication Foundation (WCF) uygulamanızın performansını hassas ayarlamalar yapabilirsiniz.  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Hizmet örnekleri ve eş zamanlı çağrılar denetleme  
 Kullanım <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> özelliği arasında etkin bir şekilde işlenen ileti sayısını belirtmek için bir <xref:System.ServiceModel.ServiceHost> sınıfı ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> en büyük sayısını belirtmek için özellik <xref:System.ServiceModel.InstanceContext> hizmet nesneleri.  
  
 Genellikle bu özellikleri ayarlarını belirleme uygulamaya karşı çalışan gerçek deneyiminden sonra yer aldığı için yükler, ayarlarını <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> özellikleri genellikle belirtilen bir yapılandırma dosyası kullanılarak uygulama [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) öğesi.  
  
 Aşağıdaki kod örneği, kullanımını gösterir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> sınıfı bir uygulama yapılandırma dosyasından ayarlar <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özellikleri basit bir örnek olarak 1. Gerçek dünyaya herhangi bir uygulama için en iyi ayarları belirler.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Tam çalışma zamanı davranışını değerlerin bağlıdır <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> ileti sayısını bir işlem içinde aynı anda ve hizmet ömrü yürütebilir denetleyen özellikler <xref:System.ServiceModel.InstanceContext> gelen kanal oturumları göre , sırasıyla.  
  
 Ayrıntılar için bkz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
