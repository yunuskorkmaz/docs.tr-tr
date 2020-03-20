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
# <a name="invoking-activity-validation"></a>Etkinlik Doğrulamayı Çağırma
Etkinlik doğrulaması, herhangi bir etkinliğin yürütülmesinden önce yapılandırmasındaki hataları tanımlamak ve bildirmek için bir yöntem sağlar. Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve iş akışı tasarımcısında doğrulama hataları veya uyarıları görüntülendiğinde oluşur. Doğrulama, bir iş akışı çağrıldığı ve herhangi bir doğrulama hatası oluştuğunda, <xref:System.Activities.InvalidWorkflowException> varsayılan doğrulama mantığı tarafından atılan çalışma zamanında da oluşur. Windows İş Akışı Temeli (WF), bir etkinliği açıkça doğrulamak için iş akışı uygulaması ve araç geliştiricileri tarafından kullanılabilecek <xref:System.Activities.Validation.ActivityValidationServices> bir sınıf sağlar. Bu konu, etkinlik <xref:System.Activities.Validation.ActivityValidationServices> doğrulama gerçekleştirmek için nasıl kullanılacağını açıklar.  
  
## <a name="using-activityvalidationservices"></a>ActivityValidationServices kullanma  
 <xref:System.Activities.Validation.ActivityValidationServices>bir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> etkinliğin doğrulama mantığını çağırmak için kullanılan iki aşırı yüklemevardır. İlk aşırı yükleme, doğrulama hataları ve uyarıları bir koleksiyon döndürür, doğrulanması için kök etkinliği alır. Aşağıdaki örnekte, iki `Add` gerekli bağımsız değişkeni olan özel bir etkinlik kullanılır.  
  
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
  
 Etkinlik, `Add` aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Activities.Statements.Sequence>, ancak iki gerekli bağımsız değişkeni bağlı değildir içinde kullanılır.  
  
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
  
 Bu iş akışı arayarak <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>doğrulanabilir. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>aşağıdaki örnekte gösterildiği gibi, etkinlik ve herhangi bir çocuk tarafından bulunan doğrulama hataları veya uyarıları bir koleksiyon döndürür.  
  
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
  
 Bu <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> örnek iş akışında çağrıldığında, iki doğrulama hatası döndürülür.  
  
 **Hata: Gerekli bir etkinlik bağımsız değişkeni 'Operand2' için değer sağlanmadı.**  
**Hata: Gerekli bir etkinlik bağımsız değişkeni 'Operand1' için değer sağlanmadı.**  Bu iş akışı çağrıldıysa, <xref:System.Activities.InvalidWorkflowException> aşağıdaki örnekte gösterildiği gibi bir atılabilir.  
  
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
  
 **System.Activities.InvalidWorkflowException:**  
**İş akışı ağacı işlenirken aşağıdaki hatalarla karşılaşıldı:**
 **'Ekle': Gerekli bir etkinlik bağımsız değişkeni için değer 'Operand2' sağlanmadı.** 
 **'Ekle': Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer verilmedi.**  Bu örnek iş akışının geçerli olabilmesi için, etkinliğin iki gerekli bağımsız değişkeninin `Add` bağlanması gerekir. Aşağıdaki örnekte, gerekli iki bağımsız değişken sonuç değeri ile birlikte iş akışı değişkenlerine bağlıdır. Bu örnekte <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken, gerekli iki bağımsız değişkenle birlikte bağlanır. Bağımsız <xref:System.Activities.Activity%601.Result%2A> değişkenin bağlı olması gerekmez ve değilse doğrulama hatasına neden olmaz. Değeri iş akışında başka bir yerde <xref:System.Activities.Activity%601.Result%2A> kullanılıyorsa, iş akışı yazarının sorumluluğundadır.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Kök Etkinliği Üzerinde Gerekli Bağımsız Değişkenleri Doğrulama  
 Bir iş akışının kök etkinliğinin bağımsız değişkenleri varsa, iş akışı çağrılana ve parametreler iş akışına geçirilene kadar bunlar bağlı değildir. Aşağıdaki iş akışı doğrulamageçer, ancak aşağıdaki örnekte gösterildiği gibi, iş akışı gerekli bağımsız değişkenleri geçmeden çağrılırsa bir özel durum atılır.  
  
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
**İş akışı tanımını düzeltin veya bu hataları düzeltmek için giriş değerlerini tedarik edin:**
 **'Ekle': Gerekli etkinlik bağımsız değişkeni 'Operand2' için değer sağlanamadı.** 
 **'Ekle': Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer verilmedi.**  Doğru bağımsız değişkenler geçirildikten sonra, aşağıdaki örnekte gösterildiği gibi iş akışı başarıyla tamamlanır.  
  
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
> Bu örnekte, kök etkinliği `Add` önceki `Activity` örnekte olduğu gibi yerine olarak bildirildi. Bu, `WorkflowInvoker.Invoke` yöntemin bağımsız değişkenler sözlüğü yerine `Add` etkinliğin sonuçlarını temsil eden `out` tek bir tamsayı döndürmesine olanak tanır. Değişken `wf` de . `Activity<int>`  
  
 Kök bağımsız değişkenleri doğrularken, iş akışı çağrıldığında gerekli tüm bağımsız değişkenlerin geçirilmesini sağlamak ana bilgisayar uygulamasının sorumluluğundadır.  
  
### <a name="invoking-imperative-code-based-validation"></a>Zorunlu Kod Tabanlı Doğrulama'yı çağırmak

Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol <xref:System.Activities.CodeActivity>sağlar <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity>, ve . Etkinlikte herhangi bir doğrulama hatası veya uyarıyı belirleyen doğrulama kodu eklenir. Etkinlikte doğrulama çağrıldığı zaman, bu uyarılar veya hatalar çağrı tarafından döndürülen <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>koleksiyonda bulunur. Aşağıdaki örnekte, `CreateProduct` bir etkinlik tanımlanır. Geçersiz `Cost` kılmadaki meta verilere <xref:System.Activities.CodeActivity.CacheMetadata%2A> bir doğrulama hatası eklenir. `Price`  
  
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
  
 Bu örnekte, iş akışı `CreateProduct` etkinlik kullanılarak yapılandırılır. Bu iş akışında, `Cost` `Price`'den büyüktür `Description` ve gerekli bağımsız değişken ayarlanmaz. Doğrulama çağrıldığında, aşağıdaki hatalar döndürülür.  
  
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
  
 **Hata: Maliyet, Fiyattan daha az veya eşit olmalıdır.**  
**Hata: Gerekli bir etkinlik bağımsız değişkeni 'Açıklama' için değer sağlanmadı.**
> [!NOTE]
> Özel etkinlik yazarları, bir etkinliğin <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılınmasında doğrulama mantığı sağlayabilir. Atılan <xref:System.Activities.CodeActivity.CacheMetadata%2A> tüm özel durumlar doğrulama hatası olarak kabul edilmez. Bu özel durumlar aramadan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> kaçar ve arayan tarafından ele alınmalıdır.  
  
## <a name="using-validationsettings"></a>Doğrulama Ayarlarını Kullanma  
 Varsayılan olarak, doğrulama tarafından <xref:System.Activities.Validation.ActivityValidationServices>çağrıldığızaman etkinlik ağacındaki tüm etkinlikler değerlendirilir. <xref:System.Activities.Validation.ValidationSettings>üç özelliğini yapılandırarak doğrulamanın birkaç farklı şekilde özelleştirilebilmesine olanak tanır. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>doğrulayıcının tüm etkinlik ağacında yürümesi mi yoksa yalnızca sağlanan faaliyete doğrulama mantığı uygulayıp uygulamaması gerektiğini belirtir. Bu değer için `false`varsayılan değer. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir türden kısıtlamalar listesine ek kısıtlama eşleme belirtir. Doğrulanan etkinlik ağacındaki her etkinliğin temel türü için <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir arama vardır. Eşleşen bir kısıtlama listesi bulunursa, listedeki tüm kısıtlamalar etkinlik için değerlendirilir. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>validatörün tüm kısıtlamaları mı yoksa yalnızca .'de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>belirtilenleri mi değerlendirmesini gerektiğini belirtir. Varsayılan değer: `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> iş akışı ana bilgisayar yazarları için fxCop gibi araçlar için ilke kısıtlamaları gibi iş akışları için ek doğrulama eklemek için yararlıdır. Kısıtlamalar hakkında daha fazla bilgi için [bildirimsel kısıtlamalara](declarative-constraints.md)bakın.  
  
 Kullanmak <xref:System.Activities.Validation.ValidationSettings>için, istenilen özellikleri yapılandırın ve sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>çağrıda geçirin. Bu örnekte, özel <xref:System.Activities.Statements.Sequence> `Add` bir etkinlik içeren bir iş akışı doğrulanır. Etkinlik `Add` iki gerekli bağımsız değişkenleri vardır.  
  
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
  
 Aşağıdaki `Add` etkinlik bir <xref:System.Activities.Statements.Sequence>, ancak iki gerekli bağımsız değişkenleri bağlı değildir kullanılır.  
  
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
  
 Aşağıdaki örnekiçin, doğrulama kümesi <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> ile `true`gerçekleştirilir , böylece <xref:System.Activities.Statements.Sequence> yalnızca kök etkinliği doğrulanır.  
  
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
  
 **Uyarı veya hata yok** `Add` Etkinlik bağlı olmayan bağımsız değişkenler gerektirmiş olsa da, yalnızca kök etkinlik değerlendirildiği için doğrulama başarılı olur. Bu doğrulama türü, bir tasarımcıdaki tek bir etkinliğin özellik değişikliğinin doğrulanması gibi bir etkinlik ağacındaki yalnızca belirli öğeleri doğrulamak için yararlıdır. Bu iş akışı çağrılması durumunda, iş akışında yapılandırılan tam doğrulamanın <xref:System.Activities.InvalidWorkflowException> değerlendirildiğini ve bir atılacağını unutmayın. <xref:System.Activities.Validation.ActivityValidationServices>ve <xref:System.Activities.Validation.ValidationSettings> yalnızca iş akışı çağrıldığı zaman oluşan doğrulamayı değil, yalnızca ana bilgisayar tarafından açıkça çağrılan doğrulamayı yapılandırın.
