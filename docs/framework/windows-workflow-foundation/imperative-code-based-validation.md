---
title: Kesin Kod Temelli Doğrulama
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 333e1e200825dd1fc8ed750abbecbb309da66663
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009779"
---
# <a name="imperative-code-based-validation"></a>Kesin Kod Temelli Doğrulama

Kesin kod temelli doğrulama doğrulama kendisi hakkında sağlamaya bir etkinlik için basit bir yol sağlar ve türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Herhangi bir doğrulama hataları veya uyarıları belirleyen bir doğrulama kodu etkinliğe eklenir.  
  
## <a name="using-code-based-validation"></a>Kod temelli doğrulama kullanma

Öğesinden türetilen etkinlikleri tarafından desteklenen kod temelli doğrulama <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Doğrulama kodu yerleştirilebileceğini <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kıl ve doğrulama hataları veya uyarılar, meta veri bağımsız değişkeni eklenebilir. Aşağıdaki örnekte, `Cost` büyüktür `Price`, meta veriler için bir doğrulama hatası eklenir.  
  
> [!NOTE]
> Unutmayın `Cost` ve `Price` etkinlik bağımsız değişkenleri değildir, ancak tasarım zamanında ayarlanır özelliklerdir. Diğer bir deyişle neden değerleri olarak doğrulanabilmesi <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar. Veri çalışma zamanına kadar akışı değil, ancak etkinlik bağımsız değişkenleri doğrulanmış bunlar kullanarak bağlı olmadığından emin olmak için tasarım zamanında bir bağımsız değişken akan veri değeri doğrulanamıyor `RequiredArgument` özniteliği ve grupları aşırı yükleme. Bu kod örneği görür `RequiredArgument` özniteliğini `Description` bağımsız değişken, bağlı değil sonra bir doğrulama hatası oluşturulur. Gerekli bağımsız değişken içinde ele alınmıştır [gerekli bağımsız değişkenler ve aşırı grupları](required-arguments-and-overload-groups.md).  
  
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
  
 Bir iş akışı iş akışı Tasarımcısı'nda değiştirilir ve herhangi bir doğrulama hataları veya uyarıları iş akışı Tasarımcısı'nda görüntülenen doğrulama gerçekleşir. Doğrulama iş akışı çağrıldığında ve herhangi bir doğrulama hatası meydana gelirse, çalışma zamanında da oluşur bir <xref:System.Activities.InvalidWorkflowException> varsayılan Doğrulama mantığı tarafından oluşturulur. Doğrulama uyarıları veya hataları erişmek ve doğrulamayı çağırma hakkında daha fazla bilgi için bkz. [etkinlik doğrulamayı çağırma](invoking-activity-validation.md).  
  
 Şuradan oluşturulduğu özel durumları <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hataları değerlendirilir. Bu özel durumlar çağrısından kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından ele alınması gerekir.  
  
 Kod temelli doğrulama kodu içeren etkinlik doğrulamak için yararlıdır, ancak diğer etkinliklere görünürlük iş akışı içinde yok. Bildirim temelli kısıtlamalar doğrulama etkinlik diğer etkinlikler iş akışı ile arasındaki ilişkileri validate olanağı sağlar ve ele alınmıştır [bildirim temelli kısıtlamalar](declarative-constraints.md) konu.
