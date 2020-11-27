---
title: Etkinlik Doğrulamayı Çağırma
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 95e6b22fe9814133df080b1faadcc4be32b60bf9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279811"
---
# <a name="invoking-activity-validation"></a>Etkinlik Doğrulamayı Çağırma

Etkinlik doğrulama, çalıştırmadan önce herhangi bir etkinliğin yapılandırmasındaki hataları tanımlamak ve raporlamak için bir yöntem sağlar. Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve herhangi bir doğrulama hatası veya uyarı iş akışı tasarımcısında görüntülendiğinde oluşur. Doğrulama işlemi, bir iş akışı çağrıldığında çalışma zamanında da oluşur ve herhangi bir doğrulama hatası oluşursa, <xref:System.Activities.InvalidWorkflowException> varsayılan doğrulama mantığı tarafından oluşturulur. Windows Workflow Foundation (WF), <xref:System.Activities.Validation.ActivityValidationServices> iş akışı uygulaması tarafından kullanılabilen sınıfı sağlar ve geliştiricilerin açıkça bir etkinliği doğrulaması için araç ekleyebilir. Bu konuda, <xref:System.Activities.Validation.ActivityValidationServices> etkinlik doğrulaması gerçekleştirmek için kullanımı açıklanmaktadır.  
  
## <a name="using-activityvalidationservices"></a>ActivityValidationServices kullanma  

 <xref:System.Activities.Validation.ActivityValidationServices> , <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> bir etkinliğin doğrulama mantığını çağırmak için kullanılan iki aşırı yüküne sahiptir. İlk aşırı yükleme kök etkinliğin doğrulanmasını sağlar ve doğrulama hatalarının ve uyarıların bir koleksiyonunu döndürür. Aşağıdaki örnekte, `Add` iki gerekli bağımsız değişkene sahip özel bir etkinlik kullanılır.  
  
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
  
 `Add`Etkinlik bir içinde kullanılır <xref:System.Activities.Statements.Sequence> , ancak aşağıdaki örnekte gösterildiği gibi, iki gerekli bağımsız değişken bağlantılı değildir.  
  
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
  
 Bu iş akışı, çağırarak doğrulanabilir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> . <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Aşağıdaki örnekte gösterildiği gibi, etkinliğin ve herhangi bir alt öğe tarafından içerilen herhangi bir doğrulama hatası veya uyarı koleksiyonu döndürür.  
  
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
  
 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Bu örnek iş akışında çağrıldığında, iki doğrulama hatası döndürülür.  
  
 **Hata: gerekli ' Işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  
**Hata: gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  Bu iş akışı çağrılırsa, <xref:System.Activities.InvalidWorkflowException> Aşağıdaki örnekte gösterildiği gibi bir oluşturulur.  
  
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
  
 **System. Activities. InvalidWorkflowException:**  
**İş akışı ağacı işlenirken aşağıdaki hatalarla karşılaşıldı:** 
 **' Add ': gerekli bir ' işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.** 
 **' Add ': gerekli bir ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  Bu örnek iş akışının geçerli olması için, etkinliğin gereken iki bağımsız değişkeni `Add` bağlanmalıdır. Aşağıdaki örnekte, iki gerekli bağımsız değişken, sonuç değeriyle birlikte iş akışı değişkenlerine bağlanır. Bu örnekte <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken, gerekli iki bağımsız değişkenle birlikte bağlanır. <xref:System.Activities.Activity%601.Result%2A>Bağımsız değişkenin bağlanması gerekli değildir ve yoksa doğrulama hatasına neden olmaz. Bu, <xref:System.Activities.Activity%601.Result%2A> değeri iş akışında başka bir yerde kullanılırsa bağlanacak iş akışı yazarının sorumluluğundadır.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Kök etkinliğinde gerekli bağımsız değişkenler doğrulanıyor  

 Bir iş akışının kök etkinliğinin bağımsız değişkenleri varsa, bu, iş akışı çağrılana ve parametreleri iş akışına geçirilene kadar bu şekilde bağlantılı değildir. Aşağıdaki iş akışı doğrulamayı geçirir, ancak aşağıdaki örnekte gösterildiği gibi iş akışı gerekli bağımsız değişkenlere geçirilmeden çağrıldığında bir özel durum oluşturulur.  
  
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
  
 **System. ArgumentException: Kök etkinliğin bağımsız değişken ayarları yanlış.**  
**Bu hataları onarmak için iş akışı tanımını veya sağlama girişi değerlerini Düzelden yapın:** 
 **' Add ': gerekli bir ' işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.** 
 **' Add ': gerekli bir ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  Doğru bağımsız değişkenler geçtikten sonra, aşağıdaki örnekte gösterildiği gibi iş akışı başarıyla tamamlanır.  
  
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
> Bu örnekte, kök etkinliği `Add` `Activity` Önceki örnekte olduğu gibi olarak bildirildi. Bu yöntem, `WorkflowInvoker.Invoke` yöntemin `Add` bağımsız değişkenlerin sözlüğü yerine etkinliğin sonuçlarını temsil eden tek bir tamsayı döndürmesini sağlar `out` . Değişken, `wf` olarak da bildirilmiştir `Activity<int>` .  
  
 Kök bağımsız değişkenler doğrulanırken, iş akışı çağrıldığında tüm gerekli bağımsız değişkenlerin geçirildiğinden emin olmak için ana bilgisayar uygulamasının sorumluluğundadır.  
  
### <a name="invoking-imperative-code-based-validation"></a>Kesinlik Code-Based doğrulaması çağrılıyor

Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol sağlar ve, ve ' den türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> . Etkinliğe herhangi bir doğrulama hatası veya uyarı eklendiğini belirleyen doğrulama kodu. Etkinlik üzerinde doğrulama çağrıldığında, bu uyarılar veya hatalar, çağrısı tarafından döndürülen koleksiyonda bulunur <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> . Aşağıdaki örnekte bir `CreateProduct` etkinlik tanımlanmıştır. , `Cost` Öğesinden büyükse, `Price` geçersiz kılma içindeki meta verilere bir doğrulama hatası eklenir <xref:System.Activities.CodeActivity.CacheMetadata%2A> .  
  
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
  
 Bu örnekte, etkinlik kullanılarak bir iş akışı yapılandırılır `CreateProduct` . Bu iş akışında,, `Cost` öğesinden büyüktür `Price` ve gerekli `Description` bağımsız değişken ayarlı değildir. Doğrulama çağrıldığında aşağıdaki hatalar döndürülür.  
  
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
  
 **Hata: maliyet, fiyattan küçük veya bu değere eşit olmalıdır.**  
**Hata: gerekli ' Description ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**
> [!NOTE]
> Özel etkinlik yazarları, bir etkinliğin <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılınmasından doğrulama mantığı sağlayabilir. Kaynağından oluşturulan tüm özel durumlar <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hatası olarak değerlendirilmez. Bu özel durumlar, çağrısından <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından işlenmelidir.  
  
## <a name="using-validationsettings"></a>ValidationSettings kullanma  

 Varsayılan olarak, etkinlik ağacındaki tüm etkinlikler, doğrulama tarafından çağrıldığında değerlendirilir <xref:System.Activities.Validation.ActivityValidationServices> . <xref:System.Activities.Validation.ValidationSettings> doğrulamanın üç özelliği yapılandırılarak birkaç farklı şekilde özelleştirilme olanağı sağlar. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Doğrulayıcının tüm etkinlik ağacını mi ilerlemelidir yoksa yalnızca belirtilen etkinliğe doğrulama mantığını uygulayıp uygulamamı uygulanacağını belirtir. Bu değer için varsayılan değer `false` . <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> bir türden bir kısıtlama listesine ek kısıtlama eşlemesi belirtir. Doğrulanan etkinlik ağacındaki her bir etkinliğin temel türü için bir arama vardır <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> . Eşleşen bir kısıtlama listesi bulunursa, listedeki tüm kısıtlamalar etkinlik için değerlendirilir. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Doğrulayıcının tüm kısıtlamaları mı yoksa yalnızca ' de belirtilen olanları değerlendirmesi gerekip gerekmediğini belirtir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> . `false` varsayılan değerdir. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> , iş akışı ana bilgisayar yazarlarının, FxCop gibi araçlara yönelik ilke kısıtlamaları gibi iş akışları için ek doğrulama eklemesi yararlı olur. Kısıtlamalar hakkında daha fazla bilgi için bkz. [bildirim temelli kısıtlamalar](declarative-constraints.md).  
  
 Kullanmak için, <xref:System.Activities.Validation.ValidationSettings> istenen özellikleri yapılandırın ve sonra çağrısına geçirin <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> . Bu örnekte, özel etkinlikten oluşan bir iş akışı <xref:System.Activities.Statements.Sequence> `Add` onaylanır. `Add`Etkinliğin iki gerekli bağımsız değişkeni vardır.  
  
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
  
 Aşağıdaki `Add` etkinlik bir içinde kullanılır <xref:System.Activities.Statements.Sequence> , ancak iki gerekli bağımsız değişken bağlantılı değildir.  
  
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
  
 Aşağıdaki örnek için doğrulama, olarak ayarlanmış olarak gerçekleştirilir <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> , bu `true` nedenle yalnızca kök <xref:System.Activities.Statements.Sequence> etkinlik doğrulanacaktır.  
  
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
  
 Bu kod aşağıdaki çıktıyı görüntüler:  
  
 **Uyarı veya hata yok** `Add` Etkinliğin bağlantılı olmayan bağımsız değişkenleri olsa da, yalnızca kök etkinlik değerlendirildiği için doğrulama başarılı olur. Bu tür bir doğrulama, bir tasarımcıda tek bir etkinliğin Özellik değişikliğinin doğrulanması gibi, yalnızca bir etkinlik ağacındaki belirli öğeleri doğrulamak için yararlıdır. Bu iş akışı çağrılırsa, iş akışında yapılandırılan tam doğrulamanın değerlendirildiğini ve bir <xref:System.Activities.InvalidWorkflowException> durum oluşturulması gerektiğini unutmayın. <xref:System.Activities.Validation.ActivityValidationServices> ve <xref:System.Activities.Validation.ValidationSettings> , bir iş akışı çağrıldığında oluşan doğrulama değil, yalnızca konak tarafından açıkça çağrılan doğrulamayı yapılandırın.
