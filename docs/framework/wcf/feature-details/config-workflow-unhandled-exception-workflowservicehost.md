---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Iş akışı Işlenmeyen özel durum davranışını WorkflowServiceHost ile yapılandırma'
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 7d32ccf1262895d948cae26f0922adf3003664ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743388"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="a5d2c-103">Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a5d2c-103">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="a5d2c-104">, <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> İçinde barındırılan bir iş akışında işlenmeyen bir özel durum oluşursa gerçekleştirilecek eylemi belirtmenizi sağlayan bir davranıştır <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="a5d2c-104">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="a5d2c-105">Bu konu, bir yapılandırma dosyasında bu davranışın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5d2c-105">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="a5d2c-106">WorkflowUnhandledExceptionBehavior 'ı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a5d2c-106">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="a5d2c-107">`workflowUnhandledException` `behavior` `serviceBehaviors` `action` Aşağıdaki örnekte gösterildiği gibi işlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirtmek için özniteliğini kullanarak bir <> öğesi içindeki bir <> öğesine bir <> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5d2c-107">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="a5d2c-108">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="a5d2c-108">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="a5d2c-109">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a5d2c-109">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="a5d2c-110">Bu davranış, aşağıdaki örnekte gösterildiği gibi, kodda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5d2c-110">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="a5d2c-111">`action`<`workflowUnhandledException`> öğesinin özniteliği aşağıdaki değerlerden birine ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="a5d2c-111">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="a5d2c-112">**iptal**</span><span class="sxs-lookup"><span data-stu-id="a5d2c-112">**abandon**</span></span>  
     <span data-ttu-id="a5d2c-113">Kalıcı örnek durumuna dokunmadan bellekteki örneği iptal eder (diğer bir deyişle, son kalıcı noktaya geri dön).</span><span class="sxs-lookup"><span data-stu-id="a5d2c-113">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="a5d2c-114">**Terk Andsusbeklet**</span><span class="sxs-lookup"><span data-stu-id="a5d2c-114">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="a5d2c-115">Bellekte örneği iptal eder ve kalıcı örneği askıya alınmış olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a5d2c-115">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="a5d2c-116">**İptal**</span><span class="sxs-lookup"><span data-stu-id="a5d2c-116">**cancel**</span></span>  
     <span data-ttu-id="a5d2c-117">Örnek için iptal işleyicileri çağırır ve sonra örnek deposundan da kaldırabilen örneği bellekte tamamlar</span><span class="sxs-lookup"><span data-stu-id="a5d2c-117">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="a5d2c-118">**sonlandırmayı**</span><span class="sxs-lookup"><span data-stu-id="a5d2c-118">**terminate**</span></span>  
     <span data-ttu-id="a5d2c-119">Örneği bellekte tamamlar ve örnek deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a5d2c-119">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="a5d2c-120">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> bkz. [Iş akışı hizmeti konak genişletilebilirliği](workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="a5d2c-120">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d2c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5d2c-121">See also</span></span>

- [<span data-ttu-id="a5d2c-122">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="a5d2c-122">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="a5d2c-123">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a5d2c-123">Workflow Services</span></span>](workflow-services.md)
