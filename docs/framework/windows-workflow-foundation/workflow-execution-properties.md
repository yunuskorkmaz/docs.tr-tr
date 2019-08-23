---
title: İş Akışı Yürütme Özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 61bf53d9cab3ddefae3709958bd1e445fb4e69dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913605"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="82758-102">İş Akışı Yürütme Özellikleri</span><span class="sxs-lookup"><span data-stu-id="82758-102">Workflow Execution Properties</span></span>
<span data-ttu-id="82758-103">İş parçacığı yerel depolaması (TLS) aracılığıyla CLR her iş parçacığı için bir yürütme bağlamı tutar.</span><span class="sxs-lookup"><span data-stu-id="82758-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="82758-104">Bu yürütme bağlamı iş parçacığı kimliği, ortam işlemi ve geçerli izin kümesi gibi bilinen iş parçacığı özelliklerinin yanı sıra adlandırılmış yuvalar gibi Kullanıcı tanımlı iş parçacığı özelliklerine ek olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="82758-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="82758-105">Programların CLR 'yi doğrudan hedeflemesini, iş akışı programlarının aksine, iş parçacığı belirsiz bir ortamda yürütülen etkinliklerin hiyerarşik olarak kapsamlı ağaçları vardır.</span><span class="sxs-lookup"><span data-stu-id="82758-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="82758-106">Bu, belirli bir iş öğesi için kapsamda hangi bağlamın olduğunu belirlemek üzere Standart TLS mekanizmalarının doğrudan kullanılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="82758-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="82758-107">Örneğin, yürütmenin iki paralel dalı farklı işlemler kullanabilir, ancak Zamanlayıcı, yürütmelerini aynı CLR iş parçacığı üzerinde ayırmada sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="82758-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="82758-108">İş akışı yürütme özellikleri, bir etkinliğin ortamına bağlama özgü özellikler eklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="82758-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="82758-109">Bu, bir etkinliğin alt ağacı için kapsamda hangi özelliklerin olduğunu bildirme ve ayrıca CLR nesneleriyle düzgün şekilde birlikte çalışmak üzere TLS ayarlama ve test etme için kancalar sağladığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="82758-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="82758-110">Iş akışı yürütme özellikleri oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="82758-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="82758-111">İş akışı yürütme özellikleri genellikle <xref:System.Activities.IExecutionProperty> arabirimini uygular, ancak mesajlaşmaya odaklanan özellikler de uygulayabilir <xref:System.ServiceModel.Activities.IReceiveMessageCallback> <xref:System.ServiceModel.Activities.ISendMessageCallback> ve bunun yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="82758-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="82758-112">Bir iş akışı yürütme özelliği oluşturmak için, <xref:System.Activities.IExecutionProperty> arabirimini uygulayan ve üyeleri <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> ve <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>uygulayan bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82758-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="82758-113">Bu Üyeler, tüm alt etkinlikler dahil olmak üzere, özelliği içeren etkinliğin her bir aşamasında iş parçacığı yerel depolama alanını düzgün bir şekilde ayarlama ve ayırma fırsatı ile yürütme özelliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82758-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="82758-114">Bu örnekte, ' ı `ConsoleColorProperty` `Console.ForegroundColor`ayarlayan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82758-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="82758-115">Etkinlik yazarları bu özelliği etkinliğin yürütme geçersiz kılması ile kaydederek kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="82758-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="82758-116">Bu örnekte, öğesini geçerli `ConsoleColorScope` `ConsoleColorProperty` <xref:System.Activities.NativeActivityContext.Properties%2A> birkoleksiyonunaekleyerekkaydeden<xref:System.Activities.NativeActivityContext>bir etkinlik tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="82758-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="82758-117">Etkinliğin gövdesi bir iş <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> darbesi başlattığında, özelliğin yöntemi çağrılır ve iş darbesi tamamlandığında <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> , çağırılır.</span><span class="sxs-lookup"><span data-stu-id="82758-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="82758-118">Bu örnekte, üç dalla bir <xref:System.Activities.Statements.Parallel> etkinlik kullanan bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82758-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="82758-119">İlk iki dal `ConsoleColorScope` etkinliği kullanır ve üçüncü dal değildir.</span><span class="sxs-lookup"><span data-stu-id="82758-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="82758-120">Üç dal de iki <xref:System.Activities.Statements.WriteLine> etkinlik ve bir <xref:System.Activities.Statements.Delay> etkinlik içerir.</span><span class="sxs-lookup"><span data-stu-id="82758-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="82758-121">Etkinlik yürütüldüğünde, dallardaki etkinlikler araya eklemeli bir şekilde yürütülür, ancak her alt etkinlik her bir alt etkinlik `ConsoleColorProperty`tarafından çalıştırıldığında doğru konsol rengi tarafından uygulanır. <xref:System.Activities.Statements.Parallel></span><span class="sxs-lookup"><span data-stu-id="82758-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="82758-122">İş akışı çağrıldığında, aşağıdaki çıktı konsol penceresine yazılır.</span><span class="sxs-lookup"><span data-stu-id="82758-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="82758-123">Önceki çıktıda gösterilmese de, konsol penceresindeki her metin satırı, belirtilen renkte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82758-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="82758-124">İş akışı yürütme özellikleri özel etkinlik yazarları tarafından kullanılabilir ve ayrıca, <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikleri gibi etkinlikler için tanıtıcı yönetimi mekanizmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="82758-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82758-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82758-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
