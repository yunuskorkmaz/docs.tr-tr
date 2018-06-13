---
title: 'Nasıl yapılır: iş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 35158c45217e764bc2e27dac26f8d680e5897fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514424"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Nasıl yapılır: iş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir
Bu konuda, iş akışları ve iş akışı hizmetleri kalıcılığını etkinleştirmek açıklar.  
  
## <a name="enable-persistence-for-workflows"></a>İş akışları için kalıcılığı etkinleştir  
 Bir örnek depolama ile ilişkilendirebilirsiniz bir **WorkflowApplication** kullanarak <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği <xref:System.Activities.WorkflowApplication> sınıfı. <xref:System.Activities.WorkflowApplication.Persist%2A> Yöntemi kaydeder veya uygulama ile ilişkili örnek deposuna bir iş akışı devam ettirir. <xref:System.Activities.WorkflowApplication.Unload%2A> Yöntemi bir iş akışı örneği deposuna devam ederse ve bellek örneğinden kaldırır. **Yük** yöntemi bir iş akışı örneği Kalıcılık deposunda saklanan akışı verileri kullanarak belleğe yükler.  
  
 **Devam ettir** yöntemi aşağıdaki adımları gerçekleştirir:  
  
1.  İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.  
  
2.  Devam ederse veya iş akışının Kalıcılık deposuna kaydeder.  
  
3.  İş akışı Zamanlayıcı sürdürür.  
  
 **Unload** yöntemi aşağıdaki adımları gerçekleştirir:  
  
1.  İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.  
  
2.  Devam ederse veya iş akışının Kalıcılık deposuna kaydeder.  
  
3.  İş akışı örneği bellekte siler.  
  
 Her iki **devam ettir** ve **Unload** yöntemleri, iş akışı no-persist bölge çıkar kadar bir iş akışı no-persist bölgesinde ederken engeller. Hayır-kalan bölge tamamlandıktan sonra yöntemi ile devam ettir veya kaldırma işlemi devam eder. No-persist bölge Zaman aşımı süresi bitmeden önce ya da kalıcılığı işlemi çok uzun sürerse tamamlanmazsa bir TimeoutException oluşturulur.  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>İş akışı hizmetleri kodda kalıcılığı etkinleştir  
 **DurableInstancingOptions** üyesi <xref:System.ServiceModel.WorkflowServiceHost> sınıfı adlı bir özelliğe sahiptir **InstanceStore** bir örnek depolama ile ilişkilendirmek için kullanabileceğiniz **WorkflowServiceHost** .  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 Zaman **WorkflowServiceHost** olan açıldı, Kalıcılık otomatik olarak etkinleştirilir **DurableInstancingOptions.InstanceStore** null değil.  
  
 Genellikle, bir hizmet davranışı kullanarak bir iş akışı hizmeti ana bilgisayarı ile kullanılacak somut örnek depolama sağlar **InstanceStore** özelliği. Örneğin, SqlWorkflowInstanceStoreBehavior bir örneğini oluşturur **SqlWorkflowInstanceStore**yapılandırır ve atar **DurableInstancingOptions.InstanceStore**.  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak iş akışı hizmetleri için kalıcılığı etkinleştir  
 Aşağıdaki kod, app.config veya web.config dosyasına ekleyerek bir uygulama yapılandırma dosyası kullanarak Kalıcılık etkinleştirilebilir:  
  
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
