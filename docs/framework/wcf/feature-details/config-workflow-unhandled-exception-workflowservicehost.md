---
title: 'Nasıl yapılır: İş akışı yapılandırma işlenmeyen özel durum davranışını WorkflowServiceHost ile'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 9a13bb9390e891295491722898bd780bc1cac587
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636163"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="1a34b-102">Nasıl yapılır: İş akışı yapılandırma işlenmeyen özel durum davranışını WorkflowServiceHost ile</span><span class="sxs-lookup"><span data-stu-id="1a34b-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="1a34b-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Barındırılan iş akışı içinde işlenmeyen bir özel durum oluşursa yapılacak eylem belirtmenize olanak tanıyan bir davranış <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1a34b-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1a34b-104">Bu konuda, bir yapılandırma dosyasında bu davranışı yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a34b-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="1a34b-105">WorkflowUnhandledExceptionBehavior yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="1a34b-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="1a34b-106">Ekleme bir <`workflowUnhandledException`> öğesinde bir <`behavior`> öğesi içinde bir <`serviceBehaviors`> öğesini kullanarak `action` aşağıdaki örnekte gösterildiği gibi işlenmeyen bir özel durum ortaya çıktığında gerçekleştirilecek eylemi belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1a34b-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="1a34b-107">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="1a34b-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="1a34b-108">Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="1a34b-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="1a34b-109">Bu davranış, aşağıdaki örnekte gösterildiği gibi kodda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a34b-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="1a34b-110">`action` Özniteliği <`workflowUnhandledException`> öğesi aşağıdaki değerlerden birine ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="1a34b-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="1a34b-111">**İptal Et**</span><span class="sxs-lookup"><span data-stu-id="1a34b-111">**abandon**</span></span>  
     <span data-ttu-id="1a34b-112">(Son kalan noktasına geri olduğu gibi) kalıcı örneği durumu dokunmadan bellekte örneği durdurur.</span><span class="sxs-lookup"><span data-stu-id="1a34b-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="1a34b-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="1a34b-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="1a34b-114">Bellekte bir örneği durdurur ve yakında askıya alınacak kalıcı örneğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1a34b-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="1a34b-115">**İptal**</span><span class="sxs-lookup"><span data-stu-id="1a34b-115">**cancel**</span></span>  
     <span data-ttu-id="1a34b-116">Örneğinin iptal işleyicisi çağırır ve ardından örneğinde bellek, ayrıca örnek Mağazası'ndan kaldırabilir tamamlar</span><span class="sxs-lookup"><span data-stu-id="1a34b-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="1a34b-117">**sonlandırma**</span><span class="sxs-lookup"><span data-stu-id="1a34b-117">**terminate**</span></span>  
     <span data-ttu-id="1a34b-118">Bellek örneğinde tamamlanır ve örnek deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1a34b-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="1a34b-119">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="1a34b-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a34b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a34b-120">See also</span></span>
- [<span data-ttu-id="1a34b-121">İş Akışı Hizmeti Konak Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="1a34b-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="1a34b-122">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1a34b-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
