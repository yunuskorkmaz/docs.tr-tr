---
title: Kesin kod temelli doğrulama
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: ac77132e3469bdffa6f88f8c6d617c6faa1c9323
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308298"
---
# <a name="imperative-code-based-validation"></a>Kesin kod temelli doğrulama

Kesin kod temelli doğrulama doğrulama kendisi hakkında sağlamaya bir etkinlik için basit bir yol sağlar ve türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Herhangi bir doğrulama hataları veya uyarıları belirleyen bir doğrulama kodu etkinliğe eklenir.  
  
## <a name="using-code-based-validation"></a>Kod temelli doğrulama kullanma

Öğesinden türetilen etkinlikleri tarafından desteklenen kod temelli doğrulama <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Doğrulama kodu yerleştirilebileceğini <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kıl ve doğrulama hataları veya uyarılar, meta veri bağımsız değişkeni eklenebilir. Aşağıdaki örnekte, `Cost` büyüktür `Price`, meta veriler için bir doğrulama hatası eklenir.  
  
> [!NOTE]
> Unutmayın `Cost` ve `Price` etkinlik bağımsız değişkenleri değildir, ancak tasarım zamanında ayarlanır özelliklerdir. Diğer bir deyişle neden değerleri olarak doğrulanabilmesi <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar. Veri çalışma zamanına kadar akışı değil, ancak etkinlik bağımsız değişkenleri doğrulanmış bunlar kullanarak bağlı olmadığından emin olmak için tasarım zamanında bir bağımsız değişken akan veri değeri doğrulanamıyor `RequiredArgument` özniteliği ve grupları aşırı yükleme. Bu kod örneği görür `RequiredArgument` özniteliğini `Description` bağımsız değişken, bağlı değil sonra bir doğrulama hatası oluşturulur. Gerekli bağımsız değişken içinde ele alınmıştır [gerekli bağımsız değişkenler ve aşırı grupları](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).  
  
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
  
 Varsayılan olarak, meta veriler için bir doğrulama hatası eklenir, <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> çağrılır. Doğrulama uyarısı eklemek için <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> alan aşırı yüklemesini bir <xref:System.Activities.Validation.ValidationError>, belirleyen <xref:System.Activities.Validation.ValidationError> ayarlayarak bir uyarı temsil <xref:System.Activities.Validation.ValidationError.IsWarning%2A> özelliği.  
  
 Bir iş akışı iş akışı Tasarımcısı'nda değiştirilir ve herhangi bir doğrulama hataları veya uyarıları iş akışı Tasarımcısı'nda görüntülenen doğrulama gerçekleşir. Doğrulama iş akışı çağrıldığında ve herhangi bir doğrulama hatası meydana gelirse, çalışma zamanında da oluşur bir <xref:System.Activities.InvalidWorkflowException> varsayılan Doğrulama mantığı tarafından oluşturulur. Doğrulama uyarıları veya hataları erişmek ve doğrulamayı çağırma hakkında daha fazla bilgi için bkz. [etkinlik doğrulamayı çağırma](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
 Şuradan oluşturulduğu özel durumları <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hataları değerlendirilir. Bu özel durumlar çağrısından kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından ele alınması gerekir.  
  
 Kod temelli doğrulama kodu içeren etkinlik doğrulamak için yararlıdır, ancak diğer etkinliklere görünürlük iş akışı içinde yok. Bildirim temelli kısıtlamalar doğrulama etkinlik diğer etkinlikler iş akışı ile arasındaki ilişkileri validate olanağı sağlar ve ele alınmıştır [bildirim temelli kısıtlamalar](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) konu.
