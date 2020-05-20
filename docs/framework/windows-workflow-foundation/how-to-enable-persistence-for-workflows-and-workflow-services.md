---
title: 'Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme'
description: İş akışları ve iş akışı hizmetleri için bir yapılandırma dosyası kullanarak, SQL Iş akışı örnek deposunu yapılandırmayı nasıl yapılandıracağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421520"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="2e589-103">Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için Kalıcılığı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2e589-103">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="2e589-104">Bu konuda, iş akışları ve iş akışı hizmetleri için kalıcılığın nasıl etkinleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2e589-104">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="2e589-105">Iş akışları için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="2e589-105">Enable Persistence for Workflows</span></span>

<span data-ttu-id="2e589-106">Sınıfının özelliğini kullanarak bir örnek depoyu bir **WorkflowApplication** ile ilişkilendirebilirsiniz <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="2e589-106">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="2e589-107"><xref:System.Activities.WorkflowApplication.Persist%2A>Yöntemi, bir iş akışını uygulamayla ilişkili örnek deposuna kaydeder veya devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="2e589-107">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="2e589-108"><xref:System.Activities.WorkflowApplication.Unload%2A>Yöntemi, örnek deposunda bir iş akışı devam ettirir ve sonra örneği bellekten kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2e589-108">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="2e589-109">**Load** yöntemi, örnek kalıcılık deposunda depolanan iş akışı verilerini kullanarak bir iş akışını belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="2e589-109">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="2e589-110">**Persist** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2e589-110">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="2e589-111">İş akışı zamanlayıcısını duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="2e589-111">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="2e589-112">İş akışını devam ettirir veya kalıcılık deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2e589-112">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="2e589-113">İş akışı zamanlayıcısını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="2e589-113">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="2e589-114">**Unload** yöntemi aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2e589-114">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="2e589-115">İş akışı zamanlayıcısını duraklatır ve iş akışı boşta durumuna girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="2e589-115">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="2e589-116">İş akışını devam ettirir veya kalıcılık deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2e589-116">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="2e589-117">İş akışı örneğini bellekte bırakır.</span><span class="sxs-lookup"><span data-stu-id="2e589-117">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="2e589-118">**Kalıcı** ve **kaldırma** yöntemlerinin her ikisi de iş akışı kalıcı olmayan bir bölgeden çıkana kadar kalıcı olmayan bir bölgede olduğunda engellenir.</span><span class="sxs-lookup"><span data-stu-id="2e589-118">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="2e589-119">Kalıcı olmayan bölge tamamlandıktan sonra yöntem kalıcı veya kaldırma işlemine devam eder.</span><span class="sxs-lookup"><span data-stu-id="2e589-119">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="2e589-120">Kalıcı olmayan bölge, zaman aşımı geçmeden önce tamamlanmazsa veya kalıcılık işlemi çok uzun sürerse, bir TimeoutException atılır.</span><span class="sxs-lookup"><span data-stu-id="2e589-120">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="2e589-121">Koddaki Iş akışı hizmetleri için kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="2e589-121">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="2e589-122">Sınıfın **DurableInstancingOptions** üyesi, <xref:System.ServiceModel.WorkflowServiceHost> bir örnek deposunu **WorkflowServiceHost**Ile ilişkilendirmek için kullanabileceğiniz, **InstanceStore** adlı bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2e589-122">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="2e589-123">**WorkflowServiceHost** açıldığında, **DurableInstancingOptions. InstanceStore** null değilse Kalıcılık otomatik olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e589-123">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="2e589-124">Genellikle, bir hizmet davranışı, bir iş akışı hizmet ana bilgisayarıyla, **InstanceStore** özelliği kullanılarak kullanılacak somut örnek deposunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e589-124">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="2e589-125">Örneğin, Sqlworkflowcestorebehavior, **SqlWorkflowInstanceStore**'un bir örneğini oluşturur, yapılandırır ve **DurableInstancingOptions. InstanceStore**öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="2e589-125">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="2e589-126">Uygulama yapılandırma dosyası kullanarak Iş akışı hizmetleri için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2e589-126">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="2e589-127">Kalıcı hale getirme, App. config veya Web. config dosyanıza aşağıdaki kodu ekleyerek bir uygulama yapılandırma dosyası kullanılarak etkinleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="2e589-127">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

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
