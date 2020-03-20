---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185318"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="bc978-102">Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bc978-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="bc978-103">Bu <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> davranış, 'de barındırılan bir iş akışı içinde işlenmemiş bir özel <xref:System.ServiceModel.Activities.WorkflowServiceHost>durum oluşursa yapılacak eylemi belirtmenizi sağlayan bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="bc978-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="bc978-104">Bu konu, yapılandırma dosyasında bu davranışın nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc978-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="bc978-105">İş Akışını yapılandırmak içinUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="bc978-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="bc978-106"><`serviceBehaviors`> `workflowUnhandledException` öğesi içindeki `behavior` <> öğesine, işlenmemiş `action` bir özel durum aşağıdaki örnekte gösterildiği gibi meydana geldiğinde yapılacak eylemi belirtmek için özniteliği kullanarak <bir> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bc978-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="bc978-107">Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="bc978-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="bc978-108">Daha fazla bilgi için Bkz. [Basitleştirilmiş Yapılandırma.](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="bc978-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="bc978-109">Bu davranış, aşağıdaki örnekte gösterildiği gibi kod olarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc978-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="bc978-110"><`action` `workflowUnhandledException`> öğesinin özniteliği aşağıdaki değerlerden birine ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="bc978-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="bc978-111">**Terk**</span><span class="sxs-lookup"><span data-stu-id="bc978-111">**abandon**</span></span>  
     <span data-ttu-id="bc978-112">Kalıcı örnek durumuna dokunmadan bellekteki örneği iptal eder (diğer bir deyişle, son kalıcı noktaya geri dön).</span><span class="sxs-lookup"><span data-stu-id="bc978-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="bc978-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="bc978-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="bc978-114">Bellekteki örneği iptal eder ve askıya alınması için kalıcı örneği güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="bc978-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="bc978-115">**İptal**</span><span class="sxs-lookup"><span data-stu-id="bc978-115">**cancel**</span></span>  
     <span data-ttu-id="bc978-116">Örnek için iptal işleyicilerini çağırır ve ardından örnek mağazadan kaldırabilecek şekilde bellekteki örneği tamamlar</span><span class="sxs-lookup"><span data-stu-id="bc978-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="bc978-117">**Sonlandır**</span><span class="sxs-lookup"><span data-stu-id="bc978-117">**terminate**</span></span>  
     <span data-ttu-id="bc978-118">Bellekteki örneği tamamlar ve örnek deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bc978-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="bc978-119">Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>daha fazla bilgi için Bkz. [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği.](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="bc978-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc978-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc978-120">See also</span></span>

- [<span data-ttu-id="bc978-121">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="bc978-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="bc978-122">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="bc978-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
