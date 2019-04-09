---
title: İş Akışı Yürütme Özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f87e58a034cbc11565fc74347e6b4362952093c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193908"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="34754-102">İş Akışı Yürütme Özellikleri</span><span class="sxs-lookup"><span data-stu-id="34754-102">Workflow Execution Properties</span></span>
<span data-ttu-id="34754-103">İş parçacığı yerel depolama ile (TLS), her iş parçacığı için bir yürütme bağlamı CLR tutar.</span><span class="sxs-lookup"><span data-stu-id="34754-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="34754-104">Bu yürütme bağlamı iş parçacığı kimliği, ortam işlem gibi bilinen iş parçacığı özellikleri yönetir ve geçerli izin ayrıca gibi kullanıcı tanımlı bir iş parçacığı özellikleri kümesine yuvaları adlı.</span><span class="sxs-lookup"><span data-stu-id="34754-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="34754-105">Doğrudan CLR'yi hedefleyen programlar farklı olarak, iş akışı hiyerarşik olarak kapsamlı bir iş parçacığı geçişte sorun yaşamaz ortamında yürütme etkinlikleri ağaçları programlardır.</span><span class="sxs-lookup"><span data-stu-id="34754-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="34754-106">Bu, standart TLS mekanizmaları hangi bağlam belirli iş öğesi için kapsamda olduğunu belirlemek için doğrudan kullanılamaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="34754-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="34754-107">Örneğin, farklı işlem yürütme iki paralel dallarından kullanabilir henüz Zamanlayıcı, aynı CLR iş parçacığı üzerinde yürütülmesi ayırma değeri.</span><span class="sxs-lookup"><span data-stu-id="34754-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="34754-108">İş akışı yürütme özellikleri etkinliğin ortama özgü özellikleri bağlam eklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="34754-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="34754-109">Bu bir etkinlik bildirmek hangi özellikler, alt ağacı kapsamı içinde ve ayrıca ayarlama ve CLR nesnesi ile düzgün çalışmak için TLS aşağı bozmadan kancaları sağlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="34754-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="34754-110">Oluşturma ve iş akışı yürütme özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="34754-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="34754-111">İş akışı yürütme özellikleri genellikle uygulama <xref:System.Activities.IExecutionProperty> mesajlaşmayı odaklı özellikleri uygulayabilir, arabirim <xref:System.ServiceModel.Activities.ISendMessageCallback> ve <xref:System.ServiceModel.Activities.IReceiveMessageCallback> yerine.</span><span class="sxs-lookup"><span data-stu-id="34754-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="34754-112">Bir iş akışı yürütme özelliği oluşturmak için uygulayan bir sınıf oluşturma <xref:System.Activities.IExecutionProperty> arabirim ve üyelerini uygulama <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> ve <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="34754-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="34754-113">Bu üyeleri yürütme özelliği düzgün şekilde ayarlanır ve her pulse herhangi bir alt etkinlik dahil olmak üzere bu özelliği içeren etkinliğin çalışma sırasında iş parçacığı yerel depolama ayırma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="34754-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="34754-114">Bu örnekte, bir `ConsoleColorProperty` bu kümeleri oluşturan `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="34754-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="34754-115">Etkinlik yazarlar içinde kaydederek bu özelliği kullanabilir etkinliğin geçersiz kılma yürütün.</span><span class="sxs-lookup"><span data-stu-id="34754-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="34754-116">Bu örnekte, bir `ConsoleColorScope` etkinliği kaydeden tanımlanır `ConsoleColorProperty` ekleyerek <xref:System.Activities.NativeActivityContext.Properties%2A> geçerli koleksiyonunu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="34754-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="34754-117">Etkinliğin gövdesi bir pulse iş başlatıldığında <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> özelliğinin yöntemi çağrılır ve pulse iş tamamlandığında, <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="34754-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="34754-118">Bu örnekte, bir iş akışı kullanan oluşturulur bir <xref:System.Activities.Statements.Parallel> üç dallarıyla etkinlik.</span><span class="sxs-lookup"><span data-stu-id="34754-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="34754-119">İlk iki dalları kullanma `ConsoleColorScope` etkinliği ve üçüncü dal desteklemez.</span><span class="sxs-lookup"><span data-stu-id="34754-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="34754-120">Tüm üç iki dalları <xref:System.Activities.Statements.WriteLine> etkinlikleri ve <xref:System.Activities.Statements.Delay> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="34754-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="34754-121">Zaman <xref:System.Activities.Statements.Parallel> etkinliği yürütür, dalları yer alan faaliyetleri şekilde bir araya eklemeli yürütme, ancak her bir alt etkinlik yürütme sırasında doğru konsol renk tarafından uygulanır `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="34754-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="34754-122">İş akışı çağrıldığında, konsol penceresinde aşağıdaki çıktıyı yazılır.</span><span class="sxs-lookup"><span data-stu-id="34754-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="34754-123">Önceki çıktısında gösterilmese konsol penceresinde metnin her satırının belirtilen renkte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="34754-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="34754-124">İş akışı yürütme özellikleri özel etkinlik yazarları tarafından kullanılabilir ve ayrıca tanıtıcısı yönetimi etkinlikleri için bir mekanizma gibi sağlarlar <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="34754-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34754-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34754-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
