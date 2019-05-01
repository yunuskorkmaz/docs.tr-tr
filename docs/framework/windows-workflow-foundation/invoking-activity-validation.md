---
title: Etkinlik Doğrulamayı Çağırma
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 19c2d4773cf15245ba20ff8523ebd7e67d5b9c1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791085"
---
# <a name="invoking-activity-validation"></a>Etkinlik Doğrulamayı Çağırma
Etkinlik doğrulamayı yürütme öncesi herhangi bir etkinliğe ilişkin yapılandırma hataları bildirmek üzere bir yöntem sağlar. Bir iş akışı iş akışı Tasarımcısı'nda değiştirilir ve herhangi bir doğrulama hataları veya uyarıları iş akışı Tasarımcısı'nda görüntülenen doğrulama gerçekleşir. Doğrulama iş akışı çağrıldığında ve herhangi bir doğrulama hatası meydana gelirse, çalışma zamanında da oluşur bir <xref:System.Activities.InvalidWorkflowException> varsayılan Doğrulama mantığı tarafından oluşturulur. Windows Workflow Foundation (WF) sağlayan <xref:System.Activities.Validation.ActivityValidationServices> sınıfı açıkça bir etkinlik doğrulamak için iş akışı uygulaması ve araç geliştiricileri tarafından kullanılabilir. Bu konu nasıl kullanılacağını açıklar <xref:System.Activities.Validation.ActivityValidationServices> etkinlik doğrulamayı gerçekleştirmek için.  
  
## <a name="using-activityvalidationservices"></a>ActivityValidationServices kullanma  
 <xref:System.Activities.Validation.ActivityValidationServices> iki <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> etkinliğin Doğrulama mantığı çağırmak için kullanılan aşırı yüklemeleri. İlk aşırı yükleme doğrulanması için Kök etkinlik alır ve doğrulama hataları ve Uyarıları koleksiyonunu döndürür. Aşağıdaki örnekte, özel bir `Add` etkinliği, iki bağımsız değişkenler zorunludur kullanılır.  
  
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
  
 `Add` Etkinliği içinde kullanılan bir <xref:System.Activities.Statements.Sequence>, ancak, iki bağımsız değişken bağlamasından, aşağıdaki örnekte gösterildiği gibi gerekli.  
  
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
  
 Bu iş akışı çağırarak doğrulanabilir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Aşağıdaki örnekte gösterildiği gibi herhangi bir doğrulama hataları veya uyarıları etkinliği ve bir alt öğesi tarafından bulunan bir koleksiyonunu döndürür.  
  
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
  
 Zaman <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Bu örnek iş akışında, iki doğrulama hataları döndürülür çağrılır.  
  
 **Hata: Povinný argument 'İşlenen2' için değer sağlanmadı.**  
**Hata: Povinný argument 'İşlenen1' için değer sağlanmadı.**  Bu iş akışı çağrıldı, bir <xref:System.Activities.InvalidWorkflowException> , aşağıdaki örnekte gösterildiği gibi durum.  
  
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
**İş akışı ağaç işlenirken şu hatalarla karşılaşıldı:**   
**'Add': Povinný argument 'İşlenen2' için değer sağlanmadı.**   
**'Add': Povinný argument 'İşlenen1' için değer sağlanmadı.**  Geçerli olması Bu örnek iş akışı için iki gerekli bağımsız değişkenleri `Add` etkinlik bağlı olmalıdır. Aşağıdaki örnekte, iki bağımsız değişken sonuç değeri yanı sıra iş akışı değişkenlerini bağlı gereklidir. Bu örnekte <xref:System.Activities.Activity%601.Result%2A> iki gerekli bağımsız değişkenler yanı sıra bağlı bağımsız değişken. <xref:System.Activities.Activity%601.Result%2A> Bağımsız değişkeni bağlanması için gerekli değildir ve bu durumda bir doğrulama hatası neden olmaz. Bağlamak için iş akışı Yazar sorumluluğundadır <xref:System.Activities.Activity%601.Result%2A> değerinin iş akışında başka bir yerde kullanılıyorsa.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Kök etkinlik bağımsız değişkenlerini doğrulanıyor  
 Bir iş akışının Kök etkinlik bağımsız değişkenleri yoksa bu parametreleri iş akışına geçirilir ve iş akışı çağrılan kadar bağlı değildir. Aşağıdaki iş akışı doğrulama başarılı, ancak iş akışını gerekli bağımsız değişkenler olarak geçirme olmadan çağrılırsa aşağıdaki örnekte gösterildiği gibi bir özel durum oluşturulur.  
  
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
  
 **System.ArgumentException: Kök etkinlik bağımsız değişkeni ayarları hatalı olabilir.**  
**İş akışı tanımını düzeltin ya da bu hataları düzeltmek için giriş değerleri sağlayın:**   
**'Add': Povinný argument 'İşlenen2' için değer sağlanmadı.**   
**'Add': Povinný argument 'İşlenen1' için değer sağlanmadı.**  İş akışı başarıyla aşağıdaki örnekte gösterildiği gibi doğru bağımsız değişkenleri geçirilir sonra tamamlar.  
  
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
> Bu örnekte, kök etkinlik olarak bildirildi `Add` yerine `Activity` önceki örnekte olduğu gibi. Böylece `WorkflowInvoker.Invoke` sonuçlarını temsil eden tek bir tamsayı döndürülmesini yöntemi `Add` sözlüğü yerine etkinlik `out` bağımsız değişkenler. Değişken `wf` ayrıca olarak bildirilmiş `Activity<int>`.  
  
 Kök bağımsız değişkenleri doğrulanırken, gerekli tüm iş akışı çağrıldığında bağımsız değişkenler geçirilir emin olmak için konak uygulamanın sorumluluğundadır.  
  
### <a name="invoking-imperative-code-based-validation"></a>Kesin kod temelli doğrulama çağırma

Kesin kod temelli doğrulama doğrulama kendisi hakkında sağlamaya bir etkinlik için basit bir yol sağlar ve türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Herhangi bir doğrulama hataları veya uyarıları belirleyen bir doğrulama kodu etkinliğe eklenir. Doğrulama etkinliği çağrıldığında, bu uyarı veya hata çağrısı tarafından döndürülen bir koleksiyonda bulunan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Aşağıdaki örnekte, bir `CreateProduct` etkinlik tanımlanır. Varsa `Cost` büyüktür `Price`, meta verilerde bir doğrulama hatası eklenir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar.  
  
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
  
 Bu örnekte, bir iş akışı kullanılarak yapılandırılan `CreateProduct` etkinlik. Bu iş akışında `Cost` büyüktür `Price`ve gerekli `Description` bağımsız değişken ayarlanmaz. Doğrulama çağrıldığında, aşağıdaki hatalar döndürülür.  
  
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
  
 **Hata: Maliyet fiyat eşit veya daha az olmalıdır.**  
**Hata: Povinný argument 'Description' için değer sağlanmadı.**    
> [!NOTE]
>  Özel Etkinlik yazarlar, etkinliğin Doğrulama mantığı sağlayabilir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar. Şuradan oluşturulduğu özel durumları <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hataları değerlendirilir. Bu özel durumlar çağrısından kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından ele alınması gerekir.  
  
## <a name="using-validationsettings"></a>ValidationSettings kullanma  
 Varsayılan olarak, tüm etkinlikler etkinliğin ağacında değerlendirilir, bu doğrulama tarafından çağrıldığında <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings> doğrulamanın birkaç farklı yolla üç özelliklerini yapılandırarak özelleştirilmesine olanak tanır. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Doğrulayıcı veya tüm etkinlik ağaçta yürüyebilir yalnızca sağlanan etkinliği Doğrulama mantığı uygulama belirtir. Bu değer için varsayılan değer `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> bir tür ek kısıtlaması eşleme kısıtlamalar listesini belirtir. Doğrulanmakta olan etkinlik ağacında her bir etkinlik temel tür yok bir arama <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Eşleşen bir sınırlama listesi bulunursa, listedeki tüm kısıtlamalar etkinliği için değerlendirilir. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Doğrulayıcı tüm kısıtlamalar değerlendirmelidir ya da yalnızca belirtilen belirtir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Varsayılan değer `false` şeklindedir. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> ilke kısıtlamaları FxCop gibi araçları gibi iş akışları için ek doğrulama eklemek iş akışı konak yazarları için kullanışlıdır. Kısıtlamaları hakkında daha fazla bilgi için bkz: [bildirim temelli kısıtlamalar](declarative-constraints.md).  
  
 Kullanılacak <xref:System.Activities.Validation.ValidationSettings>istenen özelliklerini yapılandırmak ve çağrıda geçirmek <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Bu örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> özel ile `Add` etkinlik doğrulandı. `Add` Etkinliğinde iki gerekli bağımsız değişken.  
  
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
  
 Aşağıdaki `Add` etkinlik kullanılan bir <xref:System.Activities.Statements.Sequence>, ancak, iki bağımsız değişken bağlı değil zorunlu.  
  
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
  
 Aşağıdaki örnek için doğrulama ile gerçekleştirilir <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> kümesine `true`, bu nedenle yalnızca kök <xref:System.Activities.Statements.Sequence> etkinlik doğrulandı.  
  
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
  
 Bu kod aşağıdaki çıkışı görüntüler:  
  
 **Uyarı veya hata** olsa bile `Add` etkinliği, bağlı bağımsız değişkenlerin gerekli olan, yalnızca kök etkinlik değerlendirilir olduğundan doğrulama başarılı olur. Bu doğrulama türü, yalnızca belirli bir özellik değişiminin etkinlikten tasarımcıda doğrulama gibi bir etkinlik ağacı öğelerinde doğrulamak için kullanışlıdır. Bu iş akışı çağrılması durumunda iş akışı içinde yapılandırılmış tam doğrulama değerlendirilir dikkat edin ve bir <xref:System.Activities.InvalidWorkflowException> oluşturulması. <xref:System.Activities.Validation.ActivityValidationServices> ve <xref:System.Activities.Validation.ValidationSettings> yalnızca ana bilgisayar tarafından açıkça çağrılan doğrulama ve olmayan bir iş akışı çağrıldığında oluşan doğrulama yapılandırın.
