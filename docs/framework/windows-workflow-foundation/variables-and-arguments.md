---
title: Değişkenler ve Bağımsız Değişkenler
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: f975f46a1858d204d12588f7570b7ea5a365e650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182690"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="1ef1d-102">Değişkenler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1ef1d-102">Variables and Arguments</span></span>
<span data-ttu-id="1ef1d-103">Windows İş Akışı Temeli'nde (WF) değişkenler, verilerin ve bağımsız değişkenlerin depolanmasını temsil eder ve bir etkinliğin içine ve dışına veri akışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="1ef1d-104">Bir etkinliğin bir dizi bağımsız değişkeni vardır ve bunlar etkinliğin imzasını yapar.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="1ef1d-105">Ayrıca, bir etkinlik, bir geliştiricinin iş akışının tasarımı sırasında değişkenler ekleyebileceği veya kaldırabileceği değişkenlerin listesini saklayabilir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="1ef1d-106">Bir değer döndüren bir ifade kullanılarak bir bağımsız değişken bağlanır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="1ef1d-107">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1ef1d-107">Variables</span></span>  
 <span data-ttu-id="1ef1d-108">Değişkenler veri depolama konumlarıdır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-108">Variables are storage locations for data.</span></span> <span data-ttu-id="1ef1d-109">Değişkenler iş akışının tanımının bir parçası olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="1ef1d-110">Değişkenler çalışma zamanında değerleri alır ve bu değerler iş akışı örneğinin durumunun bir parçası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="1ef1d-111">Değişken tanımı değişkenin türünü ve isteğe bağlı olarak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="1ef1d-112">Aşağıdaki kod, bir değişkenin nasıl bildirilen, bir <xref:System.Activities.Statements.Assign%601> etkinlik kullanarak bir değer atanın <xref:System.Activities.Statements.WriteLine> ve sonra bir etkinlik kullanarak konsola değerini nasıl gösterin.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="1ef1d-113">Varsayılan değer ifadesi isteğe bağlı olarak değişken bildiriminin bir parçası olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="1ef1d-114">Değişkenler de değiştiriciler olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-114">Variables also can have modifiers.</span></span> <span data-ttu-id="1ef1d-115">Örneğin, bir değişken salt okunursa, salt <xref:System.Activities.VariableModifiers> okunur değiştirici uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="1ef1d-116">Aşağıdaki örnekte, varsayılan değeri atanmış salt okunur değişken oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="1ef1d-117">Değişken Kapsam</span><span class="sxs-lookup"><span data-stu-id="1ef1d-117">Variable Scoping</span></span>  
 <span data-ttu-id="1ef1d-118">Bir değişkenin çalışma zamanındaki ömrü, onu bildiren etkinliğin ömrüne eşittir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="1ef1d-119">Bir etkinlik tamamlandığında, değişkenleri temizlenir ve artık başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="1ef1d-120">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1ef1d-120">Arguments</span></span>  
 <span data-ttu-id="1ef1d-121">Etkinlik yazarları, verilerin bir faaliyete giriş ve çıkış biçimini tanımlamak için bağımsız değişkenler kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="1ef1d-122">Her bağımsız değişkenin <xref:System.Activities.ArgumentDirection.In>belirli <xref:System.Activities.ArgumentDirection.Out>bir <xref:System.Activities.ArgumentDirection.InOut>yönü vardır: , , veya .</span><span class="sxs-lookup"><span data-stu-id="1ef1d-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="1ef1d-123">İş akışı çalışma süresi, veri hareketinin etkinliklere giriş ve çıkış zamanlaması hakkında aşağıdaki garantileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="1ef1d-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="1ef1d-124">Bir etkinlik yürütmeye başladığında, tüm giriş ve girdi/çıktı bağımsız değişkenlerinin değerleri hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="1ef1d-125">Örneğin, ne zaman <xref:System.Activities.Argument.Get%2A> çağrıldığına bakılmaksızın, döndürülen değer, `Execute`'' ' ' ' ' '</span><span class="sxs-lookup"><span data-stu-id="1ef1d-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="1ef1d-126">Çağrıldığında, <xref:System.Activities.InOutArgument%601.Set%2A> çalışma zamanı değeri hemen ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="1ef1d-127">Bağımsız değişkenler isteğe bağlı olarak belirtilebilir. <xref:System.Activities.Argument.EvaluationOrder%2A></span><span class="sxs-lookup"><span data-stu-id="1ef1d-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="1ef1d-128"><xref:System.Activities.Argument.EvaluationOrder%2A>bağımsız değişkenin değerlendirilme sırasını belirten sıfır tabanlı bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="1ef1d-129">Varsayılan olarak, bağımsız değişkenin değerlendirme sırası belirtilmemiş <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> tir ve değere eşittir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="1ef1d-130"><xref:System.Activities.Argument.EvaluationOrder%2A> Bu bağımsız değişken için bir değerlendirme sırası belirtmek için sıfırdan büyük veya eşit bir değer ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="1ef1d-131">Windows İş Akışı Temeli, artan sırada belirli bir değerlendirme sırası ile bağımsız değişkenleri değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="1ef1d-132">Belirtilmemiş bir değerlendirme sırasına sahip bağımsız değişkenlerin, belirli bir değerlendirme sırasına sahip olanlardan önce değerlendirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="1ef1d-133">Bir etkinlik yazarı, bağımsız değişkenlerini ortaya çıkarmak için güçlü bir şekilde yazılmış bir mekanizma kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="1ef1d-134">Bu, türü <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>ve <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="1ef1d-135">Bu, bir etkinlik yazarının bir faaliyete giren ve çıkan verilerle ilgili belirli bir sözleşme oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="1ef1d-136">Bir Etkinlikle Ilgili Bağımsız Değişkenleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1ef1d-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="1ef1d-137">Bağımsız değişkenler, bir etkinlik üzerinde, <xref:System.Activities.InArgument%601>ve <xref:System.Activities.OutArgument%601> <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="1ef1d-138">Aşağıdaki kod, kullanıcıya görüntülenmesi `Prompt` için bir dize alan ve kullanıcının yanıtını içeren bir dize döndüren bir etkinliğin bağımsız değişkenlerinin nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="1ef1d-139">Tek bir değer döndüren etkinlikler <xref:System.Activities.Activity%601> <xref:System.Activities.NativeActivity%601>, <xref:System.Activities.CodeActivity%601>, veya .</span><span class="sxs-lookup"><span data-stu-id="1ef1d-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="1ef1d-140">Bu etkinlikler, etkinliğin <xref:System.Activities.OutArgument%601> geri <xref:System.Activities.Activity%601.Result%2A> dönüş değerini içeren iyi tanımlanmış bir adlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="1ef1d-141">İş Akışlarında Değişkenleri ve Bağımsızları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ef1d-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="1ef1d-142">Aşağıdaki örnek, değişkenlerin ve bağımsız değişkenlerin bir iş akışında nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="1ef1d-143">İş akışı üç değişkeni bildiren bir `var1`dizidir: , `var2`ve `var3`.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="1ef1d-144">İş akışındaki ilk etkinlik, `Assign` değişkenin `var1` değerini değişkene `var2`atayan bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="1ef1d-145">Bunu, `var2` değişkenin `WriteLine` değerini yazdıran bir etkinlik izler.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="1ef1d-146">Sonraki değişkenin `Assign` `var2` değerini değişkene `var3`atayan başka bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="1ef1d-147">Son olarak `WriteLine` `var3` değişkenin değerini yazdıran başka bir etkinlik vardır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="1ef1d-148">İlk `Assign` etkinlik, `InArgument<string>` `OutArgument<string>` etkinliğin bağımsız değişkenlerinin bağlaştırışlarını açıkça temsil eden nesneleri kullanır ve nesneler.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="1ef1d-149">`InArgument<string>`değer <xref:System.Activities.Statements.Assign.Value%2A> <xref:System.Activities.Statements.Assign%601> <xref:System.Activities.Statements.Assign.Value%2A> bağımsız değişkeni üzerinden aktiviteye aktığı için `OutArgument<string>` kullanılır ve <xref:System.Activities.Statements.Assign.To%2A> değer <xref:System.Activities.Statements.Assign.To%2A> bağımsız değişkenden değişkene aktığı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="1ef1d-150">İkinci `Assign` etkinlik, örtük dökümleri kullanan daha kompakt ancak eşdeğer sözdizimi ile aynı şeyi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="1ef1d-151">Etkinlikler `WriteLine` de kompakt sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="1ef1d-152">Kod Tabanlı Etkinliklerde Değişkenleri ve Bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="1ef1d-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="1ef1d-153">Önceki örnekler, iş akışlarında ve bildirimsel etkinliklerde bağımsız değişkenlerin ve değişkenlerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="1ef1d-154">Bağımsız değişkenler ve değişkenler de kod tabanlı etkinliklerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="1ef1d-155">Kavramsal olarak kullanımı çok benzer.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="1ef1d-156">Değişkenler etkinlik içinde veri depolamayı temsil eder ve bağımsız değişkenler veri akışını etkinlik içine veya dışına temsil eder ve iş akışı yazarı tarafından iş akışı yazarı tarafından verilerin nereye veya nereden aktığını temsil eden diğer değişkenlere veya bağımsız değişkenlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="1ef1d-157">Bir etkinlikteki değişken veya bağımsız değişkenin değerini almak veya ayarlamak için, etkinliğin geçerli yürütme ortamını temsil eden bir etkinlik bağlamının kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="1ef1d-158">Bu, iş <xref:System.Activities.CodeActivity%601.Execute%2A> akışı çalışma süresi tarafından etkinlik yöntemine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="1ef1d-159">Bu örnekte, `Add` iki <xref:System.Activities.ArgumentDirection.In> bağımsız değişkeni olan özel bir etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="1ef1d-160">Bağımsız değişkenlerin değerine erişmek <xref:System.Activities.Argument.Get%2A> için yöntem kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlam kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ef1d-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="1ef1d-161">Bağımsız değişkenler, değişkenler ve koddaki ifadelerle çalışma hakkında daha fazla bilgi için [bkz.](authoring-workflows-activities-and-expressions-using-imperative-code.md) [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md)</span><span class="sxs-lookup"><span data-stu-id="1ef1d-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
