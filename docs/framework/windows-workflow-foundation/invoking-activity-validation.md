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
# <a name="invoking-activity-validation"></a>Etkinlik Doğrulamayı Çağırma
Etkinlik doğrulama, çalıştırmadan önce herhangi bir etkinliğin yapılandırmasındaki hataları tanımlamak ve raporlamak için bir yöntem sağlar. Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve herhangi bir doğrulama hatası veya uyarı iş akışı tasarımcısında görüntülendiğinde oluşur. Doğrulama işlemi, bir iş akışı çağrıldığında çalışma zamanında da oluşur ve herhangi bir <xref:System.Activities.InvalidWorkflowException> doğrulama hatası oluşursa, varsayılan doğrulama mantığı tarafından oluşturulur. Windows Workflow Foundation (WF), <xref:System.Activities.Validation.ActivityValidationServices> iş akışı uygulaması tarafından kullanılabilen sınıfı sağlar ve geliştiricilerin açıkça bir etkinliği doğrulaması için araç ekleyebilir. Bu konuda, etkinlik doğrulaması gerçekleştirmek <xref:System.Activities.Validation.ActivityValidationServices> için kullanımı açıklanmaktadır.  
  
## <a name="using-activityvalidationservices"></a>ActivityValidationServices kullanma  
 <xref:System.Activities.Validation.ActivityValidationServices>, bir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> etkinliğin doğrulama mantığını çağırmak için kullanılan iki aşırı yüküne sahiptir. İlk aşırı yükleme kök etkinliğin doğrulanmasını sağlar ve doğrulama hatalarının ve uyarıların bir koleksiyonunu döndürür. Aşağıdaki örnekte, iki gerekli bağımsız değişkene `Add` sahip özel bir etkinlik kullanılır.  
  
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
  
 `Add` Etkinlik bir<xref:System.Activities.Statements.Sequence>içinde kullanılır, ancak aşağıdaki örnekte gösterildiği gibi, iki gerekli bağımsız değişken bağlantılı değildir.  
  
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
  
 Bu iş akışı, çağırarak <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>doğrulanabilir. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Aşağıdaki örnekte gösterildiği gibi, etkinliğin ve herhangi bir alt öğe tarafından içerilen herhangi bir doğrulama hatası veya uyarı koleksiyonu döndürür.  
  
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
  
 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Bu örnek iş akışında çağrıldığında, iki doğrulama hatası döndürülür.  
  
 **Hata: Gerekli ' Işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  
**Hata: Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  Bu iş akışı çağrılırsa, aşağıdaki örnekte <xref:System.Activities.InvalidWorkflowException> gösterildiği gibi bir oluşturulur.  
  
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
**' Ekle ': Gerekli ' Işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**    
**' Ekle ': Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  Bu örnek iş akışının geçerli olması için, `Add` etkinliğin gereken iki bağımsız değişkeni bağlanmalıdır. Aşağıdaki örnekte, iki gerekli bağımsız değişken, sonuç değeriyle birlikte iş akışı değişkenlerine bağlanır. Bu örnekte <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken, gerekli iki bağımsız değişkenle birlikte bağlanır. <xref:System.Activities.Activity%601.Result%2A> Bağımsız değişkenin bağlanması gerekli değildir ve yoksa doğrulama hatasına neden olmaz. Bu, değeri iş akışında başka bir yerde kullanılırsa bağlanacak <xref:System.Activities.Activity%601.Result%2A> iş akışı yazarının sorumluluğundadır.  
  
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
  
 **System.ArgumentException: Kök etkinliğin bağımsız değişken ayarları yanlış.**  
**Bu hataları onarmak için iş akışı tanımını veya sağlama girişi değerlerini düzelden yapın:**    
**' Ekle ': Gerekli ' Işlenen2 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**    
**' Ekle ': Gerekli ' Operand1 ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**  Doğru bağımsız değişkenler geçtikten sonra, aşağıdaki örnekte gösterildiği gibi iş akışı başarıyla tamamlanır.  
  
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
> Bu örnekte, kök etkinliği önceki örnekte `Add` `Activity` olduğu gibi olarak bildirildi. Bu yöntem, `WorkflowInvoker.Invoke` yöntemin `out` bağımsız değişkenlerin sözlüğü yerine `Add` etkinliğin sonuçlarını temsil eden tek bir tamsayı döndürmesini sağlar. Değişken `wf` , olarak `Activity<int>`da bildirilmiştir.  
  
 Kök bağımsız değişkenler doğrulanırken, iş akışı çağrıldığında tüm gerekli bağımsız değişkenlerin geçirildiğinden emin olmak için ana bilgisayar uygulamasının sorumluluğundadır.  
  
### <a name="invoking-imperative-code-based-validation"></a>Zorunlu kod tabanlı doğrulama çağırma

Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol sağlar ve, <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity>' den türetilen etkinlikler için kullanılabilir. Etkinliğe herhangi bir doğrulama hatası veya uyarı eklendiğini belirleyen doğrulama kodu. Etkinlik üzerinde doğrulama çağrıldığında, bu uyarılar veya hatalar, çağrısı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>tarafından döndürülen koleksiyonda bulunur. Aşağıdaki örnekte bir `CreateProduct` etkinlik tanımlanmıştır. , Öğesinden büyükse, <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılma içindeki meta verilere bir doğrulama hatası eklenir. `Price` `Cost`  
  
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
  
 Bu örnekte, `CreateProduct` etkinlik kullanılarak bir iş akışı yapılandırılır. Bu iş akışında `Cost` ,, `Price`öğesinden büyüktür ve gerekli `Description` bağımsız değişken ayarlı değildir. Doğrulama çağrıldığında aşağıdaki hatalar döndürülür.  
  
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
  
 **Hata: Maliyet, fiyattan küçük veya bu değere eşit olmalıdır.**  
**Hata: Gerekli ' Description ' etkinlik bağımsız değişkeninin değeri sağlanmadı.**    
> [!NOTE]
> Özel etkinlik yazarları, bir etkinliğin <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılınmasından doğrulama mantığı sağlayabilir. Kaynağından <xref:System.Activities.CodeActivity.CacheMetadata%2A> oluşturulan tüm özel durumlar doğrulama hatası olarak değerlendirilmez. Bu özel durumlar, çağrısından <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından işlenmelidir.  
  
## <a name="using-validationsettings"></a>ValidationSettings kullanma  
 Varsayılan olarak, etkinlik ağacındaki tüm etkinlikler, doğrulama tarafından <xref:System.Activities.Validation.ActivityValidationServices>çağrıldığında değerlendirilir. <xref:System.Activities.Validation.ValidationSettings>doğrulamanın üç özelliği yapılandırılarak birkaç farklı şekilde özelleştirilme olanağı sağlar. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>Doğrulayıcının tüm etkinlik ağacını mi ilerlemelidir yoksa yalnızca belirtilen etkinliğe doğrulama mantığını uygulayıp uygulamamı uygulanacağını belirtir. Bu değer `false`için varsayılan değer. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir türden bir kısıtlama listesine ek kısıtlama eşlemesi belirtir. Doğrulanan etkinlik ağacındaki her bir etkinliğin temel türü için bir arama <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>vardır. Eşleşen bir kısıtlama listesi bulunursa, listedeki tüm kısıtlamalar etkinlik için değerlendirilir. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Doğrulayıcının tüm kısıtlamaları mı yoksa yalnızca ' de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>belirtilen olanları değerlendirmesi gerekip gerekmediğini belirtir. Varsayılan değer `false` şeklindedir. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> , iş akışı ana bilgisayar yazarlarının, FxCop gibi araçlara yönelik ilke kısıtlamaları gibi iş akışları için ek doğrulama eklemesi yararlı olur. Kısıtlamalar hakkında daha fazla bilgi için bkz. [bildirim temelli kısıtlamalar](declarative-constraints.md).  
  
 Kullanmak <xref:System.Activities.Validation.ValidationSettings>için, istenen özellikleri yapılandırın ve sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>çağrısına geçirin. Bu örnekte, özel <xref:System.Activities.Statements.Sequence> `Add` etkinlikten oluşan bir iş akışı onaylanır. `Add` Etkinliğin iki gerekli bağımsız değişkeni vardır.  
  
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
  
 Aşağıdaki `Add` etkinlik bir <xref:System.Activities.Statements.Sequence>içinde kullanılır, ancak iki gerekli bağımsız değişken bağlantılı değildir.  
  
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
  
 Aşağıdaki örnek için doğrulama, olarak <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> `true`ayarlanmış olarak gerçekleştirilir, bu nedenle yalnızca kök <xref:System.Activities.Statements.Sequence> etkinlik doğrulanacaktır.  
  
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
  
 **Uyarı veya hata yok** `Add` Etkinliğin bağlantılı olmayan bağımsız değişkenleri olsa da, yalnızca kök etkinlik değerlendirildiği için doğrulama başarılı olur. Bu tür bir doğrulama, bir tasarımcıda tek bir etkinliğin Özellik değişikliğinin doğrulanması gibi, yalnızca bir etkinlik ağacındaki belirli öğeleri doğrulamak için yararlıdır. Bu iş akışı çağrılırsa, iş akışında yapılandırılan tam doğrulamanın değerlendirildiğini ve bir <xref:System.Activities.InvalidWorkflowException> durum oluşturulması gerektiğini unutmayın. <xref:System.Activities.Validation.ActivityValidationServices>ve <xref:System.Activities.Validation.ValidationSettings> , bir iş akışı çağrıldığında oluşan doğrulama değil, yalnızca konak tarafından açıkça çağrılan doğrulamayı yapılandırın.
