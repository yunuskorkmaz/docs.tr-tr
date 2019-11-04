---
title: 'Nasıl yapılır: Iş akışları ve Iş akışı hizmetleri için kalıcılığı etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460886"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="f15fe-102">Nasıl yapılır: Iş akışları ve Iş akışı hizmetleri için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f15fe-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="f15fe-103">Bu konuda, iş akışları ve iş akışı hizmetleri için kalıcılığın nasıl etkinleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f15fe-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="f15fe-104">Iş akışları için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="f15fe-104">Enable Persistence for Workflows</span></span>

<span data-ttu-id="f15fe-105"><xref:System.Activities.WorkflowApplication> sınıfının <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliğini kullanarak bir örnek depoyu bir **WorkflowApplication** ile ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f15fe-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="f15fe-106"><xref:System.Activities.WorkflowApplication.Persist%2A> yöntemi bir iş akışını uygulamayla ilişkili örnek deposuna kaydeder veya devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="f15fe-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="f15fe-107"><xref:System.Activities.WorkflowApplication.Unload%2A> yöntemi bir iş akışını örnek deposuna devam ettirir ve sonra örneği bellekten kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f15fe-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="f15fe-108">**Load** yöntemi, örnek kalıcılık deposunda depolanan iş akışı verilerini kullanarak bir iş akışını belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="f15fe-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="f15fe-109">**Persist** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="f15fe-109">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="f15fe-110">İş akışı zamanlayıcısını duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="f15fe-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="f15fe-111">İş akışını devam ettirir veya kalıcılık deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f15fe-111">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="f15fe-112">İş akışı zamanlayıcısını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="f15fe-112">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="f15fe-113">**Unload** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="f15fe-113">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="f15fe-114">İş akışı zamanlayıcısını duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="f15fe-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="f15fe-115">İş akışını devam ettirir veya kalıcılık deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f15fe-115">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="f15fe-116">İş akışı örneğini bellekte bırakır.</span><span class="sxs-lookup"><span data-stu-id="f15fe-116">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="f15fe-117">**Kalıcı** ve **kaldırma** yöntemlerinin her ikisi de iş akışı kalıcı olmayan bir bölgeden çıkana kadar kalıcı olmayan bir bölgede olduğunda engellenir.</span><span class="sxs-lookup"><span data-stu-id="f15fe-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="f15fe-118">Kalıcı olmayan bölge tamamlandıktan sonra yöntem kalıcı veya kaldırma işlemine devam eder.</span><span class="sxs-lookup"><span data-stu-id="f15fe-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="f15fe-119">Kalıcı olmayan bölge, zaman aşımı geçmeden önce tamamlanmazsa veya kalıcılık işlemi çok uzun sürerse, bir TimeoutException atılır.</span><span class="sxs-lookup"><span data-stu-id="f15fe-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="f15fe-120">Koddaki Iş akışı hizmetleri için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="f15fe-120">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="f15fe-121"><xref:System.ServiceModel.WorkflowServiceHost> sınıfının **DurableInstancingOptions** üyesi, bir örnek deposunu **WorkflowServiceHost**ile Ilişkilendirmek için kullanabileceğiniz, **InstanceStore** adlı bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f15fe-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="f15fe-122">**WorkflowServiceHost** açıldığında, **DurableInstancingOptions. InstanceStore** null değilse Kalıcılık otomatik olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f15fe-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="f15fe-123">Genellikle, bir hizmet davranışı, bir iş akışı hizmet ana bilgisayarıyla, **InstanceStore** özelliği kullanılarak kullanılacak somut örnek deposunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="f15fe-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="f15fe-124">Örneğin, Sqlworkflowcestorebehavior, **SqlWorkflowInstanceStore**'un bir örneğini oluşturur, yapılandırır ve **DurableInstancingOptions. InstanceStore**öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="f15fe-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="f15fe-125">Uygulama yapılandırma dosyası kullanarak Iş akışı hizmetleri için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f15fe-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="f15fe-126">Kalıcı hale getirme, App. config veya Web. config dosyanıza aşağıdaki kodu ekleyerek bir uygulama yapılandırma dosyası kullanılarak etkinleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="f15fe-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
