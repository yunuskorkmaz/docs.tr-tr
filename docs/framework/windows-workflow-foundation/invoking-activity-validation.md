---
title: "Etkinlik doğrulama çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 752137d5e917e22d5c24e78b45714db1fa06b2a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="invoking-activity-validation"></a>Etkinlik doğrulama çağırma
Etkinlik doğrulama tanımlamak ve yürütülmesinin önce herhangi bir etkinliğe ilişkin yapılandırma hataları rapor için bir yöntem sağlar. Bir iş akışı iş akışı Tasarımcısı'nda değiştirilir ve herhangi bir doğrulama hata veya uyarı iş akışı Tasarımcısı'nda görüntülenen doğrulama oluşur. Doğrulama da ortaya çıkar çalışma zamanında bir iş akışı çalıştırıldığında ve herhangi bir doğrulama hatası oluşursa, bir <xref:System.Activities.InvalidWorkflowException> varsayılan Doğrulama mantığı tarafından oluşturulur. [!INCLUDE[wf](../../../includes/wf-md.md)]sağlar <xref:System.Activities.Validation.ActivityValidationServices> iş akışı uygulaması ve araç geliştiriciler tarafından açıkça bir etkinlik doğrulamak için kullanılabilir sınıfı. Bu konuda nasıl kullanılacağını açıklar <xref:System.Activities.Validation.ActivityValidationServices> etkinlik doğrulama gerçekleştirmek için.  
  
## <a name="using-activityvalidationservices"></a>ActivityValidationServices kullanma  
 <xref:System.Activities.Validation.ActivityValidationServices>iki sahip <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> bir etkinliğin doğrulama mantığını çağırmak için kullanılan aşırı. İlk aşırı doğrulanması için Kök etkinlik alır ve doğrulama hataları ve Uyarıları koleksiyonunu döndürür. Aşağıdaki örnekte, özel bir `Add` etkinlik, iki bağımsız değişken gerekli olduğunu kullanılır.  
  
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
  
 `Add` Etkinlik içinde kullanılan bir <xref:System.Activities.Statements.Sequence>, ancak kendi iki bağımsız değişken değil bağlı, aşağıdaki örnekte gösterildiği gibi gerekli.  
  
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
  
 Bu iş akışı çağırarak doğrulanabilir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Aşağıdaki örnekte gösterildiği gibi herhangi bir doğrulama hataları veya etkinlik ve herhangi bir alt tarafından bulunan uyarıları koleksiyonunu döndürür.  
  
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
  
 Zaman <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Bu örnek iş akışında, iki doğrulama hataları döndürülür olarak adlandırılır.  
  
 **Hata: Gerekli etkinlik bağımsız değişkeni 'Operand2' için değer girilmedi.**  
**Hata: Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer girilmedi.**  Bu iş akışı çağrıldı, bir <xref:System.Activities.InvalidWorkflowException> , aşağıdaki örnekte gösterildiği gibi durum.  
  
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
**'Add': gerekli etkinlik bağımsız değişkeni 'Operand2' sağlanmamış olan için bir değer.**   
**'Add': gerekli etkinlik bağımsız değişkeni 'Operand1' sağlanmamış olan için bir değer.**  Geçerli olması Bu örnek için iş akışı, iki gerekli bağımsız `Add` etkinlik bağlı olmalıdır. Aşağıdaki örnekte, iki bağımsız değişken sonuç değeri yanı sıra iş akışı değişkenleri bağlı gereklidir. Bu örnekte <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni ile birlikte iki gerekli bağımsız bağlı. <xref:System.Activities.Activity%601.Result%2A> Bağımsız değişkeni bağlanması için gerekli değildir ve değilse bir doğrulama hatası neden olmaz. Bağlamak için iş akışı yazarı sorumluluğundadır <xref:System.Activities.Activity%601.Result%2A> akışında değerini başka bir yerde kullandıysanız.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Kök etkinlikte gerekli bağımsız doğrulanıyor  
 Bir iş akışının Kök etkinlik bağımsız değişkenlere sahiptir, bu iş akışı çağrılır ve parametreleri iş akışına geçirilir kadar bağlı değildir. Aşağıdaki iş akışı doğrulama başarılı olur, ancak iş akışı gerekli bağımsız değişkenleri geçirme olmadan çağrılırsa aşağıdaki örnekte gösterildiği gibi bir özel durum oluşturulur.  
  
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
  
 **System.ArgumentException: Kök etkinliğin bağımsız değişkeni ayarları hatalı olabilir.**  
**İş akışı tanımını düzeltin ya da bu hataları düzeltmek için giriş değerleri girin:**   
**'Add': gerekli etkinlik bağımsız değişkeni 'Operand2' sağlanmamış olan için bir değer.**   
**'Add': gerekli etkinlik bağımsız değişkeni 'Operand1' sağlanmamış olan için bir değer.**  Doğru bağımsız değişken geçirildi sonra iş akışını başarıyla, aşağıdaki örnekte gösterildiği gibi tamamlar.  
  
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
>  Bu örnekte, kök etkinlik olarak bildirildi `Add` yerine `Activity` önceki örnekte olduğu gibi. Böylece `WorkflowInvoker.Invoke` sonuçlarını temsil eden tek bir tamsayı döndürülmesini yöntemi `Add` sözlüğü yerine etkinlik `out` bağımsız değişkenler. Değişkeni `wf` de olarak bildirilmiş `Activity<int>`.  
  
 Bu kök bağımsız değişkenleri doğrularken gerekli tüm bağımsız değişkenler iş akışı çağrıldığında geçirildiğinden emin olmak için konak uygulamanın sorumluluğundadır.  
  
### <a name="invoking-imperative-code-based-validation"></a>Kesinlik temelli kod tabanlı doğrulama çağırma  
 Kesinlik temelli kod tabanlı doğrulama kendisi hakkında doğrulama sağlamak bir etkinlik için basit bir yol sağlar ve türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Herhangi bir doğrulama hata veya uyarı belirler doğrulama kodunu aktivite eklenir. Doğrulama etkinliği çağrıldığında, bu uyarılar veya hatalar çağrısı tarafından döndürülen koleksiyon bulunan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Aşağıdaki örnekte, geçen [temel doğrulama](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) örnek, bir `CreateProduct` etkinlik tanımlanır. Varsa `Cost` değerinden daha büyük `Price`, meta verilerde bir doğrulama hatası eklenir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar.  
  
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
  
 Bu örnekte, bir iş akışı kullanarak yapılandırılır `CreateProduct` etkinlik. Bu iş akışındaki `Cost` değerinden daha büyük `Price`ve gerekli `Description` bağımsız değişkeni ayarlı değil. Doğrulama çağrıldığında, aşağıdaki hata döndürülür.  
  
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
**Hata: Gerekli etkinlik bağımsız değişkeni 'Description' için değer girilmedi.**    
> [!NOTE]
>  Özel Etkinlik yazarları bir etkinliğin Doğrulama mantığı sağlayabilir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar. Öğesinden oluşturulan özel durumlar <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hata olarak kabul edilmediği. Bu özel durumlar için çağrısından kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından yapılması gerekir.  
  
## <a name="using-validationsettings"></a>ValidationSettings kullanma  
 Doğrulama tarafından çağrıldığında varsayılan olarak, tüm etkinlikleri ve etkinlik ağacında değerlendirilir <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings>birçok farklı yöntemle üç özelliklerini yapılandırarak özelleştirilmek üzere doğrulama sağlar. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>Doğrulayıcı veya tüm etkinlik ağaç yol yalnızca sağlanan etkinlik için doğrulama mantığını uygulamak belirtir. Bu değer için varsayılan değer `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>Ek kısıtlama eşlemeye türünden kısıtlamalar listesini belirtir. Her etkinlik Doğrulanmakta olan etkinlik ağacında temel tür yok içine bir arama <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Eşleşen bir sınırlama listesi bulunursa, listedeki tüm kısıtlamalar etkinliği için değerlendirilir. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Doğrulayıcı tüm kısıtlamalar değerlendirmelidir ya da yalnızca belirtilen belirtir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Varsayılan değer `false` şeklindedir. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>ve <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> FxCop gibi araçları için ilke kısıtlamaları gibi iş akışları için ek doğrulama eklemek iş akışı ana yazarları için faydalıdır. [!INCLUDE[crabout](../../../includes/crabout-md.md)]kısıtlamaları bkz [bildirim temelli kısıtlamaları](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).  
  
 Kullanılacak <xref:System.Activities.Validation.ValidationSettings>, istenen özelliklerini yapılandırmak ve çağrısında geçirmek <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Bu örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.Sequence> özel ile `Add` etkinlik doğrulandı. `Add` Etkinlik iki gerekli bağımsız değişkeni vardır.  
  
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
  
 Aşağıdaki `Add` etkinlik kullanılıyor bir <xref:System.Activities.Statements.Sequence>, ancak kendi iki bağımsız değişken bağlı olmayan gerekli.  
  
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
  
 Aşağıdaki örneğin ile doğrulandığını <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> kümesine `true`, bu nedenle yalnızca kök <xref:System.Activities.Statements.Sequence> etkinlik doğrulandı.  
  
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
  
 Bu kod, aşağıdaki çıkış görüntüler:  
  
 **Herhangi bir uyarı veya hata** olsa bile `Add` etkinlik bağlı olmayan bağımsız değişkenler gerekli, yalnızca kök etkinlik değerlendirildiğinden doğrulama başarılı olur. Bu doğrulama türü, yalnızca belirli öğeleri özellik değişikliği bir Tasarımcısı'nda tek bir etkinliğin doğrulanması gibi bir etkinlik ağacında doğrulamak için kullanışlıdır. Bu iş akışı çağrılırsa iş akışı içinde yapılandırılmış tam doğrulama değerlendirilir unutmayın ve bir <xref:System.Activities.InvalidWorkflowException> durum. <xref:System.Activities.Validation.ActivityValidationServices>ve <xref:System.Activities.Validation.ValidationSettings> yalnızca ana bilgisayar tarafından açıkça çağrılan doğrulama ve olmayan iş akışı çağrıldığında oluşan doğrulama yapılandırın.
