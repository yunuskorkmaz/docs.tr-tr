---
title: Etkinlik Doğrulamayı Çağırma
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 1241e6445cde20a192581e8132e563e0f7ca8d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182880"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="e3eeb-102">Etkinlik Doğrulamayı Çağırma</span><span class="sxs-lookup"><span data-stu-id="e3eeb-102">Invoking Activity Validation</span></span>
<span data-ttu-id="e3eeb-103">Etkinlik doğrulaması, herhangi bir etkinliğin yürütülmesinden önce yapılandırmasındaki hataları tanımlamak ve bildirmek için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="e3eeb-104">Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve iş akışı tasarımcısında doğrulama hataları veya uyarıları görüntülendiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="e3eeb-105">Doğrulama, bir iş akışı çağrıldığı ve herhangi bir doğrulama hatası oluştuğunda, <xref:System.Activities.InvalidWorkflowException> varsayılan doğrulama mantığı tarafından atılan çalışma zamanında da oluşur.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="e3eeb-106">Windows İş Akışı Temeli (WF), bir etkinliği açıkça doğrulamak için iş akışı uygulaması ve araç geliştiricileri tarafından kullanılabilecek <xref:System.Activities.Validation.ActivityValidationServices> bir sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="e3eeb-107">Bu konu, etkinlik <xref:System.Activities.Validation.ActivityValidationServices> doğrulama gerçekleştirmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="e3eeb-108">ActivityValidationServices kullanma</span><span class="sxs-lookup"><span data-stu-id="e3eeb-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="e3eeb-109"><xref:System.Activities.Validation.ActivityValidationServices>bir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> etkinliğin doğrulama mantığını çağırmak için kullanılan iki aşırı yüklemevardır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="e3eeb-110">İlk aşırı yükleme, doğrulama hataları ve uyarıları bir koleksiyon döndürür, doğrulanması için kök etkinliği alır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="e3eeb-111">Aşağıdaki örnekte, iki `Add` gerekli bağımsız değişkeni olan özel bir etkinlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-112">Etkinlik, `Add` aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Activities.Statements.Sequence>, ancak iki gerekli bağımsız değişkeni bağlı değildir içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-113">Bu iş akışı arayarak <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="e3eeb-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>aşağıdaki örnekte gösterildiği gibi, etkinlik ve herhangi bir çocuk tarafından bulunan doğrulama hataları veya uyarıları bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-115">Bu <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> örnek iş akışında çağrıldığında, iki doğrulama hatası döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="e3eeb-116">**Hata: Gerekli bir etkinlik bağımsız değişkeni 'Operand2' için değer sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="e3eeb-117">**Hata: Gerekli bir etkinlik bağımsız değişkeni 'Operand1' için değer sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="e3eeb-118">Bu iş akışı çağrıldıysa, <xref:System.Activities.InvalidWorkflowException> aşağıdaki örnekte gösterildiği gibi bir atılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="e3eeb-120">**İş akışı ağacı işlenirken aşağıdaki hatalarla karşılaşıldı:**
 **'Ekle': Gerekli bir etkinlik bağımsız değişkeni için değer 'Operand2' sağlanmadı.** 
 **'Ekle': Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer verilmedi.**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-120">**The following errors were encountered while processing the workflow tree:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="e3eeb-121">Bu örnek iş akışının geçerli olabilmesi için, etkinliğin iki gerekli bağımsız değişkeninin `Add` bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-121">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="e3eeb-122">Aşağıdaki örnekte, gerekli iki bağımsız değişken sonuç değeri ile birlikte iş akışı değişkenlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-122">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="e3eeb-123">Bu örnekte <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken, gerekli iki bağımsız değişkenle birlikte bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-123">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="e3eeb-124">Bağımsız <xref:System.Activities.Activity%601.Result%2A> değişkenin bağlı olması gerekmez ve değilse doğrulama hatasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-124">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="e3eeb-125">Değeri iş akışında başka bir yerde <xref:System.Activities.Activity%601.Result%2A> kullanılıyorsa, iş akışı yazarının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-125">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="e3eeb-126">Kök Etkinliği Üzerinde Gerekli Bağımsız Değişkenleri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="e3eeb-126">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="e3eeb-127">Bir iş akışının kök etkinliğinin bağımsız değişkenleri varsa, iş akışı çağrılana ve parametreler iş akışına geçirilene kadar bunlar bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-127">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="e3eeb-128">Aşağıdaki iş akışı doğrulamageçer, ancak aşağıdaki örnekte gösterildiği gibi, iş akışı gerekli bağımsız değişkenleri geçmeden çağrılırsa bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-128">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-129">**System.ArgumentException: Kök etkinliğin bağımsız değişken ayarları yanlış.**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-129">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="e3eeb-130">**İş akışı tanımını düzeltin veya bu hataları düzeltmek için giriş değerlerini tedarik edin:**
 **'Ekle': Gerekli etkinlik bağımsız değişkeni 'Operand2' için değer sağlanamadı.** 
 **'Ekle': Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer verilmedi.**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-130">**Either fix the workflow definition or supply input values to fix these errors:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="e3eeb-131">Doğru bağımsız değişkenler geçirildikten sonra, aşağıdaki örnekte gösterildiği gibi iş akışı başarıyla tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-131">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="e3eeb-132">Bu örnekte, kök etkinliği `Add` önceki `Activity` örnekte olduğu gibi yerine olarak bildirildi.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-132">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="e3eeb-133">Bu, `WorkflowInvoker.Invoke` yöntemin bağımsız değişkenler sözlüğü yerine `Add` etkinliğin sonuçlarını temsil eden `out` tek bir tamsayı döndürmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-133">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="e3eeb-134">Değişken `wf` de . `Activity<int>`</span><span class="sxs-lookup"><span data-stu-id="e3eeb-134">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="e3eeb-135">Kök bağımsız değişkenleri doğrularken, iş akışı çağrıldığında gerekli tüm bağımsız değişkenlerin geçirilmesini sağlamak ana bilgisayar uygulamasının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-135">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="e3eeb-136">Zorunlu Kod Tabanlı Doğrulama'yı çağırmak</span><span class="sxs-lookup"><span data-stu-id="e3eeb-136">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="e3eeb-137">Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol <xref:System.Activities.CodeActivity>sağlar <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity>, ve .</span><span class="sxs-lookup"><span data-stu-id="e3eeb-137">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="e3eeb-138">Etkinlikte herhangi bir doğrulama hatası veya uyarıyı belirleyen doğrulama kodu eklenir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-138">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="e3eeb-139">Etkinlikte doğrulama çağrıldığı zaman, bu uyarılar veya hatalar çağrı tarafından döndürülen <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>koleksiyonda bulunur.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-139">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="e3eeb-140">Aşağıdaki örnekte, `CreateProduct` bir etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-140">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="e3eeb-141">Geçersiz `Cost` kılmadaki meta verilere <xref:System.Activities.CodeActivity.CacheMetadata%2A> bir doğrulama hatası eklenir. `Price`</span><span class="sxs-lookup"><span data-stu-id="e3eeb-141">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-142">Bu örnekte, iş akışı `CreateProduct` etkinlik kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-142">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="e3eeb-143">Bu iş akışında, `Cost` `Price`'den büyüktür `Description` ve gerekli bağımsız değişken ayarlanmaz.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-143">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="e3eeb-144">Doğrulama çağrıldığında, aşağıdaki hatalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-144">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-145">**Hata: Maliyet, Fiyattan daha az veya eşit olmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-145">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="e3eeb-146">**Hata: Gerekli bir etkinlik bağımsız değişkeni 'Açıklama' için değer sağlanmadı.**</span><span class="sxs-lookup"><span data-stu-id="e3eeb-146">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>
> [!NOTE]
> <span data-ttu-id="e3eeb-147">Özel etkinlik yazarları, bir etkinliğin <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılınmasında doğrulama mantığı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-147">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="e3eeb-148">Atılan <xref:System.Activities.CodeActivity.CacheMetadata%2A> tüm özel durumlar doğrulama hatası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-148">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="e3eeb-149">Bu özel durumlar aramadan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> kaçar ve arayan tarafından ele alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-149">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="e3eeb-150">Doğrulama Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e3eeb-150">Using ValidationSettings</span></span>  
 <span data-ttu-id="e3eeb-151">Varsayılan olarak, doğrulama tarafından <xref:System.Activities.Validation.ActivityValidationServices>çağrıldığızaman etkinlik ağacındaki tüm etkinlikler değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-151">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="e3eeb-152"><xref:System.Activities.Validation.ValidationSettings>üç özelliğini yapılandırarak doğrulamanın birkaç farklı şekilde özelleştirilebilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-152"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="e3eeb-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>doğrulayıcının tüm etkinlik ağacında yürümesi mi yoksa yalnızca sağlanan faaliyete doğrulama mantığı uygulayıp uygulamaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="e3eeb-154">Bu değer için `false`varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-154">The default for this value is `false`.</span></span> <span data-ttu-id="e3eeb-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir türden kısıtlamalar listesine ek kısıtlama eşleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="e3eeb-156">Doğrulanan etkinlik ağacındaki her etkinliğin temel türü için <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir arama vardır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-156">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="e3eeb-157">Eşleşen bir kısıtlama listesi bulunursa, listedeki tüm kısıtlamalar etkinlik için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-157">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="e3eeb-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>validatörün tüm kısıtlamaları mı yoksa yalnızca .'de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>belirtilenleri mi değerlendirmesini gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="e3eeb-159">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-159">The default value is `false`.</span></span> <span data-ttu-id="e3eeb-160"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> iş akışı ana bilgisayar yazarları için fxCop gibi araçlar için ilke kısıtlamaları gibi iş akışları için ek doğrulama eklemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-160"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="e3eeb-161">Kısıtlamalar hakkında daha fazla bilgi için [bildirimsel kısıtlamalara](declarative-constraints.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-161">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="e3eeb-162">Kullanmak <xref:System.Activities.Validation.ValidationSettings>için, istenilen özellikleri yapılandırın ve sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>çağrıda geçirin.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-162">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="e3eeb-163">Bu örnekte, özel <xref:System.Activities.Statements.Sequence> `Add` bir etkinlik içeren bir iş akışı doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-163">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="e3eeb-164">Etkinlik `Add` iki gerekli bağımsız değişkenleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-164">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-165">Aşağıdaki `Add` etkinlik bir <xref:System.Activities.Statements.Sequence>, ancak iki gerekli bağımsız değişkenleri bağlı değildir kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-165">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-166">Aşağıdaki örnekiçin, doğrulama kümesi <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> ile `true`gerçekleştirilir , böylece <xref:System.Activities.Statements.Sequence> yalnızca kök etkinliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-166">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="e3eeb-167">Bu kod aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="e3eeb-167">This code displays the following output:</span></span>  
  
 <span data-ttu-id="e3eeb-168">**Uyarı veya hata yok** `Add` Etkinlik bağlı olmayan bağımsız değişkenler gerektirmiş olsa da, yalnızca kök etkinlik değerlendirildiği için doğrulama başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-168">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="e3eeb-169">Bu doğrulama türü, bir tasarımcıdaki tek bir etkinliğin özellik değişikliğinin doğrulanması gibi bir etkinlik ağacındaki yalnızca belirli öğeleri doğrulamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-169">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="e3eeb-170">Bu iş akışı çağrılması durumunda, iş akışında yapılandırılan tam doğrulamanın <xref:System.Activities.InvalidWorkflowException> değerlendirildiğini ve bir atılacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-170">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="e3eeb-171"><xref:System.Activities.Validation.ActivityValidationServices>ve <xref:System.Activities.Validation.ValidationSettings> yalnızca iş akışı çağrıldığı zaman oluşan doğrulamayı değil, yalnızca ana bilgisayar tarafından açıkça çağrılan doğrulamayı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e3eeb-171"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
