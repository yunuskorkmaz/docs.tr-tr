---
title: WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 44cc924de0c3079bb2f8125a7ac63fa494d4aca1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289418"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma

<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>Sınıfı, uygulama düzeyinde kaç örnek veya oturum oluşturulduğunu sınırlandırmak için kullanabileceğiniz özellikleri sunar. Bu davranışı kullanarak, Windows Communication Foundation (WCF) uygulamanızın performansı üzerinde ince ayar yapabilirsiniz.  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Hizmet örnekleri ve eşzamanlı çağrılar denetleniyor  

 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>Bir sınıf üzerinde etkin olarak işlenen en fazla ileti sayısını <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> hizmette en fazla nesne sayısını belirtmek için özelliğini kullanın <xref:System.ServiceModel.InstanceContext> .  
  
 Bu özelliklerin ayarlarının belirlenmesi genellikle uygulamayı yüklere karşı çalıştırmanın gerçek dünya deneyiminden sonra gerçekleştiğinden, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> özelliklerin ayarları genellikle öğesi kullanılarak bir uygulama yapılandırma dosyasında belirtilir [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) .  
  
 Aşağıdaki kod örneği <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> ,,, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özelliklerini önemsiz bir örnek olarak 1 olarak ayarlayan bir uygulama yapılandırma dosyasından sınıfın kullanımını gösterir. Gerçek hayatta deneyim, belirli bir uygulama için en iyi ayarları belirler.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Tam çalışma zamanı davranışı, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliklerinin, bir kerede bir işlem içinde nasıl yürütümeyeceğini ve hizmetin yaşam sürelerini <xref:System.ServiceModel.InstanceContext> sırasıyla gelen kanal oturumlarına göre denetleyen ve özelliklerin değerlerine bağlıdır.  
  
 Ayrıntılar için bkz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> . ve.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
