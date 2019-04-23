---
title: Etkinlik Uzantıları Kullanma
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768968"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="d795a-102">Etkinlik Uzantıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d795a-102">Using Activity Extensions</span></span>
<span data-ttu-id="d795a-103">Etkinlikler, ana iş akışında açıkça modellenmiş değil ek işlevler sağlamasına olanak tanıyan bir iş akışı uygulama uzantıları ile etkileşim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="d795a-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="d795a-104">Bu konu, bir etkinliği yürütür sayısını saymak için bir uzantı oluşturup kullanacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d795a-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="d795a-105">Yürütme sayısı için bir etkinlik uzantısını kullanma</span><span class="sxs-lookup"><span data-stu-id="d795a-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="d795a-106">Visual Studio 2010'u açın.</span><span class="sxs-lookup"><span data-stu-id="d795a-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="d795a-107">Seçin **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="d795a-107">Select **New**, **Project**.</span></span> <span data-ttu-id="d795a-108">Altında **Visual C#** düğümünü **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="d795a-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="d795a-109">Seçin **iş akışı konsol uygulaması** şablonları listesinden.</span><span class="sxs-lookup"><span data-stu-id="d795a-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="d795a-110">Projeyi adlandırın `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="d795a-110">Name the project `Extensions`.</span></span> <span data-ttu-id="d795a-111">Tıklayın **Tamam** projeyi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d795a-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="d795a-112">Ekleme bir `using` deyimi Program.cs dosyasındaki **System.Collections.Generic** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d795a-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="d795a-113">Program.cs dosyasında adlı yeni bir sınıf oluşturun **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="d795a-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="d795a-114">Aşağıdaki kod örnek kimlikleri izleyen bir iş akışı uzantısı oluşturur, kendi **kaydetme** yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d795a-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

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

4. <span data-ttu-id="d795a-115">Kullanan bir etkinlik oluşturursunuz **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="d795a-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="d795a-116">Aşağıdaki kod alır bir etkinlik tanımlar **ExecutionCountExtension** çağrıları ve çalışma zamanı nesneden kendi **kaydetme** etkinlik yürütüldüğünde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d795a-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

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

5. <span data-ttu-id="d795a-117">Etkinlik uygulayan **ana** program.cs dosyasının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d795a-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="d795a-118">Aşağıdaki kod, iki farklı iş akışları oluşturmak, her bir iş akışı birkaç kez yürütün ve uzantısı'nda bulunan sonuç verileri görüntülemek için yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="d795a-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

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
