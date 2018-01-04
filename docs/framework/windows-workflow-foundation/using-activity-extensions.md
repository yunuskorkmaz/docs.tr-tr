---
title: "Etkinlik uzantıları kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bc2e498a4073f6f0881e011b00de6ac89f4f2fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-activity-extensions"></a>Etkinlik uzantıları kullanma
Etkinlikler iş akışında açıkça Modellenen değil ek işlevsellik sağlamak için ana iş akışı uygulama uzantılar etkileşim kurabilirsiniz.  Bu konu, oluşturma ve etkinlik yürütür sayısı saymak için uzantı kullanma açıklar.  
  
### <a name="to-use-an-activity-extension-to-count-executions"></a>Bir etkinlik uzantısını yürütmeleri saymak için kullanma  
  
1.  Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]. Seçin **yeni**, **proje**. Altında **Visual C#** düğümü, select **iş akışı**.  Seçin **iş akışı konsol uygulaması** şablonları listesinden. Proje adı `Extensions`. Tıklatın **Tamam** projesi oluşturmak için.  
  
2.  Ekleme bir `using` deyimi için Program.cs dosyasında **System.Collections.Generic** ad alanı.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
3.  Program.cs dosyasında adlı yeni bir sınıf oluşturun **ExecutionCountExtension**. Aşağıdaki kod örneği kimlikleri izleyen bir iş akışı uzantısı oluşturur, kendi **kaydetmek** yöntemi çağrılır.  
  
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
  
4.  Tüketen bir etkinlik oluşturmak **ExecutionCountExtension**. Aşağıdaki kod alır bir etkinlik tanımlar **ExecutionCountExtension** çağrıları ve çalışma zamanı nesnesinden kendi **kaydetmek** etkinlik yürüttüğünde yöntemi.  
  
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
  
5.  Etkinlik uygulayan **ana** program.cs dosyasının yöntemi. Aşağıdaki kod iki farklı iş akışları oluşturmak, birkaç kez her iş akışını yürütmek ve uzantısı'nda bulunan sonuç verileri görüntülemek için yöntemler içerir.  
  
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
