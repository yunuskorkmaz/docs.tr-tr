---
title: Etkinlik Uzantıları Kullanma
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 3a9cabda9fe92b2ea4e708da8f853f3029328775
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293292"
---
# <a name="using-activity-extensions"></a>Etkinlik Uzantıları Kullanma

Etkinlikler, konağın iş akışında açıkça Modellenmemiş ek işlevler sağlamasına izin veren iş akışı uygulama uzantılarıyla etkileşime geçebilir.  Bu konu başlığı altında, etkinliğin kaç kez yürütüleneceğini saymak için bir uzantının nasıl oluşturulduğu ve kullanılacağı açıklanmaktadır.

### <a name="to-use-an-activity-extension-to-count-executions"></a>Yürütmeleri saymak için bir etkinlik uzantısı kullanmak için

1. Visual Studio 2010 ' i açın. **Yeni**, **Proje**' yi seçin. **Visual C#** düğümünün altında **iş akışı**' nı seçin.  Şablonlar listesinden **Iş akışı konsol uygulaması** ' nı seçin. Projeyi adlandırın `Extensions` . Projeyi oluşturmak için **Tamam**'a tıklayın.

2. `using` **System. Collections. Generic** ad alanı için program.cs dosyasına bir ifade ekleyin.

    ```csharp
    using System.Collections.Generic;
    ```

3. Program.cs dosyasında, **Executioncountextension** adlı yeni bir sınıf oluşturun. Aşağıdaki kod, **yazmaç** yöntemi çağrıldığında örnek kimliklerini izleyen bir iş akışı uzantısı oluşturur.

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

4. **Executioncountextension** öğesini tüketen bir etkinlik oluşturun. Aşağıdaki kod, çalışma zamanından **Executioncountextension** nesnesini alan ve etkinlik yürütüldüğünde **register** metodunu çağıran bir etkinliği tanımlar.

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

5. Etkinliği program.cs dosyasının **Main** yönteminde uygulayın. Aşağıdaki kod, iki farklı iş akışı oluşturmak, her bir iş akışını birkaç kez yürütmek ve uzantısında yer alan elde edilen verileri göstermek için yöntemler içerir.

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
