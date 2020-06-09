---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 3881d1af21dcc0c211c6738162360e522648d949
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593600"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="2b7d4-102">Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2b7d4-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="2b7d4-103">, <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> İçinde barındırılan bir iş akışında işlenmeyen bir özel durum oluşursa gerçekleştirilecek eylemi belirtmenizi sağlayan bir davranıştır <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="2b7d4-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="2b7d4-104">Bu konu, bir yapılandırma dosyasında bu davranışın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b7d4-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="2b7d4-105">WorkflowUnhandledExceptionBehavior 'ı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="2b7d4-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="2b7d4-106">`workflowUnhandledException` `behavior` `serviceBehaviors` `action` Aşağıdaki örnekte gösterildiği gibi işlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirtmek için özniteliğini kullanarak bir <> öğesi içindeki bir <> öğesine bir <> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2b7d4-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="2b7d4-107">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="2b7d4-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="2b7d4-108">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2b7d4-108">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="2b7d4-109">Bu davranış, aşağıdaki örnekte gösterildiği gibi, kodda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b7d4-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="2b7d4-110">`action`<`workflowUnhandledException`> öğesinin özniteliği aşağıdaki değerlerden birine ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="2b7d4-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="2b7d4-111">**iptal**</span><span class="sxs-lookup"><span data-stu-id="2b7d4-111">**abandon**</span></span>  
     <span data-ttu-id="2b7d4-112">Kalıcı örnek durumuna dokunmadan bellekteki örneği iptal eder (diğer bir deyişle, son kalıcı noktaya geri dön).</span><span class="sxs-lookup"><span data-stu-id="2b7d4-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="2b7d4-113">**Terk Andsusbeklet**</span><span class="sxs-lookup"><span data-stu-id="2b7d4-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="2b7d4-114">Bellekte örneği iptal eder ve kalıcı örneği askıya alınmış olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="2b7d4-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="2b7d4-115">**İptal**</span><span class="sxs-lookup"><span data-stu-id="2b7d4-115">**cancel**</span></span>  
     <span data-ttu-id="2b7d4-116">Örnek için iptal işleyicileri çağırır ve sonra örnek deposundan da kaldırabilen örneği bellekte tamamlar</span><span class="sxs-lookup"><span data-stu-id="2b7d4-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="2b7d4-117">**sonlandırmayı**</span><span class="sxs-lookup"><span data-stu-id="2b7d4-117">**terminate**</span></span>  
     <span data-ttu-id="2b7d4-118">Örneği bellekte tamamlar ve örnek deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2b7d4-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="2b7d4-119">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> bkz. [Iş akışı hizmeti konak genişletilebilirliği](workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="2b7d4-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7d4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b7d4-120">See also</span></span>

- [<span data-ttu-id="2b7d4-121">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="2b7d4-121">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="2b7d4-122">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2b7d4-122">Workflow Services</span></span>](workflow-services.md)
