---
title: İş Akışını Duraklatma ve Sürdürme
ms.date: 03/30/2017
ms.assetid: 11f38339-79c7-4295-b610-24a7223bbf6d
ms.openlocfilehash: dc6bdfe7cc10837fb8721ab12490d244d5ec1ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142972"
---
# <a name="pausing-and-resuming-a-workflow"></a><span data-ttu-id="1cfad-102">İş Akışını Duraklatma ve Sürdürme</span><span class="sxs-lookup"><span data-stu-id="1cfad-102">Pausing and Resuming a Workflow</span></span>
<span data-ttu-id="1cfad-103">İş akışları, yer imleri ve engelleme etkinliklerine <xref:System.Activities.Statements.Delay>yanıt olarak duraklar ve devam eder, ancak iş akışı da açıkça duraklatılmış, boşaltılabilir ve kalıcılık kullanılarak devam ettirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1cfad-103">Workflows will pause and resume in response to bookmarks and blocking activities such as <xref:System.Activities.Statements.Delay>, but a workflow can also be explicitly paused, unloaded, and resumed by using persistence.</span></span>  
  
## <a name="pausing-a-workflow"></a><span data-ttu-id="1cfad-104">İş Akışını Duraklatma</span><span class="sxs-lookup"><span data-stu-id="1cfad-104">Pausing a Workflow</span></span>  
 <span data-ttu-id="1cfad-105">İş akışını duraklatmak <xref:System.Activities.WorkflowApplication.Unload%2A>için .</span><span class="sxs-lookup"><span data-stu-id="1cfad-105">To pause a workflow, use <xref:System.Activities.WorkflowApplication.Unload%2A>.</span></span>  <span data-ttu-id="1cfad-106">Bu yöntem, iş akışının devam edip boşaltmasını <xref:System.TimeoutException> ister ve iş akışı 30 saniye içinde boşaltMazsa bir akış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cfad-106">This method requests that the workflow persist and unload, and will throw a <xref:System.TimeoutException> if the workflow does not unload in 30 seconds.</span></span>  
  
```csharp  
try  
{  
    // attempt to unload will fail if the workflow is idle within a NoPersistZone  
    application.Unload(TimeSpan.FromSeconds(5));  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
## <a name="resuming-a-workflow"></a><span data-ttu-id="1cfad-107">İş Akışını Sürdürme</span><span class="sxs-lookup"><span data-stu-id="1cfad-107">Resuming a Workflow</span></span>  
 <span data-ttu-id="1cfad-108">Daha önce duraklatılmış ve boşaltılan <xref:System.Activities.WorkflowApplication.Load%2A>iş akışını devam ettirmek için .</span><span class="sxs-lookup"><span data-stu-id="1cfad-108">To resume a previously paused and unloaded workflow, use <xref:System.Activities.WorkflowApplication.Load%2A>.</span></span> <span data-ttu-id="1cfad-109">Bu yöntem, kalıcıbir depodan belleğe bir iş akışı yükler.</span><span class="sxs-lookup"><span data-stu-id="1cfad-109">This method loads a workflow from a persistence store into memory.</span></span>  
  
```csharp  
WorkflowApplication application = new WorkflowApplication(activity);  
application.InstanceStore = instanceStore;  
application.Load(id);  
```  
  
## <a name="example"></a><span data-ttu-id="1cfad-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cfad-110">Example</span></span>  
 <span data-ttu-id="1cfad-111">Aşağıdaki kod örneği, kalıcılığı kullanarak bir iş akışını nasıl duraklatacağı ve devam ettirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cfad-111">The following code sample demonstrates how to pause and resume a workflow by using persistence.</span></span>  
  
```csharp  
static string bkName = "bkName";  
static void Main(string[] args)
{  
    StartAndUnloadInstance();  
}  
  
static void StartAndUnloadInstance()
{  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    SqlWorkflowInstanceStore instanceStore = SetupSqlpersistenceStore();  
    wfApp.InstanceStore = instanceStore;  
    wfApp.Extensions.Add(SetupMyFileTrackingParticipant);  
    wfApp.PersistableIdle = (e) => {          ///persists application state and remove it from memory
    return PersistableIdleAction.Unload;  
    };  
    wfApp.Unloaded = (e) => {  
        waitHandler.Set();  
    };  
    Guid id = wfApp.Id;  
    wfApp.Run();  
    waitHandler.WaitOne();  
    LoadAndCompleteInstance(id);  
}  
  
static void LoadAndCompleteInstance(Guid id)
{
    Console.WriteLine("Press <enter> to load the persisted workflow");  
    Console.ReadLine();  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    wfApp.InstanceStore =  
        new SqlWorkflowInstanceStore(ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString());  
    wfApp.Completed = (workflowApplicationCompletedEventArgs) => {  
        Console.WriteLine("\nWorkflowApplication has Completed in the {0} state.",  
            workflowApplicationCompletedEventArgs.CompletionState);  
    };  
    wfApp.Unloaded = (workflowApplicationEventArgs) => {  
        Console.WriteLine("WorkflowApplication has Unloaded\n");  
        waitHandler.Set();  
    };  
    wfApp.Load(id);  
    wfApp.Run();  
    waitHandler.WaitOne();  
}  
  
public static Activity GetDelayedWF()
{  
    return new Sequence {  
        Activities ={  
            new WriteLine{Text="Workflow Started"},  
            new Delay{Duration=TimeSpan.FromSeconds(10)},  
            new WriteLine{Text="Workflow Ended"}  
        }  
    };  
}  
  
private static SqlWorkflowInstanceStore SetupSqlpersistenceStore()
{
     string connectionString = ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString();  
    SqlWorkflowInstanceStore sqlWFInstanceStore = new SqlWorkflowInstanceStore(connectionString);  
    sqlWFInstanceStore.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    InstanceHandle handle = sqlWFInstanceStore.CreateInstanceHandle();  
    InstanceView view = sqlWFInstanceStore.Execute(handle, new CreateWorkflowOwnerCommand(), TimeSpan.FromSeconds(5));  
    handle.Free();  
    sqlWFInstanceStore.DefaultInstanceOwner = view.InstanceOwner;  
    return sqlWFInstanceStore;  
}  
```
