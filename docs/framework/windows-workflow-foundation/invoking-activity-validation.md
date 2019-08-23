---
title: Etkinlik Doğrulamayı Çağırma
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: b45840081f5fc142cf3ec88853dea984b204c9d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934969"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="89327-102">Etkinlik Doğrulamayı Çağırma</span><span class="sxs-lookup"><span data-stu-id="89327-102">Invoking Activity Validation</span></span>
<span data-ttu-id="89327-103">Etkinlik doğrulama, çalıştırmadan önce herhangi bir etkinliğin yapılandırmasındaki hataları tanımlamak ve raporlamak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="89327-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="89327-104">Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve herhangi bir doğrulama hatası veya uyarı iş akışı tasarımcısında görüntülendiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="89327-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="89327-105">Doğrulama işlemi, bir iş akışı çağrıldığında çalışma zamanında da oluşur ve herhangi bir <xref:System.Activities.InvalidWorkflowException> doğrulama hatası oluşursa, varsayılan doğrulama mantığı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89327-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="89327-106">Windows Workflow Foundation (WF), <xref:System.Activities.Validation.ActivityValidationServices> iş akışı uygulaması tarafından kullanılabilen sınıfı sağlar ve geliştiricilerin açıkça bir etkinliği doğrulaması için araç ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="89327-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="89327-107">Bu konuda, etkinlik doğrulaması gerçekleştirmek <xref:System.Activities.Validation.ActivityValidationServices> için kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89327-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="89327-108">ActivityValidationServices kullanma</span><span class="sxs-lookup"><span data-stu-id="89327-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="89327-109"><xref:System.Activities.Validation.ActivityValidationServices>, bir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> etkinliğin doğrulama mantığını çağırmak için kullanılan iki aşırı yüküne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="89327-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="89327-110">İlk aşırı yükleme kök etkinliğin doğrulanmasını sağlar ve doğrulama hatalarının ve uyarıların bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="89327-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="89327-111">Aşağıdaki örnekte, iki gerekli bağımsız değişkene `Add` sahip özel bir etkinlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89327-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="89327-112">`Add` Etkinlik bir<xref:System.Activities.Statements.Sequence>içinde kullanılır, ancak aşağıdaki örnekte gösterildiği gibi, iki gerekli bağımsız değişken bağlantılı değildir.</span><span class="sxs-lookup"><span data-stu-id="89327-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="89327-113">Bu iş akışı, çağırarak <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="89327-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="89327-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Aşağıdaki örnekte gösterildiği gibi, etkinliğin ve herhangi bir alt öğe tarafından içerilen herhangi bir doğrulama hatası veya uyarı koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="89327-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="89327-115"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Bu örnek iş akışında çağrıldığında, iki doğrulama hatası döndürülür.</span><span class="sxs-lookup"><span data-stu-id="89327-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="89327-116">**Hata: Gerekli ' Işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="89327-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="89327-117">**Hata: Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="89327-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="89327-118">Bu iş akışı çağrılırsa, aşağıdaki örnekte <xref:System.Activities.InvalidWorkflowException> gösterildiği gibi bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89327-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="89327-119">**System. Activities. InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="89327-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="89327-120">**İş akışı ağacı işlenirken aşağıdaki hatalarla karşılaşıldı:**  </span><span class="sxs-lookup"><span data-stu-id="89327-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="89327-121">**' Ekle ': Gerekli ' Işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  </span><span class="sxs-lookup"><span data-stu-id="89327-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="89327-122">**' Ekle ': Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="89327-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="89327-123">Bu örnek iş akışının geçerli olması için, `Add` etkinliğin gereken iki bağımsız değişkeni bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89327-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="89327-124">Aşağıdaki örnekte, iki gerekli bağımsız değişken, sonuç değeriyle birlikte iş akışı değişkenlerine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="89327-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="89327-125">Bu örnekte <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken, gerekli iki bağımsız değişkenle birlikte bağlanır.</span><span class="sxs-lookup"><span data-stu-id="89327-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="89327-126"><xref:System.Activities.Activity%601.Result%2A> Bağımsız değişkenin bağlanması gerekli değildir ve yoksa doğrulama hatasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="89327-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="89327-127">Bu, değeri iş akışında başka bir yerde kullanılırsa bağlanacak <xref:System.Activities.Activity%601.Result%2A> iş akışı yazarının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="89327-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="89327-128">Kök etkinliğinde gerekli bağımsız değişkenler doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="89327-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="89327-129">Bir iş akışının kök etkinliğinin bağımsız değişkenleri varsa, bu, iş akışı çağrılana ve parametreleri iş akışına geçirilene kadar bu şekilde bağlantılı değildir.</span><span class="sxs-lookup"><span data-stu-id="89327-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="89327-130">Aşağıdaki iş akışı doğrulamayı geçirir, ancak aşağıdaki örnekte gösterildiği gibi iş akışı gerekli bağımsız değişkenlere geçirilmeden çağrıldığında bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89327-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="89327-131">**System.ArgumentException: Kök etkinliğin bağımsız değişken ayarları yanlış.**</span><span class="sxs-lookup"><span data-stu-id="89327-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="89327-132">**Bu hataları onarmak için iş akışı tanımını veya sağlama girişi değerlerini düzelden yapın:**  </span><span class="sxs-lookup"><span data-stu-id="89327-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="89327-133">**' Ekle ': Gerekli ' Işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  </span><span class="sxs-lookup"><span data-stu-id="89327-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="89327-134">**' Ekle ': Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="89327-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="89327-135">Doğru bağımsız değişkenler geçtikten sonra, aşağıdaki örnekte gösterildiği gibi iş akışı başarıyla tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="89327-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="89327-136">Bu örnekte, kök etkinliği önceki örnekte `Add` `Activity` olduğu gibi olarak bildirildi.</span><span class="sxs-lookup"><span data-stu-id="89327-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="89327-137">Bu yöntem, `WorkflowInvoker.Invoke` yöntemin `out` bağımsız değişkenlerin sözlüğü yerine `Add` etkinliğin sonuçlarını temsil eden tek bir tamsayı döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="89327-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="89327-138">Değişken `wf` , olarak `Activity<int>`da bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="89327-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="89327-139">Kök bağımsız değişkenler doğrulanırken, iş akışı çağrıldığında tüm gerekli bağımsız değişkenlerin geçirildiğinden emin olmak için ana bilgisayar uygulamasının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="89327-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="89327-140">Zorunlu kod tabanlı doğrulama çağırma</span><span class="sxs-lookup"><span data-stu-id="89327-140">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="89327-141">Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol sağlar ve, <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity>' den türetilen etkinlikler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89327-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="89327-142">Etkinliğe herhangi bir doğrulama hatası veya uyarı eklendiğini belirleyen doğrulama kodu.</span><span class="sxs-lookup"><span data-stu-id="89327-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="89327-143">Etkinlik üzerinde doğrulama çağrıldığında, bu uyarılar veya hatalar, çağrısı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>tarafından döndürülen koleksiyonda bulunur.</span><span class="sxs-lookup"><span data-stu-id="89327-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="89327-144">Aşağıdaki örnekte bir `CreateProduct` etkinlik tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89327-144">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="89327-145">, Öğesinden büyükse, <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılma içindeki meta verilere bir doğrulama hatası eklenir. `Price` `Cost`</span><span class="sxs-lookup"><span data-stu-id="89327-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="89327-146">Bu örnekte, `CreateProduct` etkinlik kullanılarak bir iş akışı yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="89327-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="89327-147">Bu iş akışında `Cost` ,, `Price`öğesinden büyüktür ve gerekli `Description` bağımsız değişken ayarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="89327-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="89327-148">Doğrulama çağrıldığında aşağıdaki hatalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="89327-148">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="89327-149">**Hata: Maliyet, fiyattan küçük veya bu değere eşit olmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="89327-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="89327-150">**Hata: Gerekli ' Description ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="89327-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
> <span data-ttu-id="89327-151">Özel etkinlik yazarları, bir etkinliğin <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılınmasından doğrulama mantığı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="89327-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="89327-152">Kaynağından <xref:System.Activities.CodeActivity.CacheMetadata%2A> oluşturulan tüm özel durumlar doğrulama hatası olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="89327-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="89327-153">Bu özel durumlar, çağrısından <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="89327-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="89327-154">ValidationSettings kullanma</span><span class="sxs-lookup"><span data-stu-id="89327-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="89327-155">Varsayılan olarak, etkinlik ağacındaki tüm etkinlikler, doğrulama tarafından <xref:System.Activities.Validation.ActivityValidationServices>çağrıldığında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="89327-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="89327-156"><xref:System.Activities.Validation.ValidationSettings>doğrulamanın üç özelliği yapılandırılarak birkaç farklı şekilde özelleştirilme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="89327-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="89327-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>Doğrulayıcının tüm etkinlik ağacını mi ilerlemelidir yoksa yalnızca belirtilen etkinliğe doğrulama mantığını uygulayıp uygulamamı uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89327-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="89327-158">Bu değer `false`için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="89327-158">The default for this value is `false`.</span></span> <span data-ttu-id="89327-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir türden bir kısıtlama listesine ek kısıtlama eşlemesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="89327-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="89327-160">Doğrulanan etkinlik ağacındaki her bir etkinliğin temel türü için bir arama <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>vardır.</span><span class="sxs-lookup"><span data-stu-id="89327-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="89327-161">Eşleşen bir kısıtlama listesi bulunursa, listedeki tüm kısıtlamalar etkinlik için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="89327-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="89327-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Doğrulayıcının tüm kısıtlamaları mı yoksa yalnızca ' de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>belirtilen olanları değerlendirmesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89327-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="89327-163">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="89327-163">The default value is `false`.</span></span> <span data-ttu-id="89327-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> , iş akışı ana bilgisayar yazarlarının, FxCop gibi araçlara yönelik ilke kısıtlamaları gibi iş akışları için ek doğrulama eklemesi yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="89327-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="89327-165">Kısıtlamalar hakkında daha fazla bilgi için bkz. [bildirim temelli kısıtlamalar](declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="89327-165">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="89327-166">Kullanmak <xref:System.Activities.Validation.ValidationSettings>için, istenen özellikleri yapılandırın ve sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>çağrısına geçirin.</span><span class="sxs-lookup"><span data-stu-id="89327-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="89327-167">Bu örnekte, özel <xref:System.Activities.Statements.Sequence> `Add` etkinlikten oluşan bir iş akışı onaylanır.</span><span class="sxs-lookup"><span data-stu-id="89327-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="89327-168">`Add` Etkinliğin iki gerekli bağımsız değişkeni vardır.</span><span class="sxs-lookup"><span data-stu-id="89327-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="89327-169">Aşağıdaki `Add` etkinlik bir <xref:System.Activities.Statements.Sequence>içinde kullanılır, ancak iki gerekli bağımsız değişken bağlantılı değildir.</span><span class="sxs-lookup"><span data-stu-id="89327-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="89327-170">Aşağıdaki örnek için doğrulama, olarak <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> `true`ayarlanmış olarak gerçekleştirilir, bu nedenle yalnızca kök <xref:System.Activities.Statements.Sequence> etkinlik doğrulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="89327-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="89327-171">Bu kod aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="89327-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="89327-172">**Uyarı veya hata yok** `Add` Etkinliğin bağlantılı olmayan bağımsız değişkenleri olsa da, yalnızca kök etkinlik değerlendirildiği için doğrulama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="89327-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="89327-173">Bu tür bir doğrulama, bir tasarımcıda tek bir etkinliğin Özellik değişikliğinin doğrulanması gibi, yalnızca bir etkinlik ağacındaki belirli öğeleri doğrulamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="89327-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="89327-174">Bu iş akışı çağrılırsa, iş akışında yapılandırılan tam doğrulamanın değerlendirildiğini ve bir <xref:System.Activities.InvalidWorkflowException> durum oluşturulması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="89327-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="89327-175"><xref:System.Activities.Validation.ActivityValidationServices>ve <xref:System.Activities.Validation.ValidationSettings> , bir iş akışı çağrıldığında oluşan doğrulama değil, yalnızca konak tarafından açıkça çağrılan doğrulamayı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="89327-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
