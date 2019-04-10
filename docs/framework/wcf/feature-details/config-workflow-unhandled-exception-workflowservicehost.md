---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: cd3729019b5371b5313bba3814758c723c0d448a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318753"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="58b27-102">Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="58b27-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="58b27-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Barındırılan iş akışı içinde işlenmeyen bir özel durum oluşursa yapılacak eylem belirtmenize olanak tanıyan bir davranış <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="58b27-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="58b27-104">Bu konuda, bir yapılandırma dosyasında bu davranışı yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58b27-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="58b27-105">WorkflowUnhandledExceptionBehavior yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="58b27-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="58b27-106">Ekleme bir <`workflowUnhandledException`> öğesinde bir <`behavior`> öğesi içinde bir <`serviceBehaviors`> öğesini kullanarak `action` aşağıdaki örnekte gösterildiği gibi işlenmeyen bir özel durum ortaya çıktığında gerçekleştirilecek eylemi belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="58b27-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="58b27-107">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="58b27-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="58b27-108">Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="58b27-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="58b27-109">Bu davranış, aşağıdaki örnekte gösterildiği gibi kodda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="58b27-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="58b27-110">`action` Özniteliği <`workflowUnhandledException`> öğesi aşağıdaki değerlerden birine ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="58b27-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     **<span data-ttu-id="58b27-111">İptal Et</span><span class="sxs-lookup"><span data-stu-id="58b27-111">abandon</span></span>**  
     <span data-ttu-id="58b27-112">(Son kalan noktasına geri olduğu gibi) kalıcı örneği durumu dokunmadan bellekte örneği durdurur.</span><span class="sxs-lookup"><span data-stu-id="58b27-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     **<span data-ttu-id="58b27-113">abandonAndSuspend</span><span class="sxs-lookup"><span data-stu-id="58b27-113">abandonAndSuspend</span></span>**  
     <span data-ttu-id="58b27-114">Bellekte bir örneği durdurur ve yakında askıya alınacak kalıcı örneğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="58b27-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     **<span data-ttu-id="58b27-115">İptal</span><span class="sxs-lookup"><span data-stu-id="58b27-115">cancel</span></span>**  
     <span data-ttu-id="58b27-116">Örneğinin iptal işleyicisi çağırır ve ardından örneğinde bellek, ayrıca örnek Mağazası'ndan kaldırabilir tamamlar</span><span class="sxs-lookup"><span data-stu-id="58b27-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     **<span data-ttu-id="58b27-117">terminate</span><span class="sxs-lookup"><span data-stu-id="58b27-117">terminate</span></span>**  
     <span data-ttu-id="58b27-118">Bellek örneğinde tamamlanır ve örnek deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="58b27-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="58b27-119">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="58b27-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b27-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58b27-120">See also</span></span>

- [<span data-ttu-id="58b27-121">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="58b27-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="58b27-122">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="58b27-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
