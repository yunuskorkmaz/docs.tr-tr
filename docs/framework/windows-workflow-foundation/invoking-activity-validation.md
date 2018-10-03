---
title: Etkinlik doğrulamayı çağırma
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 61491e906bfc58bbd19cf43a5980b2781493411b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035142"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="0a5ad-102">Etkinlik doğrulamayı çağırma</span><span class="sxs-lookup"><span data-stu-id="0a5ad-102">Invoking Activity Validation</span></span>
<span data-ttu-id="0a5ad-103">Etkinlik doğrulamayı yürütme öncesi herhangi bir etkinliğe ilişkin yapılandırma hataları bildirmek üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="0a5ad-104">Bir iş akışı iş akışı Tasarımcısı'nda değiştirilir ve herhangi bir doğrulama hataları veya uyarıları iş akışı Tasarımcısı'nda görüntülenen doğrulama gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="0a5ad-105">Doğrulama iş akışı çağrıldığında ve herhangi bir doğrulama hatası meydana gelirse, çalışma zamanında da oluşur bir <xref:System.Activities.InvalidWorkflowException> varsayılan Doğrulama mantığı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="0a5ad-106">Windows Workflow Foundation (WF) sağlayan <xref:System.Activities.Validation.ActivityValidationServices> sınıfı açıkça bir etkinlik doğrulamak için iş akışı uygulaması ve araç geliştiricileri tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="0a5ad-107">Bu konu nasıl kullanılacağını açıklar <xref:System.Activities.Validation.ActivityValidationServices> etkinlik doğrulamayı gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="0a5ad-108">ActivityValidationServices kullanma</span><span class="sxs-lookup"><span data-stu-id="0a5ad-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="0a5ad-109"><xref:System.Activities.Validation.ActivityValidationServices> iki <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> etkinliğin Doğrulama mantığı çağırmak için kullanılan aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="0a5ad-110">İlk aşırı yükleme doğrulanması için Kök etkinlik alır ve doğrulama hataları ve Uyarıları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="0a5ad-111">Aşağıdaki örnekte, özel bir `Add` etkinliği, iki bağımsız değişkenler zorunludur kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-112">`Add` Etkinliği içinde kullanılan bir <xref:System.Activities.Statements.Sequence>, ancak, iki bağımsız değişken bağlamasından, aşağıdaki örnekte gösterildiği gibi gerekli.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-113">Bu iş akışı çağırarak doğrulanabilir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="0a5ad-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Aşağıdaki örnekte gösterildiği gibi herhangi bir doğrulama hataları veya uyarıları etkinliği ve bir alt öğesi tarafından bulunan bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-115">Zaman <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Bu örnek iş akışında, iki doğrulama hataları döndürülür çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="0a5ad-116">**Hata: Povinný argument 'İşlenen2' için değer sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="0a5ad-117">**Hata: Povinný argument 'İşlenen1' için değer sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="0a5ad-118">Bu iş akışı çağrıldı, bir <xref:System.Activities.InvalidWorkflowException> , aşağıdaki örnekte gösterildiği gibi durum.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="0a5ad-120">**İş akışı ağaç işlenirken şu hatalarla karşılaşıldı:** </span><span class="sxs-lookup"><span data-stu-id="0a5ad-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="0a5ad-121">**'Add': povinný argument 'İşlenen2' sağlanmadı için bir değer.** </span><span class="sxs-lookup"><span data-stu-id="0a5ad-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="0a5ad-122">**'Add': povinný argument 'İşlenen1' sağlanmadı için bir değer.**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="0a5ad-123">Geçerli olması Bu örnek iş akışı için iki gerekli bağımsız değişkenleri `Add` etkinlik bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="0a5ad-124">Aşağıdaki örnekte, iki bağımsız değişken sonuç değeri yanı sıra iş akışı değişkenlerini bağlı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="0a5ad-125">Bu örnekte <xref:System.Activities.Activity%601.Result%2A> iki gerekli bağımsız değişkenler yanı sıra bağlı bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="0a5ad-126"><xref:System.Activities.Activity%601.Result%2A> Bağımsız değişkeni bağlanması için gerekli değildir ve bu durumda bir doğrulama hatası neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="0a5ad-127">Bağlamak için iş akışı Yazar sorumluluğundadır <xref:System.Activities.Activity%601.Result%2A> değerinin iş akışında başka bir yerde kullanılıyorsa.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="0a5ad-128">Kök etkinlik bağımsız değişkenlerini doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="0a5ad-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="0a5ad-129">Bir iş akışının Kök etkinlik bağımsız değişkenleri yoksa bu parametreleri iş akışına geçirilir ve iş akışı çağrılan kadar bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="0a5ad-130">Aşağıdaki iş akışı doğrulama başarılı, ancak iş akışını gerekli bağımsız değişkenler olarak geçirme olmadan çağrılırsa aşağıdaki örnekte gösterildiği gibi bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-131">**System.ArgumentException: Kök etkinlik bağımsız değişkeni ayarları yanlış.**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="0a5ad-132">**İş akışı tanımını düzeltin ya da bu hataları düzeltmek için giriş değerleri sağlayın:** </span><span class="sxs-lookup"><span data-stu-id="0a5ad-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="0a5ad-133">**'Add': povinný argument 'İşlenen2' sağlanmadı için bir değer.** </span><span class="sxs-lookup"><span data-stu-id="0a5ad-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="0a5ad-134">**'Add': povinný argument 'İşlenen1' sağlanmadı için bir değer.**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="0a5ad-135">İş akışı başarıyla aşağıdaki örnekte gösterildiği gibi doğru bağımsız değişkenleri geçirilir sonra tamamlar.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="0a5ad-136">Bu örnekte, kök etkinlik olarak bildirildi `Add` yerine `Activity` önceki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="0a5ad-137">Böylece `WorkflowInvoker.Invoke` sonuçlarını temsil eden tek bir tamsayı döndürülmesini yöntemi `Add` sözlüğü yerine etkinlik `out` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="0a5ad-138">Değişken `wf` ayrıca olarak bildirilmiş `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="0a5ad-139">Kök bağımsız değişkenleri doğrulanırken, gerekli tüm iş akışı çağrıldığında bağımsız değişkenler geçirilir emin olmak için konak uygulamanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="0a5ad-140">Kesin kod temelli doğrulama çağırma</span><span class="sxs-lookup"><span data-stu-id="0a5ad-140">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="0a5ad-141">Kesin kod temelli doğrulama doğrulama kendisi hakkında sağlamaya bir etkinlik için basit bir yol sağlar ve türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="0a5ad-142">Herhangi bir doğrulama hataları veya uyarıları belirleyen bir doğrulama kodu etkinliğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="0a5ad-143">Doğrulama etkinliği çağrıldığında, bu uyarı veya hata çağrısı tarafından döndürülen bir koleksiyonda bulunan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="0a5ad-144">Aşağıdaki örnekte, bir `CreateProduct` etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-144">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="0a5ad-145">Varsa `Cost` büyüktür `Price`, meta verilerde bir doğrulama hatası eklenir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-146">Bu örnekte, bir iş akışı kullanılarak yapılandırılan `CreateProduct` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="0a5ad-147">Bu iş akışında `Cost` büyüktür `Price`ve gerekli `Description` bağımsız değişken ayarlanmaz.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="0a5ad-148">Doğrulama çağrıldığında, aşağıdaki hatalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-148">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-149">**Hata: Maliyeti fiyat eşit veya daha az olmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="0a5ad-150">**Hata: Povinný argument 'Description' için değer sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="0a5ad-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="0a5ad-151">Özel Etkinlik yazarlar, etkinliğin Doğrulama mantığı sağlayabilir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="0a5ad-152">Şuradan oluşturulduğu özel durumları <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hataları değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="0a5ad-153">Bu özel durumlar çağrısından kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından ele alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="0a5ad-154">ValidationSettings kullanma</span><span class="sxs-lookup"><span data-stu-id="0a5ad-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="0a5ad-155">Varsayılan olarak, tüm etkinlikler etkinliğin ağacında değerlendirilir, bu doğrulama tarafından çağrıldığında <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="0a5ad-156"><xref:System.Activities.Validation.ValidationSettings> doğrulamanın birkaç farklı yolla üç özelliklerini yapılandırarak özelleştirilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="0a5ad-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Doğrulayıcı veya tüm etkinlik ağaçta yürüyebilir yalnızca sağlanan etkinliği Doğrulama mantığı uygulama belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="0a5ad-158">Bu değer için varsayılan değer `false`.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-158">The default for this value is `false`.</span></span> <span data-ttu-id="0a5ad-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> bir tür ek kısıtlaması eşleme kısıtlamalar listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="0a5ad-160">Doğrulanmakta olan etkinlik ağacında her bir etkinlik temel tür yok bir arama <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="0a5ad-161">Eşleşen bir sınırlama listesi bulunursa, listedeki tüm kısıtlamalar etkinliği için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="0a5ad-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Doğrulayıcı tüm kısıtlamalar değerlendirmelidir ya da yalnızca belirtilen belirtir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="0a5ad-163">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-163">The default value is `false`.</span></span> <span data-ttu-id="0a5ad-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> ilke kısıtlamaları FxCop gibi araçları gibi iş akışları için ek doğrulama eklemek iş akışı konak yazarları için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="0a5ad-165">Kısıtlamaları hakkında daha fazla bilgi için bkz: [bildirim temelli kısıtlamalar](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="0a5ad-165">For more information about constraints, see [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="0a5ad-166">Kullanılacak <xref:System.Activities.Validation.ValidationSettings>istenen özelliklerini yapılandırmak ve çağrıda geçirmek <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="0a5ad-167">Bu örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> özel ile `Add` etkinlik doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="0a5ad-168">`Add` Etkinliğinde iki gerekli bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-169">Aşağıdaki `Add` etkinlik kullanılan bir <xref:System.Activities.Statements.Sequence>, ancak, iki bağımsız değişken bağlı değil zorunlu.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-170">Aşağıdaki örnek için doğrulama ile gerçekleştirilir <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> kümesine `true`, bu nedenle yalnızca kök <xref:System.Activities.Statements.Sequence> etkinlik doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="0a5ad-171">Bu kod aşağıdaki çıkışı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="0a5ad-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="0a5ad-172">**Uyarı veya hata** olsa bile `Add` etkinliği, bağlı bağımsız değişkenlerin gerekli olan, yalnızca kök etkinlik değerlendirilir olduğundan doğrulama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="0a5ad-173">Bu doğrulama türü, yalnızca belirli bir özellik değişiminin etkinlikten tasarımcıda doğrulama gibi bir etkinlik ağacı öğelerinde doğrulamak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="0a5ad-174">Bu iş akışı çağrılması durumunda iş akışı içinde yapılandırılmış tam doğrulama değerlendirilir dikkat edin ve bir <xref:System.Activities.InvalidWorkflowException> oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="0a5ad-175"><xref:System.Activities.Validation.ActivityValidationServices> ve <xref:System.Activities.Validation.ValidationSettings> yalnızca ana bilgisayar tarafından açıkça çağrılan doğrulama ve olmayan bir iş akışı çağrıldığında oluşan doğrulama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="0a5ad-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
