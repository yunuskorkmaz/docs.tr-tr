---
title: Etkinlik Uzantıları Kullanma
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321295"
---
# <a name="using-activity-extensions"></a>Etkinlik Uzantıları Kullanma
Etkinlikler, ana iş akışında açıkça modellenmiş değil ek işlevler sağlamasına olanak tanıyan bir iş akışı uygulama uzantıları ile etkileşim kurabilir.  Bu konu, bir etkinliği yürütür sayısını saymak için bir uzantı oluşturup kullanacağınızı açıklar.

### <a name="to-use-an-activity-extension-to-count-executions"></a>Yürütme sayısı için bir etkinlik uzantısını kullanma

1. Visual Studio 2010'u açın. Seçin **yeni**, **proje**. Altında **Visual C#** düğümünü **iş akışı**.  Seçin **iş akışı konsol uygulaması** şablonları listesinden. Projeyi adlandırın `Extensions`. Tıklayın **Tamam** projeyi oluşturmak için.

2. Ekleme bir `using` deyimi Program.cs dosyasındaki **System.Collections.Generic** ad alanı.

    ```
    using System.Collections.Generic;
    ```

3. Program.cs dosyasında adlı yeni bir sınıf oluşturun **ExecutionCountExtension**. Aşağıdaki kod örnek kimlikleri izleyen bir iş akışı uzantısı oluşturur, kendi **kaydetme** yöntemi çağrılır.

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

4. Kullanan bir etkinlik oluşturursunuz **ExecutionCountExtension**. Aşağıdaki kod alır bir etkinlik tanımlar **ExecutionCountExtension** çağrıları ve çalışma zamanı nesneden kendi **kaydetme** etkinlik yürütüldüğünde yöntemi.

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

5. Etkinlik uygulayan **ana** program.cs dosyasının yöntemi. Aşağıdaki kod, iki farklı iş akışları oluşturmak, her bir iş akışı birkaç kez yürütün ve uzantısı'nda bulunan sonuç verileri görüntülemek için yöntemler içerir.

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
