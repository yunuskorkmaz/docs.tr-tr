---
title: WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 9cc5141805504bc46391105f475860b032f12d32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600237"
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
