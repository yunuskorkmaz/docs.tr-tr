---
title: Değişkenler ve Bağımsız Değişkenler
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 251641c924bbf33c176f519f8fc4f9dec59e2eb8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962193"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="2d67e-102">Değişkenler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2d67e-102">Variables and Arguments</span></span>
<span data-ttu-id="2d67e-103">Windows Workflow Foundation (WF) içinde, değişkenler verilerin ve bağımsız değişkenlerin depolanmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2d67e-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="2d67e-104">Etkinliğin bir dizi bağımsız değişkeni vardır ve etkinliğin imzasını yapar.</span><span class="sxs-lookup"><span data-stu-id="2d67e-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="2d67e-105">Ayrıca, bir etkinlik, bir geliştiricinin iş akışının tasarımı sırasında değişkenler ekleyebileceği veya kaldırabileceği değişkenlerin bir listesini de koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="2d67e-106">Bir bağımsız değişken, bir değer döndüren bir ifade kullanılarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="2d67e-107">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2d67e-107">Variables</span></span>  
 <span data-ttu-id="2d67e-108">Değişkenler, veriler için depolama konumlarıdır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-108">Variables are storage locations for data.</span></span> <span data-ttu-id="2d67e-109">Değişkenler, bir iş akışı tanımının parçası olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="2d67e-110">Değişkenler çalışma zamanında değerleri alır ve bu değerler bir iş akışı örneği durumunun parçası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="2d67e-111">Değişken tanımı, değişkenin türünü ve isteğe bağlı olarak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="2d67e-112">Aşağıdaki kod, bir değişkeni nasıl bildirecağınızı, bir <xref:System.Activities.Statements.Assign%601> etkinliği kullanarak bir değer atamayı ve sonra bir <xref:System.Activities.Statements.WriteLine> etkinliği kullanarak değerini konsola görüntülemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="2d67e-113">Varsayılan değer ifadesi, isteğe bağlı olarak bir değişken bildiriminin parçası olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="2d67e-114">Değişkenler aynı zamanda değiştiricilere de sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-114">Variables also can have modifiers.</span></span> <span data-ttu-id="2d67e-115">Örneğin, bir değişken salt okunurdur, salt-okunurdur <xref:System.Activities.VariableModifiers> değiştiricisi uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="2d67e-116">Aşağıdaki örnekte, varsayılan değeri atanmış bir salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="2d67e-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="2d67e-117">Değişken kapsamı</span><span class="sxs-lookup"><span data-stu-id="2d67e-117">Variable Scoping</span></span>  
 <span data-ttu-id="2d67e-118">Çalışma zamanında bir değişkenin ömrü, onu bildiren etkinliğin kullanım ömrüne eşittir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="2d67e-119">Bir etkinlik tamamlandığında, değişkenleri temizlenir ve artık başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="2d67e-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="2d67e-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="2d67e-120">Arguments</span></span>  
 <span data-ttu-id="2d67e-121">Etkinlik yazarları verilerin bir etkinliğin içine ve dışına nasıl akacağını tanımlamak için bağımsız değişkenler kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="2d67e-122">Her bağımsız değişken belirtilen bir yöne sahiptir <xref:System.Activities.ArgumentDirection.In>: <xref:System.Activities.ArgumentDirection.Out>,, <xref:System.Activities.ArgumentDirection.InOut>veya.</span><span class="sxs-lookup"><span data-stu-id="2d67e-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="2d67e-123">İş akışı çalışma zamanı, verilerin taşınmasının ve etkinlik dışı bırakılmasının zamanlaması hakkında aşağıdaki garantisi sağlar:</span><span class="sxs-lookup"><span data-stu-id="2d67e-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="2d67e-124">Bir etkinlik yürütülmeye başladığında, tüm giriş ve giriş/çıkış bağımsız değişkenlerinin değerleri hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="2d67e-125">Örneğin, çağrıldığında ne olursa olsun <xref:System.Activities.Argument.Get%2A> döndürülen değer, çalışma zamanı tarafından, `Execute`çağrısından önce hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="2d67e-126"><xref:System.Activities.InOutArgument%601.Set%2A> Çağrıldığında, çalışma zamanı değeri hemen ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="2d67e-127">Bağımsız değişkenler, isteğe bağlı <xref:System.Activities.Argument.EvaluationOrder%2A> olarak belirli bir şekilde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="2d67e-128"><xref:System.Activities.Argument.EvaluationOrder%2A>, bağımsız değişkenin değerlendirildiği sırayı belirten sıfır tabanlı bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="2d67e-129">Varsayılan olarak, bağımsız değişkenin değerlendirme sırası belirtilmemiş ve <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> değere eşittir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="2d67e-130">Bu <xref:System.Activities.Argument.EvaluationOrder%2A> bağımsız değişken için bir değerlendirme sırası belirtmek üzere sıfıra eşit veya daha büyük bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2d67e-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="2d67e-131">Windows Workflow Foundation, belirtilen değerlendirme sırasıyla bağımsız değişkenleri artan düzende değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="2d67e-132">Belirtilmemiş bir değerlendirme siparişi olan bağımsız değişkenlerin, belirtilen değerlendirme sırasıyla hesaplanmadan önce değerlendirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2d67e-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="2d67e-133">Etkinlik yazarı bağımsız değişkenlerini göstermek için türü kesin belirlenmiş bir mekanizma kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="2d67e-134">Bu,, ve <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601> <xref:System.Activities.InOutArgument%601>türündeki Özellikler bildirerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="2d67e-135">Bu, etkinlik yazarının bir etkinliğin içine ve dışına giden veriler hakkında belirli bir sözleşme kurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d67e-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="2d67e-136">Etkinlik üzerinde bağımsız değişkenleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2d67e-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="2d67e-137">Bağımsız değişkenler, <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601>, ve <xref:System.Activities.InOutArgument%601>türünün özellikleri belirtilerek bir etkinlikte tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="2d67e-138">Aşağıdaki kod, kullanıcıya göstermek için bir dizede geçen bir `Prompt` etkinliğin bağımsız değişkenlerinin nasıl tanımlanacağını gösterir ve kullanıcının yanıtını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d67e-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="2d67e-139">Tek bir değer döndüren etkinlikler, <xref:System.Activities.Activity%601> <xref:System.Activities.NativeActivity%601>veya <xref:System.Activities.CodeActivity%601>öğesinden türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="2d67e-140">Bu etkinliklerin, etkinliğin dönüş değerini içeren <xref:System.Activities.OutArgument%601> iyi <xref:System.Activities.Activity%601.Result%2A> tanımlanmış bir adlandırılmış adı vardır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="2d67e-141">Iş akışlarında değişkenleri ve bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="2d67e-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="2d67e-142">Aşağıdaki örnek, bir iş akışında değişkenlerin ve bağımsız değişkenlerin nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="2d67e-143">İş akışı üç değişken bildiren bir dizidir: `var1`, `var2`ve `var3`.</span><span class="sxs-lookup"><span data-stu-id="2d67e-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="2d67e-144">İş akışındaki ilk etkinlik, değişkenin değerini `Assign` `var1` değişkenine `var2`atayan bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="2d67e-145">Bu, `var2` değişkenin değerini yazdıran `WriteLine` bir etkinlik izler.</span><span class="sxs-lookup"><span data-stu-id="2d67e-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="2d67e-146">Next, değişkenin `Assign` değerini `var2` değişkenine `var3`atayan başka bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="2d67e-147">Son olarak, `var3` değişkenin `WriteLine` değerini yazdıran başka bir etkinlik vardır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="2d67e-148">İlk `Assign` etkinlik kullanır `InArgument<string>` ve `OutArgument<string>` etkinliğin bağımsız değişkenlerinin bağlamalarını açıkça temsil eden nesneler.</span><span class="sxs-lookup"><span data-stu-id="2d67e-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="2d67e-149">`InArgument<string>`<xref:System.Activities.Statements.Assign.Value%2A> <xref:System.Activities.Statements.Assign.To%2A> , değeri bağımsız değişkeni aracılığıyla <xref:System.Activities.Statements.Assign%601> etkinliğe `OutArgument<string>` akdığı ve için kullanıldığı için kullanıldığından, değeri bağımsız değişkeni değişkenine akar <xref:System.Activities.Statements.Assign.To%2A>. <xref:System.Activities.Statements.Assign.Value%2A></span><span class="sxs-lookup"><span data-stu-id="2d67e-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="2d67e-150">İkinci `Assign` etkinlik, daha fazla sıkıştırma ile aynı şeyi gerçekleştirir, ancak örtülü yayınları kullanan eşdeğer sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="2d67e-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="2d67e-151">`WriteLine` Etkinlikler Ayrıca Compact söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="2d67e-152">Kod tabanlı etkinliklerde değişkenleri ve bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="2d67e-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="2d67e-153">Önceki örneklerde, iş akışlarında ve bildirim temelli etkinliklerdeki bağımsız değişkenlerin ve değişkenlerin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="2d67e-154">Bağımsız değişkenler ve değişkenler kod tabanlı etkinliklerde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="2d67e-155">Kavramsal olarak kullanım çok benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="2d67e-156">Değişkenler, etkinlik içindeki veri depolamayı temsil eder ve bağımsız değişkenler, etkinliğin veri akışını ve etkinlik akışını temsil eder ve iş akışı yazarı tarafından, verilerin nerede veya dışarı akışının bulunduğu yeri temsil eden iş akışındaki diğer değişkenlere veya bağımsız değişkenlere bağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="2d67e-157">Bir etkinliğin bir değişkeninin veya bağımsız değişkeninin değerini almak veya ayarlamak için, etkinliğin geçerli yürütme ortamını temsil eden bir etkinlik bağlamı kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="2d67e-158">Bu, iş akışı çalışma <xref:System.Activities.CodeActivity%601.Execute%2A> zamanı tarafından etkinliğin yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2d67e-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="2d67e-159">Bu örnekte, iki `Add` <xref:System.Activities.ArgumentDirection.In> bağımsız değişkene sahip özel bir etkinlik tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="2d67e-160">Bağımsız değişkenlerin değerine erişmek için, <xref:System.Activities.Argument.Get%2A> yöntemi kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlam kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d67e-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="2d67e-161">Koddaki bağımsız değişkenlerle, değişkenlerle ve ifadelerde çalışma hakkında daha fazla bilgi için bkz. [using Iş akışları, etkinlikler ve deyimler Için kesinlik](authoring-workflows-activities-and-expressions-using-imperative-code.md) , zorunlu kod ve [gerekli bağımsız değişkenler ve aşırı yükleme grupları](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="2d67e-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
