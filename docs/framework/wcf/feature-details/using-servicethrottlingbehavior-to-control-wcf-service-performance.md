---
title: "WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ead2990285f10400cfae11c21bce76a5b6c362f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="8f714-102">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="8f714-102">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>
<span data-ttu-id="8f714-103"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Sınıfı kaç örnekleri sınırlandırmak için kullanabilir ya da oturumları uygulama düzeyinde oluşturduğunuz özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="8f714-103">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="8f714-104">Bu davranış kullanarak performansını ayrıntılandırabilirsiniz, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="8f714-104">Using this behavior, you can fine-tune the performance of your [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="8f714-105">Hizmet örneği ve eşzamanlı çağrıları denetleme</span><span class="sxs-lookup"><span data-stu-id="8f714-105">Controlling Service Instances and Concurrent Calls</span></span>  
 <span data-ttu-id="8f714-106">Kullanım <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> özelliği etkin olarak işleme iletileri en fazla sayısını belirtmek için bir <xref:System.ServiceModel.ServiceHost> sınıfı ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> en fazla sayısını belirtmek için özellik <xref:System.ServiceModel.InstanceContext> hizmet nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8f714-106">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="8f714-107">Bu özellikleri için ayarlar genellikle belirleme uygulamaya karşı çalışan gerçek deneyimi sonra gerçekleşir çünkü yükler, ayarlarını <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> özellikleri genellikle belirtilen bir yapılandırma dosyası kullanılarak uygulama [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="8f714-107">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="8f714-108">Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> ayarlar bir uygulama yapılandırma dosyası sınıfından <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özelliklerini önemsiz bir örnek olarak 1.</span><span class="sxs-lookup"><span data-stu-id="8f714-108">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="8f714-109">Gerçek dünya deneyimi herhangi belirli bir uygulama için en iyi ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="8f714-109">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="8f714-110">Tam çalışma zamanı davranışı değerlerin bağlıdır <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> kaç iletileri bir işlem içinde aynı anda ve yaşam süreleri hizmetinin yürütebilir denetleyen özellikler <xref:System.ServiceModel.InstanceContext> gelen kanal oturumları göre , sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8f714-110">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="8f714-111">Ayrıntılar için bkz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f714-111">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f714-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f714-112">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
