---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: aec2fd80e10ae1959b29c0883d51c4045517d792
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957253"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="75c17-102">Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="75c17-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="75c17-103">, <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> İçinde<xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışında işlenmeyen bir özel durum oluşursa gerçekleştirilecek eylemi belirtmenizi sağlayan bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="75c17-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="75c17-104">Bu konu, bir yapılandırma dosyasında bu davranışın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75c17-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="75c17-105">WorkflowUnhandledExceptionBehavior 'ı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="75c17-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="75c17-106">Aşağıdaki örnekte gösterildiği`workflowUnhandledException`gibi işlenmeyen bir özel durum`behavior`oluştuğunda gerçekleştirilecek eylemi belirtmek için`serviceBehaviors` `action` özniteliğini kullanarak bir < > öğesi içindeki bir < > öğesine bir < > öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="75c17-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="75c17-107">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="75c17-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="75c17-108">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="75c17-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="75c17-109">Bu davranış, aşağıdaki örnekte gösterildiği gibi, kodda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="75c17-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="75c17-110">`action` <`workflowUnhandledException`> Öğesinin özniteliği aşağıdaki değerlerden birine ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="75c17-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="75c17-111">**iptal**</span><span class="sxs-lookup"><span data-stu-id="75c17-111">**abandon**</span></span>  
     <span data-ttu-id="75c17-112">Kalıcı örnek durumuna dokunmadan bellekteki örneği iptal eder (diğer bir deyişle, son kalıcı noktaya geri dön).</span><span class="sxs-lookup"><span data-stu-id="75c17-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="75c17-113">**Terk Andsusbeklet**</span><span class="sxs-lookup"><span data-stu-id="75c17-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="75c17-114">Bellekte örneği iptal eder ve kalıcı örneği askıya alınmış olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="75c17-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="75c17-115">**İptal**</span><span class="sxs-lookup"><span data-stu-id="75c17-115">**cancel**</span></span>  
     <span data-ttu-id="75c17-116">Örnek için iptal işleyicileri çağırır ve sonra örnek deposundan da kaldırabilen örneği bellekte tamamlar</span><span class="sxs-lookup"><span data-stu-id="75c17-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="75c17-117">**sonlandırmayı**</span><span class="sxs-lookup"><span data-stu-id="75c17-117">**terminate**</span></span>  
     <span data-ttu-id="75c17-118">Örneği bellekte tamamlar ve örnek deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="75c17-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="75c17-119">Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>daha fazla bilgi için bkz. [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="75c17-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c17-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75c17-120">See also</span></span>

- [<span data-ttu-id="75c17-121">İş Akışı Hizmeti Konak Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="75c17-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="75c17-122">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="75c17-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
