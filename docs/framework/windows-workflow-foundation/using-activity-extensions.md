---
title: Etkinlik uzantıları kullanma
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 32c465ae42a1f0238fab7bba5ea795486db3b562
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517231"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="0c344-102">Etkinlik uzantıları kullanma</span><span class="sxs-lookup"><span data-stu-id="0c344-102">Using Activity Extensions</span></span>
<span data-ttu-id="0c344-103">Etkinlikler iş akışında açıkça Modellenen değil ek işlevsellik sağlamak için ana iş akışı uygulama uzantılar etkileşim kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c344-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="0c344-104">Bu konu, oluşturma ve etkinlik yürütür sayısı saymak için uzantı kullanma açıklar.</span><span class="sxs-lookup"><span data-stu-id="0c344-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>  
  
### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="0c344-105">Bir etkinlik uzantısını yürütmeleri saymak için kullanma</span><span class="sxs-lookup"><span data-stu-id="0c344-105">To use an activity extension to count executions</span></span>  
  
1.  <span data-ttu-id="0c344-106">Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c344-106">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span> <span data-ttu-id="0c344-107">Seçin **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="0c344-107">Select **New**, **Project**.</span></span> <span data-ttu-id="0c344-108">Altında **Visual C#** düğümü, select **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="0c344-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="0c344-109">Seçin **iş akışı konsol uygulaması** şablonları listesinden.</span><span class="sxs-lookup"><span data-stu-id="0c344-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="0c344-110">Proje adı `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="0c344-110">Name the project `Extensions`.</span></span> <span data-ttu-id="0c344-111">Tıklatın **Tamam** projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0c344-111">Click **OK** to create the project.</span></span>  
  
2.  <span data-ttu-id="0c344-112">Ekleme bir `using` deyimi için Program.cs dosyasında **System.Collections.Generic** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0c344-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
3.  <span data-ttu-id="0c344-113">Program.cs dosyasında adlı yeni bir sınıf oluşturun **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="0c344-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="0c344-114">Aşağıdaki kod örneği kimlikleri izleyen bir iş akışı uzantısı oluşturur, kendi **kaydetmek** yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0c344-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>  
  
    ```  
    // This extension collects a list of workflow Ids  
    public class ExecutionCountExtension  
    {  
        IList<Guid> instances = new List<Guid>();  
  
        public int ExecutionCount  
        {  
            get  
            {  
                return this.instances.Count;  
            }  
        }  
  
        public IEnumerable<Guid> InstanceIds  
        {  
            get  
            {  
                return this.instances;  
            }  
        }  
  
        public void Register(Guid activityInstanceId)  
        {  
            if (!this.instances.Contains<Guid>(activityInstanceId))  
            {  
                instances.Add(activityInstanceId);  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="0c344-115">Tüketen bir etkinlik oluşturmak **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="0c344-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="0c344-116">Aşağıdaki kod alır bir etkinlik tanımlar **ExecutionCountExtension** çağrıları ve çalışma zamanı nesnesinden kendi **kaydetmek** etkinlik yürüttüğünde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c344-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>  
  
    ```  
    // Activity that consumes an extension provided by the host. If the extension is available  
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)  
    public class MyActivity: CodeActivity  
    {  
        protected override void Execute(CodeActivityContext context)  
        {  
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();  
            if (ext != null)  
            {  
                ext.Register(context.WorkflowInstanceId);                         
            }  
  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="0c344-117">Etkinlik uygulayan **ana** program.cs dosyasının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c344-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="0c344-118">Aşağıdaki kod iki farklı iş akışları oluşturmak, birkaç kez her iş akışını yürütmek ve uzantısı'nda bulunan sonuç verileri görüntülemek için yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="0c344-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>  
  
    ```  
    class Program  
    {  
        // Creates a workflow that uses the activity that consumes the extension  
        static Activity CreateWorkflow1()  
        {  
            return new Sequence  
            {  
                Activities =  
                {  
                    new MyActivity()  
                }  
            };  
        }  
  
        // Creates a workflow that uses two instances of the activity that consumes the extension  
        static Activity CreateWorkflow2()  
        {  
            return new Sequence  
            {  
                Activities =  
                {  
                    new MyActivity(),  
                    new MyActivity()  
                }  
            };  
        }  
  
        static void Main(string[] args)  
        {  
            // create the extension   
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();  
  
            // configure the first invoker and execute 3 times  
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());  
            invoker.Extensions.Add(executionCountExt);                          
            invoker.Invoke();  
            invoker.Invoke();  
            invoker.Invoke();  
  
            // configure the second invoker and execute 2 times  
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());  
            invoker2.Extensions.Add(executionCountExt);  
            invoker2.Invoke();  
            invoker2.Invoke();  
  
            // show the data in the extension  
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);  
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));  
        }  
    }  
    ```
