---
description: 'Daha fazla bilgi edinin: bir Iş akışını duraklatma ve sürdürme'
title: İş Akışını Duraklatma ve Sürdürme
ms.date: 03/30/2017
ms.assetid: 11f38339-79c7-4295-b610-24a7223bbf6d
ms.openlocfilehash: 787dc2e2ddac03a059df30798645d561cb57437b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787896"
---
# <a name="pausing-and-resuming-a-workflow"></a><span data-ttu-id="037e2-103">İş Akışını Duraklatma ve Sürdürme</span><span class="sxs-lookup"><span data-stu-id="037e2-103">Pausing and Resuming a Workflow</span></span>

<span data-ttu-id="037e2-104">İş akışları, gibi yer işaretlerine ve engelleme etkinliklerine yanıt olarak duraklatıp devam eder <xref:System.Activities.Statements.Delay> , ancak bir iş akışı Ayrıca kalıcı olarak duraklatılabilir, kaldırılabilirler ve kalıcılık kullanılarak devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="037e2-104">Workflows will pause and resume in response to bookmarks and blocking activities such as <xref:System.Activities.Statements.Delay>, but a workflow can also be explicitly paused, unloaded, and resumed by using persistence.</span></span>  
  
## <a name="pausing-a-workflow"></a><span data-ttu-id="037e2-105">Bir Iş akışını duraklatma</span><span class="sxs-lookup"><span data-stu-id="037e2-105">Pausing a Workflow</span></span>  

 <span data-ttu-id="037e2-106">Bir iş akışını duraklatmak için kullanın <xref:System.Activities.WorkflowApplication.Unload%2A> .</span><span class="sxs-lookup"><span data-stu-id="037e2-106">To pause a workflow, use <xref:System.Activities.WorkflowApplication.Unload%2A>.</span></span>  <span data-ttu-id="037e2-107">Bu yöntem iş akışının devam ediyor ve bellekten kaldırılmasına ve <xref:System.TimeoutException> iş akışı 30 saniye içinde bellekten kaldırıldığında bir oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="037e2-107">This method requests that the workflow persist and unload, and will throw a <xref:System.TimeoutException> if the workflow does not unload in 30 seconds.</span></span>  
  
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
  
## <a name="resuming-a-workflow"></a><span data-ttu-id="037e2-108">Iş akışı sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="037e2-108">Resuming a Workflow</span></span>  

 <span data-ttu-id="037e2-109">Daha önce duraklatılmış ve yüklenmemiş bir iş akışını sürdürmesini sağlamak için kullanın <xref:System.Activities.WorkflowApplication.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="037e2-109">To resume a previously paused and unloaded workflow, use <xref:System.Activities.WorkflowApplication.Load%2A>.</span></span> <span data-ttu-id="037e2-110">Bu yöntem bir kalıcılık deposundan bir iş akışını belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="037e2-110">This method loads a workflow from a persistence store into memory.</span></span>  
  
```csharp  
WorkflowApplication application = new WorkflowApplication(activity);  
application.InstanceStore = instanceStore;  
application.Load(id);  
```  
  
## <a name="example"></a><span data-ttu-id="037e2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="037e2-111">Example</span></span>  

 <span data-ttu-id="037e2-112">Aşağıdaki kod örneği, kalıcılığı kullanarak bir iş akışının nasıl duraklatılacağını ve sürdürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="037e2-112">The following code sample demonstrates how to pause and resume a workflow by using persistence.</span></span>  
  
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
