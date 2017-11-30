---
title: "Değişkenleri ve bağımsız değişkenler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e09548b617fec71ed9cec73f09ef19a8c5b41fe5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="variables-and-arguments"></a><span data-ttu-id="26e9f-102">Değişkenleri ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="26e9f-102">Variables and Arguments</span></span>
<span data-ttu-id="26e9f-103">İçinde [!INCLUDE[wf](../../../includes/wf-md.md)]değişkenlerini temsil eden veri depolama ve bağımsız değişkenleri içine ve dışına aktivite veri akışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="26e9f-103">In [!INCLUDE[wf](../../../includes/wf-md.md)], variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="26e9f-104">Bir etkinlik bir bağımsız değişkenler kümesine sahip ve etkinlik imza yapın.</span><span class="sxs-lookup"><span data-stu-id="26e9f-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="26e9f-105">Ayrıca, aktivite Geliştirici ekleyebilir veya değişkenleri bir iş akışı tasarım sırasında kaldırma değişkenlerin listesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26e9f-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="26e9f-106">Bağımsız değişken bir değer döndüren bir ifadeye kullanarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="26e9f-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="26e9f-107">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="26e9f-107">Variables</span></span>  
 <span data-ttu-id="26e9f-108">Veri depolama konumları değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-108">Variables are storage locations for data.</span></span> <span data-ttu-id="26e9f-109">Değişkenleri bir iş akışı tanımının bir parçası olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="26e9f-110">Değerleri çalışma zamanında değişkenleri alın ve bu değerleri bir iş akışı örneğinin durumunu bir parçası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="26e9f-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="26e9f-111">Bir değişken tanımını değişkeni ve isteğe bağlı olarak, ad türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="26e9f-112">Aşağıdaki kod kullanarak bir değere bir değişken, Ata bildirmeyi gösterir bir <xref:System.Activities.Statements.Assign%601> etkinlik ve ardından konsol kullanmaya değerini görüntülemek bir <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="26e9f-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="26e9f-113">Varsayılan değer ifadesi bir değişken bildirimi bir parçası olarak isteğe bağlı olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="26e9f-114">Değişkenleri değiştiricileri da sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26e9f-114">Variables also can have modifiers.</span></span> <span data-ttu-id="26e9f-115">Örneğin, bir değişken salt okunur ise sonra salt okunur için <xref:System.Activities.VariableModifiers> değiştiricisi uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="26e9f-116">Aşağıdaki örnekte, bir salt okunur değişken atanan varsayılan değer olan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="26e9f-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="26e9f-117">Değişken kapsamı</span><span class="sxs-lookup"><span data-stu-id="26e9f-117">Variable Scoping</span></span>  
 <span data-ttu-id="26e9f-118">Çalışma zamanında bir değişken ömrü onu tanımlandığı etkinlik için kullanım ömrü eşittir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="26e9f-119">Bir etkinlik tamamlandığında değişkenlerini temizlenmesini ve artık başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="26e9f-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="26e9f-120">Arguments</span></span>  
 <span data-ttu-id="26e9f-121">Etkinlik yazarlar şekilde verileri tanımlamak için bağımsız değişkenleri kullanma içine ve dışına bir etkinlik akışı.</span><span class="sxs-lookup"><span data-stu-id="26e9f-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="26e9f-122">Belirtilen yöne her bağımsız değişkenlere sahiptir: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, veya <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="26e9f-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="26e9f-123">İş akışı çalışma zamanı veri taşıma içine ve dışına etkinlikleri zamanlama hakkında aşağıdaki garantisi yapar:</span><span class="sxs-lookup"><span data-stu-id="26e9f-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1.  <span data-ttu-id="26e9f-124">Bir etkinlik yürütme başladığında, tüm giriş ve giriş/çıkış değişkenlerinin değerlerini hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="26e9f-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="26e9f-125">Örneğin, bağımsız olarak ne zaman <xref:System.Activities.Argument.Get%2A> olan adlı bir hesaplanan kendi çağrılması önce çalışma zamanı tarafından döndürülen değer `Execute`.</span><span class="sxs-lookup"><span data-stu-id="26e9f-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2.  <span data-ttu-id="26e9f-126">Zaman <xref:System.Activities.InOutArgument%601.Set%2A> olan çağrılmadan hemen değeri çalışma zamanı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="26e9f-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3.  <span data-ttu-id="26e9f-127">Bağımsız değişkenler isteğe bağlı olarak olabilir kendi <xref:System.Activities.Argument.EvaluationOrder%2A> belirtilen.</span><span class="sxs-lookup"><span data-stu-id="26e9f-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="26e9f-128"><xref:System.Activities.Argument.EvaluationOrder%2A>bağımsız değişken değerlendirildiği sırayı belirtir sıfır tabanlı bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="26e9f-129">Varsayılan olarak bağımsız değişkenin değerlendirme sırası belirtilmezse, eşittir <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> değeri.</span><span class="sxs-lookup"><span data-stu-id="26e9f-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="26e9f-130">Ayarlama <xref:System.Activities.Argument.EvaluationOrder%2A> bu bağımsız değişken için bir değerlendirme sıra belirtmek sıfıra eşit veya daha büyük bir değer.</span><span class="sxs-lookup"><span data-stu-id="26e9f-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> [!INCLUDE[wf2](../../../includes/wf2-md.md)]<span data-ttu-id="26e9f-131">artan düzende belirtilen değerlendirme sırası değişkenleriyle değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-131"> evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="26e9f-132">Belirtilmeyen değerlendirme sırası değişkenleriyle belirtilen değerlendirme sırası olanlar önce değerlendirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="26e9f-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="26e9f-133">Bir etkinlik Yazar kesin türü belirtilmiş bir mekanizma değişkenlerinin gösterme için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26e9f-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="26e9f-134">Bu tür özelliklerini bildirerek gerçekleştirilir <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, ve <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="26e9f-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="26e9f-135">Bu, belirli bir sözleşme içine ve dışına bir etkinlik giderek verilerle ilgili kurmak bir etkinlik Yazar sağlar.</span><span class="sxs-lookup"><span data-stu-id="26e9f-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="26e9f-136">Bir etkinliği bağımsız değişkenleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="26e9f-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="26e9f-137">Bağımsız değişkenler tanımlanabilir üzerinde bir etkinlik türünün özelliklerini belirterek <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, ve <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="26e9f-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="26e9f-138">Aşağıdaki kod, bağımsız değişkenleri tanımlamak gösterilmiştir bir `Prompt` etkinliği kullanıcıya görüntülenecek bir dize alır ve kullanıcının yanıtı içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="26e9f-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="26e9f-139">Tek bir değer döndürmesi etkinlikler türetilen <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, veya <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="26e9f-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="26e9f-140">Bu etkinlikler iyi tanımlanmış olması <xref:System.Activities.OutArgument%601> adlı <xref:System.Activities.Activity%601.Result%2A> etkinliğin dönüş değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="26e9f-141">İş akışlarında değişkenler ve bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="26e9f-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="26e9f-142">Aşağıdaki örnek, değişkenler ve bağımsız değişkenleri bir iş akışında nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="26e9f-143">İş akışı üç değişkenleri bildiren bir dizidir: `var1`, `var2`, ve `var3`.</span><span class="sxs-lookup"><span data-stu-id="26e9f-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="26e9f-144">İş akışındaki ilk etkinliği bir `Assign` değişkeninin değeri atar etkinlik `var1` değişkenine `var2`.</span><span class="sxs-lookup"><span data-stu-id="26e9f-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="26e9f-145">Bu tarafından izlenir bir `WriteLine` değerini yazdırır etkinlik `var2` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="26e9f-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="26e9f-146">Sonraki başka olduğu `Assign` değişkeninin değeri atar etkinlik `var2` değişkenine `var3`.</span><span class="sxs-lookup"><span data-stu-id="26e9f-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="26e9f-147">Son olarak olduğundan başka `WriteLine` değerini yazdırır etkinlik `var3` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="26e9f-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="26e9f-148">İlk `Assign` aktivitesi kullanır `InArgument<string>` ve `OutArgument<string>` açıkça etkinliğin bağımsız değişkenler için olan bağlamaları temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="26e9f-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="26e9f-149">`InArgument<string>`için kullanılan <xref:System.Activities.Statements.Assign.Value%2A> değeri içine akan çünkü <xref:System.Activities.Statements.Assign%601> etkinliği aracılığıyla kendi <xref:System.Activities.Statements.Assign.Value%2A> bağımsız değişkeni, ve `OutArgument<string>` için kullanılan <xref:System.Activities.Statements.Assign.To%2A> değeri dışı akan olduğundan <xref:System.Activities.Statements.Assign.To%2A> bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="26e9f-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="26e9f-150">İkinci `Assign` etkinlik daha fazla ile aynı işlevi gerçekleştirir örtük atamaları kullanır ancak eşdeğer sözdizimi sıkıştırın.</span><span class="sxs-lookup"><span data-stu-id="26e9f-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="26e9f-151">`WriteLine` Etkinlikleri de compact sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="26e9f-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="26e9f-152">Değişken ve bağımsız değişkenler kod tabanlı etkinlikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="26e9f-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="26e9f-153">Önceki örneklerde bağımsız ve iş akışları ve bildirim temelli etkinlikleri değişkenler nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26e9f-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="26e9f-154">Bağımsız değişkenler ve değişkenleri kod tabanlı etkinlikleri de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26e9f-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="26e9f-155">Kavramsal kullanım çok benzer.</span><span class="sxs-lookup"><span data-stu-id="26e9f-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="26e9f-156">Değişkenleri veri depolama etkinlik temsil eder ve bağımsız değişkenleri içine veya etkinlik dışı veri akışını temsil eder ve burada veriler veya akar temsil eden diğer değişkenleri veya bağımsız değişkenler iş akışı iş akışı yazarı tarafından bağlı.</span><span class="sxs-lookup"><span data-stu-id="26e9f-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="26e9f-157">GET veya etkinliğin geçerli yürütme ortamı temsil eden bir değişken veya bir etkinlik, bir etkinlik bağlamı değişkeninde değerini kullanılmalıdır kümesi.</span><span class="sxs-lookup"><span data-stu-id="26e9f-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="26e9f-158">Bu içine geçirilir <xref:System.Activities.CodeActivity%601.Execute%2A> etkinlik iş akışı çalışma zamanı tarafından yöntemi.</span><span class="sxs-lookup"><span data-stu-id="26e9f-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="26e9f-159">Bu örnekte, özel bir `Add` etkinlik tanımlanmış iki sahip <xref:System.Activities.ArgumentDirection.In> bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="26e9f-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="26e9f-160">Bağımsız değişken değeri erişmek için <xref:System.Activities.Argument.Get%2A> yöntemi kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlamı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26e9f-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="26e9f-161">bağımsız değişkenler, değişkenleri ve kodda ifadeleri ile çalışma, bkz: [geliştirme iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) ve [gerekli bağımsız değişkenleri ve aşırı grupları](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="26e9f-161"> working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span></span>
