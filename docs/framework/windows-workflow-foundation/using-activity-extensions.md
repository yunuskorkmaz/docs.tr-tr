---
title: Etkinlik Uzantıları Kullanma
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 551ce24db8c0adc8225ac94a1d05f998a26873a9
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988628"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="e3d76-102">Etkinlik Uzantıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e3d76-102">Using Activity Extensions</span></span>
<span data-ttu-id="e3d76-103">Etkinlikler, konağın iş akışında açıkça Modellenmemiş ek işlevler sağlamasına izin veren iş akışı uygulama uzantılarıyla etkileşime geçebilir.</span><span class="sxs-lookup"><span data-stu-id="e3d76-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="e3d76-104">Bu konu başlığı altında, etkinliğin kaç kez yürütüleneceğini saymak için bir uzantının nasıl oluşturulduğu ve kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3d76-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="e3d76-105">Yürütmeleri saymak için bir etkinlik uzantısı kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e3d76-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="e3d76-106">Visual Studio 2010 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="e3d76-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="e3d76-107">**Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e3d76-107">Select **New**, **Project**.</span></span> <span data-ttu-id="e3d76-108">**C# Görsel** düğüm altında **iş akışı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e3d76-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="e3d76-109">Şablonlar listesinden **Iş akışı konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e3d76-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="e3d76-110">Projeyi `Extensions`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e3d76-110">Name the project `Extensions`.</span></span> <span data-ttu-id="e3d76-111">Projeyi oluşturmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e3d76-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="e3d76-112">`using` **System. Collections. Generic** ad alanı için program.cs dosyasına bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3d76-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```csharp
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="e3d76-113">Program.cs dosyasında, **Executioncountextension**adlı yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3d76-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="e3d76-114">Aşağıdaki kod, **yazmaç** yöntemi çağrıldığında örnek kimliklerini izleyen bir iş akışı uzantısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e3d76-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```csharp
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

4. <span data-ttu-id="e3d76-115">**Executioncountextension**öğesini tüketen bir etkinlik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3d76-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="e3d76-116">Aşağıdaki kod, çalışma zamanından **Executioncountextension** nesnesini alan ve etkinlik yürütüldüğünde **register** metodunu çağıran bir etkinliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3d76-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```csharp
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

5. <span data-ttu-id="e3d76-117">Etkinliği program.cs dosyasının **Main** yönteminde uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e3d76-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="e3d76-118">Aşağıdaki kod, iki farklı iş akışı oluşturmak, her bir iş akışını birkaç kez yürütmek ve uzantısında yer alan elde edilen verileri göstermek için yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="e3d76-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```csharp
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
