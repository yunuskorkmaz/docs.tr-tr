---
title: "İş akışı yürütme özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d119d721964df7ea1c007eadd17a8db54f4f8cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="75909-102">İş akışı yürütme özellikleri</span><span class="sxs-lookup"><span data-stu-id="75909-102">Workflow Execution Properties</span></span>
<span data-ttu-id="75909-103">İş parçacığı yerel depolaması (TLS), her iş parçacığı için yürütme bağlamı CLR tutar.</span><span class="sxs-lookup"><span data-stu-id="75909-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="75909-104">Bu yürütme bağlamı ortam işlem iş parçacığı kimliği gibi bilinen iş parçacığı özellikleri yönetir ve ayrıca gibi kullanıcı tanımlı iş parçacığı özellikleri için geçerli izni yuvaları adlı.</span><span class="sxs-lookup"><span data-stu-id="75909-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="75909-105">Doğrudan CLR hedefleme programlar, iş akışını bir iş parçacığı belirsiz ortamında yürütme etkinliklerin hiyerarşik olarak kapsamlı ağaçları programlardır.</span><span class="sxs-lookup"><span data-stu-id="75909-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="75909-106">Bu, standart TLS mekanizmaları hangi bağlam belirli iş öğesi kapsamında olduğunu belirlemek için doğrudan kullanılamaz olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="75909-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="75909-107">Örneğin, iki paralel yürütme dallarını farklı işlemler kullanabilir henüz Zamanlayıcı aynı CLR iş parçacığı üzerinde kendi yürütme Interleave.</span><span class="sxs-lookup"><span data-stu-id="75909-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="75909-108">İş akışı yürütme özellikleri bir etkinliğin ortama bağlam belirli özellikleri eklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="75909-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="75909-109">Bu bir etkinlik bildirmek hangi özellikler kendi alt ağaç kapsamında ve ayrıca ayarlama ve CLR nesneleriyle birlikte düzgün çalışmak için TLS aşağı hattının kaldırılması kancaları sağlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="75909-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="75909-110">Oluşturma ve iş akışı yürütme özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="75909-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="75909-111">İş akışı yürütme özellikleri genellikle uygulama <xref:System.Activities.IExecutionProperty> mesajlaşmayı odaklı özellikleri uygulayabilir, arabirim <xref:System.ServiceModel.Activities.ISendMessageCallback> ve <xref:System.ServiceModel.Activities.IReceiveMessageCallback> yerine.</span><span class="sxs-lookup"><span data-stu-id="75909-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="75909-112">Bir iş akışı yürütme özelliği oluşturmak için uygulayan bir sınıf oluşturun <xref:System.Activities.IExecutionProperty> arabirim ve üyeleri uygulayan <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> ve <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="75909-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="75909-113">Bu üyeler yürütme özelliği düzgün şekilde ayarlayabilir ve her alt etkinlikler dahil olmak üzere bu özelliği içerir etkinliğin çalışma pulse sırasında iş parçacığı yerel depolaması ayırma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="75909-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="75909-114">Bu örnekte, bir `ConsoleColorProperty` bu kümeleri oluşturulan `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="75909-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75909-115">Bu konudaki aşağıdaki kod örneği, dayanır [yürütme özellikleri](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="75909-115">The following example code in this topic is based on the [Execution Properties](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) sample.</span></span>  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 <span data-ttu-id="75909-116">Etkinlik yazarlar, bu özellik içinde kaydederek kullanabilir etkinliğe ilişkin geçersiz kılma yürütün.</span><span class="sxs-lookup"><span data-stu-id="75909-116">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="75909-117">Bu örnekte, bir `ConsoleColorScope` etkinliği kaydeden tanımlanır `ConsoleColorProperty` ekleyerek <xref:System.Activities.NativeActivityContext.Properties%2A> geçerli koleksiyonunu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="75909-117">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="75909-118">Etkinliğin gövdesi, çalışmanın pulse başladığında <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> özelliğinin yöntemi çağrılır ve pulse iş tamamlandığında, <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="75909-118">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="75909-119">Bu örnekte, bir iş akışı kullanan oluşturulur bir <xref:System.Activities.Statements.Parallel> üç dalları etkinlikle.</span><span class="sxs-lookup"><span data-stu-id="75909-119">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="75909-120">İlk iki dalları kullanma `ConsoleColorScope` etkinliği ve üçüncü dalı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="75909-120">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="75909-121">Tüm üç iki dalları <xref:System.Activities.Statements.WriteLine> etkinlikleri ve <xref:System.Activities.Statements.Delay> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="75909-121">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="75909-122">Zaman <xref:System.Activities.Statements.Parallel> etkinlik yürütür, bir araya eklemeli şekilde dallarda içerdiği etkinlikleri yürütmek, ancak her alt etkinlik yürütür gibi doğru konsol renk tarafından uygulanan `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="75909-122">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =   
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =   
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="75909-123">İş akışı çağrıldığında, aşağıdaki çıkış konsol penceresine yazılır.</span><span class="sxs-lookup"><span data-stu-id="75909-123">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="75909-124">Önceki çıktısında gösterilmese de, her konsol penceresinde metin satırının belirtilen renkte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="75909-124">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="75909-125">İş akışı yürütme özellikleri özel etkinlik yazarlar tarafından kullanılabilir ve ayrıca tanıtıcısı yönetimi etkinlikleri için mekanizması gibi sağlarlar <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="75909-125">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75909-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75909-126">See Also</span></span>  
 <xref:System.Activities.IExecutionProperty>  
 <xref:System.Activities.IPropertyRegistrationCallback>  
 <xref:System.Activities.RegistrationContext>
