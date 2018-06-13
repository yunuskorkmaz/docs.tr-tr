---
title: Etkinlik doğrulama çağırma
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 7e8be762e6c5c67687864727dcd4ca1cde9a8e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520181"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="8626d-102">Etkinlik doğrulama çağırma</span><span class="sxs-lookup"><span data-stu-id="8626d-102">Invoking Activity Validation</span></span>
<span data-ttu-id="8626d-103">Etkinlik doğrulama tanımlamak ve yürütülmesinin önce herhangi bir etkinliğe ilişkin yapılandırma hataları rapor için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8626d-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="8626d-104">Bir iş akışı iş akışı Tasarımcısı'nda değiştirilir ve herhangi bir doğrulama hata veya uyarı iş akışı Tasarımcısı'nda görüntülenen doğrulama oluşur.</span><span class="sxs-lookup"><span data-stu-id="8626d-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="8626d-105">Doğrulama da ortaya çıkar çalışma zamanında bir iş akışı çalıştırıldığında ve herhangi bir doğrulama hatası oluşursa, bir <xref:System.Activities.InvalidWorkflowException> varsayılan Doğrulama mantığı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8626d-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="8626d-106">Windows Workflow Foundation (WF) sağlayan <xref:System.Activities.Validation.ActivityValidationServices> iş akışı uygulaması ve araç geliştiriciler tarafından açıkça bir etkinlik doğrulamak için kullanılabilir sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8626d-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="8626d-107">Bu konuda nasıl kullanılacağını açıklar <xref:System.Activities.Validation.ActivityValidationServices> etkinlik doğrulama gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="8626d-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="8626d-108">ActivityValidationServices kullanma</span><span class="sxs-lookup"><span data-stu-id="8626d-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="8626d-109"><xref:System.Activities.Validation.ActivityValidationServices> iki sahip <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> bir etkinliğin doğrulama mantığını çağırmak için kullanılan aşırı.</span><span class="sxs-lookup"><span data-stu-id="8626d-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="8626d-110">İlk aşırı doğrulanması için Kök etkinlik alır ve doğrulama hataları ve Uyarıları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8626d-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="8626d-111">Aşağıdaki örnekte, özel bir `Add` etkinlik, iki bağımsız değişken gerekli olduğunu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8626d-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="8626d-112">`Add` Etkinlik içinde kullanılan bir <xref:System.Activities.Statements.Sequence>, ancak kendi iki bağımsız değişken değil bağlı, aşağıdaki örnekte gösterildiği gibi gerekli.</span><span class="sxs-lookup"><span data-stu-id="8626d-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="8626d-113">Bu iş akışı çağırarak doğrulanabilir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="8626d-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="8626d-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Aşağıdaki örnekte gösterildiği gibi herhangi bir doğrulama hataları veya etkinlik ve herhangi bir alt tarafından bulunan uyarıları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8626d-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="8626d-115">Zaman <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Bu örnek iş akışında, iki doğrulama hataları döndürülür olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8626d-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="8626d-116">**Hata: Gerekli etkinlik bağımsız değişkeni 'Operand2' için değer girilmedi.**</span><span class="sxs-lookup"><span data-stu-id="8626d-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="8626d-117">**Hata: Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer girilmedi.**</span><span class="sxs-lookup"><span data-stu-id="8626d-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="8626d-118">Bu iş akışı çağrıldı, bir <xref:System.Activities.InvalidWorkflowException> , aşağıdaki örnekte gösterildiği gibi durum.</span><span class="sxs-lookup"><span data-stu-id="8626d-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="8626d-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="8626d-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="8626d-120">**İş akışı ağaç işlenirken şu hatalarla karşılaşıldı:** </span><span class="sxs-lookup"><span data-stu-id="8626d-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="8626d-121">**'Add': gerekli etkinlik bağımsız değişkeni 'Operand2' sağlanmamış olan için bir değer.** </span><span class="sxs-lookup"><span data-stu-id="8626d-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="8626d-122">**'Add': gerekli etkinlik bağımsız değişkeni 'Operand1' sağlanmamış olan için bir değer.**</span><span class="sxs-lookup"><span data-stu-id="8626d-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="8626d-123">Geçerli olması Bu örnek için iş akışı, iki gerekli bağımsız `Add` etkinlik bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8626d-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="8626d-124">Aşağıdaki örnekte, iki bağımsız değişken sonuç değeri yanı sıra iş akışı değişkenleri bağlı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8626d-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="8626d-125">Bu örnekte <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni ile birlikte iki gerekli bağımsız bağlı.</span><span class="sxs-lookup"><span data-stu-id="8626d-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="8626d-126"><xref:System.Activities.Activity%601.Result%2A> Bağımsız değişkeni bağlanması için gerekli değildir ve değilse bir doğrulama hatası neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="8626d-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="8626d-127">Bağlamak için iş akışı yazarı sorumluluğundadır <xref:System.Activities.Activity%601.Result%2A> akışında değerini başka bir yerde kullandıysanız.</span><span class="sxs-lookup"><span data-stu-id="8626d-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="8626d-128">Kök etkinlikte gerekli bağımsız doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="8626d-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="8626d-129">Bir iş akışının Kök etkinlik bağımsız değişkenlere sahiptir, bu iş akışı çağrılır ve parametreleri iş akışına geçirilir kadar bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8626d-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="8626d-130">Aşağıdaki iş akışı doğrulama başarılı olur, ancak iş akışı gerekli bağımsız değişkenleri geçirme olmadan çağrılırsa aşağıdaki örnekte gösterildiği gibi bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8626d-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="8626d-131">**System.ArgumentException: Kök etkinliğin bağımsız değişkeni ayarları hatalı olabilir.**</span><span class="sxs-lookup"><span data-stu-id="8626d-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="8626d-132">**İş akışı tanımını düzeltin ya da bu hataları düzeltmek için giriş değerleri girin:** </span><span class="sxs-lookup"><span data-stu-id="8626d-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="8626d-133">**'Add': gerekli etkinlik bağımsız değişkeni 'Operand2' sağlanmamış olan için bir değer.** </span><span class="sxs-lookup"><span data-stu-id="8626d-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="8626d-134">**'Add': gerekli etkinlik bağımsız değişkeni 'Operand1' sağlanmamış olan için bir değer.**</span><span class="sxs-lookup"><span data-stu-id="8626d-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="8626d-135">Doğru bağımsız değişken geçirildi sonra iş akışını başarıyla, aşağıdaki örnekte gösterildiği gibi tamamlar.</span><span class="sxs-lookup"><span data-stu-id="8626d-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="8626d-136">Bu örnekte, kök etkinlik olarak bildirildi `Add` yerine `Activity` önceki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="8626d-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="8626d-137">Böylece `WorkflowInvoker.Invoke` sonuçlarını temsil eden tek bir tamsayı döndürülmesini yöntemi `Add` sözlüğü yerine etkinlik `out` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="8626d-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="8626d-138">Değişkeni `wf` de olarak bildirilmiş `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="8626d-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="8626d-139">Bu kök bağımsız değişkenleri doğrularken gerekli tüm bağımsız değişkenler iş akışı çağrıldığında geçirildiğinden emin olmak için konak uygulamanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="8626d-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="8626d-140">Kesinlik temelli kod tabanlı doğrulama çağırma</span><span class="sxs-lookup"><span data-stu-id="8626d-140">Invoking Imperative Code-Based Validation</span></span>  
 <span data-ttu-id="8626d-141">Kesinlik temelli kod tabanlı doğrulama kendisi hakkında doğrulama sağlamak bir etkinlik için basit bir yol sağlar ve türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="8626d-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="8626d-142">Herhangi bir doğrulama hata veya uyarı belirler doğrulama kodunu aktivite eklenir.</span><span class="sxs-lookup"><span data-stu-id="8626d-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="8626d-143">Doğrulama etkinliği çağrıldığında, bu uyarılar veya hatalar çağrısı tarafından döndürülen koleksiyon bulunan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="8626d-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="8626d-144">Aşağıdaki örnekte, geçen [temel doğrulama](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) örnek, bir `CreateProduct` etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8626d-144">In the following example, taken from the [Basic Validation](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) sample, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="8626d-145">Varsa `Cost` değerinden daha büyük `Price`, meta verilerde bir doğrulama hatası eklenir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="8626d-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="8626d-146">Bu örnekte, bir iş akışı kullanarak yapılandırılır `CreateProduct` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="8626d-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="8626d-147">Bu iş akışındaki `Cost` değerinden daha büyük `Price`ve gerekli `Description` bağımsız değişkeni ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="8626d-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="8626d-148">Doğrulama çağrıldığında, aşağıdaki hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8626d-148">When validation is invoked, the following errors are returned.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =   
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="8626d-149">**Hata: Maliyet fiyat eşit veya daha az olmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="8626d-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="8626d-150">**Hata: Gerekli etkinlik bağımsız değişkeni 'Description' için değer girilmedi.**</span><span class="sxs-lookup"><span data-stu-id="8626d-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="8626d-151">Özel Etkinlik yazarları bir etkinliğin Doğrulama mantığı sağlayabilir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="8626d-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="8626d-152">Öğesinden oluşturulan özel durumlar <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hata olarak kabul edilmediği.</span><span class="sxs-lookup"><span data-stu-id="8626d-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="8626d-153">Bu özel durumlar için çağrısından kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8626d-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="8626d-154">ValidationSettings kullanma</span><span class="sxs-lookup"><span data-stu-id="8626d-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="8626d-155">Doğrulama tarafından çağrıldığında varsayılan olarak, tüm etkinlikleri ve etkinlik ağacında değerlendirilir <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="8626d-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="8626d-156"><xref:System.Activities.Validation.ValidationSettings> birçok farklı yöntemle üç özelliklerini yapılandırarak özelleştirilmek üzere doğrulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="8626d-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="8626d-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Doğrulayıcı veya tüm etkinlik ağaç yol yalnızca sağlanan etkinlik için doğrulama mantığını uygulamak belirtir.</span><span class="sxs-lookup"><span data-stu-id="8626d-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="8626d-158">Bu değer için varsayılan değer `false`.</span><span class="sxs-lookup"><span data-stu-id="8626d-158">The default for this value is `false`.</span></span> <span data-ttu-id="8626d-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> Ek kısıtlama eşlemeye türünden kısıtlamalar listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8626d-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="8626d-160">Her etkinlik Doğrulanmakta olan etkinlik ağacında temel tür yok içine bir arama <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="8626d-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="8626d-161">Eşleşen bir sınırlama listesi bulunursa, listedeki tüm kısıtlamalar etkinliği için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8626d-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="8626d-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Doğrulayıcı tüm kısıtlamalar değerlendirmelidir ya da yalnızca belirtilen belirtir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="8626d-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="8626d-163">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="8626d-163">The default value is `false`.</span></span> <span data-ttu-id="8626d-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> FxCop gibi araçları için ilke kısıtlamaları gibi iş akışları için ek doğrulama eklemek iş akışı ana yazarları için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="8626d-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="8626d-165">Kısıtlamaları hakkında daha fazla bilgi için bkz: [bildirim temelli kısıtlamaları](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="8626d-165">For more information about constraints, see [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="8626d-166">Kullanılacak <xref:System.Activities.Validation.ValidationSettings>, istenen özelliklerini yapılandırmak ve çağrısında geçirmek <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="8626d-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="8626d-167">Bu örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> özel ile `Add` etkinlik doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="8626d-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="8626d-168">`Add` Etkinlik iki gerekli bağımsız değişkeni vardır.</span><span class="sxs-lookup"><span data-stu-id="8626d-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="8626d-169">Aşağıdaki `Add` etkinlik kullanılıyor bir <xref:System.Activities.Statements.Sequence>, ancak kendi iki bağımsız değişken bağlı olmayan gerekli.</span><span class="sxs-lookup"><span data-stu-id="8626d-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="8626d-170">Aşağıdaki örneğin ile doğrulandığını <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> kümesine `true`, bu nedenle yalnızca kök <xref:System.Activities.Statements.Sequence> etkinlik doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="8626d-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="8626d-171">Bu kod, aşağıdaki çıkış görüntüler:</span><span class="sxs-lookup"><span data-stu-id="8626d-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="8626d-172">**Herhangi bir uyarı veya hata** olsa bile `Add` etkinlik bağlı olmayan bağımsız değişkenler gerekli, yalnızca kök etkinlik değerlendirildiğinden doğrulama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="8626d-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="8626d-173">Bu doğrulama türü, yalnızca belirli öğeleri özellik değişikliği bir Tasarımcısı'nda tek bir etkinliğin doğrulanması gibi bir etkinlik ağacında doğrulamak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="8626d-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="8626d-174">Bu iş akışı çağrılırsa iş akışı içinde yapılandırılmış tam doğrulama değerlendirilir unutmayın ve bir <xref:System.Activities.InvalidWorkflowException> durum.</span><span class="sxs-lookup"><span data-stu-id="8626d-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="8626d-175"><xref:System.Activities.Validation.ActivityValidationServices> ve <xref:System.Activities.Validation.ValidationSettings> yalnızca ana bilgisayar tarafından açıkça çağrılan doğrulama ve olmayan iş akışı çağrıldığında oluşan doğrulama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="8626d-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
