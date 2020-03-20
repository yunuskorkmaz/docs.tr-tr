---
title: İş Akışı Yürütme Özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f958e7e112bfddc2740c2605d446493f2d49010
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182659"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="2a3c1-102">İş Akışı Yürütme Özellikleri</span><span class="sxs-lookup"><span data-stu-id="2a3c1-102">Workflow Execution Properties</span></span>
<span data-ttu-id="2a3c1-103">ClR, iş parçacığı yerel depolama (TLS) aracılığıyla her iş parçacığı için bir yürütme bağlamı tutar.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="2a3c1-104">Bu yürütme bağlamı, iş parçacığı kimliği, ortam hareketi ve adlandırılmış yuvalar gibi kullanıcı tanımlı iş parçacığı özelliklerine ek olarak geçerli izin kümesi gibi iyi bilinen iş parçacığı özelliklerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="2a3c1-105">Doğrudan CLR'yi hedefleyen programların aksine, iş akışı programları hiyerarşik olarak iş parçacığı agnostik bir ortamda çalışan etkinliklerin ağaçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="2a3c1-106">Bu, standart TLS mekanizmalarının, belirli bir iş öğesi için kapsamda hangi bağlamın olduğunu belirlemek için doğrudan kullanılamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="2a3c1-107">Örneğin, iki paralel yürütme dalı farklı hareketler kullanabilir, ancak zamanlayıcı yürütmelerini aynı CLR iş parçacığı üzerinde bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="2a3c1-108">İş akışı yürütme özellikleri, bir etkinliğin ortamına bağlamaya özgü özellikler eklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="2a3c1-109">Bu, bir etkinliğin alt ağacı için hangi özelliklerin kapsamda olduğunu beyan etmesine olanak tanır ve ayrıca TLS'nin CLR nesneleri ile düzgün bir şekilde birlikte çalışması için TLS'yi kurmak ve yıkmak için kancalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="2a3c1-110">İş Akışı Yürütme Özellikleri Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="2a3c1-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="2a3c1-111">İş akışı yürütme özellikleri <xref:System.Activities.IExecutionProperty> genellikle arabirimi uygular, ancak <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> iletiye odaklanmış özellikler yerine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="2a3c1-112">Bir iş akışı yürütme özelliği oluşturmak <xref:System.Activities.IExecutionProperty> için, arabirimi uygulayan <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> bir <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>sınıf oluşturmak ve üyeleri ve.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="2a3c1-113">Bu üyeler, herhangi bir alt etkinlik de dahil olmak üzere özelliği içeren etkinliğin her darbe sırasında iş parçacığı yerel depolama düzgün kurmak ve yıkmak için bir fırsat yürütme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="2a3c1-114">Bu örnekte, `ConsoleColorProperty` bir . `Console.ForegroundColor`</span><span class="sxs-lookup"><span data-stu-id="2a3c1-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="2a3c1-115">Etkinlik yazarları bu özelliği, etkinliğin yürütülme geçersiz kılındırına kaydederek kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="2a3c1-116">Bu örnekte, `ConsoleColorScope` `ConsoleColorProperty` geçerli <xref:System.Activities.NativeActivityContext.Properties%2A> <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="2a3c1-117">Aktivitenin vücut çalışma bir darbe başladığında, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> özelliğin yöntemi denir, ve işin nabzı <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> tamamlandığında, denir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="2a3c1-118">Bu örnekte, üç dallı bir <xref:System.Activities.Statements.Parallel> etkinlik kullanan bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="2a3c1-119">İlk iki dal `ConsoleColorScope` etkinliği kullanır ve üçüncü dal kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="2a3c1-120">Her üç dal <xref:System.Activities.Statements.WriteLine> da <xref:System.Activities.Statements.Delay> iki etkinlik ve bir etkinlik içerir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="2a3c1-121"><xref:System.Activities.Statements.Parallel> Etkinlik yürütüldüğünde, dallarda bulunan etkinlikler ara sıra yürütülür, ancak her alt etkinlik yürütülürken doğru `ConsoleColorProperty`konsol rengi .</span><span class="sxs-lookup"><span data-stu-id="2a3c1-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="2a3c1-122">İş akışı çağrıldığızaman, aşağıdaki çıktı konsol penceresine yazılır.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="2a3c1-123">Önceki çıktıda gösterilmese de, konsol penceresindeki her metin satırı belirtilen renkte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="2a3c1-124">İş akışı yürütme özellikleri özel etkinlik yazarları tarafından kullanılabilir ve onlar da <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikler gibi etkinlikler için işleme yönetimi için mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3c1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a3c1-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
