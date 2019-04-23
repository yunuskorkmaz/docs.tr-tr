---
title: 'Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772712"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme
Bu konu, iş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir açıklar.  
  
## <a name="enable-persistence-for-workflows"></a>İş akışları için kalıcılığı etkinleştir  
 Bir örnek deposuyla ilişkilendirebilirsiniz bir **WorkflowApplication** kullanarak <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği <xref:System.Activities.WorkflowApplication> sınıfı. <xref:System.Activities.WorkflowApplication.Persist%2A> Yöntemi kaydederken ya da uygulamayla ilişkili örnek depoya bir iş akışı devam ettirir. <xref:System.Activities.WorkflowApplication.Unload%2A> Yöntemi bir iş akışı örneği deposuna devam ediyorsa ve sonra bellek örneğinden kaldırır. **Yük** yöntemi bir iş akışı örneği sürdürme deposunda saklanan iş akışı verileri kullanarak bellek yükler.  
  
 **Kalan** yöntemi aşağıdaki adımları gerçekleştirir:  
  
1. İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.  
  
2. Devam eden veya iş akışı kalıcılığı deposuna kaydeder.  
  
3. İş akışı Zamanlayıcı sürdürür.  
  
 **Kaldırma** yöntemi aşağıdaki adımları gerçekleştirir:  
  
1. İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.  
  
2. Devam eden veya iş akışı kalıcılığı deposuna kaydeder.  
  
3. İş akışı örneği bellekte siler.  
  
 Her iki **kalan** ve **kaldırma** yöntemleri, iş akışı no-persist bölge çıkana kadar bir iş akışı no-persist bölgesinde ederken engeller. Hayır-kalan bölge tamamlandıktan sonra yöntemi ile kalıcı veya kaldırma işlemi devam eder. Bir TimeoutException no-persist bölge Zaman aşımı dolmadan veya Kalıcılık işlemi çok uzun sürerse tamamlanmazsa oluşturulur.  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>Kod içinde iş akışı hizmetleri için kalıcılığı etkinleştir  
 **DurableInstancingOptions** üyesi <xref:System.ServiceModel.WorkflowServiceHost> sınıfında adlı bir özellik **InstanceStore** bir örnek deposuna ile ilişkilendirmek için kullanabileceğiniz **WorkflowServiceHost** .  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 Zaman **WorkflowServiceHost** olan açıldı, Kalıcılık otomatik olarak etkinleştirilir **DurableInstancingOptions.InstanceStore** null değil.  
  
 Genellikle, bir hizmet davranışını kullanarak bir iş akışı hizmeti konağı ile kullanılacak somut örnek depolama sağlar **InstanceStore** özelliği. Örneğin, SqlWorkflowInstanceStoreBehavior örneği oluşturur **SqlWorkflowInstanceStore**yapılandırır ve buna atayan **DurableInstancingOptions.InstanceStore**.  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak iş akışı hizmetleri için kalıcılığı etkinleştir  
 Kalıcılık için app.config veya web.config dosyanızda aşağıdaki kodu ekleyerek bir uygulama yapılandırma dosyası kullanılarak etkinleştirilebilir:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
