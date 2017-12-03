---
title: "Nasıl yapılır: iş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1db45ecad833c4c05ba240569da9c85271e0b69e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="cad1c-102">Nasıl yapılır: iş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="cad1c-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="cad1c-103">Bu konuda, iş akışları ve iş akışı hizmetleri kalıcılığını etkinleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="cad1c-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="cad1c-104">İş akışları için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="cad1c-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="cad1c-105">Bir örnek depolama ile ilişkilendirebilirsiniz bir **WorkflowApplication** kullanarak <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği <xref:System.Activities.WorkflowApplication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cad1c-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="cad1c-106"><xref:System.Activities.WorkflowApplication.Persist%2A> Yöntemi kaydeder veya uygulama ile ilişkili örnek deposuna bir iş akışı devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="cad1c-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="cad1c-107"><xref:System.Activities.WorkflowApplication.Unload%2A> Yöntemi bir iş akışı örneği deposuna devam ederse ve bellek örneğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cad1c-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="cad1c-108">**Yük** yöntemi bir iş akışı örneği Kalıcılık deposunda saklanan akışı verileri kullanarak belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="cad1c-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="cad1c-109">**Devam ettir** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="cad1c-109">The **Persist** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="cad1c-110">İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="cad1c-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="cad1c-111">Devam ederse veya iş akışının Kalıcılık deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cad1c-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="cad1c-112">İş akışı Zamanlayıcı sürdürür.</span><span class="sxs-lookup"><span data-stu-id="cad1c-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="cad1c-113">**Unload** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="cad1c-113">The **Unload** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="cad1c-114">İş akışı Zamanlayıcı duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="cad1c-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="cad1c-115">Devam ederse veya iş akışının Kalıcılık deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cad1c-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="cad1c-116">İş akışı örneği bellekte siler.</span><span class="sxs-lookup"><span data-stu-id="cad1c-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="cad1c-117">Her iki **devam ettir** ve **Unload** yöntemleri, iş akışı no-persist bölge çıkar kadar bir iş akışı no-persist bölgesinde ederken engeller.</span><span class="sxs-lookup"><span data-stu-id="cad1c-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="cad1c-118">Hayır-kalan bölge tamamlandıktan sonra yöntemi ile devam ettir veya kaldırma işlemi devam eder.</span><span class="sxs-lookup"><span data-stu-id="cad1c-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="cad1c-119">No-persist bölge Zaman aşımı süresi bitmeden önce ya da kalıcılığı işlemi çok uzun sürerse tamamlanmazsa bir TimeoutException oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cad1c-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="cad1c-120">İş akışı hizmetleri kodda kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="cad1c-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="cad1c-121">**DurableInstancingOptions** üyesi <xref:System.ServiceModel.WorkflowServiceHost> sınıfı adlı bir özelliğe sahiptir **InstanceStore** bir örnek depolama ile ilişkilendirmek için kullanabileceğiniz **WorkflowServiceHost** .</span><span class="sxs-lookup"><span data-stu-id="cad1c-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="cad1c-122">Zaman **WorkflowServiceHost** olan açıldı, Kalıcılık otomatik olarak etkinleştirilir **DurableInstancingOptions.InstanceStore** null değil.</span><span class="sxs-lookup"><span data-stu-id="cad1c-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="cad1c-123">Genellikle, bir hizmet davranışı kullanarak bir iş akışı hizmeti ana bilgisayarı ile kullanılacak somut örnek depolama sağlar **InstanceStore** özelliği.</span><span class="sxs-lookup"><span data-stu-id="cad1c-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="cad1c-124">Örneğin, SqlWorkflowInstanceStoreBehavior bir örneğini oluşturur **SqlWorkflowInstanceStore**yapılandırır ve atar **DurableInstancingOptions.InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="cad1c-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="cad1c-125">Uygulama yapılandırma dosyası kullanarak iş akışı hizmetleri için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="cad1c-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="cad1c-126">Aşağıdaki kod, app.config veya web.config dosyasına ekleyerek bir uygulama yapılandırma dosyası kullanarak Kalıcılık etkinleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="cad1c-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
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
