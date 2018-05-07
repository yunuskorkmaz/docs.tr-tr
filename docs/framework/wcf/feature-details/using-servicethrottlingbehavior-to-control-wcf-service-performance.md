---
title: WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: b54d1d6146b9751fdd12502771de01fe52854c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Sınıfı kaç örnekleri sınırlandırmak için kullanabilir ya da oturumları uygulama düzeyinde oluşturduğunuz özellikler sunar. Bu davranış kullanarak, Windows Communication Foundation (WCF) uygulamanızın performansını ince ayar yapabilirsiniz.  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Hizmet örneği ve eşzamanlı çağrıları denetleme  
 Kullanım <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> özelliği etkin olarak işleme iletileri en fazla sayısını belirtmek için bir <xref:System.ServiceModel.ServiceHost> sınıfı ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> en fazla sayısını belirtmek için özellik <xref:System.ServiceModel.InstanceContext> hizmet nesneleri.  
  
 Bu özellikleri için ayarlar genellikle belirleme uygulamaya karşı çalışan gerçek deneyimi sonra gerçekleşir çünkü yükler, ayarlarını <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> özellikleri genellikle belirtilen bir yapılandırma dosyası kullanılarak uygulama [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) öğesi.  
  
 Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> ayarlar bir uygulama yapılandırma dosyası sınıfından <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özelliklerini önemsiz bir örnek olarak 1. Gerçek dünya deneyimi herhangi belirli bir uygulama için en iyi ayarları belirler.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Tam çalışma zamanı davranışı değerlerin bağlıdır <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> kaç iletileri bir işlem içinde aynı anda ve yaşam süreleri hizmetinin yürütebilir denetleyen özellikler <xref:System.ServiceModel.InstanceContext> gelen kanal oturumları göre , sırasıyla.  
  
 Ayrıntılar için bkz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
