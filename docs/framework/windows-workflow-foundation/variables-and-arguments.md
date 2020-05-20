---
title: Değişkenler ve Bağımsız Değişkenler
description: Bu makalede, veri depolamayı temsil eden değişkenler ve Iş akışı temeli içindeki bir etkinliğe/içinden veri akışını temsil eden bağımsız değişkenler açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 47b8a7bddc8c3a9a8427bcb3e93760a63e5fa976
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421312"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="3d982-103">Değişkenler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3d982-103">Variables and Arguments</span></span>
<span data-ttu-id="3d982-104">Windows Workflow Foundation (WF) içinde, değişkenler verilerin ve bağımsız değişkenlerin depolanmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d982-104">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="3d982-105">Etkinliğin bir dizi bağımsız değişkeni vardır ve etkinliğin imzasını yapar.</span><span class="sxs-lookup"><span data-stu-id="3d982-105">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="3d982-106">Ayrıca, bir etkinlik, bir geliştiricinin iş akışının tasarımı sırasında değişkenler ekleyebileceği veya kaldırabileceği değişkenlerin bir listesini de koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-106">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="3d982-107">Bir bağımsız değişken, bir değer döndüren bir ifade kullanılarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="3d982-107">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="3d982-108">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3d982-108">Variables</span></span>  
 <span data-ttu-id="3d982-109">Değişkenler, veriler için depolama konumlarıdır.</span><span class="sxs-lookup"><span data-stu-id="3d982-109">Variables are storage locations for data.</span></span> <span data-ttu-id="3d982-110">Değişkenler, bir iş akışı tanımının parçası olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-110">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="3d982-111">Değişkenler çalışma zamanında değerleri alır ve bu değerler bir iş akışı örneği durumunun parçası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="3d982-111">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="3d982-112">Değişken tanımı, değişkenin türünü ve isteğe bağlı olarak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d982-112">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="3d982-113">Aşağıdaki kod, bir değişkeni nasıl bildirecağınızı, bir etkinliği kullanarak bir değer atamayı <xref:System.Activities.Statements.Assign%601> ve sonra bir etkinliği kullanarak değerini konsola görüntülemeyi gösterir <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="3d982-113">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="3d982-114">Varsayılan değer ifadesi, isteğe bağlı olarak bir değişken bildiriminin parçası olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-114">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="3d982-115">Değişkenler aynı zamanda değiştiricilere de sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-115">Variables also can have modifiers.</span></span> <span data-ttu-id="3d982-116">Örneğin, bir değişken salt okunurdur, salt-okunurdur <xref:System.Activities.VariableModifiers> değiştiricisi uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-116">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="3d982-117">Aşağıdaki örnekte, varsayılan değeri atanmış bir salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="3d982-117">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="3d982-118">Değişken kapsamı</span><span class="sxs-lookup"><span data-stu-id="3d982-118">Variable Scoping</span></span>  
 <span data-ttu-id="3d982-119">Çalışma zamanında bir değişkenin ömrü, onu bildiren etkinliğin kullanım ömrüne eşittir.</span><span class="sxs-lookup"><span data-stu-id="3d982-119">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="3d982-120">Bir etkinlik tamamlandığında, değişkenleri temizlenir ve artık başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="3d982-120">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="3d982-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d982-121">Arguments</span></span>  
 <span data-ttu-id="3d982-122">Etkinlik yazarları verilerin bir etkinliğin içine ve dışına nasıl akacağını tanımlamak için bağımsız değişkenler kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d982-122">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="3d982-123">Her bağımsız değişken belirtilen bir yöne sahiptir: <xref:System.Activities.ArgumentDirection.In> , <xref:System.Activities.ArgumentDirection.Out> , veya <xref:System.Activities.ArgumentDirection.InOut> .</span><span class="sxs-lookup"><span data-stu-id="3d982-123">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="3d982-124">İş akışı çalışma zamanı, verilerin taşınmasının ve etkinlik dışı bırakılmasının zamanlaması hakkında aşağıdaki garantisi sağlar:</span><span class="sxs-lookup"><span data-stu-id="3d982-124">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="3d982-125">Bir etkinlik yürütülmeye başladığında, tüm giriş ve giriş/çıkış bağımsız değişkenlerinin değerleri hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3d982-125">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="3d982-126">Örneğin, çağrıldığında ne olursa olsun <xref:System.Activities.Argument.Get%2A> döndürülen değer, çalışma zamanı tarafından, çağrısından önce hesaplanır `Execute` .</span><span class="sxs-lookup"><span data-stu-id="3d982-126">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="3d982-127"><xref:System.Activities.InOutArgument%601.Set%2A>Çağrıldığında, çalışma zamanı değeri hemen ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d982-127">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="3d982-128">Bağımsız değişkenler, isteğe bağlı olarak belirli bir şekilde <xref:System.Activities.Argument.EvaluationOrder%2A> belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-128">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="3d982-129"><xref:System.Activities.Argument.EvaluationOrder%2A>, bağımsız değişkenin değerlendirildiği sırayı belirten sıfır tabanlı bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="3d982-129"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="3d982-130">Varsayılan olarak, bağımsız değişkenin değerlendirme sırası belirtilmemiş ve <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> değere eşittir.</span><span class="sxs-lookup"><span data-stu-id="3d982-130">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="3d982-131"><xref:System.Activities.Argument.EvaluationOrder%2A>Bu bağımsız değişken için bir değerlendirme sırası belirtmek üzere sıfıra eşit veya daha büyük bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3d982-131">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="3d982-132">Windows Workflow Foundation, belirtilen değerlendirme sırasıyla bağımsız değişkenleri artan düzende değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3d982-132">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="3d982-133">Belirtilmemiş bir değerlendirme siparişi olan bağımsız değişkenlerin, belirtilen değerlendirme sırasıyla hesaplanmadan önce değerlendirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3d982-133">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="3d982-134">Etkinlik yazarı bağımsız değişkenlerini göstermek için türü kesin belirlenmiş bir mekanizma kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-134">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="3d982-135">Bu,, ve türündeki Özellikler bildirerek yapılır <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601> <xref:System.Activities.InOutArgument%601> .</span><span class="sxs-lookup"><span data-stu-id="3d982-135">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="3d982-136">Bu, etkinlik yazarının bir etkinliğin içine ve dışına giden veriler hakkında belirli bir sözleşme kurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d982-136">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="3d982-137">Etkinlik üzerinde bağımsız değişkenleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="3d982-137">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="3d982-138">Bağımsız değişkenler,, ve türünün özellikleri belirtilerek bir etkinlikte tanımlanabilir <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601> <xref:System.Activities.InOutArgument%601> .</span><span class="sxs-lookup"><span data-stu-id="3d982-138">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="3d982-139">Aşağıdaki kod, `Prompt` kullanıcıya göstermek için bir dizede geçen bir etkinliğin bağımsız değişkenlerinin nasıl tanımlanacağını gösterir ve kullanıcının yanıtını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d982-139">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="3d982-140">Tek bir değer döndüren etkinlikler <xref:System.Activities.Activity%601> , veya öğesinden türetilebilir <xref:System.Activities.NativeActivity%601> <xref:System.Activities.CodeActivity%601> .</span><span class="sxs-lookup"><span data-stu-id="3d982-140">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="3d982-141">Bu etkinliklerin <xref:System.Activities.OutArgument%601> <xref:System.Activities.Activity%601.Result%2A> , etkinliğin dönüş değerini içeren iyi tanımlanmış bir adlandırılmış adı vardır.</span><span class="sxs-lookup"><span data-stu-id="3d982-141">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="3d982-142">Iş akışlarında değişkenleri ve bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="3d982-142">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="3d982-143">Aşağıdaki örnek, bir iş akışında değişkenlerin ve bağımsız değişkenlerin nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d982-143">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="3d982-144">İş akışı üç değişken bildiren bir dizidir: `var1` , `var2` ve `var3` .</span><span class="sxs-lookup"><span data-stu-id="3d982-144">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="3d982-145">İş akışındaki ilk etkinlik, değişkenin `Assign` değerini değişkenine atayan bir etkinliktir `var1` `var2` .</span><span class="sxs-lookup"><span data-stu-id="3d982-145">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="3d982-146">Bu, `WriteLine` değişkenin değerini yazdıran bir etkinlik izler `var2` .</span><span class="sxs-lookup"><span data-stu-id="3d982-146">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="3d982-147">Next, değişkenin `Assign` değerini değişkenine atayan başka bir etkinliktir `var2` `var3` .</span><span class="sxs-lookup"><span data-stu-id="3d982-147">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="3d982-148">Son olarak, `WriteLine` değişkenin değerini yazdıran başka bir etkinlik vardır `var3` .</span><span class="sxs-lookup"><span data-stu-id="3d982-148">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="3d982-149">İlk `Assign` etkinlik kullanır `InArgument<string>` ve `OutArgument<string>` etkinliğin bağımsız değişkenlerinin bağlamalarını açıkça temsil eden nesneler.</span><span class="sxs-lookup"><span data-stu-id="3d982-149">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="3d982-150">`InArgument<string>`, <xref:System.Activities.Statements.Assign.Value%2A> değeri <xref:System.Activities.Statements.Assign%601> bağımsız değişkeni aracılığıyla etkinliğe akdığı ve için kullanıldığı için kullanıldığından, değeri bağımsız değişkeni <xref:System.Activities.Statements.Assign.Value%2A> `OutArgument<string>` <xref:System.Activities.Statements.Assign.To%2A> <xref:System.Activities.Statements.Assign.To%2A> değişkenine akar.</span><span class="sxs-lookup"><span data-stu-id="3d982-150">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="3d982-151">İkinci `Assign` etkinlik, daha fazla sıkıştırma ile aynı şeyi gerçekleştirir, ancak örtülü yayınları kullanan eşdeğer sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="3d982-151">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="3d982-152">`WriteLine`Etkinlikler Ayrıca Compact söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d982-152">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="3d982-153">Kod tabanlı etkinliklerde değişkenleri ve bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="3d982-153">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="3d982-154">Önceki örneklerde, iş akışlarında ve bildirim temelli etkinliklerdeki bağımsız değişkenlerin ve değişkenlerin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d982-154">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="3d982-155">Bağımsız değişkenler ve değişkenler kod tabanlı etkinliklerde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d982-155">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="3d982-156">Kavramsal olarak kullanım çok benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3d982-156">Conceptually the usage is very similar.</span></span> <span data-ttu-id="3d982-157">Değişkenler, etkinlik içindeki veri depolamayı temsil eder ve bağımsız değişkenler, etkinliğin veri akışını ve etkinlik akışını temsil eder ve iş akışı yazarı tarafından, verilerin nerede veya dışarı akışının bulunduğu yeri temsil eden iş akışındaki diğer değişkenlere veya bağımsız değişkenlere bağlanır.</span><span class="sxs-lookup"><span data-stu-id="3d982-157">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="3d982-158">Bir etkinliğin bir değişkeninin veya bağımsız değişkeninin değerini almak veya ayarlamak için, etkinliğin geçerli yürütme ortamını temsil eden bir etkinlik bağlamı kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d982-158">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="3d982-159">Bu, <xref:System.Activities.CodeActivity%601.Execute%2A> iş akışı çalışma zamanı tarafından etkinliğin yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3d982-159">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="3d982-160">Bu örnekte, `Add` iki bağımsız değişkene sahip özel bir etkinlik tanımlanmıştır <xref:System.Activities.ArgumentDirection.In> .</span><span class="sxs-lookup"><span data-stu-id="3d982-160">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="3d982-161">Bağımsız değişkenlerin değerine erişmek için, <xref:System.Activities.Argument.Get%2A> yöntemi kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlam kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d982-161">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="3d982-162">Koddaki bağımsız değişkenlerle, değişkenlerle ve ifadelerde çalışma hakkında daha fazla bilgi için bkz. [using Iş akışları, etkinlikler ve deyimler Için kesinlik](authoring-workflows-activities-and-expressions-using-imperative-code.md) , zorunlu kod ve [gerekli bağımsız değişkenler ve aşırı yükleme grupları](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="3d982-162">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
