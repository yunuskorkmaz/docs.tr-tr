---
title: 'Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340158"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="69aae-102">Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="69aae-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="69aae-103">Bu konu, iş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir açıklar.</span><span class="sxs-lookup"><span data-stu-id="69aae-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="69aae-104">İş akışları için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="69aae-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="69aae-105">Bir örnek deposuyla ilişkilendirebilirsiniz bir **WorkflowApplication** kullanarak <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği <xref:System.Activities.WorkflowApplication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="69aae-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="69aae-106"><xref:System.Activities.WorkflowApplication.Persist%2A> Yöntemi kaydederken ya da uygulamayla ilişkili örnek depoya bir iş akışı devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="69aae-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="69aae-107"><xref:System.Activities.WorkflowApplication.Unload%2A> Yöntemi bir iş akışı örneği deposuna devam ediyorsa ve sonra bellek örneğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="69aae-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="69aae-108">**Yük** yöntemi bir iş akışı örneği sürdürme deposunda saklanan iş akışı verileri kullanarak bellek yükler.</span><span class="sxs-lookup"><span data-stu-id="69aae-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="69aae-109">**Kalan** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="69aae-109">The **Persist** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="69aae-110">İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="69aae-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="69aae-111">Devam eden veya iş akışı kalıcılığı deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="69aae-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="69aae-112">İş akışı Zamanlayıcı sürdürür.</span><span class="sxs-lookup"><span data-stu-id="69aae-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="69aae-113">**Kaldırma** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="69aae-113">The **Unload** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="69aae-114">İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="69aae-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="69aae-115">Devam eden veya iş akışı kalıcılığı deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="69aae-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="69aae-116">İş akışı örneği bellekte siler.</span><span class="sxs-lookup"><span data-stu-id="69aae-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="69aae-117">Her iki **kalan** ve **kaldırma** yöntemleri, iş akışı no-persist bölge çıkana kadar bir iş akışı no-persist bölgesinde ederken engeller.</span><span class="sxs-lookup"><span data-stu-id="69aae-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="69aae-118">Hayır-kalan bölge tamamlandıktan sonra yöntemi ile kalıcı veya kaldırma işlemi devam eder.</span><span class="sxs-lookup"><span data-stu-id="69aae-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="69aae-119">Bir TimeoutException no-persist bölge Zaman aşımı dolmadan veya Kalıcılık işlemi çok uzun sürerse tamamlanmazsa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="69aae-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="69aae-120">Kod içinde iş akışı hizmetleri için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="69aae-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="69aae-121">**DurableInstancingOptions** üyesi <xref:System.ServiceModel.WorkflowServiceHost> sınıfında adlı bir özellik **InstanceStore** bir örnek deposuna ile ilişkilendirmek için kullanabileceğiniz **WorkflowServiceHost** .</span><span class="sxs-lookup"><span data-stu-id="69aae-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="69aae-122">Zaman **WorkflowServiceHost** olan açıldı, Kalıcılık otomatik olarak etkinleştirilir **DurableInstancingOptions.InstanceStore** null değil.</span><span class="sxs-lookup"><span data-stu-id="69aae-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="69aae-123">Genellikle, bir hizmet davranışını kullanarak bir iş akışı hizmeti konağı ile kullanılacak somut örnek depolama sağlar **InstanceStore** özelliği.</span><span class="sxs-lookup"><span data-stu-id="69aae-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="69aae-124">Örneğin, SqlWorkflowInstanceStoreBehavior örneği oluşturur **SqlWorkflowInstanceStore**yapılandırır ve buna atayan **DurableInstancingOptions.InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="69aae-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="69aae-125">Uygulama yapılandırma dosyası kullanarak iş akışı hizmetleri için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="69aae-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="69aae-126">Kalıcılık için app.config veya web.config dosyanızda aşağıdaki kodu ekleyerek bir uygulama yapılandırma dosyası kullanılarak etkinleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="69aae-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
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
